---
title: Einrichten eines R-Data Science-Clients
description: Installieren Sie lokale R-Bibliotheken und -Tools auf einer Entwicklungsarbeitsstation für Remoteverbindungen mit SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 06/13/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7d3b2da6c649c514dff31225253292642212cd41
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92195788"
---
# <a name="set-up-a-data-science-client-for-r-development-on-sql-server"></a>Einrichten eines Data Science-Clients für die Entwicklung in R auf SQL Server
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Die Integration von R ist ab SQL Server 2016 verfügbar, wenn Sie die R-Sprachoption bei der Installation von [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) oder [SQL Server-Machine Learning Services (datenbankintern)](../install/sql-machine-learning-services-windows-install.md) einbeziehen. 

Um R-Lösungen für SQL Server zu entwickeln und bereitzustellen, installieren Sie [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) auf Ihrer Entwicklungsarbeitsstation, damit Sie [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) und andere R-Bibliotheken nutzen können. Mit der RevoScaleR-Bibliothek, die auch auf der SQL Server-Remoteinstanz erforderlich ist, lassen sich Computinganforderungen zwischen beiden Systemen koordinieren. 

In diesem Artikel erfahren Sie, wie Sie eine R-Cliententwicklungs-Arbeitsstation so konfigurieren, dass Sie mit einer SQL Server-Remoteinstanz interagieren können, die für die Integration von Machine Learning und R aktiviert ist. Nachdem Sie die in diesem Artikel beschriebenen Schritte ausgeführt haben, verfügen Sie über dieselben R-Bibliotheken wie auf SQL Server. Außerdem erfahren Sie, wie Sie Berechnungen von einer lokalen R-Sitzung an eine R-Remotesitzung auf SQL Server übertragen.

![Client/Server-Komponenten](media/sqlmls-r-client-revo.png "Lokale und Remotesitzungen und -bibliotheken mit R")

Verwenden Sie zur Überprüfung der Installation wie in diesem Artikel beschrieben das integrierte **RGUI**-Tool, oder [verknüpfen Sie die Bibliotheken](#install-ide) mit RStudio oder einer anderen IDE, die Sie normalerweise verwenden.

> [!Note]
> Eine Alternative zur Installation einer Clientbibliothek ist die Verwendung eines [eigenständigen Servers](../install/sql-machine-learning-standalone-windows-install.md) als Rich Client. Einige Kunden bevorzugen diese Vorgehensweise, da sie eine eingehendere Szenariobearbeitung ermöglicht. Ein eigenständiger Server ist vollständig von SQL Server entkoppelt, kann aber als Client für datenbankinterne SQL Server-Analysen verwendet werden, da er über dieselben R-Bibliotheken verfügt. Sie können ihn auch für Aufgaben verwenden, die nicht im Zusammenhang mit SQL stehen, wie etwa den Import und die Modellierung von Daten von anderen Datenplattformen. Für die Installation eines eigenständigen Servers finden Sie die ausführbare R-Datei an folgendem Speicherort: `C:\Program Files\Microsoft SQL Server\140\R_SERVER`. Wenn Sie die Installation überprüfen möchten, [öffnen Sie eine R-Konsolen-App](#R-tools), um mithilfe der Datei „R.exe“ Befehle auszuführen.

## <a name="commonly-used-tools"></a>Häufig verwendete Tools

Unabhängig davon, ob Sie ein R-Entwickler sind, der zum ersten Mal mit SQL arbeitet, oder ein SQL-Entwickler, der noch keine Erfahrung mit R und datenbankinternen Analysen besitzt: Sie benötigen sowohl ein R-Entwicklungstool als auch einen T-SQL-Abfrage-Editor wie z. B. [SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md), um alle Funktionen der datenbankinternen Analysen nutzen zu können.

Für einfache R-Entwicklungsszenarien können Sie die ausführbare RGUI-Datei verwenden, die im Bundle in der Basis-R-Distribution in MRO und SQL Server enthalten ist. In diesem Artikel wird erläutert, wie Sie RGUI sowohl für lokale als auch Remote-R-Sitzungen verwenden. Um die Produktivität zu verbessern, sollten Sie eine IDE mit vollem Funktionsumfang verwenden, wie z. B. [RStudio oder Visual Studio](#install-ide).

Bei SSMS handelt es sich um einen separaten Download, der zum Erstellen und Ausführen von gespeicherten Prozeduren auf SQL Server nützlich ist, einschließlich derjenigen, die R-Code enthalten. Sie können nahezu jeden R-Code, den Sie in einer Entwicklungsumgebung schreiben, in eine gespeicherte Prozedur einbetten. Informationen zu [SSMS und eingebettetem R-Code](../tutorials/r-taxi-classification-introduction.md) finden Sie in weiteren Tutorials.

## <a name="1---install-r-packages"></a>1 – Installieren von R-Paketen

Die R-Pakete von Microsoft sind in mehreren Produkten und Diensten verfügbar. Auf einer lokalen Arbeitsstation sollten Sie Microsoft R Client installieren. Der R Client bietet [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler), [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package), [SQLRUtils](/machine-learning-server/r-reference/sqlrutils/sqlrutils) und andere R-Pakete.

1. [Herunterladen von Microsoft R Client](https://aka.ms/rclient/download).

2. Übernehmen oder ändern Sie im Installations-Assistenten den Standardinstallationspfad, akzeptieren oder ändern Sie die Liste der Komponenten, und akzeptieren Sie die Microsoft R Client-Lizenzbedingungen.

   Wenn die Installation abgeschlossen ist, erhalten Sie im Begrüßungsbildschirm eine Einführung zu Produkt und Dokumentation.

3. Erstellen Sie eine MKL_CBWR-Systemumgebungsvariable, um die konsistente Ausgabe über die Intel Math Kernel Library-Berechnungen (MKL) sicherzustellen.

   + Klicken Sie in der Systemsteuerung auf **System und Sicherheit** > **System** > **Erweiterte Systemeinstellungen** > **Umgebungsvariablen**.
   + Erstellen Sie eine neue Systemvariable mit dem Namen **MKL_CBWR**, wobei ein Wert auf **AUTO** festgelegt ist.

## <a name="2---locate-executables"></a>Schritt 2: Suchen nach ausführbaren Dateien

Suchen Sie den Inhalt des Installationsordners, und listen Sie ihn auf, um sicherzugehen, dass die Datei „R.exe“, RGUI und andere Pakete installiert sind. 

1. Öffnen Sie im Datei-Explorer den Ordner „C:\Programme\Microsoft\R Client\R_SERVER\bin folder“, um den Speicherort von „R. exe“ zu bestätigen.

2. Öffnen Sie den Unterordner „x64“, um **RGUI** zu bestätigen. Sie werden dieses Tool im nächsten Schritt verwenden.

3. Öffnen Sie „C:\Programme\Microsoft\R Client\R_SERVER\library“, um die Liste der mit dem R Client installierten Pakete zu überprüfen, unter anderem RevoScaleR und MicrosoftML.


<a name="R-tools"></a>
 
## <a name="3---start-rgui"></a>3 – Starten von RGUI

Wenn Sie R mit SQL Server installieren, erhalten Sie dieselben R-Tools, die für jede Basisinstallation von R Standard sind, wie z. B. RGui, Rterm usw. Diese Tools sind einfach und nützlich zum Überprüfen von Paket- und Bibliotheksinformationen, Ausführen von Ad-hoc-Befehlen bzw. -Skripts oder Durcharbeiten von Tutorials. Sie können diese Tools verwenden, um R-Versionsinformationen zu erhalten und die Konnektivität zu bestätigen.

1. Öffnen Sie „C:\Programme\Microsoft\R Client\R_SERVER\bin\x64“, und doppelklicken Sie auf **RGui**, um eine R-Sitzung mit einer R-Eingabeaufforderung zu starten.

   Wenn Sie eine R-Sitzung aus einem Microsoft-Programmordner starten, werden mehrere Pakete einschließlich RevoScaleR automatisch geladen. 

2. Geben Sie `print(Revo.version)` an der Eingabeaufforderung ein, um die Informationen zur RevoScaleR-Paketversion zurückzugeben. Sie sollten über die RevoScaleR-Version 9.2.1 oder 9.3.0 verfügen.

3. Geben Sie **search()** an der R-Eingabeaufforderung ein, um eine Liste der installierten Pakete zu erhalten.

   ![Versionsinformationen beim Laden von R](../install/media/rclient-rgui-r-prompt.png "Öffnen einer R-Eingabeaufforderung")


## <a name="4---get-sql-permissions"></a>Schritt 4: Anfordern von SQL-Berechtigungen

In R Client ist die R-Verarbeitung auf zwei Threads und In-Memory-Daten begrenzt. Bei der skalierbaren Verarbeitung mit mehreren Kernen und großen Datasets können Sie die Ausführung (als *Computekontext* bezeichnet) auf die Datasets und die Rechenleistung einer Remote-SQL Server-Instanz verschieben. Diese Vorgehensweise wird für die Clientintegration in eine Produktions-SQL Server-Instanz empfohlen, und Sie benötigen Berechtigungen und Verbindungsinformationen, damit dies funktioniert.

Wenn Sie eine Verbindung mit einer SQL Server-Instanz herstellen möchten, um Skripts auszuführen und Daten hochzuladen, benötigen Sie einen gültigen Anmeldenamen auf dem Datenbankserver. Sie können entweder einen SQL-Anmeldenamen oder die integrierte Windows-Authentifizierung verwenden. Im Allgemeinen wird die Verwendung der integrierten Windows-Authentifizierung empfohlen. Für einige Szenarios ist die Verwendung des SQL-Anmeldenamens jedoch einfacher, insbesondere wenn Ihr Skript Verbindungszeichenfolgen zu externen Daten enthält.

Das zum Ausführen von Code verwendete Konto muss mindestens über eine Berechtigung zum Lesen der Datenbanken verfügen, mit denen Sie arbeiten. Zudem ist die spezielle Berechtigung „EXECUTE ANY EXTERNAL SCRIPT“ erforderlich. Die meisten Entwickler benötigen auch Berechtigungen zum Erstellen von gespeicherten Prozeduren und zum Schreiben von Daten in Tabellen, die Trainingsdaten oder bewertete Daten enthalten. 

Bitten Sie den Datenbankadministrator, in der Datenbank, in der Sie R verwenden, die [folgenden Berechtigungen für Ihr Konto](../security/user-permission.md) zu konfigurieren:

+ **EXECUTE ANY EXTERNAL SCRIPT** zum Ausführen von R-Skripts auf dem Server.
+ **db_datareader** zum Ausführen der Abfragen, die zum Trainieren des Modells verwendet werden
+ **db_datawriter** zum Schreiben von Trainingsdaten oder bewerteten Daten
+ **db_owner** zum Erstellen von Objekten wie z. B. gespeicherte Prozeduren, Tabellen und Funktionen. 
  **db_owner** ist auch zum Erstellen von Beispiel- und Testdatenbanken erforderlich. 

Sind für Ihren Code Pakete erforderlich, die nicht standardmäßig mit SQL Server installiert werden, vereinbaren Sie mit dem Datenbankadministrator, dass die Pakete mit der Instanz installiert werden. SQL Server ist eine gesicherte Umgebung, in der es Einschränkungen hinsichtlich der Installation von Paketen gibt. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete auf SQL Server](../package-management/install-additional-r-packages-on-sql-server.md).

## <a name="5---test-connections"></a>5 – Testen von Verbindungen

Verwenden Sie als Überprüfungsschritt **RGUI** und RevoScaleR, um die Konnektivität mit dem Remoteserver zu bestätigen. SQL Server muss für [Remoteverbindungen](../../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md) aktiviert sein, und Sie müssen über Berechtigungen verfügen, einschließlich einer Benutzeranmeldung und einer Datenbank, mit der eine Verbindung hergestellt werden soll. 

In den folgenden Schritten werden die Demodatenbank [NYCTaxi_Sample](../tutorials/demo-data-nyctaxi-in-sql.md) und Windows-Authentifizierung vorausgesetzt.

1. Öffnen Sie **RGUI** auf der Clientarbeitsstation. Wechseln Sie z. B. zu `~\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64`, und doppelklicken Sie auf **RGui.exe**, um sie zu starten.

2. RevoScaleR wird automatisch geladen. Bestätigen Sie, dass RevoScaleR betriebsbereit ist, indem Sie diesen Befehl ausführen: `print(Revo.version)`

3. Geben Sie ein Demoskript ein, das auf dem Remoteserver ausgeführt wird. Sie müssen das folgende Beispielskript so ändern, dass ein gültiger Name für eine Remote-SQL Server-Instanz enthalten ist. Diese Sitzung beginnt als lokale Sitzung, aber die **rxSummary**-Funktion wird auf der Remote-SQL Server-Instanz ausgeführt.

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

   Dieses Skript stellt eine Verbindung mit einer Datenbank auf dem Remoteserver her, erstellt eine Computekontext-`cc`-Anweisung für die Remotecodeausführung und stellt dann die RevoScaleR-Funktion **rxSummary** zur Rückgabe einer statistischen Zusammenfassung der Abfrageergebnisse bereit.

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

4. Rufen Sie den Computekontext ab, und legen Sie ihn fest. Nachdem Sie einen Computekontext festgelegt haben, bleibt er für die Dauer der Sitzung wirksam. Wenn Sie nicht sicher sind, ob die Berechnung lokal oder remote erfolgt, führen Sie den folgenden Befehl aus, um dies festzustellen. Ergebnisse, die eine Verbindungszeichenfolge angeben, weisen auf einen Remotecomputekontext hin.

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

5. Rückgabe von Informationen zu Variablen in der Datenquelle einschließlich Name und Typ.

   ```R
   rxGetVarInfo(data = inDataSource)
   ```
   Die Ergebnisse enthalten 23 Variablen.


6. Generieren Sie ein Punktdiagramm, um zu überprüfen, ob Abhängigkeiten zwischen zwei Variablen vorhanden sind. 

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

   Der folgende Screenshot zeigt die Eingabe sowie die Ausgabe als Punktdiagramm:

   ![Punktdiagramm in RGUI](media/rclient-setup-scatterplot.png "Punktdiagramm für NYC Taxi-Demodaten")

<a name="install-ide"></a>

## <a name="6---link-tools-to-rexe"></a>6 – Verknüpfen von Tools mit „R.exe“

Für dauerhafte und wichtige Entwicklungsprojekte sollten Sie eine integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) installieren. SQL Server-Tools und die integrierten R-Tools sind nicht für eine komplexe R-Entwicklung konzipiert. Sobald Sie über einen funktionierenden Code verfügen, können Sie ihn als gespeicherte Prozedur zur Ausführung auf SQL Server bereitstellen.

Verweisen Sie Ihre IDE auf die lokalen R-Bibliotheken: base R, RevoScaleR usw. Workloads werden auf einer Remote-SQL Server-Instanz während der Ausführung des Skripts ausgeführt, wenn Ihr Skript einen Remotecomputekontext auf SQL Server aufruft und auf diesem Server auf Daten und Vorgänge zugreift.

### <a name="rstudio"></a>RStudio

Wenn Sie [RStudio](https://www.rstudio.com/) verwenden, können Sie die Umgebung so konfigurieren, dass die R-Bibliotheken und ausführbaren Dateien verwendet werden, die denjenigen auf einer Remote-SQL Server-Instanz entsprechen.

1. Überprüfen Sie die auf SQL Server installierten R-Paketversionen. Weitere Informationen finden Sie unter [Abrufen von Paketinformationen für R](../package-management/r-package-information.md).

1. Installieren Sie Microsoft R Client oder eine der eigenständigen Serveroptionen, um RevoScaleR und andere R-Pakete hinzuzufügen, einschließlich der von Ihrer SQL Server-Instanz verwendeten Basis-R-Verteilung. Wählen Sie eine Version auf derselben Ebene oder niedriger (Pakete sind abwärtskompatibel), die die gleichen Paketversionen wie auf dem Server bietet. Versionsinformationen finden Sie in diesem Artikel in der Versionszuordnung: [Upgrade von R- und Python-Komponenten](../install/upgrade-r-and-python.md).

1. [Aktualisieren Sie Ihren R-Pfad](https://support.rstudio.com/hc/articles/200486138-Using-Different-Versions-of-R) in RStudio, sodass er auf die R-Umgebung verweist, die RevoScaleR, Microsoft R Open und andere Microsoft-Pakete bereitstellt. 

   + Um eine R Client-Installation zu finden, suchen Sie nach „C:\Programme\Microsoft\R Client\R_SERVER\bin\x64“.
   + Um einen eigenständigen Server zu finden, suchen Sie nach „C:\Programme\Microsoft SQL Server\140\R_SERVER\Library“ oder „C:\Programme\Microsoft SQL Server\130\R_SERVER\Library“.

1. Schließen Sie RStudio, und öffnen Sie es erneut.

Wenn Sie RStudio erneut öffnen, ist die ausführbare R-Datei von R Client (oder des eigenständigen Servers) die Standard-R-Engine.


### <a name="r-tools-for-visual-studio-rtvs"></a>R-Tools für Visual Studio (RTVS)

Wenn Sie nicht bereits über eine bevorzugte IDE für R verfügen, sollten Sie **R Tools für Visual Studio** verwenden.

+ [Herunterladen von R-Tools für Visual Studio (RTVS)](https://marketplace.visualstudio.com/items?itemName=MikhailArkhipov007.RTVS2019)
+ [Installationsanweisungen](/visualstudio/rtvs/installing-r-tools-for-visual-studio) – RTVS sind in verschiedenen Versionen von Visual Studio verfügbar.
+ [Erste Schritte mit den R Tools für Visual Studio](/visualstudio/rtvs/getting-started-with-r)

### <a name="connect-to-sql-server-from-rtvs"></a>Herstellen einer Verbindung mit SQL Server von RTVS aus

In diesem Beispiel wird Visual Studio 2017 Community Edition verwendet, wobei die Data Science-Workload installiert ist.

1. Wählen Sie im Menü **Datei** die Option **Neu**aus, und wählen Sie dann **Projekt** aus.

2. Der linke Bereich enthält eine Liste vorinstallierter Vorlagen. Klicken Sie auf **R**, und wählen Sie **R-Projekt**aus. Geben Sie im Feld **Name**`dbtest` ein, und klicken Sie auf **OK**. 

   Visual Studio erstellt einen neuen Projektordner und eine Standardskriptdatei, `Script.R`. 

3. Geben Sie `.libPaths()` in der ersten Zeile der Skriptdatei ein, und drücken Sie dann STRG+EINGABETASTE.

   Der aktuelle R-Bibliothekspfad sollte im Fenster **R Interactive** angezeigt werden. 

4. Klicken Sie auf das Menü **R-Tools**, und wählen Sie **Windows** aus, um eine Liste anderer R-spezifischer Fenster anzuzeigen, die Sie in Ihrem Arbeitsbereich anzeigen können.
 
   + Um Hilfe zu Paketen in der aktuellen Bibliothek anzuzeigen, drücken Sie STRG+3.
   + Um R-Variablen im **Variablen-Explorer** anzuzeigen, drücken Sie STRG+8.

## <a name="next-steps"></a>Nächste Schritte

Zwei verschiedene Tutorials enthalten Übungen, mit denen Sie das Umschalten des Computekontexts von lokal zu einer Remote-SQL Server-Instanz üben können.

+ [Tutorial: Verwenden von RevoScaleR-Funktionen für R mit SQL Server-Daten](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [Lückenlose exemplarische Data Science-Vorgehensweise](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)