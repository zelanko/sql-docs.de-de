---
title: R-spracherweiterung – SQL Server-Machine Learning-Programmierung
description: Informationen Sie zur Ausführung von R-Code und integrierte R-Bibliotheken in SQL Server 2016 R Services oder SQL Server 2017-Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: cb9b710ca5ec06e05a93dbee5f22ee0860f7f4ca
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432763"
---
# <a name="r-language-extension-in-sql-server"></a>Erweiterung der Sprache R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Die R-Erweiterung ist Teil der SQL Server Machine Learning Services-Add-On der relationalen Datenbank-Engine. Fügt eine ausführungsumgebung für R, basisverteilung von R mit standard-Bibliotheken und Tools, und die Microsoft R-Bibliotheken: [RevoScaleR](../r/ref-r-revoscaler.md) für Analysen im größeren Umfang und [MicrosoftML](../r/ref-r-microsoftml.md) für Machine Learning-Algorithmen und anderen Bibliotheken für den Zugriff auf Daten oder R-Code in SQL Server.

R-Integration ist in SQL Server ab SQL Server 2016 verfügbar [R Services](../r/sql-server-r-services.md), und als Teil des weiterleiten [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md).

## <a name="r-components"></a>R-Komponenten

SQL Server umfasst sowohl Open Source- und proprietären Pakete. R-Basisbibliotheken werden über die Microsoft-Distribution von Open-Source-r installiert. Microsoft R Open (MRO). Aktuelle Benutzer von R sollten in der Lage, ihren R-Code portieren, und führen Sie es als externer Prozess auf SQL Server mit nur wenigen oder ohne Änderungen. MRO ist unabhängig von der SQL-Tools installiert, und außerhalb der Kern-Engine-Prozesse, in dem Extensibility Framework ausgeführt wird. Während der Installation müssen Sie die Bedingungen der Open-Source-Lizenz zustimmen. Danach können Sie standard-R-Pakete ohne weitere Änderung ausführen wie in anderen Open-Source-Distribution von r 

SQL Server ändert sich nicht auf der Basis ausführbaren R-Dateien, aber Sie müssen die Version von R, die von Setup installiert werden, da diese Version der ist, dass der proprietären Pakete erstellt und getestet verwenden. Weitere Informationen dazu, wie MRO eine basisverteilung von R unterscheidet, die Sie vom CRAN erhalten können, finden Sie unter [Interoperabilität mit R-Sprache und Microsoft R-Produkte und Funktionen](https://docs.microsoft.com/r-server/what-is-r-server-interoperability).

Die R-Basispaket-Verteilung von Setup installiert finden Sie in den Ordner mit der Instanz verknüpft ist. Z. B. Wenn Sie auf einer Standardinstanz von SQL Server 2016 R Services installiert haben, die R-Bibliotheken befinden sich in diesem Ordner werden standardmäßig: `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`. Auf ähnliche Weise verknüpft ist, mit der Standardinstanz von R Tools befindet sich in diesem Ordner werden standardmäßig: `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin`.

R-Pakete, die von Microsoft für parallelen und verteilten Workloads hinzugefügt enthalten die folgenden Bibliotheken.

| Bibliothek | Description |
|---------|-------------|
| [**RevoScaleR**](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | Unterstützt von Datenquellenobjekten und Durchsuchen von Daten, Manipulation, Transformation und Visualisierung. Es unterstützt die Erstellung von remotecomputekontexte sowie verschiedene skalierbare Machine Learning-Modellen wie z. B. **RxLinMod**. Die APIs wurden optimiert, um Datensätze zu analysieren, die zu groß sind, um in den Arbeitsspeicher zu passen und Berechnungen über mehrere Kerne oder Prozessoren verteilt auszuführen. Das RevoScaleR-Paket unterstützt auch das XDF-Dateiformat für schnellere Bewegungen und Speicherung von Daten, die für die Analyse verwendet. Das XDF-Format verwendet die spaltenweise Speicherung, ist übertragbar und kann zum Laden und anschließend zum Ändern der Daten aus verschiedenen Quellen, z.B. Text, SPSS oder eine ODBC-Verbindung verwendet werden. |
| [**MicrosoftML**](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package) | Enthält die Machine Learning-Algorithmen, die wurden optimiert Geschwindigkeit und Genauigkeit als auch Inline-Transformationen für die Arbeit mit Text und Bilder. Weitere Informationen finden Sie unter [MicrosoftML in SQL Server](../r/ref-r-microsoftml.md). | 

## <a name="using-r-in-sql-server"></a>Verwenden von R in SQLServer

Sie können Skripts für R, die mit grundlegenden Funktionen, aber um von Multi-Processing profitieren zu können, müssen Sie importieren die **RevoScaleR** und **MicrosoftML** Module in Ihre R-Code, und rufen Sie dann die Funktionen zum Erstellen modelliert, parallel ausgeführt. 
 
Unterstützte Datenquellen umfassen die ODBC-Datenbanken, SQL Server und einer XDF-Datei-Format zum Austauschen von Daten mit anderen Datenquellen oder mit R-Lösungen. Eingabedaten müssen tabellarische sein. Alle R-Ergebnisse müssen in Form von einem Datenrahmen zurückgegeben werden.

Unterstützte computekontexte umfassen lokal oder remote SQL Server-computekontext. Ein remotecomputekontext bezieht sich auf die Ausführung von Code, der auf einem Computer, z. B. eine Arbeitsstation beginnt, aber dann Switches der skriptausführung auf einem Remotecomputer befindet. Wechseln den computekontext erfordert, dass beide Systeme die gleiche RevoScaleR-Bibliothek.

Lokalen computekontext zu erwarten, umfasst die Ausführung von R-Code auf dem gleichen Server wie die Datenbank-Engine-Instanz, mit Code in T-SQL oder in einer gespeicherten Prozedur eingebettet. Sie können auch führen Sie den Code von einer lokalen R-IDE und das Skript auf dem SQL Server-Computer ausgeführt werden, durch die Definition einer Remote-computekontext.

## <a name="execution-architecture"></a>Ausführung-Architektur

Die folgenden Diagramme stellen die Interaktion des SQL Server-Komponenten mit der R-Laufzeitumgebung in jeder der unterstützten Szenarien: Ausführung des Skripts in der Datenbank und remote über eine R-Befehlszeile, mit einem SQL Server-computekontext ausgeführt.

### <a name="r-scripts-executed-from-sql-server-in-database"></a>R-Skripts, die von SQL Server in-Database ausgeführt

R-Code, der in "Inside" SQL Server ausgeführt wird, durch den Aufruf einer gespeicherten Prozedur ausgeführt wird. Daher kann jede Anwendung, die eine gespeicherte Prozedur aufrufen kann, die Ausführung von R-Code initiieren.  SQL Server verwaltet anschließend die Ausführung von R-Code wie im folgenden Diagramm zusammengefasst.

![rsql_indb780-01](../r/media/script_in-db-r.png)

1. Eine Anforderung für die R-Laufzeit wird vom Parameter _@language='R'_ indiziert, der an die gespeicherte Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) übergeben wird. SQL-Server sendet diese Anforderung an den Launchpad-Dienst.
2. Der Launchpad-Dienst startet das entsprechende Startprogramm; In diesem Fall „RLauncher“.
3. RLauncher startet den externen Prozess von R.
4. BxlServer koordiniert mit der R-Laufzeit, um den Austausch von Daten mit SQL Server und Speicherung von Arbeitsergebnissen zu verwalten.
5. SQL-Satellit verwaltet die Kommunikation über verwandte Aufgaben und Prozesse mit SQL Server.
6. BxlServer verwendet SQL-Satellit zum Status und Ergebnisse an SQL Server zu kommunizieren.
7. SQL Server ruft die Ergebnisse ab und schließt Verwandte Aufgaben und Prozesse.

### <a name="r-scripts-executed-from-a-remote-client"></a>Von einem Remoteclient ausgeführte R-Skripts

Wenn aus einem Data Science-Remoteclient eine Verbindung herstellen, die von Microsoft R unterstützt, können Sie R-Funktionen im Kontext von SQL Server ausführen, mithilfe der RevoScaleR-Funktionen. Dieser Workflow unterscheidet sich vom vorherigen und wird im folgenden Diagramm zusammengefasst.

![rsql_fromR2db-01](../r/media/remote-sqlcc-from-r2.png)

1. Für die RevoScaleR-Funktionen Ruft die R-Laufzeit eine Verknüpfungsfunktion wiederum BxlServer aufruft.
2. BxlServer wird in Microsoft R und in einem separaten Prozess von der R-Laufzeit bereitgestellt.
3. BxlServer bestimmt das Verbindungsziel und initiiert eine Verbindung mithilfe von ODBC, wobei Anmeldeinformationen, die als Teil der Verbindungszeichenfolge im R-Datenquellenprojekt bereitgestellt werden, übergeben werden.
4. BxlServer öffnet eine Verbindung mit SQL Server-Instanz.
5. Für einen R-Aufruf, der Launchpad-Dienst aufgerufen wird, mit die ist startet des erforderliche Startprogramms, RLauncher. Die Verarbeitung von R-Code ähnelt dem Vorgang, R-Code von T-SQL auszuführen.
6. "Rlauncher" Ruft die Instanz des R-Laufzeitmoduls, die auf dem SQL Server-Computer installiert ist.
7. Ergebnisse werden an BxlServer zurückgegeben.
8. SQL-Satellit verwaltet die Kommunikation mit SQL Server und die Bereinigung verwandter Auftragsobjekte.
9. SQL Server übergibt die Ergebnisse an den Client zurück.

## <a name="see-also"></a>Siehe auch

+ [Extensibility Framework im SQL Server](extensibility-framework.md)
+ [Python und Machine learning-Erweiterungen in SQL Server](extension-python.md)