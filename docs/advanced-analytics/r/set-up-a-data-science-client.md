---
title: Einrichten eines Data Science-Clients für die R-Entwicklung
description: Installieren Sie lokale R-Bibliotheken und-Tools auf einer Entwicklungs Arbeitsstation für Remote Verbindungen mit SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0f8cc5aaa10beeb5b91b27111e15013cc705ed20
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469960"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Einrichten eines Data Science-Clients für die R-Entwicklung auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die Integration von r ist in SQL Server 2016 oder höher verfügbar, wenn Sie die Option r Language in eine [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) -oder [SQL Server 2017 Machine Learning Services (in-Database)-](../install/sql-machine-learning-services-windows-install.md) Installation einschließen. 

Zum entwickeln und Bereitstellen von R-Lösungen für SQL Server installieren Sie [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) auf Ihrer entwicklungsarbeits Station, um [revoscaler](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) und andere R-Bibliotheken zu erhalten. Die revoscaler-Bibliothek, die ebenfalls auf der Remote SQL Server-Instanz erforderlich ist, koordiniert das Berechnen von Anforderungen zwischen beiden Systemen. 

In diesem Artikel erfahren Sie, wie Sie eine Entwicklungs Arbeitsstation für R-Clients so konfigurieren, dass Sie mit einer Remote SQL Server interagieren können, die für Machine Learning-und R-Integration aktiviert ist. Nachdem Sie die Schritte in diesem Artikel ausgeführt haben, verfügen Sie über dieselben R-Bibliotheken wie die in SQL Server. Sie wissen auch, wie Berechnungen von einer lokalen r-Sitzung an eine Remote-r-Sitzung auf SQL Server Übertragung erfolgt.

![Client-Server-Komponenten](media/sqlmls-r-client-revo.png "Lokale und Remote-R-Sitzungen und-Bibliotheken")

Zum Überprüfen der Installation können Sie das integrierte **rgui** -Tool verwenden, wie in diesem Artikel beschrieben, oder Sie können [die Bibliotheken](#install-ide) mit rstudio oder einer anderen IDE verknüpfen, die Sie normalerweise verwenden.

> [!Note]
> Eine Alternative zur Installation der Client Bibliothek ist die Verwendung eines [eigenständigen Servers](../install/sql-machine-learning-standalone-windows-install.md) als Rich Client, den einige Kunden für eine tiefere szenarioarbeit bevorzugen. Ein eigenständiger Server ist vollständig von SQL Server entkoppelt, aber da er die gleichen R-Bibliotheken hat, können Sie ihn als Client für SQL Server in-Database-Analyse verwenden. Sie können Sie auch für nicht-SQL-bezogene Arbeiten verwenden, einschließlich der Möglichkeit, Daten von anderen Daten Plattformen zu importieren und zu modellieren. Wenn Sie einen eigenständigen Server installieren, finden Sie die ausführbare R-Datei an `C:\Program Files\Microsoft SQL Server\140\R_SERVER`diesem Speicherort:. Um die Installation zu überprüfen, [Öffnen Sie eine r-Konsolen-App](#R-tools) , um Befehle mithilfe von r. exe an diesem Speicherort auszuführen.

## <a name="commonly-used-tools"></a>Häufig verwendete Tools

Unabhängig davon, ob Sie ein r-Entwickler sind, der neu bei SQL ist, oder ein SQL-Entwickler, der für r-und in-Database-Analysen neu ist, benötigen Sie ein r-Entwicklungs Tool und einen T-SQL-Abfrage-Editor wie [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) , um alle Funktionen von in-Database Analytik.

Für einfache r-Entwicklungsszenarien können Sie die ausführbare rgui-Datei, gebündelt in der Basis-r-Distribution in MRO und SQL Server verwenden. In diesem Artikel wird erläutert, wie Sie die rgui sowohl für lokale als auch Remote-R-Sitzungen verwenden. Um die Produktivität zu verbessern, sollten Sie eine IDE mit vollem Funktionsumfang wie [rstudio oder Visual Studio](#install-ide)verwenden.

SSMS ist ein separater Download, der für das Erstellen und Ausführen gespeicherter Prozeduren auf SQL Server nützlich ist, einschließlich derjenigen, die R-Code enthalten. Nahezu jeder R-Code, den Sie in einer Entwicklungsumgebung schreiben, kann in eine gespeicherte Prozedur eingebettet werden. Sie können weitere Tutorials durchlaufen, um mehr über [SSMS und eingebettete R](../tutorials/sqldev-in-database-r-for-sql-developers.md)zu erfahren.

## <a name="1---install-r-packages"></a>1: Installieren von R-Paketen

Die R-Pakete von Microsoft sind in mehreren Produkten und Diensten verfügbar. Es wird empfohlen, auf einer lokalen Arbeitsstation Microsoft R Client zu installieren. R Client stellt [revoscaler](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), [microsoftml](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package), [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)und andere r-Pakete bereit.

1. [Laden Sie Microsoft R Client herunter](https://aka.ms/rclient/download).

2. Übernehmen oder ändern Sie im Installations-Assistenten den Standard Installationspfad, akzeptieren oder ändern Sie die Liste der Komponenten, und akzeptieren Sie die Microsoft R Client-Lizenzbedingungen.

  Wenn die Installation abgeschlossen ist, werden Sie in einem Begrüßungsbildschirm zum Produkt und zur Dokumentation.

3. Erstellen Sie eine MKL_CBWR-System Umgebungsvariable, um eine konsistente Ausgabe in Intel Math Kernel Library (MKL)-Berechnungen sicherzustellen.

  + Klicken Sie in der Systemsteuerung auf **System-und Sicherheits** > **System** > **Erweiterte Systemeinstellungen** > **Umgebungsvariablen**.
  + Erstellen Sie eine neue System Variable mit dem Namen **MKL_CBWR**, wobei der Wert auf **Auto**festgelegt ist.

## <a name="2---locate-executables"></a>2\. ausführbare Dateien suchen

Suchen und auflisten Sie den Inhalt des-Installations Ordners, um zu bestätigen, dass R. exe, rgui und andere Pakete installiert sind. 

1. Öffnen Sie im Datei-Explorer den Ordner c:\programme\microsoft\r Client\R_SERVER\bin, um den Speicherort von "R. exe" zu bestätigen.

2. Öffnen Sie den Unterordner x64, um die **rgui**zu bestätigen. Dieses Tool wird im nächsten Schritt verwendet.

3. Öffnen Sie c:\programme\microsoft\r Client\R_SERVER\library, um die Liste der mit R Client installierten Pakete zu überprüfen, einschließlich revoscaler, microsoftml und anderen.


<a name="R-tools"></a>
 
## <a name="3---start-rgui"></a>3: Starten der rgui

Wenn Sie r mit SQL Server installieren, erhalten Sie dieselben R-Tools, die für jede Basisinstallation von r Standard sind, wie z. b. rgui, RTERM usw. Diese Tools sind einfach und nützlich zum Überprüfen von Paket-und Bibliotheksinformationen, Ausführen von Ad-hoc-Befehlen oder-Skripts oder Ausführen von Tutorials. Sie können diese Tools verwenden, um R-Versionsinformationen zu erhalten und die Konnektivität zu bestätigen.

1. Öffnen Sie c:\programme\microsoft\r Client\R_SERVER\bin\x64, und doppelklicken Sie auf **rgui** , um eine r-Sitzung mit einer r-Eingabeaufforderung zu starten.

  Wenn Sie eine R-Sitzung aus einem Microsoft-Programmordner starten, werden von mehreren Paketen, einschließlich revoscaler, automatisch geladen. 

2. Geben `print(Revo.version)` Sie an der Eingabeaufforderung ein, um revoscaler-Paket Versionsinformationen zurückzugeben. Sie sollten über die Version 9.2.1 oder 9.3.0 für revoscaler verfügen.

3. Geben Sie in der R-Eingabeaufforderung **Search ()** ein, um eine Liste der installierten Pakete zu finden.

   ![Versionsinformationen beim Laden von R](../install/media/rclient-rgui-r-prompt.png "Öffnen einer R-Eingabeaufforderung")


## <a name="4---get-sql-permissions"></a>4: SQL-Berechtigungen erhalten

Im r-Client wird die r-Verarbeitung auf zwei Threads und in-Memory-Daten begrenzt. Bei der skalierbaren Verarbeitung mit mehreren Kernen und großen Datasets können Sie die Ausführung (als *computekontext*bezeichnet) auf die Datasets und die Rechenleistung einer Remote SQL Server-Instanz umstellen. Dies ist die empfohlene Vorgehensweise für die Client Integration in eine Produktions SQL Server Instanz, und Sie benötigen Berechtigungen und Verbindungsinformationen, damit Sie funktioniert.

Zum Herstellen einer Verbindung mit einer Instanz von SQL Server zum Ausführen von Skripts und Hochladen von Daten müssen Sie über einen gültigen Anmelde Namen auf dem Daten Bank Server verfügen. Sie können entweder einen SQL-Anmeldenamen oder die integrierte Windows-Authentifizierung verwenden. Im Allgemeinen wird empfohlen, die integrierte Windows-Authentifizierung zu verwenden, aber die Verwendung der SQL-Anmeldung ist für einige Szenarien einfacher, insbesondere wenn Ihr Skript Verbindungs Zeichenfolgen zu externen Daten enthält.

Das zum Ausführen von Code verwendete Konto muss mindestens über die Berechtigung zum Lesen der Datenbanken verfügen, mit denen Sie arbeiten, sowie über die spezielle Berechtigung zum Ausführen externer Skripts. Die meisten Entwickler benötigen auch Berechtigungen zum Erstellen gespeicherter Prozeduren und zum Schreiben von Daten in Tabellen, die Trainingsdaten oder bewertete Daten enthalten. 

Bitten Sie den Datenbankadministrator, [die folgenden Berechtigungen für Ihr Konto](../security/user-permission.md)in der Datenbank zu konfigurieren, in der Sie R verwenden:

+ **Führen Sie ein externes Skript** zum Ausführen des R-Skripts auf dem Server aus.
+ **db_datareader** Berechtigungen zum Ausführen der Abfragen, die zum Trainieren des Modells verwendet werden.
+ **db_datawriter** Schreiben von Trainingsdaten oder bewerteten Daten.
+ **db_owner** Erstellen von Objekten, wie z. b. gespeicherte Prozeduren, Tabellen und Funktionen. 
  Außerdem benötigen Sie **db_owner** , um Beispiel-und Testdatenbanken zu erstellen. 

Wenn für den Code Pakete erforderlich sind, die nicht standardmäßig mit SQL Server installiert werden, müssen Sie mit dem Datenbankadministrator anordnen, damit die Pakete mit der-Instanz installiert werden. SQL Server ist eine gesicherte Umgebung, und es gibt Einschränkungen hinsichtlich der Installation von Paketen. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete auf SQL Server](install-additional-r-packages-on-sql-server.md).

## <a name="5---test-connections"></a>5: Testen von Verbindungen

 Verwenden Sie als Überprüfungs Schritt **rgui** und revoscaler, um die Konnektivität mit dem Remote Server zu bestätigen. SQL Server müssen für [Remote Verbindungen](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server) aktiviert sein, und Sie müssen über Berechtigungen verfügen, einschließlich einer Benutzeranmeldung und einer Datenbank, mit der eine Verbindung hergestellt werden soll. 

In den folgenden Schritten wird von der Demo Database, [NYCTaxi_Sample](../tutorials/demo-data-nyctaxi-in-sql.md)und Windows-Authentifizierung ausgegangen.

1. Öffnen Sie die **rgui** auf der Client Arbeitsstation. Wechseln Sie z. b `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` . zu, und doppelklicken Sie auf **rgui. exe** , um ihn zu starten.

2. Revoscaler wird automatisch geladen. Bestätigen Sie, dass revoscaler betriebsbereit ist, indem Sie diesen Befehl ausführen`print(Revo.version)`

3. Geben Sie ein Demoskript ein, das auf dem Remote Server ausgeführt wird. Sie müssen das folgende Beispielskript so ändern, dass ein gültiger Name für eine Remote SQL Server-Instanz enthalten ist. Diese Sitzung beginnt als lokale Sitzung, die **rxsummary** -Funktion wird jedoch auf der Remote SQL Server-Instanz ausgeführt.

  ```R
  # Define a connection. Replace server with a valid server name.
  connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
  
  # Specify the input data in a SQL query.
  sampleQuery <-"SELECT DISTINCT TOP(100) tip_amount FROM [dbo].nyctaxi_sample ORDER BY tip_amount DESC;"
  
  # Define a remote compute context based on the remote server.
  cc <-RxInSqlServer(connectionString=connStr)

  # Execute the function using the remote compute context.
  rxSummary(formula = ~ ., data = RxSqlServerData(sqlQuery=sampleQuery, connectionString=connStr), computeContext=cc)
  ```

  **Ergebnisse:**

  Dieses Skript stellt eine Verbindung mit einer Datenbank auf dem Remote Server her, stellt eine Abfrage bereit, erstellt `cc` eine computekontexts-Anweisung für die Remote Codeausführung und stellt dann die revoscaler-Funktion **rxsummary** bereit, um eine statistische Zusammenfassung der Abfrage zurückzugeben. Folgen.

  ```R
    Call:
  rxSummary(formula = ~., data = RxSqlServerData(sqlQuery = sampleQuery, 
      connectionString = connStr), computeContext = cc)

  Summary Statistics Results for: ~.
  Data: RxSqlServerData(sqlQuery = sampleQuery, connectionString = connStr) (RxSqlServerData Data Source)
  Number of valid observations: 100 
  
  Name       Mean   StdDev   Min Max ValidObs MissingObs
  tip_amount 63.245 31.61087 36  180 100      0     
  ```

4. Sie erhalten den computekontext und legen ihn fest. Nachdem Sie einen computekontext festgelegt haben, bleibt er für die Dauer der Sitzung wirksam. Wenn Sie nicht sicher sind, ob die Berechnung lokal oder Remote erfolgt, führen Sie den folgenden Befehl aus, um zu ermitteln. Ergebnisse, die eine Verbindungs Zeichenfolge angeben, geben einen remotecomputekontext an.

  ```R
  # Return the current compute context.
  rxGetComputeContext()

  # Revert to a local compute context.
  rxSetComputeContext("local")
  rxGetComputeContext()

  # Switch back to remote.
  connStr <- "Driver=SQL Server;Server=<your-server-name>;Database=NYCTaxi_Sample;Trusted_Connection=true"
  cc <-RxInSqlServer(connectionString=connStr)
  rxSetComputeContext(cc)
  rxGetComputeContext()
  ```  

5. Gibt Informationen zu Variablen in der Datenquelle zurück, einschließlich Name und Typ.

  ```R
  rxGetVarInfo(data = inDataSource)
  ```
  Die Ergebnisse enthalten 23 Variablen.


6. Generieren Sie ein Punkt Diagramm, um zu überprüfen, ob Abhängigkeiten zwischen zwei Variablen vorhanden sind. 

  ```R
  # Set the connection string. Substitute a valid server name for the placeholder.
  connStr <- "Driver=SQL Server;Server=<your database name>;Database=NYCTaxi_Sample;Trusted_Connection=true"

  # Specify a query on the nyctaxi_sample table.
  # For variables on each axis, remove nulls. Use a WHERE clause and <> to do this.
  sampleQuery <-"SELECT DISTINCT TOP 100 * from [dbo].[nyctaxi_sample] WHERE fare_amount <> '' AND  tip_amount <> ''"
  cc <-RxInSqlServer(connectionString=connStr)

  # Generate a scatter plot.
  rxLinePlot(fare_amount ~ tip_amount, data = RxSqlServerData(sqlQuery=sampleQuery, connectionString=connStr, computeContext=cc), type="p")
  ```

  Der folgende Screenshot zeigt die Ausgabe des Eingabe-und Punkt Diagramms.

   Punkt ![Diagramm in rgui] Punkt (media/rclient-setup-scatterplot.png "Diagramm für NYC Taxi-Demodaten")

<a name="install-ide"></a>

## <a name="6---link-tools-to-rexe"></a>6: Verknüpfen von Tools mit R. exe

Für dauerhafte und schwerwiegende Entwicklungsprojekte sollten Sie eine integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) installieren. SQL Server Tools und die integrierten r-Tools sind nicht für eine hohe R-Entwicklung konzipiert. Sobald Sie über einen funktionierenden Code verfügen, können Sie ihn als gespeicherte Prozedur zur Ausführung auf SQL Server bereitstellen.

Verweisen Sie Ihre IDE auf die lokalen r-Bibliotheken: Base R, revoscaler usw. Das Ausführen von Arbeits Auslastungen auf einer Remote SQL Server tritt während der Ausführung des Skripts auf, wenn Ihr Skript einen remotecomputekontext auf SQL Server aufruft und auf Daten und Vorgänge auf diesem Server zugreift.

### <a name="rstudio"></a>RStudio

Wenn Sie [rstudio](https://www.rstudio.com/)verwenden, können Sie die Umgebung so konfigurieren, dass die R-Bibliotheken und ausführbaren Dateien verwendet werden, die den Elementen einer Remote SQL Server entsprechen.

1. Überprüfen Sie die auf SQL Server installierten R-Paketversionen. Weitere Informationen finden Sie unter [Get R Package Information](../package-management/installed-package-information.md).

1. Installieren Sie Microsoft R Client oder eine der eigenständigen Serveroptionen, um revoscaler und andere r-Pakete hinzuzufügen, einschließlich der von Ihrer SQL Server Instanz verwendeten Basis-r-Verteilung. Wählen Sie eine Version auf derselben Ebene oder niedriger (Pakete sind abwärts kompatibel), die die gleichen Paketversionen wie auf dem Server bereitstellt. Versionsinformationen finden Sie in der Versions Zuordnung in diesem Artikel: [Aktualisieren Sie die R-und python-Komponenten](../install/upgrade-r-and-python.md).

1. Aktualisieren Sie in rstudio [ihren R-Pfad](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) so, dass er auf die r-Umgebung verweist, die revoscaler, Microsoft R Open und andere Microsoft-Pakete bereitstellt. 

  + Suchen Sie für eine R-Client Installation nach c:\programme\microsoft\r Client\R_SERVER\bin\x64
  + Einen eigenständigen Server finden Sie unter "c:\Programme\Microsoft SQL Server\140\R_SERVER\Library" oder "c:\Programme\Microsoft SQL Server\130\R_SERVER\Library".

2. Schließen Sie rstudio, und öffnen Sie es.

Wenn Sie rstudio erneut öffnen, ist die r-ausführbare Datei des r-Clients (oder des eigenständigen Servers) die Standard-r-Engine.


### <a name="r-tools-for-visual-studio-rtvs"></a>R Tools für Visual Studio (rtvs)

Wenn Sie nicht bereits über eine bevorzugte IDE für R verfügen, empfehlen wir **R Tools für Visual Studio**.

+ [Download R Tools für Visual Studio (rtvs)](https://visualstudio.microsoft.com/vs/features/rtvs/)
+ [Installationsanweisungen](https://docs.microsoft.com/visualstudio/rtvs/installing-r-tools-for-visual-studio) : rtvs ist in mehreren Versionen von Visual Studio verfügbar.
+ [Beginnen Sie mit R Tools für Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r)

### <a name="connect-to-sql-server-from-rtvs"></a>Herstellen einer Verbindung mit SQL Server von rtvs

In diesem Beispiel wird Visual Studio 2017 Community Edition verwendet, wobei die Data Science Arbeitsauslastung installiert ist.

1. Wählen Sie im Menü **Datei** die Option **neu** aus, und wählen Sie dann **Projekt**aus.

2. Der linke Bereich enthält eine Liste vorinstallierter Vorlagen. Klicken Sie auf **r**, und wählen Sie **r Project**aus. Geben`dbtest` Sie im Feld **Name** ein, und klicken Sie auf **OK**. 

  Visual Studio erstellt einen neuen Projektordner und eine Standardskript Datei, `Script.R`. 

3. Geben `.libPaths()` Sie in die erste Zeile der Skriptdatei ein, und drücken Sie dann STRG + EINGABETASTE.

  Der aktuelle R-Bibliotheks Pfad sollte im **R Interactive** Fenster angezeigt werden. 

4. Klicken Sie auf das Menü **r Tools** , und wählen Sie **Windows** aus, um eine Liste mit anderen R-spezifischen Fenstern anzuzeigen, die Sie in Ihrem Arbeitsbereich anzeigen können.
 
  + Anzeigen der Hilfe zu Paketen in der aktuellen Bibliothek durch Drücken von STRG + 3.
  + Sehen Sie sich die R-Variablen im **Variablen-Explorer**an, indem Sie STRG + 8 drücken.

## <a name="next-steps"></a>Nächste Schritte

Zwei verschiedene Tutorials enthalten Übungen, mit denen Sie die Umstellung des computekontexts vom lokalen auf eine Remote SQL Server-Instanz üben können.

+ [Tutorial: Verwenden von revoscaler R-Funktionen mit SQL Server Daten](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Lückenlose exemplarische Data Science-Vorgehensweise](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)