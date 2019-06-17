---
title: 'Richten Sie eine Data Science-Client für R-Entwicklungstools: SQL Server Machine Learning Services'
description: Installieren Sie die lokale R-Bibliotheken und Tools auf einer entwicklungsworkstation für Remoteverbindungen zur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 1b18844e6899615ac978e63cefa6c712f8f194ea
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140348"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Richten Sie eine Data Science-Client für die Entwicklung von R auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

R-Integration ist verfügbar in SQL Server 2016 oder höher, wenn Sie die Option im R-Sprache einschließen einer [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) oder [SQL Server 2017-Machine Learning Services (Datenbankintern)](../install/sql-machine-learning-services-windows-install.md) Installation. 

Installieren Sie zum Entwickeln und Bereitstellen von R-Lösungen für SQL Server, [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client) auf Ihrer Entwicklungsarbeitsstation abzurufenden [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) und andere R-Bibliotheken. Die RevoScaleR-Bibliothek, die auch auf der Remoteinstanz von SQL Server erforderlich ist, koordiniert Compute-Anforderungen zwischen den beiden Systemen. 

Erfahren Sie in diesem Artikel, wie ein R-Clientarbeitsstation Entwicklung so konfigurieren, dass Sie mit einem SQL-Remoteserver für Machine Learning und R-Integration aktiviert interagieren können. Nach Abschluss der Schritte in diesem Artikel müssen Sie die gleichen R-Bibliotheken wie die auf SQL Server. Außerdem lernen Sie, wie Sie Berechnungen in einer lokalen R-Sitzung an eine Remotesitzung von R auf SQL Server zu senden.

![Client / Server-Komponenten](media/sqlmls-r-client-revo.png "lokal und remote-R-Sitzungen und Bibliotheken")

Um die Installation zu überprüfen, können Sie integrierte **RGUI** Tools wie in diesem Artikel beschriebenen oder [verknüpfen Sie die Bibliotheken](#install-ide) RStudio oder alle eine andere IDE, die Sie normalerweise verwenden.

> [!Note]
> Eine Alternative zur Installation des Client-Bibliothek ist die Verwendung einer [eigenständiger Server](../install/sql-machine-learning-standalone-windows-install.md) als rich-Clients, die für die Arbeit für umfangreichere Szenario einige Kunden bevorzugen. Ein eigenständiger Server wird von SQL Server vollständig entkoppelt, aber da sie die gleichen R-Bibliotheken verfügt, können Sie sie als Client für SQL Server in-Database-Analyse. Außerdem können Sie sie für nicht-SQL-bezogenen arbeiten, einschließlich der Fähigkeit zum Importieren und Modellieren von Daten von anderen Data-Plattformen. Wenn Sie einen eigenständigen Server installieren, finden Sie die R-ausführbare Datei an diesem Speicherort: `C:\Program Files\Microsoft SQL Server\140\R_SERVER`. So überprüfen Sie Ihre Installation, [öffnen Sie eine R-Konsolen-app](#R-tools) zum Ausführen von Befehlen, die mit der R.exe an diesem Speicherort.

## <a name="commonly-used-tools"></a>Häufig verwendete tools

Ob Sie ein R-Entwickler, die noch nicht mit SQL oder in R und datenbankinternen Analysen, neue SQL-Entwickler sind, benötigen Sie sowohl eine R-Entwicklungstools und einen T-SQL-Abfrage-Editor wie z. B. [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) So führen Sie alle aus der die Funktionen der datenbankinternen Analysen.

Für einfache Szenarien für die R-Entwicklung können Sie der ausführbaren Datei RGUI verwenden, in der basisverteilung von R in MRO und SQL Server gebündelt. In diesem Artikel wird erläutert, wie RGUI für lokale und remote-R-Sitzungen verwendet wird. Verbesserte Produktivität, verwenden Sie für eine IDE mit vollem Funktionsumfang wie z. B. [RStudio oder Visual Studio](#install-ide).

SSMS ist ein separater Download, der nützlich zum Erstellen und Ausführen von gespeicherten Prozeduren in SQL Server, einschließlich derjenigen, die R-Code enthält. Fast alle R-Code, den Sie in einer Entwicklungsumgebung zu schreiben, kann in einer gespeicherten Prozedur eingebettet werden. Sie können über die anderen Tutorials erfahren Sie Schritt [SSMS und eingebettete R](../tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="1---install-r-packages"></a>1: Installieren von R-Pakete

Von Microsoft R-Pakete stehen in mehreren Produkten und Diensten zur Verfügung. Es wird empfohlen, auf einer lokalen Arbeitsstation Microsoft R Client installieren. R Client bietet [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package), [SQLRUtils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils), und andere R-Pakete.

1. [Laden Sie Microsoft R Client](https://aka.ms/rclient/download).

2. Im Installations-Assistenten akzeptieren oder Ändern der Standardinstallationspfad, akzeptieren oder ändern Sie die Liste der Komponenten und akzeptiere die Lizenzbedingungen für Microsoft R Client.

  Wenn die Installation abgeschlossen ist, stellt eine Willkommensseite das Produkt und Dokumentation.

3. Erstellen Sie eine MKL_CBWR System-Umgebungsvariable, um sicherzustellen, dass konsistente Ausgabe in der Intel Math Kernel Library (MKL) Berechnungen.

  + Klicken Sie in der Systemsteuerung auf **System und Sicherheit** > **System** > **Erweiterte Systemeinstellungen**  >   **Umgebungsvariablen**.
  + Erstellen Sie eine neue Systemvariable namens **MKL_CBWR**, mit dem ein Wert **automatisch**.

## <a name="2---locate-executables"></a>2: Suchen von ausführbaren Dateien

Suchen und listet den Inhalt des Installationsordners "zu bestätigen, dass R.exe RGUI und andere Pakete installiert sind. 

1. Öffnen Sie im Datei-Explorer den Ordner c:\Programme\Microsoft Files\Microsoft\R Client\R_SERVER\bin, um den Speicherort der R.exe überprüfen.

2. Öffnen Sie die X64-Unterordner, um zu bestätigen **RGUI**. Sie verwenden dieses Tool im nächsten Schritt.

3. Öffnen Sie c:\Programme\Microsoft Files\Microsoft\R Client\R_SERVER\library zum Überprüfen der Liste der Pakete mit R-Client, einschließlich RevoScaleR, MicrosoftML und andere Benutzer installiert.


<a name="R-tools"></a>
 
## <a name="3---start-rgui"></a>3 – Start RGUI

Wenn Sie R mit SQL Server installieren, erhalten Sie den gleichen R-Tools, die standardmäßig auf alle Basisinstallation von R, z.B. RGui und Rterm usw. verwendet werden. Diese Tools sind einfache – nützlich zum Überprüfen der Informationen Paket und die Bibliothek, das Ausführen von ad-hoc-Befehle oder eines Skripts oder schrittweise Lernprogramme. Sie können diese Tools verwenden, um R-Versionsinformationen abzurufen, und gewährleisten Sie Konnektivität.

1. Öffnen Sie c:\Programme\Microsoft Files\Microsoft\R Client\R_SERVER\bin\x64, und doppelklicken Sie auf **RGui** um eine R-Sitzung mit einer R-Eingabeaufforderung zu starten.

  Wenn Sie eine R-Sitzung aus einem Ordner der Microsoft-Programm starten, werden mehrere Pakete, einschließlich von RevoScaleR, automatisch geladen. 

2. Geben Sie `print(Revo.version)` Versionsinformationen an der Eingabeaufforderung zum Zurückgeben von RevoScaleR-Paket. Sie sollten Version 9.2.1 oder 9.3.0 für RevoScaleR verwenden.

3. Geben Sie **search()** an der R-Eingabeaufforderung eine Liste der installierten Pakete.

   ![Versionsinformationen, die beim Laden von R](../install/media/rclient-rgui-r-prompt.png "eine R-Eingabeaufforderung öffnen")


## <a name="4---get-sql-permissions"></a>4: Abrufen von SQL-Berechtigungen

In R Client ist die R-Verarbeitung auf zwei Threads und Daten im Arbeitsspeicher begrenzt. Für die skalierbare Verarbeitung mit mehreren Kernen und große Datasets können Sie shift-Ausführung (genannt *computekontext*) auf die Datasets und die rechenleistung von SQL Server-Remoteinstanz. Dies ist die empfohlene Vorgehensweise für die Clientintegration mit einer Produktionsinstanz von SQL Server, und Sie benötigen Berechtigungen und die Verbindungsinformationen, damit sie funktioniert.

Herstellen der Verbindung mit einer Instanz von SQL Server zum Ausführen von Skripts und Daten hochzuladen, müssen Sie eine gültige Anmeldung auf dem Datenbankserver verfügen. Sie können entweder einen SQL-Anmeldenamen oder die integrierte Windows-Authentifizierung verwenden. Im Allgemeinen wird empfohlen, dass Sie die integrierte Windows-Authentifizierung verwenden, mit der SQL-Anmeldung ist jedoch einfacher für einige Szenarien, insbesondere dann, wenn Ihr Skript Verbindungszeichenfolgen zu externen Daten enthält.

Mindestens muss das Konto zum Ausführen von Code verwendet die Berechtigung zum Lesen aus den Datenbanken, mit dem Sie arbeiten, sowie die speziellen Berechtigungen ausgeführt, ANY EXTERNAL SCRIPT haben. Die meisten Entwickler auch benötigen Berechtigungen zum Erstellen von gespeicherter Prozeduren und zum Schreiben von Daten in Tabellen mit Daten oder Daten bewertet. 

Bitten Sie den Datenbankadministrator, [konfigurieren Sie die folgenden Berechtigungen für Ihr Konto](../security/user-permission.md), in der Datenbank, in dem Sie r verwenden,

+ **EXECUTE ANY EXTERNAL SCRIPT** zum Ausführen von R-Skripts auf dem Server.
+ **Db_datareader** Privilegien zum Ausführen von Abfragen zum Trainieren des Modells verwendet.
+ **Db_datawriter** Trainings- oder ausgewerteten Daten schreiben.
+ **Db_owner** zum Erstellen von Objekten, z. B. gespeicherte Prozeduren, Tabellen, Funktionen. 
  Sie müssen auch **Db_owner** Beispiel und Test-Datenbanken erstellen. 

Wenn Ihr Code Pakete, die nicht standardmäßig mit SQL Server installiert sind erfordert, ordnen Sie den Datenbankadministrator, um die mit der Instanz installierten Pakete zu erhalten. SQL Server ist eine sichere Umgebung, und es gibt Einschränkungen für die Pakete installiert werden können. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete unter SQL Server](install-additional-r-packages-on-sql-server.md).

## <a name="5---test-connections"></a>5: Testen von Verbindungen

 Verwenden Sie als Überprüfungsschritt, **RGUI** und RevoScaleR, die Verbindung mit dem Remoteserver konfiguriert. SQL Server muss aktiviert sein, für die [Remoteverbindungen](https://docs.microsoft.com/sql/database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server) und Sie benötigen Berechtigungen, einschließlich einer Benutzeranmeldung und eine Datenbank für die Verbindung. 

Die folgenden Schritte setzen voraus, die Demodatenbank [NYCTaxi_Sample](../tutorials/demo-data-nyctaxi-in-sql.md), und die Windows-Authentifizierung.

1. Open **RGUI** auf der Clientarbeitsstation. Wechseln Sie z. B. zum `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64` und doppelklicken Sie auf **RGui.exe** zu starten.

2. RevoScaleR wird automatisch geladen. Vergewissern Sie sich, dass RevoScaleR betriebsbereit ist, mit dem folgenden Befehl: `print(Revo.version)`

3. Geben Sie ein Beispielskript, die auf dem Remoteserver ausgeführt wird. Sie müssen das folgende Beispielskript enthält einen gültigen Namen für eine Remoteinstanz von SQL Server ändern. Diese Sitzung beginnt, wie eine lokale Sitzung, aber die **RxSummary** Funktion, die auf der Remoteinstanz von SQL Server ausgeführt wird.

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

  Dieses Skript eine Verbindung mit einer Datenbank auf dem Remoteserver hergestellt wird, stellt eine Abfrage, erstellt einen computekontext `cc` Anleitungen für die codeausführung von Remotestandorten, anschließend werden die RevoScaleR-Funktion **RxSummary** eine statistische zurückgegeben. Zusammenfassung der Ergebnisse der Abfrage.

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

4. Abrufen Sie und festlegen Sie des computekontexts. Wenn Sie einen computekontext festgelegt haben, bleibt er für die Dauer der Sitzung wirksam. Wenn Sie nicht sicher sind, ob die Berechnung lokal oder remote ist, führen Sie den folgenden Befehl aus, um herauszufinden, aus. Ergebnisse, die eine Verbindungszeichenfolge angeben, geben einen remotecomputekontext.

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

5. Zurückgeben von Informationen zu Variablen in der Datenquelle, einschließlich Name und Typ.

  ```R
  rxGetVarInfo(data = inDataSource)
  ```
  Die Ergebnisse enthalten 23 Variablen.


6. Generieren Sie ein Punktdiagramm, um zu untersuchen, ob Abhängigkeiten zwischen zwei Variablen vorhanden sind. 

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

  Der folgende Screenshot zeigt die Eingabe und Punktdiagrammen Plot-Ausgabe.

   ![Punktdiagramm in RGUI](media/rclient-setup-scatterplot.png "Punktdiagramm auf NYC Taxi-Demo-Daten")

<a name="install-ide"></a>

## <a name="6---link-tools-to-rexe"></a>6 - Link-Tools für R.exe

Beständige und schwerwiegende Entwicklungsprojekten sollten Sie eine integrierte Entwicklungsumgebung (IDE) installieren. SQL Server-Tools und die integrierte R-Tools sind nicht für hohen R-Entwicklungstools ausgestattet. Nachdem Sie den funktionierenden Code haben, können Sie es als eine gespeicherte Prozedur für die Ausführung auf SQL Server bereitstellen.

Zeigen Sie Ihre IDE auf die lokalen R-Bibliotheken: Basis-R, RevoScaleR und So weiter. Ausführung von Workloads auf einem Remotecomputer mit SQL Server tritt auf, während der Ausführung des Skripts, wenn Ihr Skript einen remotecomputekontext auf SQL Server, den Zugriff auf Daten und Vorgänge auf dem Server aufruft.

### <a name="rstudio"></a>RStudio

Bei Verwendung [RStudio](https://www.rstudio.com/), Sie können konfigurieren, dass die Umgebung für die Verwendung der R-Bibliotheken und ausführbare Dateien, die auf einem Remotecomputer mit SQL Server entsprechen.

1. Überprüfen Sie die R-Paket-Versionen auf SQL Server installiert. Weitere Informationen finden Sie unter [erste R-Paketinformationen](../package-management/installed-package-information.md).

1. Installieren Sie Microsoft R Client oder eines eigenständigen Serveroptionen zum Hinzufügen von RevoScaleR und anderen R-Paketen, einschließlich der basisverteilung von R, die von Ihrer SQL Server-Instanz verwendet. Wählen Sie eine Version gleichzeitig aus, oder niedriger (Pakete sind abwärtskompatibel), die Versionen des gleichen Pakets wie auf dem Server bereitstellt. Versionsinformationen finden Sie in der Version, die in diesem Artikel zuzuordnen: [Aktualisieren Sie R- und Python-Komponenten](../install/upgrade-r-and-python.md).

1. In RStudio [aktualisieren Sie den R-Pfad](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) auf der R-Umgebung, die Bereitstellung von RevoScaleR, Microsoft R Open und andere Microsoft-Pakete verweisen. 

  + Suchen Sie für ein R-Client-Installation nach c:\Programme\Microsoft Files\Microsoft\R Client\R_SERVER\bin\x64
  + Suchen Sie für einen eigenständigen Server nach C:\Program Files\Microsoft SQL Server\140\R_SERVER\Library "oder" C:\Program Files\Microsoft SQL Server\130\R_SERVER\Library

2. Schließen Sie und öffnen Sie RStudio.

Wenn Sie RStudio erneut öffnen, wird von R-Client (oder ein eigenständiger Server) ausführbare R die Standard-R-Engine.


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

## <a name="next-steps"></a>Nächste Schritte

Zwei andere Lernprogramme enthalten Übungen, damit Sie üben können den computekontext von einer lokalen SQL Server-Remoteinstanz wechseln.

+ [Tutorial: Verwenden der RevoScaleR-R-Funktionen mit SQL Server-Daten](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Lückenlose exemplarische Data Science-Vorgehensweise](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)