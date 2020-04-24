---
title: R-Spracherweiterung
description: Erfahren Sie mehr über die Ausführung von R-Code und integrierte R-Bibliotheken in SQL Server R Services bzw. SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/04/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c85839d89fbdb2d69752ac989abb40637f9d13ca
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487560"
---
# <a name="r-language-extension-in-sql-server"></a>R-Spracherweiterung in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die R-Erweiterung ist Teil des SQL Server Machine Learning Services-Add-Ons für die relationale Datenbank-Engine. Sie fügt eine R-Ausführungsumgebung, eine Basis-R-Verteilung mit Standardbibliotheken und -tools sowie die Microsoft R-Bibliotheken hinzu: [RevoScaleR](../r/ref-r-revoscaler.md) für skalierte Analysen, [MicrosoftML](../r/ref-r-microsoftml.md) für Algorithmen für maschinelles Lernen sowie andere Bibliotheken für den Zugriff auf Daten oder R-Code in SQL Server.

Die R-Integration ist in [SQL Server R Services](../r/sql-server-r-services.md) und in [SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) verfügbar.

## <a name="r-components"></a>R-Komponenten

SQL Server enthält sowohl Open Source- als auch proprietäre Pakete. Die Basis-R-Bibliotheken werden über die Microsoft-Verteilung von Open Source-R installiert: Microsoft R Open (MRO). Aktuelle Benutzer von R sollten in der Lage sein, ihren R-Code zu portieren und mit wenigen oder keinen Änderungen als externen Prozess auf SQL Server auszuführen. MRO wird unabhängig von SQL-Tools installiert und außerhalb der Kernprozesse der Engine im Erweiterbarkeitsframework ausgeführt. Während der Installation müssen Sie den Bedingungen der Open-Source-Lizenz zustimmen. Anschließend können Sie Standard-R-Pakete ohne weitere Änderungen ausführen, wie Sie es von jeder anderen Open-Source-Verteilung von R gewohnt sind. 

SQL Server ändert die ausführbaren R-Basisdateien nicht, Sie müssen jedoch die Version von R verwenden, die von Setup installiert wird, da auf dieser Version die proprietären Pakete erstellt und getestet werden. Weitere Informationen über die Unterschiede zwischen MRO und einer Basisverteilung von R, die Sie möglicherweise von CRAN erhalten, finden Sie unter [Interoperabilität mit R-Sprache und Microsoft R-Produkten und-Funktionen](https://docs.microsoft.com/r-server/what-is-r-server-interoperability).

Die von Setup installierte R-Basispaketverteilung befindet sich in dem der Instanz zugeordneten Ordner. Wenn Sie beispielsweise R Services auf einer SQL Server-Standardinstanz installiert haben, befinden sich die R-Bibliotheken standardmäßig in diesem Ordner: `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`. Entsprechend befinden sich die mit der Standardinstanz verknüpften R-Tools standardmäßig in folgendem Ordner: `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin`.

R-Pakete, die von Microsoft für parallele und verteilte Workloads hinzugefügt wurden, umfassen die folgenden Bibliotheken.

| Bibliothek | BESCHREIBUNG |
|---------|-------------|
| [**RevoScaleR**](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | Unterstützt Datenquellenobjekte sowie die Exploration, Manipulation, Transformation und Visualisierung von Daten. Unterstützt die Erstellung von Remotecomputekontexten sowie verschiedene skalierbare Machine Learning-Modelle wie **rxLinMod**. Die APIs wurden optimiert, um Datensätze zu analysieren, die zu groß sind, um in den Arbeitsspeicher zu passen und Berechnungen über mehrere Kerne oder Prozessoren verteilt auszuführen. Das RevoScaleR-Paket unterstützt auch das XDF-Dateiformat für schnellere Verschiebungen und die Speicherung von Daten, die für die Analyse verwendet werden. Das XDF-Format verwendet die spaltenweise Speicherung, ist übertragbar und kann zum Laden und anschließend zum Ändern der Daten aus verschiedenen Quellen, z.B. Text, SPSS oder eine ODBC-Verbindung verwendet werden. |
| [**MicrosoftML**](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package) | Enthält Algorithmen für das maschinelle Lernen, die hinsichtlich Geschwindigkeit und Genauigkeit optimiert wurden, sowie Inline-Transformationen für die Arbeit mit Text und Bildern. Weitere Informationen finden Sie unter [MicrosoftML in SQL Server](../r/ref-r-microsoftml.md). | 

## <a name="using-r-in-sql-server"></a>Verwenden von R in SQL Server

Sie können Skripts für R mithilfe von Basisfunktionen erstellen, um jedoch von Multiprocessing zu profitieren, müssen Sie die Module **RevoScaleR** und **MicrosoftML** in Ihren R-Code importieren und anschließend deren Funktionen aufrufen, um parallel ausgeführte Modelle zu erstellen. 
 
Unterstützte Datenquellen sind ODBC-Datenbanken, SQL Server und das XDF-Dateiformat, um Daten mit anderen Quellen oder mit R-Lösungen auszutauschen. Eingabedaten müssen tabellarisch sein. Alle R-Ergebnisse müssen in Form eines Datenrahmens zurückgegeben werden.

Unterstützte Computekontexte sind lokale oder SQL Server-Remotecomputekontexte. Ein Remotecomputekontext bezieht sich auf die Codeausführung, die auf einem Computer (beispielsweise einer Arbeitsstation) beginnt, aber dann die Skriptausführung auf einen Remotecomputer schaltet. Zum Wechseln des Computekontexts müssen beide Systeme dieselbe RevoScaleR-Bibliothek aufweisen.

Ein lokaler Computekontext umfasst naturgemäß die Ausführung von R-Code auf demselben Server wie die Instanz der Datenbank-Engine, wobei sich der Code in T-SQL befindet oder in eine gespeicherte Prozedur eingebettet ist. Sie können den Code auch aus einer lokalen R-IDE ausführen und das Skript auf dem SQL Server-Computer ausführen lassen, indem Sie einen Remotecomputekontext definieren.

## <a name="execution-architecture"></a>Ausführungsarchitektur

Die folgenden Diagramme zeigen die Interaktion von SQL Server-Komponenten mit der R-Runtime in jedem der unterstützten Szenarios: datenbankinternes Ausführen von Skripts und Remoteausführung von einer R-Befehlszeile aus unter Verwendung eines SQL Server-Computekontexts.

### <a name="r-scripts-executed-from-sql-server-in-database"></a>R-Skripts, die von SQL Server datenbankintern ausgeführt werden

R-Code, der „innerhalb“ von SQL Server ausgeführt wird, wird durch das Aufrufen einer gespeicherten Prozedur ausgeführt. Daher kann jede Anwendung, die eine gespeicherte Prozedur aufrufen kann, die Ausführung von R-Code initiieren.  Anschließend verwaltet SQL Server die Ausführung von R-Code, wie dies im folgenden Diagramm gezeigt wird.

![rsql_indb780-01](../r/media/script_in-db-r.png)

1. Eine Anforderung für die R-Laufzeit wird vom Parameter _@language='R'_ indiziert, der an die gespeicherte Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) übergeben wird. SQL Server sendet diese Anforderung an den Launchpad-Dienst.
Unter Linux verwendet SQL einen **launchpadd**-Dienst, um mit einem separaten Launchpad-Prozess für jeden Benutzer zu kommunizieren. Ausführliche Informationen finden Sie im [Diagramm zur Erweiterbarkeitsarchitektur](extensibility-framework.md#architecture-diagram).
2. Der Launchpad-Dienst startet das entsprechende Startprogramm, in diesem Fall RLauncher.
3. RLauncher startet den externen Prozess von R.
4. BxlServer koordiniert mit der R-Runtime, um den Datenaustausch mit SQL Server und die Speicherung von Arbeitsergebnissen zu verwalten.
5. SQL Satellite verwaltet die Kommunikation über zugehörige Aufgaben und Prozesse mit SQL Server.
6. BxlServer verwendet SQL Satellite, um Status und Ergebnisse an SQL Server zu übermitteln.
7. SQL Server ruft die Ergebnisse ab und schließt zugehörige Aufgaben und Prozesse.

### <a name="r-scripts-executed-from-a-remote-client"></a>Von einem Remoteclient ausgeführte R-Skripts

Wenn Sie eine Verbindung von einem Remote-Data Science-Client herstellen, der Microsoft R unterstützt, können Sie R-Funktionen im Kontext von SQL Server durch Verwenden der RevoScaleR-Funktionen ausführen. Dieser Workflow unterscheidet sich vom vorherigen und wird im folgenden Diagramm zusammengefasst.

![rsql_fromR2db-01](../r/media/remote-sqlcc-from-r2.png)

1. Die R-Runtime ruft für RevoScaleR-Funktionen eine Verknüpfungsfunktion auf, die wiederum BxlServer aufruft.
2. BxlServer wird in Microsoft R und in einem separaten Prozess von der R-Laufzeit bereitgestellt.
3. BxlServer bestimmt das Verbindungsziel und initiiert eine Verbindung mithilfe von ODBC, wobei Anmeldeinformationen, die als Teil der Verbindungszeichenfolge im R-Datenquellenprojekt bereitgestellt werden, übergeben werden.
4. BxlServer öffnet eine Verbindung mit der SQL Server-Instanz.
5. Für einen R-Aufruf wird der Launchpad-Dienst aufgerufen, der wiederum das erforderliche Startprogramm, RLauncher, startet. Die Verarbeitung von R-Code ähnelt dem Vorgang, R-Code von T-SQL auszuführen.
6. RLauncher ruft die Instanz der R-Runtime ab, die auf dem SQL Server-Computer gespeichert ist.
7. Ergebnisse werden an BxlServer zurückgegeben.
8. SQL Satellite verwaltet die Kommunikation mit SQL Server sowie die Bereinigung zugehöriger Auftragsobjekte.
9. SQL Server gibt die Ergebnisse an den Client zurück.

## <a name="see-also"></a>Weitere Informationen

+ [Erweiterbarkeitsframework in SQL Server](extensibility-framework.md)
+ [Python- und Machine Learning-Erweiterungen in SQL Server](extension-python.md)