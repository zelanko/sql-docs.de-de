---
title: Erweiterung der R-Programmiersprache
description: Erfahren Sie mehr über die Ausführung von r-Code und integrierte r-Bibliotheken in SQL Server 2016 R Services oder SQL Server 2017 Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 300b5d25d62be24c1e5590f5cd9795d08da7f2c1
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470499"
---
# <a name="r-language-extension-in-sql-server"></a>R-Spracherweiterung in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die R-Erweiterung ist Teil des SQL Server Machine Learning Services-Add-on der relationalen Datenbank-Engine. Dabei wird eine r-Ausführungsumgebung, eine Basis-r-Verteilung mit Standardbibliotheken und-Tools und die Microsoft R-Bibliotheken hinzugefügt: [Revoscaler](../r/ref-r-revoscaler.md) für Analysen in der Skala, [microsoftml](../r/ref-r-microsoftml.md) für Machine Learning-Algorithmen und andere Bibliotheken für den Zugriff auf Daten oder R-Code in SQL Server.

Die Integration von r ist in SQL Server ab SQL Server 2016 mit [r Services](../r/sql-server-r-services.md)verfügbar und wird im Rahmen [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)fortgesetzt.

## <a name="r-components"></a>R-Komponenten

SQL Server enthält sowohl Open Source-als auch proprietäre Pakete. Die Basis-r-Bibliotheken werden über die Microsoft-Distribution von Open Source-r installiert: Microsoft R Open (MRO). Aktuelle Benutzer von r sollten in der Lage sein, ihren R-Code zu portieren und ihn als externen Prozess auf SQL Server mit wenigen oder gar keinen Änderungen auszuführen. MRO wird unabhängig von SQL-Tools installiert und außerhalb der Kern-Engine-Prozesse im Erweiterbarkeits Framework ausgeführt. Während der Installation müssen Sie den Bedingungen der Open-Source-Lizenz zustimmen. Anschließend können Sie Standard-R-Pakete ohne weitere Änderung ausführen, genauso wie bei jeder anderen Open-Source-Distribution von r. 

SQL Server ändert die ausführbaren r-Basisdateien nicht, aber Sie müssen die Version von r verwenden, die vom-Setup installiert wird, da diese Version die Version ist, auf der die proprietären Pakete erstellt und getestet werden. Weitere Informationen über die Unterschiede zwischen MRO und der basisverteilung von R, die Sie möglicherweise von CRAN erhalten, finden Sie unter [Interoperabilität mit r-Sprache und Microsoft r-Produkte und-Funktionen](https://docs.microsoft.com/r-server/what-is-r-server-interoperability).

Die vom-Setup installierte R-Basispaket Verteilung befindet sich im Ordner, der der-Instanz zugeordnet ist. Wenn Sie z. b. r Services auf einer SQL Server 2016-Standard Instanz installiert haben, befinden sich die r-Bibliotheken standardmäßig `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`in diesem Ordner:. Ebenso befinden sich die R-Tools, die der Standard Instanz zugeordnet sind, standardmäßig `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin`in diesem Ordner.

R-Pakete, die von Microsoft für parallele und verteilte Workloads hinzugefügt wurden, umfassen die folgenden Bibliotheken.

| Library | Beschreibung |
|---------|-------------|
| [**RevoScaleR**](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | Unterstützt Datenquellen Objekte sowie das Durchsuchen, manipulieren, Transformieren und Visualisieren von Daten. Es unterstützt die Erstellung von remotecomputekontexten sowie verschiedene skalierbare Machine Learning-Modelle, wie z. **b. rxlinmod**. Die APIs wurden optimiert, um Datensätze zu analysieren, die zu groß sind, um in den Arbeitsspeicher zu passen und Berechnungen über mehrere Kerne oder Prozessoren verteilt auszuführen. Das revoscaler-Paket unterstützt auch das Xdf-Dateiformat zum schnelleren verschieben und Speichern von Daten, die für die Analyse verwendet werden. Das XDF-Format verwendet die spaltenweise Speicherung, ist übertragbar und kann zum Laden und anschließend zum Ändern der Daten aus verschiedenen Quellen, z.B. Text, SPSS oder eine ODBC-Verbindung verwendet werden. |
| [**MicrosoftML**](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package) | Enthält Machine Learning-Algorithmen, die für Geschwindigkeit und Genauigkeit optimiert wurden, sowie Inline Transformationen zum Arbeiten mit Text und Bildern. Weitere Informationen finden Sie unter [microsoftml in SQL Server](../r/ref-r-microsoftml.md). | 

## <a name="using-r-in-sql-server"></a>Verwenden von R in SQL Server

Sie können Skripts für R mithilfe von Basisfunktionen erstellen, aber um von der multiverarbeitung zu profitieren, müssen Sie die **revoscaler** -und **microsoftml** -Module in ihren R-Code importieren und anschließend die zugehörigen Funktionen zum Erstellen von Modellen, die parallel ausgeführt werden, aufzurufen. 
 
Zu den unterstützten Datenquellen gehören ODBC-Datenbanken, SQL Server und das Xdf-Dateiformat zum Austauschen von Daten mit anderen Quellen oder R-Lösungen. Eingabedaten müssen tabellarisch sein. Alle R-Ergebnisse müssen in Form eines Daten Rahmens zurückgegeben werden.

Unterstützte computekontexte sind lokale oder Remote SQL Server computekontext. Ein remotecomputekontext bezieht sich auf die Codeausführung, die auf einem Computer (z. b. einer Arbeitsstation) gestartet wird, die Skriptausführung jedoch auf einen Remote Computer schaltet. Zum Wechseln des computekontexts muss beide Systeme dieselbe revoscaler-Bibliothek aufweisen.

Der lokale computekontext umfasst erwartungsgemäß die Ausführung von R-Code auf demselben Server wie die Datenbank-Engine-Instanz, mit Code in T-SQL oder eingebettet in eine gespeicherte Prozedur. Sie können den Code auch über eine lokale R-IDE ausführen und das Skript auf dem SQL Server Computer ausführen lassen, indem Sie einen remotecomputekontext definieren.

## <a name="execution-architecture"></a>Ausführungs Architektur

Die folgenden Diagramme zeigen die Interaktion von SQL Server-Komponenten mit der r-Laufzeit in jedem der unterstützten Szenarien: Ausführen von Skripts in der Datenbank und Remote Ausführung über eine R-Befehlszeile mithilfe eines SQL Server computekontexts.

### <a name="r-scripts-executed-from-sql-server-in-database"></a>R-Skripts, die von SQL Server in-Database

R-Code, der von "innerhalb" SQL Server ausgeführt wird, wird durch Aufrufen einer gespeicherten Prozedur ausgeführt. Daher kann jede Anwendung, die eine gespeicherte Prozedur aufrufen kann, die Ausführung von R-Code initiieren.  Danach verwaltet SQL Server die Ausführung von R-Code, wie im folgenden Diagramm zusammengefasst.

![rsql_indb780-01](../r/media/script_in-db-r.png)

1. Eine Anforderung für die R-Laufzeit wird vom Parameter _@language='R'_ indiziert, der an die gespeicherte Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) übergeben wird. SQL Server sendet diese Anforderung an den Launchpad-Dienst.
2. Der Launchpad-Dienst startet das entsprechende Startprogramm; In diesem Fall „RLauncher“.
3. RLauncher startet den externen Prozess von R.
4. Bxlserver koordiniert mit der R-Laufzeit, um den Austausch von Daten mit SQL Server und der Speicherung von Arbeitsergebnissen zu verwalten.
5. Der SQL-Satellit verwaltet die Kommunikation über verwandte Aufgaben und Prozesse mit SQL Server.
6. Bxlserver verwendet den SQL-Satelliten, um den Status und die Ergebnisse SQL Server zu übermitteln.
7. SQL Server ruft Ergebnisse ab und schließt Verwandte Aufgaben und Prozesse.

### <a name="r-scripts-executed-from-a-remote-client"></a>Von einem Remoteclient ausgeführte R-Skripts

Beim Herstellen einer Verbindung von einem Remote Data Science Client, der Microsoft R unterstützt, können Sie R-Funktionen im Kontext von SQL Server ausführen, indem Sie die revoscaler-Funktionen verwenden. Dieser Workflow unterscheidet sich vom vorherigen und wird im folgenden Diagramm zusammengefasst.

![rsql_fromR2db-01](../r/media/remote-sqlcc-from-r2.png)

1. Für revoscaler-Funktionen ruft die R-Laufzeit eine Verknüpfungs Funktion auf, die wiederum bxlserver aufruft.
2. BxlServer wird in Microsoft R und in einem separaten Prozess von der R-Laufzeit bereitgestellt.
3. BxlServer bestimmt das Verbindungsziel und initiiert eine Verbindung mithilfe von ODBC, wobei Anmeldeinformationen, die als Teil der Verbindungszeichenfolge im R-Datenquellenprojekt bereitgestellt werden, übergeben werden.
4. Bxlserver öffnet eine Verbindung mit der SQL Server Instanz.
5. Bei einem R-Aufruf wird der Launchpad-Dienst aufgerufen, der wiederum das entsprechende Start Programm startet, rlauncher. Die Verarbeitung von R-Code ähnelt dem Vorgang, R-Code von T-SQL auszuführen.
6. Rlauncher Ruft die Instanz der R-Laufzeit auf, die auf dem SQL Server Computer installiert ist.
7. Ergebnisse werden an BxlServer zurückgegeben.
8. Der SQL-Satellit verwaltet die Kommunikation mit SQL Server und Bereinigung verwandter Auftrags Objekte.
9. SQL Server übergibt die Ergebnisse an den Client zurück.

## <a name="see-also"></a>Siehe auch

+ [Erweiterbarkeits Framework in SQL Server](extensibility-framework.md)
+ [Python-und Machine Learning-Erweiterungen in SQL Server](extension-python.md)