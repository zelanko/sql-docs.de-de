---
title: Richten Sie eine Data Science-Client für die Entwicklung von R auf SQL Server | Microsoft-Dokumentation
description: Installieren Sie die lokale R-Bibliotheken und Tools auf einer entwicklungsworkstation für Remoteverbindungen zur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f88c8d715fabb5af8d1af49c3b39b3aa0734c369
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "40434840"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Einrichten eines Data Science-Clients für die Entwicklung von R auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Nach der Konfiguration einer Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] um Machine Learning zu unterstützen, sollten Sie Einrichten einer R-Entwicklungsumgebung, die eine Verbindung herstellen kann an den Server für die Remoteausführung und Bereitstellung.

### <a name="evaluation-and-independent-development"></a>Evaluierungs- und unabhängige Entwicklung
 
Wenn Sie haben die Developer Edition und der Plan R-Skript lokal arbeiten, die Sie mit SQL Server verschieben möchten, fahren Sie zum [Installieren einer IDE](#install-ide) und zeigen Sie das Tool auf der lokalen R-Bibliotheken, die von SQL Server verwendet.

> [!Tip]
> Eine Demonstration und video zur exemplarischen Vorgehensweise finden Sie [Ausführen von R als auch Remote in SQL Server von Jupyter-Notebooks oder eine beliebige IDE Python](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/) oder [YouTube-Video](https://youtu.be/D5erljpJDjE).

## <a name="1---install-r-packages"></a>1: Installieren von R-Pakete

R-Funktionen in Microsoft-Produkten ist mehreren Ebenen. Es beginnt mit von Microsoft Open Source-Basis-R-Verteilung und wird dann erweitert, mit der Produkt-spezifische Pakete, z. B. [RevoScaleR](revoscaler-overview.md), remoterechenkontexte und parallele Ausführung von R-Aufgaben, mit denen.

Koordinierte Vorgänge zwischen einem Client und einem Remoteserver müssen beide Systeme müssen die gleichen Pakete. Rufen Sie die umfassende Auswahl von Bibliotheken auf einer Clientarbeitsstation installieren Sie eines der Softwarepakete in der folgenden Tabelle aus. 

| Bibliotheksanbieter | Verwendung  |
|------------------|--------------------------------|
| [Microsoft R Client](http://aka.ms/rclient/download) |  Dieser kostenlose Download umfasst RevoScaleR, MicrosoftML und anderen R-Paketen, jedoch höchstens zwei Threads und in-Memory-Daten. Jedoch Sie können immer noch erstellen R-Lösungen, die lokal zu starten, und verschieben Sie die Ausführung (genannt *computekontext*) den Zugriff auf Daten und die rechenleistung von SQL Server-Remoteinstanz. Dies ist die empfohlene Vorgehensweise für die Clientintegration mit einer Produktionsinstanz von SQL Server. Weitere Informationen zu diesem Tool finden Sie unter [neuerungen von Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client).|
| Eigenständige Server | Klicken Sie unter **freigegebene Funktionen**, SQL Server-Setup enthält Optionen für die Installation von eigenständigen Server für SQL Server 2016 R Services und SQL Server 2017-Machine-Learning. Diese sind voll funktionsfähige-Server, die vollständig entkoppelt von SQL Server, mit der Möglichkeit, eine Verbindung herstellen und Daten von mehreren Data-Plattformen verwenden. Aber möglicherweise können die Software in einer Client-Kapazität auf SQL Server-Datenbank-Engine-Instanz Ausführen von R und Python-Aufgaben. [SQL Server 2017 Machine Learning Server (eigenständig)](../install/sql-machine-learning-standalone-windows-install.md) hat die gleichen Bibliotheken als eine SQL Server 2017-Machine Learning-Instanz. [SQL Server 2016 R Server (eigenständig)](../install/sql-r-standalone-windows-install.md) hat die gleiche SQL Server 2016 R Services-Bibliothek. |


<a name="r-tool"></a>
 
## <a name="2---open-an-r-prompt"></a>2: Öffnen Sie eine R-Eingabeaufforderung

Wenn Sie R mit SQL Server installieren, erhalten Sie den gleichen R-Tools, die standardmäßig auf alle Basisinstallation von R, z.B. RGui und Rterm usw. verwendet werden. Diese Tools sind einfache – nützlich zum Überprüfen der Informationen Paket und die Bibliothek, das Ausführen von ad-hoc-Befehle oder eines Skripts oder schrittweise Lernprogramme. Sie können diese Tools verwenden, um R-Versionsinformationen abzurufen, und gewährleisten Sie Konnektivität.

Um die Version von R mit SQL Server oder R-Client installiert verwenden zu können, öffnen Sie eine R-Eingabeaufforderung aus dem SQL Server oder R-Client-Programmordner. Die folgenden Schritte sind für R-Client und RGui.exe.

1. R Client finden Sie unter `~\Program Files\Microsoft\R Client\R_SERVER\bin\x64`.
2. Doppelklicken Sie auf **RGui.exe** um eine R-Sitzung mit einer R-Eingabeaufforderung zu starten.

Wenn Sie eine R-Sitzung aus einem Ordner der Microsoft-Programm starten, werden mehrere Pakete, einschließlich von RevoScaleR, automatisch geladen. Geben Sie **search()** an der R-Eingabeaufforderung zur Bestätigung.

   ![Versionsinformationen, die beim Laden von R](../install/media/rclient-rgui-r-prompt.png "eine R-Eingabeaufforderung öffnen")

### <a name="tool-list-and-location"></a>Toolliste und den Speicherort

| Tool | Description | 
|------|-------------|
| **RTerm**: | Ein befehlszeilenterminal für die Ausführung von R-Skripts | 
| **RGui.exe** | Einen einfachen interaktiven Editor für R. Die Befehlszeilenargumente sind identisch für RGui.exe und RTerm. |
| **RScript** | Ein Befehlszeilenprogramm zum Ausführen von R-Skripts im Batchmodus ausgeführt. |

Befinden sich Tools **Bin** Ordner für die Basis von R als SQL Server installiert oder R Client. Die folgenden Pfade sind die gültigen Speicherorte für die Tools, je nachdem, welche Version des Produkts, die und das Feature Sie installiert:

| Microsoft-Produkt | Speicherort des R-Tools |
|-------------------|-----------------|
| Microsoft R Client | `~\Program Files\Microsoft\R Client\R_SERVER\bin\x64` |
| Microsoft Machine Learning (R)-Server | `~\Program Files\Microsoft\R_SERVER\bin\x64`
| SQL Server 2016 R Services | `~\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64`|
| SQL Server 2016 R eigenständiger Server | `~\Program Files\Microsoft SQL Server\130\R_SERVER\bin\x64` 
| SQL Server 2017-Machine Learning-Dienste von (R) | `~\Program Files\Microsoft SQL Server\MSSQL14.<instancename>\R_SERVICES\bin\x64`|
| SQL Server 2017-Machine Learning (R) eigenständiger Server | `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` |

## <a name="3---permissions"></a>3 - Berechtigungen

Herstellen der Verbindung mit einer Instanz von SQL Server zum Ausführen von Skripts und Daten hochzuladen, müssen Sie eine gültige Anmeldung auf dem Datenbankserver verfügen. Sie können entweder einen SQL-Anmeldenamen oder die integrierte Windows-Authentifizierung verwenden. Im Allgemeinen wird empfohlen, dass Sie die integrierte Windows-Authentifizierung verwenden, mit der SQL-Anmeldung ist jedoch einfacher für einige Szenarien.

Mindestens muss das Konto zum Ausführen von Code verwendet die Berechtigung zum Lesen aus den Datenbanken, mit dem Sie arbeiten, sowie die speziellen Berechtigungen ausgeführt, ANY EXTERNAL SCRIPT haben. Die meisten Entwickler auch benötigen Berechtigungen zum Erstellen neuer Objekte in Form von gespeicherten Prozeduren, die mit Ihrem Skript, und Schreiben von Daten in Tabellen mit den Trainingsdaten oder Daten bewertet. 

Bitten Sie den Datenbankadministrator so konfigurieren Sie die folgenden Berechtigungen für das Konto in der Datenbank, in dem Sie r verwenden

+ **EXECUTE ANY EXTERNAL SCRIPT** R auf dem Server ausführen.
+ **Db_datareader** Privilegien zum Ausführen von Abfragen zum Trainieren des Modells verwendet.
+ **Db_datawriter** Trainings- oder ausgewerteten Daten schreiben.
+ **Db_owner** zum Erstellen von Objekten, z. B. gespeicherte Prozeduren, Tabellen, Funktionen. 
  Sie müssen auch **Db_owner** Beispiel und Test-Datenbanken erstellen. 

Wenn Ihr Code Pakete, die nicht standardmäßig mit SQL Server installiert sind erfordert, ordnen Sie den Datenbankadministrator, um die mit der Instanz installierten Pakete zu erhalten. SQL Server ist eine sichere Umgebung, und es gibt Einschränkungen für die Pakete installiert werden können. Ad-hoc-Installation von Paketen als Teil des Codes wird nicht empfohlen, auch wenn Sie über Zugriffsrechte verfügen. Darüber hinaus immer sorgfältig Auswirkungen auf die Sicherheit vor der Installation neuer Pakete in der Serverbibliothek.

> [!Tip]
> Wenn Sie mit SQL Server und die Arbeit in einer lokalen Entwicklungsumgebung nicht vertraut sind, können Sie für dieses Tutorial Weitere Informationen zu Anmeldungen und Festlegen von Berechtigungen für Schritt: [tauchgang RevoScaleR](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)

## <a name="4---test-connections"></a>4: Testen von Verbindungen

SQL Server muss aktiviert sein, für die [Remoteverbindungen](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md) und Sie benötigen Berechtigungen, einschließlich einer Benutzeranmeldung und eine Datenbank für die Verbindung. Die folgenden Schritte setzen voraus, die Demodatenbank [NYCTaxi_Sample](../tutorials/sqldev-download-the-sample-data.md) und Windows-Authentifizierung.

 Verwenden Sie als Überprüfungsschritt ein integriertes Tool und die RevoScaleR, die Verbindung mit dem Remoteserver konfiguriert.

1. Zunächst [öffnen ein R-Tool](#r-tool) auf der Clientarbeitsstation. RevoScaleR wird automatisch geladen. Wechseln Sie z. B. zum `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` und doppelklicken Sie auf **RGui.exe** zu starten.

2. Vergewissern Sie sich, dass RevoScaleR betriebsbereit ist, mit dem folgenden Befehl aus, die statistische Zusammenfassung für ein Demodataset zurückgibt. Stellen Sie sicher, dass Sie einen gültigen Servernamen für die SQL Server-Datenbank-Engine-Instanz bereitstellen.

```r
connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=TaxiNYC_Sample;Trusted_Connection=true"
testQuery <-"SELECT DISTINCT TOP(100) tip_amount FROM [dbo].nyctaxi_sample ORDER BY tip_amount DESC;"
cc <-RxInSqlServer(connectionString=connStr)
rxSummary(formula = ~ ., data = RxSqlServerData(sqlQuery=testQuery, connectionString=connStr), computeContext=cc)
```
Dieses Skript eine Verbindung mit einer Datenbank auf dem Remoteserver hergestellt wird, stellt eine Abfrage, erstellt einen computekontext `cc` Anleitungen für die codeausführung von Remotestandorten, anschließend werden die RevoScaleR-Funktion **RxSummary** eine statistische zurückgegeben. Zusammenfassung der Ergebnisse der Abfrage.

<a name="install-ide"></a>

## <a name="5---install-an-ide"></a>5: Installieren einer IDE

Beständige und schwerwiegende Entwicklungsprojekten sollten Sie eine integrierte Entwicklungsumgebung (IDE) installieren. SQL Server-Tools und die integrierte R-Tools sind nicht für hohen R-Entwicklungstools ausgestattet. Nachdem Sie den funktionierenden Code haben, können Sie es als eine gespeicherte Prozedur für die Ausführung auf SQL Server bereitstellen.

Sie sollten Ihre IDE zeigen Sie auf der lokalen R-Bibliotheken: Basis-R, RevoScaleR und So weiter. Ausführung von Workloads auf einem Remotecomputer mit SQL Server tritt auf, während der Ausführung des Skripts, wenn Ihr Skript einen remotecomputekontext auf SQL Server, den Zugriff auf Daten und Vorgänge auf dem Server aufruft.

### <a name="rstudio"></a>RStudio

Bei Verwendung [RStudio](https://www.rstudio.com/), Sie können konfigurieren, dass die Umgebung für die Verwendung der R-Bibliotheken und ausführbare Dateien, die auf einem Remotecomputer mit SQL Server entsprechen.

1. Überprüfen Sie die R-Paket-Versionen auf SQL Server installiert. Weitere Informationen finden Sie unter [erste R-Paketinformationen](determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).

1. Installieren Sie Microsoft R Client oder eines eigenständigen Serveroptionen zum Hinzufügen von RevoScaleR und anderen R-Paketen, einschließlich der basisverteilung von R, die von Ihrer SQL Server-Instanz verwendet. Wählen Sie eine Version gleichzeitig aus, oder niedriger (Pakete sind abwärtskompatibel), Versionen des gleichen Pakets wie auf dem Server bereitstellt. Informationen zur Version finden Sie unter der Version, die in diesem Artikel zuzuordnen: [ein Upgrade von R und Python-Komponenten](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

1. In RStudio [aktualisieren Sie den R-Pfad](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) auf der R-Umgebung, die Bereitstellung von RevoScaleR, Microsoft R Open und andere Microsoft-Pakete verweisen. Je nachdem, wie RevoScaleR und andere Bibliotheken erworben wurde ist es sehr wahrscheinlich eine der folgenden Pfade:

  + C:\Program Files\Microsoft SQL Server\130\R_SERVER\Library
  + C:\Program Files\Microsoft SQL Server\140\R_SERVER\Library
  + C:\Programme\Microsoft Files\Microsoft\R Client\R_SERVER\bin\x64

### <a name="r-tools-for-visual-studio-rtvs"></a>R Tools für Visual Studio (RTVS)

Wenn Sie bereits eine bevorzugte IDE für R haben, empfehlen wir **R-Tools für Visual Studio**.

+ [Herunterladen von R-Tools für Visual Studio (RTVS)](https://visualstudio.microsoft.com/vs/features/rtvs/)
+ [Anweisungen zur Installation](https://docs.microsoft.com/visualstudio/rtvs/installing-r-tools-for-visual-studio) -RTVS in mehreren Versionen von Visual Studio verfügbar ist.
+ [Erste Schritte mit R Tools für Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r)

### <a name="connect-to-sql-server-from-rtvs"></a>Verbinden Sie mit SQLServer von RTVS

Dieses Beispiel verwendet Visual Studio 2017 Community Edition, mit der Data Science-Workload installiert.

1. Von der **Datei** , wählen Sie im Menü **neu** und wählen Sie dann **Projekt**.

2. Der linke Bereich enthält eine Liste der vorinstallierten Vorlagen. Klicken Sie auf **R**, und wählen Sie **R-Projekts**. In der **Namen** geben `dbtest` , und klicken Sie auf **OK**. 

  Visual Studio erstellt einen neuen Projektordner und einer Standard-Skriptdatei `Script.R`. 

3. Typ `.libPaths()` in der ersten Zeile des Skripts Datei aus, und drücken Sie STRG + EINGABETASTE.

  Der Pfad der aktuelle R-Bibliothek angezeigt werden soll, der **R Interactive** Fenster. 

4. Klicken Sie auf die **R-Tools** Menü **Windows** um eine Liste von anderen R-spezifische Windows anzuzeigen, die Sie in Ihrem Arbeitsbereich anzeigen können.
 
    + Anzeigen von Hilfe für die Pakete in der aktuellen Bibliothek durch Drücken von STRG + 3.
    + Finden Sie unter R-Variablen in der **Variablen-Explorer**, durch Drücken von STRG + 8.

5. Erstellen Sie eine Verbindungszeichenfolge für SQL Server-Instanz, und verwenden Sie die Verbindungszeichenfolge im Konstruktor RxInSqlServer, um ein SQL Server-Datenquellenobjekt zu erstellen. 

    ```r
    connStr <- "Driver=SQL Server;Server=MyServer;Database=MyTestDB;Uid=;Pwd="
    sqlShareDir <- paste("C:\\AllShare\\", Sys.getenv("USERNAME"), sep = "")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    cc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    sampleDataQuery <- "SELECT TOP 100 * from [dbo].[MyTestTable]"
    inDataSource <- RxSqlServerData(sqlQuery = sampleDataQuery, connectionString = connStr, rowsPerRead = 500)
    ```
    > [!TIP]
    > Wählen Sie die Zeilen, die Sie verwenden möchten, führen Sie aus, und drücken STRG + EINGABETASTE, um ein Batch ausgeführt werden.

6. Legen Sie den computekontext auf den Server, und führen Sie einfache R-Code für die Daten.

    ```r
    rxSetComputeContext(cc)
    rxGetVarInfo(data = inDataSource)
    ```

    Ergebnisse werden zurückgegeben, der **R Interactive** Fenster.
    
    Wenn Sie möchten sicherstellen, dass der Code für die SQL Server-Instanz ausgeführt wird, können Sie Profiler, zum Erstellen einer Ablaufverfolgung.

## <a name="next-steps"></a>Nächste Schritte

Zwei andere Lernprogramme enthalten Übungen, damit Sie üben können den computekontext von einer lokalen SQL Server-Remoteinstanz wechseln.

+ [Tutorial: RevoScaleR die R-Funktionen mit SQL Server-Daten](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Lückenlose exemplarische Data Science-Vorgehensweise](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)