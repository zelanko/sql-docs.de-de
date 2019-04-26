---
title: Konvertieren von R-Code für gespeicherte Prozeduren – SQL Server Machine Learning Services
description: Migrieren Sie R-Code an eine gespeicherte SQL Server-Prozedur für die Lösung und den Zugriff auf relationale Daten in SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: a3348058b03ff1441256cc8298ddc1b5b2216b0d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642788"
---
# <a name="convert-r-code-for-execution-in-sql-server-in-database-instances"></a>Konvertieren von R-Code für die Ausführung in Instanzen von SQL Server (Datenbankintern)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel enthält die Anleitung auf hoher Ebene zum Ändern von R-Code in SQL Server funktionieren. 

Wenn Sie R-Code von R Studio oder einer anderen Umgebung mit SQL Server verschieben, meistens funktioniert der Code ohne weitere Änderung: z. B. wenn der Code einfach ist, z. B. eine Funktion, die einige akzeptiert Eingaben und gibt einen Wert zurück. Es ist auch einfacher, Port-Lösungen, in denen die **RevoScaleR** oder **MicrosoftML** -Pakete, die Ausführung in unterschiedliche Ausführungskontexte mit minimalen Änderungen zu unterstützen.

Erfordert jedoch möglicherweise der Code wesentliche Änderungen, wenn eine der folgenden Bedingungen zutrifft:

+ Sie verwenden die R-Bibliotheken, die auf das Netzwerk zugreifen, oder, kann nicht auf SQL Server installiert werden.
+ Der Code führt separate Aufrufe von Datenquellen außerhalb von SQL Server, wie z. B. Excel-Arbeitsblättern, Dateien auf Dateifreigaben und anderen Datenbanken. 
+ Sie möchten, um den Code auszuführen, der *@script* Parameter der [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) und auch die gespeicherte Prozedur zu parametrisieren.
+ Die ursprüngliche Projektmappe umfasst mehrere Schritte, die möglicherweise eine effizientere in einer produktionsumgebung, wenn z. B. die Vorbereitung der Daten oder Feature-Entwicklung im Vergleich zu Modell trainieren, bewerten und berichterstellung unabhängig voneinander ausgeführt.
+ Sie verbessern möchten Optimieren der Leistung von Bibliotheken zu ändern, verwenden die parallele Ausführung oder eine Verarbeitung mit SQL Server-Abladung. 

## <a name="step-1-plan-requirements-and-resources"></a>Schritt 1: Planen der Anforderungen und Ressourcen

**Pakete**

+ Ermitteln, welche Pakete benötigt werden, und stellen Sie sicher, dass sie auf SQL Server funktionieren.
 
+ Installieren von Paketen im Voraus auf den Standard-paketbibliothek, die von Machine Learning-Dienste verwendet. Benutzerbibliotheken werden nicht unterstützt.

**Datenquellen** 

+ Wenn Sie beabsichtigen, betten Sie Ihre R-Code in [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), identifizieren Sie primäre und sekundäre Datenquellen. 

    + **Primäre** Datenquellen sind große Datasets, z. B. modelltrainingsdaten oder Eingabedaten für Vorhersagen. Ihr größte Dataset an den Eingabeparameter der zuzuordnen möchten [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    + **Sekundäre** Datenquellen sind in der Regel kleiner Datenmengen verwendet werden, z. B. Listen mit Faktoren oder weitere gruppierungsvariablen. 
    
    Sp_execute_external_script unterstützt derzeit nur ein einzelnes Dataset als Eingabe für die gespeicherte Prozedur an. Allerdings können Sie auch mehrere skalare oder binäre Eingaben hinzufügen.

    Vor dem Ausführen von gespeicherten Prozeduraufrufen können nicht verwendet werden, als Eingabe für [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Sie können Abfragen, Sichten oder eine andere gültige SELECT-Anweisung verwenden.

+ Bestimmen Sie die Ausgaben, die Sie benötigen. Wenn Sie R-Code mithilfe von Sp_execute_external_script ausführen, kann die gespeicherte Prozedur daher nur einen Datenrahmen ausgeben. Allerdings können Sie auch mehrere skalare Ausgaben, darunter Elemente ausgeben und Modelle im Binärformat als auch andere Skalare Werte, der von R-Code oder SQL Parameter abgeleitet.

**Datentypen**

+ Stellen Sie eine Prüfliste der möglichen Probleme bei Datentypen zusammen.

    Alle R-Datentypen werden von SQL Server Machine Learning-Dienste unterstützt. Allerdings [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt eine größere Vielfalt von Datentypen als R. Aus diesem Grund werden einige implizite datentypkonvertierungen ausgeführt, beim Senden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten an R und umgekehrt. Sie sollten explizit umwandeln oder konvertieren einige Daten. 

    NULL-Werte werden unterstützt. R verwendet jedoch die `na` repositorytypbibliothek zur Darstellung von eines fehlenden Wert, dem ein NULL-Wert ähnelt.

+ Entfernen Sie die Abhängigkeit von Daten, die von r, z. B. Rowid verwendet werden können und GUID-Datentypen von SQL Server können nicht von R verwendet werden und die Fehler generieren.

    Weitere Informationen finden Sie unter [R-Bibliotheken und-Datentypen](../r/r-libraries-and-data-types.md).

## <a name="step-2-convert-or-repackage-code"></a>Schritt 2: Konvertieren oder neu Verpacken von code

Wie viel Sie den Code ändern, hängt davon ab, ob Sie zum Übermitteln von R-Code von einem Remoteclient in den SQL Server-computekontext ausgeführt werden soll, oder möchten den Code als Teil einer gespeicherten Prozedur bereit, die eine bessere Leistung und Sicherheit der Daten bereitstellen können. Umschließen den Code in einer gespeicherten Prozedur stellt einige zusätzlichen Anforderungen. 

+ Definieren Sie Ihre primären Eingabedaten als SQL-Abfrage, wo immer dies möglich ist, um datenverschiebungen zu vermeiden.

+ Bei der Ausführung von R in einer gespeicherten Prozedur können Sie über mehrere übergeben **skalare** Eingaben. Für alle Parameter, die Sie in der Ausgabe verwenden möchten, fügen die **Ausgabe** Schlüsselwort. 

    Z. B. die folgenden skalaren Eingabe `@model_name` enthält der Name des Modells, der auch die Ausgabe in einer eigenen Spalte in den Ergebnissen ist:

    ```sql
    EXEC sp_execute_external_script @model_name="DefaultModel" OUTPUT, @language=N'R', @script=N'R code here'
    ``` 

+ Alle Variablen, die Sie als Parameter der gespeicherten Prozedur übergeben [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) müssen Variablen im R-Code zugeordnet werden. Standardmäßig werden die Variablen nach Namen zugeordnet.

    Alle Spalten im Eingabedataset müssen auch auf Variablen im R-Skript zugeordnet werden.  Nehmen wir beispielsweise an, dass Ihr R-Skript enthält, eine Formel wie diese:

    ```R
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek
    ```
    
    Ein Fehler wird ausgelöst, wenn das Eingabe-Dataset keine Spalten mit den entsprechenden Namen ArrDelay, CRSDepTime, DayOfWeek, CRSDepHour und DayOfWeek enthält.

+ In einigen Fällen muss ein Ausgabeschema im Voraus für die Ergebnisse definiert werden.

    Z. B. um die Daten in eine Tabelle einzufügen, müssen Sie verwenden die **WITH RESULT SET** -Klausel, um das Schema anzugeben.

    Das Ausgabeschema ist auch erforderlich, wenn das R-Skript, das Argument verwendet `@parallel=1`. Grund hierfür ist, dass mehrere Prozesse von SQL Server zum Ausführen der Abfrage möglicherweise parallel erstellt und die Ergebnisse am Ende gesammelten werden. Aus diesem Grund muss das Ausgabeschema vorbereitet werden, bevor die parallelen Prozesse erstellt werden können.
    
    In anderen Fällen können Sie das ergebnisschema weglassen, mit der Option **RESULT SETS UNDEFINED**. Diese Anweisung gibt das Dataset aus dem R-Skript ohne benennen die Spalten oder Angeben der SQL-Datentypen zurück.

+ Erwägen Sie die Generierung der zeitlichen Steuerung oder Tracking-Daten, die mithilfe von T-SQL anstelle von r

    Beispielsweise könnten Sie übergeben die Systemzeit oder andere Informationen, die für die Überwachung und -Speicher verwendet wird, durch Hinzufügen eines T-SQL-Aufrufs, das auf die Ergebnisse durchlaufen, anstatt die ähnliche Daten im R-Skript generieren. 

**Verbessern der Leistung und Sicherheit**

+ Vermeiden Sie vorhersagen oder Zwischenergebnisse in eine Datei schreiben. Schreiben Sie vorhersagen stattdessen in eine Tabelle, um datenverschiebungen zu vermeiden.

+ Führen Sie alle Abfragen im voraus, und überprüfen Sie die SQL Server-Abfragepläne, um Aufgaben zu identifizieren, die parallel ausgeführt werden können.

    Wenn die Eingabeabfrage parallelisiert werden kann, legen Sie `@parallel=1` als Teil Ihrer Argumente auf [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). 

    Eine Parallelverarbeitung mit diesem Flag ist in der Regel jedes Mal möglich, wenn SQL Server mit partitionierten Tabellen arbeiten oder eine Abfrage zwischen mehreren Prozessen verteilen kann und die Ergebnisse am Ende aggregiert. Eine Parallelverarbeitung mit diesem Flag ist nicht möglich, wenn Sie Modelle mithilfe von Algorithmen trainieren, die ein Lesen aller Daten voraussetzen, oder wenn Sie Aggregate erstellen müssen.

+ Überprüfen Sie Ihren R-Code, um Schritte zu identifizieren, die unabhängig oder effizienter ausgeführt werden können, und verwenden Sie dazu einen separat gespeicherten Prozeduraufruf. Beispielsweise erhalten Sie möglicherweise eine bessere Leistung durch Featureentwicklung oder featureextraktion getrennt, und speichern die Werte in einer Tabelle.

+ Suchen Sie nach Möglichkeiten zur Verwendung von T-SQL anstelle von R-Code für satzbasierte Berechnungen.

    Beispielsweise diese R-Lösung zeigt, wie eine benutzerdefinierte T-SQL-Funktionen und R kann die gleichen Feature-Entwicklungsaufgabe ausführen: [Exemplarische Data Science End-to-End-Vorgehensweise](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md).

+ Ersetzen Sie nach Möglichkeit konventionelle R-Funktionen mit **ScaleR** Funktionen, die verteilte Ausführung unterstützen. Weitere Informationen finden Sie unter [Vergleich von Basis-R und Scale R-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r).

+ Wenden Sie sich an einem Datenbankentwickler, um zu bestimmen, Möglichkeiten zum Verbessern der Leistung mithilfe von SQL Server-Funktionen wie z. B. [Speicheroptimierte Tabellen](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables), oder, wenn Sie Enterprise Edition verfügen [Resource Governor](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor)).

    Weitere Informationen finden Sie unter [Tipps zur Optimierung von SQL Server und Tricks für die Analytics-Dienste](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

### <a name="step-3-prepare-for-deployment"></a>Schritt 3: Vorbereiten der Bereitstellung

+ Benachrichtigen Sie den Administrator, damit Pakete installiert und im Voraus getestet werden, bevor Sie Ihren Code bereitstellen. 

    In einer Entwicklungsumgebung befindet kann es zum Installieren von Paketen als Teil des Codes kein Problem sein, aber dies ist kein empfehlenswertes Verfahren in einer produktionsumgebung. 

    Benutzerbibliotheken werden nicht unterstützt, unabhängig davon, ob Sie mithilfe einer gespeicherten Prozedur oder R-Code in den SQL Server-computekontext ausgeführt werden.

**Packen Sie Ihren R-Code in einer gespeicherten Prozedur**

+ Wenn Ihr Code relativ einfach ist, können Sie es in einer T-SQL eine benutzerdefinierte Funktion ohne Änderung einbetten, wie in diesen Beispielen beschrieben:

    + [Erstellen Sie eine R-Funktion, die in RxExec ausgeführt wird.](../tutorials/deepdive-create-a-simple-simulation.md)
    + [Entwickeln Sie Features mithilfe von T-SQL und R](../tutorials/sqldev-create-data-features-using-t-sql.md)

+ Wenn der Code komplexer ist, verwenden Sie das R-Paket **Sqlrutils** konvertieren Ihren Code. Dieses Paket dient erfahrene R-Benutzer, die gute gespeicherte Prozedur-Code schreiben zu können. 

    Der erste Schritt besteht, Schreiben Sie Ihren R-Code als eine einzelne Funktion mit klar definierten Eingaben und Ausgaben.

    Verwenden Sie dann die **Sqlrutils** Paket, um das richtige Format der Eingaben und Ausgaben zu generieren. Die **Sqlrutils** Paket Code der Abschluss der gespeicherten Prozedur für Sie generiert und können auch die gespeicherte Prozedur in der Datenbank registrieren. 

    Weitere Informationen und Beispiele finden Sie unter [Sqlrutils (SQL)](ref-r-sqlrutils.md).

**Integrieren in andere workflows**

+ Nutzen Sie T-SQL-Tools und ETL-Prozesse. Führen Sie die Feature-Engineering, featureextraktion und DatenBereinigung als Teil von Datenworkflows mit im voraus.

    Bei der Arbeit in eine dedizierte R-Entwicklungsumgebung wie z. B. [!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)] oder RStudio, Sie können Abrufen von Daten auf Ihrem Computer, iterativ, zu analysieren und und zu schreiben oder die Ergebnisse werden angezeigt. 
    
    Allerdings beim eigenständigen R-Code zu SQL Server migriert wird, kann Großteil dieses Prozesses werden vereinfacht oder an andere SQL Server-Tools delegiert. 

+ Verwenden Sie sichere, asynchrone Visualisierung Strategien.

    Benutzer von SQL Server häufig können nicht auf Dateien auf dem Server zugreifen, und SQL-Clienttools in der Regel nicht unterstützt das R-Grafikgerät. Wenn Sie Diagramme oder andere Grafik als Teil der Lösung generiert haben, sollten Sie Sie exportieren die Diagramme als binäre Daten und das Speichern in einer Tabelle oder schreiben.

+ Umschließen Sie Vorhersage und Bewertung Funktionen in gespeicherten Prozeduren für den direkten Zugriff von Anwendungen.

### <a name="other-resources"></a>Weitere Ressourcen

Beispiele wie eine R-Lösung in SQL Server bereitgestellt werden kann, finden Sie in diesen Beispielen:

+ [Erstellen eines prädiktiven Modells für skiverleih mithilfe von R und SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Datenbankinterne Analysen für SQL-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md) wird verdeutlicht, wie Sie Ihren R-Code etwas modularer durch Einbinden in gespeicherten Prozeduren

+ [End-to-End Data Science-Lösung](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) enthält einen Vergleich der Featureentwicklung in R und T-SQL
