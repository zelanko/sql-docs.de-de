---
title: Konvertieren von R-Code für gespeicherte Prozeduren
description: Migrieren Sie R-Code zu einer SQL Server gespeicherten Prozedur für die Lösungs Bereitstellung und den Datenzugriff auf relationale Daten auf SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 713c5cc8de5daecec77ff984a22f85b220ece2a2
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251341"
---
# <a name="convert-r-code-for-execution-in-sql-server-in-database-instances"></a>Konvertieren von R-Code für die Ausführung in SQL Server Instanzen (in der Datenbank)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel enthält allgemeine Anleitungen zum Ändern von R-Code für die Arbeit in SQL Server. 

Wenn Sie r-Code aus r Studio oder einer anderen Umgebung in SQL Server verschieben, funktioniert der Code meistens ohne weitere Änderung: z. b. wenn der Code einfach ist, z. b. eine Funktion, die einige Eingaben annimmt und einen Wert zurückgibt. Es ist auch einfacher, Lösungen zu portieren, die die **revoscaler** -oder **microsoftml** -Pakete verwenden, die die Ausführung in verschiedenen Ausführungs Kontexten mit minimalen Änderungen unterstützen.

Der Code erfordert jedoch möglicherweise wesentliche Änderungen, wenn eine der folgenden Bedingungen zutrifft:

+ Sie verwenden R-Bibliotheken, die auf das Netzwerk zugreifen oder auf SQL Server nicht installiert werden können.
+ Der Code führt getrennte Aufrufe von Datenquellen außerhalb SQL Server aus, z. b. Excel-Arbeitsblätter, Dateien auf Freigaben und andere Datenbanken. 
+ Sie möchten den Code im *\@script-* Parameter von [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) ausführen und die gespeicherte Prozedur ebenfalls parametrisieren.
+ Die ursprüngliche Lösung umfasst mehrere Schritte, die in einer Produktionsumgebung effizienter sein können, wenn Sie unabhängig ausgeführt werden, wie z. b. Daten Vorbereitung oder Featureentwicklung im Vergleich zu Modell Schulungen,-Bewertungen oder-Berichten.
+ Sie möchten die Leistungsoptimierung verbessern, indem Sie Bibliotheken ändern, eine parallele Ausführung verwenden oder einige Verarbeitungsvorgänge auf SQL Server verlagern. 

## <a name="step-1-plan-requirements-and-resources"></a>Schritt 1: Planen von Anforderungen und Ressourcen

**Pakete**

+ Bestimmen Sie, welche Pakete benötigt werden, und stellen Sie sicher, dass Sie auf SQL Server funktionieren.
 
+ Installieren Sie Pakete vorab in der von Machine Learning Services verwendeten Standardpaket Bibliothek. Benutzer Bibliotheken werden nicht unterstützt.

**Datenquellen** 

+ Wenn Sie Ihren R-Code in [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)einbetten möchten, identifizieren Sie primäre und sekundäre Datenquellen. 

    + **Primäre** Datenquellen sind große Datasets, wie z. b. Modell Trainingsdaten oder Eingabedaten für Vorhersagen. Planen Sie, das größte DataSet dem Eingabeparameter von [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)zuzuordnen.

    + **Sekundäre** Datenquellen sind in der Regel kleinere Datasets, wie z. b. Listen von Faktoren oder zusätzliche Gruppierungs Variablen. 
    
    Derzeit unterstützt sp_execute_external_script nur ein einzelnes Dataset als Eingabe für die gespeicherte Prozedur. Sie können jedoch mehrere skalare oder binäre Eingaben hinzufügen.

    Aufrufe gespeicherter Prozeduren, denen Execute vorangestellt ist, können nicht als Eingabe für [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)verwendet werden. Sie können Abfragen, Sichten oder eine beliebige andere gültige SELECT-Anweisung verwenden.

+ Bestimmen Sie die benötigten Ausgaben. Wenn Sie R-Code mithilfe von sp_execute_external_script ausführen, kann die gespeicherte Prozedur als Ergebnis nur einen Datenrahmen ausgeben. Sie können jedoch auch mehrere skalare Ausgaben ausgeben, einschließlich Plots und Modelle im Binärformat, sowie andere skalare Werte, die von R-Code oder SQL-Parametern abgeleitet werden.

**Datentypen**

+ Stellen Sie eine Prüfliste der möglichen Probleme bei Datentypen zusammen.

    Alle R-Datentypen werden von SQL Server Machine Learning-Diensten unterstützt. Allerdings unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine größere Vielfalt von Datentypen als R. Daher werden einige implizite Datentyp Konvertierungen beim Senden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Daten an R und umgekehrt ausgeführt. Möglicherweise müssen Sie einige Daten explizit umwandeln oder konvertieren. 

    NULL-Werte werden unterstützt. Allerdings verwendet R das `na`-Daten Konstrukt, um einen fehlenden Wert darzustellen, der einem NULL-Wert ähnelt.

+ Entfernen Sie die Abhängigkeit von Daten, die von r nicht verwendet werden können. beispielsweise können ROWID-und GUID-Datentypen aus SQL Server nicht von r genutzt werden und Fehler generieren.

    Weitere Informationen finden Sie unter [R-Bibliotheken und-Datentypen](../r/r-libraries-and-data-types.md).

## <a name="step-2-convert-or-repackage-code"></a>Schritt 2: Code konvertieren oder neu verpacken

Wie viel Sie Ihren Code ändern, hängt davon ab, ob Sie den R-Code von einem Remote Client zur Ausführung im SQL Server computekontext übermitteln möchten, oder ob der Code als Teil einer gespeicherten Prozedur bereitgestellt werden soll, wodurch eine bessere Leistung und Datensicherheit erzielt werden kann. Wenn Sie Ihren Code in eine gespeicherte Prozedur Umpacken, werden einige zusätzliche Anforderungen auferlegt. 

+ Definieren Sie möglichst die primären Eingabedaten als SQL-Abfrage, um Daten Verschiebungen zu vermeiden.

+ Wenn Sie R in einer gespeicherten Prozedur ausführen, können Sie mehrere **skalare** Eingaben durchlaufen. Fügen Sie für alle Parameter, die Sie in der Ausgabe verwenden möchten, das **Output** -Schlüsselwort hinzu. 

    Beispielsweise enthält die folgende skalare Eingabe `@model_name` den Modellnamen, der auch in der eigenen Spalte in den Ergebnissen ausgegeben wird:

    ```sql
    EXEC sp_execute_external_script @model_name="DefaultModel" OUTPUT, @language=N'R', @script=N'R code here'
    ``` 

+ Alle Variablen, die Sie als Parameter der gespeicherten Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) übergeben, müssen Variablen im R-Code zugeordnet werden. Standardmäßig werden die Variablen nach Namen zugeordnet.

    Alle Spalten im Eingabe DataSet müssen auch Variablen im R-Skript zugeordnet werden.  Nehmen Sie beispielsweise an, das R-Skript enthält eine Formel wie die folgende:

    ```R
    formula <- ArrDelay ~ CRSDepTime + DayOfWeek + CRSDepHour:DayOfWeek
    ```
    
    Wenn das Eingabe DataSet keine Spalten mit den übereinstimmenden Namen arrdelay, crsdeptime, DayOfWeek, crsdephour und DayOfWeek enthält, wird ein Fehler ausgelöst.

+ In einigen Fällen muss ein Ausgabe Schema für die Ergebnisse im Voraus definiert werden.

    Wenn Sie z. b. die Daten in eine Tabelle einfügen möchten, müssen Sie die **with Result Set** -Klausel verwenden, um das Schema anzugeben.

    Das Ausgabe Schema ist auch erforderlich, wenn das R-Skript das Argument `@parallel=1` verwendet. Grund hierfür ist, dass mehrere Prozesse von SQL Server zum Ausführen der Abfrage möglicherweise parallel erstellt und die Ergebnisse am Ende gesammelten werden. Daher muss das Ausgabe Schema vorbereitet werden, bevor die parallelen Prozesse erstellt werden können.
    
    In anderen Fällen können Sie das Ergebnis Schema unterdrücken, indem Sie die-Option **mit nicht definierten Resultsets**verwenden. Diese Anweisung gibt das DataSet aus dem R-Skript zurück, ohne die Spalten zu benennen oder die SQL-Datentypen anzugeben.

+ Ziehen Sie in Erwägung, Zeit-oder Überwachungsdaten mit T-SQL anstelle von R zu erzeugen.

    Beispielsweise können Sie die Systemzeit oder andere Informationen, die für die Überwachung und Speicherung verwendet werden, übergeben, indem Sie einen T-SQL-Aufruf hinzufügen, der an die Ergebnisse weitergeleitet wird, anstatt ähnliche Daten im R-Skript zu erstellen. 

**Verbessern der Leistung und Sicherheit**

+ Schreiben Sie keine Vorhersagen oder Zwischenergebnisse in die Datei. Schreiben Sie stattdessen Vorhersagen in eine Tabelle, um Daten Verschiebungen zu vermeiden.

+ Führen Sie alle Abfragen im Voraus aus, und überprüfen Sie die SQL Server Abfrage Pläne, um Aufgaben zu identifizieren, die parallel ausgeführt werden können.

    Wenn die Eingabe Abfrage parallelisiert werden kann, legen Sie `@parallel=1` als Teil ihrer Argumente auf [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)fest. 

    Eine Parallelverarbeitung mit diesem Flag ist in der Regel jedes Mal möglich, wenn SQL Server mit partitionierten Tabellen arbeiten oder eine Abfrage zwischen mehreren Prozessen verteilen kann und die Ergebnisse am Ende aggregiert. Eine Parallelverarbeitung mit diesem Flag ist nicht möglich, wenn Sie Modelle mithilfe von Algorithmen trainieren, die ein Lesen aller Daten voraussetzen, oder wenn Sie Aggregate erstellen müssen.

+ Überprüfen Sie Ihren R-Code, um Schritte zu identifizieren, die unabhängig oder effizienter ausgeführt werden können, und verwenden Sie dazu einen separat gespeicherten Prozeduraufruf. Beispielsweise können Sie eine bessere Leistung erzielen, indem Sie die Featureentwicklung oder die featureextraktion separat durchgeführt und die Werte in einer Tabelle speichern.

+ Suchen Sie nach Möglichkeiten, T-SQL anstelle von R-Code für Satz basierte Berechnungen zu verwenden.

    Diese R-Lösung zeigt z. b., wie benutzerdefinierte T-SQL-Funktionen und R dieselbe Funktions Entwicklungsaufgabe ausführen können: Exemplarische [Data Science-Ende-zu-Ende-](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)Vorgehensweise.

+ Ersetzen Sie nach Möglichkeit herkömmliche R-Funktionen durch **Scaler** -Funktionen, die die verteilte Ausführung unterstützen. Weitere Informationen finden Sie unter [Vergleich der r-Funktionen der Basis-r und Skalierung](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler-compared-to-base-r).

+ Wenden Sie sich an einen Datenbankentwickler, um Möglichkeiten zum Verbessern der Leistung zu ermitteln, indem Sie SQL Server Features wie [Speicher optimierte Tabellen](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables)verwenden, oder wenn Sie Enterprise Edition [Resource Governor](https://docs.microsoft.com/sql/relational-databases/resource-governor/resource-governor)).

    Weitere Informationen finden Sie unter [SQL Server Optimierungs Tipps und Tricks für Analysedienste](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services) .

### <a name="step-3-prepare-for-deployment"></a>Schritt 3: Vorbereiten der Bereitstellung

+ Benachrichtigen Sie den Administrator, damit Pakete installiert und im Voraus getestet werden, bevor Sie Ihren Code bereitstellen. 

    In einer Entwicklungsumgebung kann es sinnvoll sein, Pakete als Teil Ihres Codes zu installieren, aber dies ist eine bewährte Vorgehensweise in einer Produktionsumgebung. 

    Benutzer Bibliotheken werden nicht unterstützt, unabhängig davon, ob Sie eine gespeicherte Prozedur verwenden oder R-Code im SQL Server computekontext ausführen.

**Verpacken des R-Codes in einer gespeicherten Prozedur**

+ Wenn Ihr Code relativ einfach ist, können Sie ihn ohne Änderung in eine benutzerdefinierte T-SQL-Funktion einbetten, wie in diesen Beispielen beschrieben:

    + [Erstellen einer R-Funktion, die in rxexec ausgeführt wird](../tutorials/deepdive-create-a-simple-simulation.md)
    + [Funktionsentwicklung mit T-SQL und R](../tutorials/sqldev-create-data-features-using-t-sql.md)

+ Wenn der Code komplexer ist, verwenden Sie das R-Paket **sqlrutils** , um den Code zu konvertieren. Dieses Paket ist so konzipiert, dass erfahrene R-Benutzer guten Code für gespeicherte Prozeduren schreiben können. 

    Der erste Schritt besteht darin, ihren R-Code als einzelne Funktion mit klar definierten Eingaben und Ausgaben umzuschreiben.

    Verwenden Sie dann das **sqlrutils** -Paket, um die Eingabe und die Ausgaben im richtigen Format zu generieren. Das **sqlrutils** -Paket generiert den gesamten Code für die gespeicherte Prozedur und kann auch die gespeicherte Prozedur in der-Datenbank registrieren. 

    Weitere Informationen und Beispiele finden Sie unter [sqlrutils (SQL)](ref-r-sqlrutils.md).

**Integrieren in andere Workflows**

+ Nutzen Sie T-SQL-Tools und ETL-Prozesse. Führen Sie die Featureentwicklung, die featureextraktion und die Datenbereinigung im Voraus als Teil von Daten Workflows aus.

    Wenn Sie in einer dedizierten R-Entwicklungsumgebung wie [!INCLUDE[rsql_rtvs_md](../../includes/rsql-rtvs-md.md)] oder rstudio arbeiten, können Sie Daten auf Ihren Computer überführen, iterativ analysieren und dann die Ergebnisse schreiben oder anzeigen. 
    
    Wenn jedoch eigenständiger R-Code zu SQL Server migriert wird, kann ein Großteil dieses Prozesses vereinfacht oder an andere SQL Server Tools delegiert werden. 

+ Verwenden Sie sichere, asynchrone Visualisierungs Strategien.

    Benutzer von SQL Server können häufig nicht auf Dateien auf dem Server zugreifen, und die SQL-Client Tools unterstützen das R-Grafikgerät in der Regel nicht. Wenn Sie Diagramme oder andere Grafiken als Teil der Projekt Mappe generieren, sollten Sie die Plots als Binärdaten exportieren und in einer Tabelle speichern oder schreiben.

+ Umschließen von Vorhersage-und Bewertungs Funktionen in gespeicherten Prozeduren für direkten Zugriff durch Anwendungen.

### <a name="other-resources"></a>Weitere Ressourcen

Beispiele für die Bereitstellung einer R-Lösung in SQL Server finden Sie in den folgenden Beispielen:

+ [Erstellen eines Vorhersagemodells für Ski Rental Business mithilfe von R und SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Daten bankübergreifende Analysen für SQL-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md) Veranschaulicht, wie Sie Ihren R-Code modularer machen können, indem Sie ihn in gespeicherten Prozeduren packen.

+ [End-to-End-Data Science-Lösung](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) Enthält einen Vergleich der Featureentwicklung in R und T-SQL.
