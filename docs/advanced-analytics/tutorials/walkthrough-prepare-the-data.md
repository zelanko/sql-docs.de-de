---
title: Vorbereiten der Daten mithilfe von PowerShell (Exemplarische Vorgehensweise) | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 5206213c06b283e8736dea8079f6909149e670e9
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703678"
---
# <a name="prepare-the-data-using-powershell-walkthrough"></a>Vorbereiten der Daten mithilfe von PowerShell (Exemplarische Vorgehensweise)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Zu diesem Zeitpunkt sollten Sie eine der folgenden Produkte installiert haben:

+ SQL Server 2016 R Services
+ SQL Server 2017 Machine Learning Services, mit der Sprache R aktiviert

In dieser Lektion Laden Sie die Daten, R-Pakete und R-Skripts verwendet, in der exemplarischen Vorgehensweise aus einem Github-Repository herunter. Sie können alles, was mithilfe eines PowerShell-Skripts der Einfachheit halber herunterladen.

Sie müssen auch einige zusätzliche R-Pakete, sowohl auf dem Server als auch auf Ihrer R-Arbeitsstation installieren. Es werden die Schritte beschrieben.

Anschließend verwenden Sie ein zweites Powershellskript, runsql_r_walkthrough. ps1, die Datenbank zu konfigurieren, die für die Modellierung und Bewertung verwendet wird. Skript ein Massenladen von Daten in die Datenbank ausgeführt. Sie geben, und erstellt dann eine SQL-Funktionen und gespeicherten Prozeduren, die Data Science-Aufgaben zu vereinfachen.

Fangen wir an!

## <a name="1-download-the-data-and-scripts"></a>1. Herunterladen der Daten und Skripts

Der benötigte Code wurde in einem GitHub-Repository bereitgestellt. Mithilfe eines PowerShell-Skripts können Sie eine lokale Kopie der Dateien erstellen.

1.  Öffnen Sie auf Ihrem Data Science-Clientcomputer eine Windows PowerShell-Eingabeaufforderung als Administrator.

2.  Führen Sie diesen Befehl aus, um das heruntergeladene Skript fehlerfrei ausführen zu können: Damit werden vorübergehend Skripts ohne Änderung der Standardeinstellungen des Systems zugelassen.

    ```
    Set-ExecutionPolicy Unrestricted -Scope Process -Force
    ```
      
3.  Führen Sie den folgenden Powershell-Befehl zum Herunterladen von Skriptdateien in ein lokales Verzeichnis aus. Wenn Sie kein anderes Verzeichnis angeben, werden standardmäßig den Ordner `C:\tempR` wird erstellt und alle Dateien, die dort gespeichert.
  
    ```
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_R_Walkthrough.ps1'  
    $ps1_dest = "$pwd\Download_Scripts_R_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_R_Walkthrough.ps1 –DestDir 'C:\tempR'
    ```
  
    Wenn Sie die Dateien in einem anderen Verzeichnis speichern möchten, bearbeiten Sie die Werte des Parameters *DestDir* , und geben Sie einen anderen Ordner auf Ihrem Computer an. Wenn Sie einen Ordnernamen eingeben, der nicht vorhanden ist, erstellt das PowerShell-Skript den Ordner für Sie.
  
4.  Das Herunterladen kann eine Weile dauern. Wenn es abgeschlossen ist, sollte die Windows PowerShell-Befehlskonsole wie folgt aussehen:
  
    ![Nach Abschluss des PowerShell-Skripts](media/rsql-e2e-psscriptresults.PNG "Nach Abschluss des PowerShell-Skripts")
  
5.  Führen Sie in der PowerShell-Konsole den Befehl `ls` zum Anzeigen einer Liste der Dateien aus, die in *DestDir*heruntergeladen wurden.  Eine Beschreibung der Dateien, finden Sie unter [Neige geht](#whats-included-in-the-sample).

## <a name="2-install-required-r-packages"></a>2. Installieren der erforderlichen R-Pakete

Diese exemplarische Vorgehensweise erfordert einige R-Bibliotheken, die nicht standardmäßig als Teil von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]installiert sind. Sie müssen die Pakete jeweils auf dem Client installieren, wo Sie die Lösung entwickeln und auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computer, in dem Sie die Lösung bereitstellen.

### <a name="install-required-packages-on-the-client"></a>Installieren der erforderlichen Pakete auf dem Client

Das R-Skript, das Sie heruntergeladen haben, enthält die Befehle zum Herunterladen und Installieren der Pakete.

1. Öffnen Sie die Skriptdatei RSQL_R_Walkthrough.R in Ihrer R-Umgebung.

2. Markieren Sie diese Zeilen, und führen Sie sie aus.
    
    ```
    # Install required R libraries, if they are not already installed.
    if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
    if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
    if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
    if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
    ```
    
    Einige Pakete installieren ferner erforderlichen Pakete. Insgesamt sind etwa 32 Pakete erforderlich.

### <a name="install-required-packages-on-the-server"></a>Installieren der erforderlichen Pakete auf dem Server

Es gibt viele verschiedene Möglichkeiten, die Sie Pakete auf SQL Server installieren können. Z. B. SQL Server bietet [R-paketverwaltung](../r/install-additional-r-packages-on-sql-server.md) -Feature, können Datenbankadministratoren, erstellen Sie ein paketrepository, und weisen Sie Benutzer die Rechte, um ihre eigenen Pakete zu installieren. Jedoch wenn Sie ein Administrator auf dem Computer sind, können Sie neue Pakete, die mithilfe von R, installieren, solange Sie in der richtigen Bibliothek installieren.

> [!NOTE]
> Auf dem Server **nicht** in einer Benutzerbibliothek installieren, auch wenn Sie dazu aufgefordert werden. Wenn Sie in einer Benutzerbibliothek installieren, SQL Server-Instanz nicht gefunden, oder führen Sie die Pakete. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete in SQL Server](../r/install-additional-r-packages-on-sql-server.md).

1. Öffnen Sie auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computer **als Administrator** RGui.exe.  Wenn Sie SQL Server R Services mithilfe der Standardeinstellungen installiert haben, finden Sie RGui.exe unter C:\Programme\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64).

2.  Führen Sie an einer R-Eingabeaufforderung die folgenden R-Befehle aus:
  
    ```
    install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
    install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
    install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
    install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
    ```

    - Dieses Beispiel verwendet die "GREP"-Funktion von R, suchen den Vektor der verfügbaren Pfade aus, und suchen Sie den Pfad an, der "Program Files" enthält. Weitere Informationen finden Sie unter [ https://www.rdocumentation.org/packages/base/functions/grep ](https://www.rdocumentation.org/packages/base/functions/grep).

    - Sollten Sie die Pakete bereits installiert haben, überprüfen Sie die Liste der installierten Pakete mit `installed.packages()`.

## <a name="3-prepare-the-environment-using-runsqlrwalkthroughps1"></a>3. Vorbereiten der Umgebung mit runsql_r_walkthrough. ps1

Zusammen mit den Datendateien, R-Skripts und T-SQL-Skripts, der Download enthält das PowerShell-Skript `RunSQL_R_Walkthrough.ps1`. Das Skript führt folgende Aktionen aus:

- Überprüft, ob der SQL Native Client und das Befehlszeilenprogrammen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert sind. Die Befehlszeilentools werden für die Ausführung des [Hilfsprogramms bcp](../../tools/bcp-utility.md) benötigt, das für schnelles Massenladen von Daten in SQL-Tabellen verwendet wird.

- Stellt eine Verbindung mit der angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her und führt einige [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts aus, die die Datenbank konfigurieren und die Tabellen für das Modell und die Daten erstellen.

- Führt eine SQL-Skript aus, um mehrere gespeicherte Prozeduren zu erstellen.

- Lädt die Daten, die Sie zuvor heruntergeladen haben, in die Tabelle `nyctaxi_sample`.

- Schreibt die Argumente in der R-Skriptdatei neu, um den von Ihnen angegebenen Datenbanknamen zu verwenden.

Führen Sie dieses Skript auf dem Computer, in dem Sie die Projektmappe erstellen: z. B. der Laptop, in dem Sie entwickeln und Testen Ihren R-Code. Dieser Computer, den wir als Data Science-Client bezeichnen, muss in der Lage sein, eine Verbindung zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computer mithilfe des Named Pipes-Protokolls herzustellen.

1. Öffnen Sie eine PowerShell-Befehlszeile **als Administrator**.
  
2.  Navigieren Sie zu dem Ordner, in dem Sie die Skripts heruntergeladen haben, und geben Sie den Namen des Skripts an, wie hier veranschaulicht. Drücken Sie die EINGABETASTE.

    ```
    .\RunSQL_R_Walkthrough.ps1
    ```
  
3.  Sie werden aufgefordert, für jede der folgenden Parameter:
  
    **Name des Datenbankservers**: der Name der SQL Server-Instanz, auf dem Machine learning-Services oder R Services installiert ist.

    Je nach Netzwerkanforderungen muss der Instanzname ggf. mit einem oder mehreren Subnetznamen qualifiziert werden.  Wenn beispielsweise MYSERVER nicht funktioniert, versuchen Sie „myserver.subnet.mycompany.com“.
    
    **Name der zu erstellenden Datenbank**: Geben Sie z.B. **Tutorial** oder **Taxi** ein.

    **Benutzername**: Geben Sie ein Konto an, das über Zugriffsberechtigungen für die Datenbanken verfügt. Zwei Optionen stehen zur Verfügung:
    
    + Geben Sie den Namen einer SQL-Anmeldung mit CREATE DATABASE-Berechtigungen und das SQL-Kennwort an einer nachfolgenden Eingabeaufforderung an.
    + Drücken Sie die EINGABETASTE, ohne einen Namen einzugeben, damit Ihre eigene Windows-Identität verwendet wird. Geben Sie anschließend an der geschützten Eingabeaufforderung Ihr Windows-Kennwort ein. PowerShell unterstützt nicht das Eingeben eines anderen Windows-Benutzernamens.
    + Wenn Sie einen gültigen Benutzer angeben, wird standardmäßig das Skript, mit der integrierten Windows-Authentifizierung.
    
      > [!WARNING]
      > Wenn Sie die Aufforderung im PowerShell-Skript verwenden, Ihre Anmeldeinformationen angeben, wird das Kennwort in die aktualisierte Skriptdatei im nur-Text geschrieben. Bearbeiten Sie die Datei sofort nach dem Erstellen der erforderlichen R-Objekte, um die Anmeldeinformationen zu entfernen.
      
    **Pfad der CSV-Datei**: Geben Sie den vollständigen Pfad zur Datendatei an. Der Standard für Pfad und Dateiname ist `C:\tempR\nyctaxi1pct.csv`.
  
4.  Drücken Sie die EINGABETASTE, um das Skript auszuführen.

    Das Skript sollte die Datei herunterladen und die Daten automatisch in die Datenbank laden. Dies kann eine Weile dauern. Beobachten Sie die Statusmeldungen im PowerShell-Fenster.
      
    Wenn Massenimport oder jeder anderen Schritt ein Fehler auftritt, können Sie die Daten manuell, wie in beschrieben laden die [Problembehandlung](#bkmk_Troubleshooting) Abschnitt.

**Ergebnisse (erfolgreicher Abschluss)**

```
Execution successful
Completed registering all stored procedures used in this walkthrough.
This step (registering all stored procedures) takes 0.39 seconds.
Plug in the database server name, database name, user name and password into the R script file
This step (plugging in database information) takes 0.48 seconds.
```

Klicken Sie auf diesen Link, um zur nächsten Lektion wechseln: [anzeigen und Durchsuchen von Daten mit SQL](walkthrough-view-and-explore-the-data.md)

## <a name="bkmk_Troubleshooting"></a>Problembehandlung

Wenn Sie Probleme in Bezug auf das PowerShell-Skript verfügen, können Sie alle oder einige der Schritte manuell ausführen verwenden die Zeilen des PowerShell-Skripts als Beispiele. Dieser Abschnitt enthält einige häufig auftretende Probleme und problemumgehungen.

### <a name="powershell-script-didnt-download-the-data"></a>PowerShell-Skript hat die Daten nicht heruntergeladen

Um die Daten manuell herunterzuladen, klicken Sie mit der rechten Maustaste auf den folgenden Link, und wählen Sie **Ziel speichern unter**aus.

[https://getgoing.blob.core.windows.net/public/nyctaxi1pct.csv](https://getgoing.blob.core.windows.net/public/nyctaxi1pct.csv)

Notieren Sie den Pfad zu der heruntergeladenen Datendatei und dem Dateinamen, unter der bzw. dem die Daten gespeichert wurden. Sie benötigen den vollständigen Pfad zum Laden der Daten in die Tabelle mithilfe **Bcp**.

### <a name="unable-to-download-the-data"></a>Daten konnten nicht heruntergeladen werden

Die Datendatei ist groß. Müssen Sie einen Computer, die eine relativ gute Internetverbindung verwenden, oder der Download kein Timeout eintritt.

### <a name="could-not-connect-or-script-failed"></a>Fehler bei der Verbindungsherstellung oder Skriptfehler

Möglicherweise wird Ihnen beim Ausführen eines der Skripts folgender Fehler angezeigt: *Netzwerkbezogener oder instanzspezifischer Fehler beim Herstellen einer Verbindung mit SQL Server*

+ Überprüfen Sie die Schreibweise des Instanznamens.
+ Überprüfen Sie die vollständige Verbindungszeichenfolge.
+ Je nach Netzwerkanforderungen muss der Instanzname ggf. mit einem oder mehreren Subnetznamen qualifiziert werden.  Wenn beispielsweise MYSERVER nicht funktioniert, versuchen Sie „myserver.subnet.mycompany.com“.
+ Überprüfen Sie, ob die Windows-Firewall Verbindungen von SQL Server zulässt.
+ Versuchen Sie, Ihren Server zu registrieren, und stellen Sie sicher, dass er Remoteverbindungen zulässt.
+ Wenn Sie eine benannte Instanz verwenden, können Sie den SQL-Browser aktivieren, um Verbindungen zu erleichtern.

### <a name="network-error-or-protocol-not-found"></a>Netzwerkfehler oder Protokoll nicht gefunden

+ Stellen Sie sicher, dass die Instanz die Remoteverbindungen unterstützt.
+ Stellen Sie sicher, dass der angegebene SQL-Benutzer eine Remoteverbindung zur Datenbank herstellen kann.
+ Aktivieren Sie Named Pipes auf der Instanz.
+ Überprüfen Sie die Berechtigungen des Kontos. Das Konto, das Sie angegeben haben, verfügt möglicherweise nicht über die Berechtigungen, eine neue Datenbank zu erstellen und Daten hochzuladen.

### <a name="bcp-did-not-run"></a>bcp wurde nicht ausgeführt

+ Überprüfen Sie, ob das Hilfsprogramm [bcp](../../tools/bcp-utility.md) auf Ihrem Computer verfügbar ist. Sie können **bcp** entweder in einem PowerShell-Fenster oder an einer Windows-Eingabeaufforderung ausführen.
+ Wenn Sie eine Fehlermeldung erhalten, fügen Sie den Speicherort des Hilfsprogramms **bcp** zur Systemumgebungsvariablen PATH hinzu, und versuchen Sie es erneut.

### <a name="the-table-schema-was-created-but-the-table-has-no-data"></a>Das Tabellenschema wurde erstellt, aber die Tabelle enthält keine Daten

Wenn der Rest des Skripts ohne Probleme ausgeführt wurde, können Sie die Daten manuell in die Tabelle laden, indem Sie **bcp** über die Befehlszeile wie folgt aufrufen:

#### <a name="using-a-sql-login"></a>Verwenden einer SQL-Anmeldung

~~~~
bcp TutorialDB.dbo.nyctaxi_sample in c:\tempR\nyctaxi1pct.csv -t ',' -S rtestserver.contoso.com -f C:\tempR\taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U <SQL login> -P <password>
~~~~

#### <a name="using-windows-authentication"></a>Verwenden der Windows-Authentifizierung

~~~~
bcp TutorialDB.dbo.nyctaxi_sample in c:\tempR\nyctaxi1pct.csv -t ',' -S rtestserver.contoso.com -f C:\tempR\taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -T
~~~~

+ Die `in` -Schlüsselwort Gibt die Richtung der datenverschiebung an.
+ Das Argument  **-f** erfordert, dass Sie den vollständigen Pfad einer Formatdatei angeben. Eine Formatdatei ist erforderlich, wenn Sie die Option **in** verwenden.
+ Verwenden Sie die Argumente **-U** und **-P** , wenn bcp mit einer SQL-Anmeldung ausgeführt wird.
+ Verwenden Sie das Argument **-T** bei Verwendung der integrierten Windows-Authentifizierung.

Wenn das Skript die Daten nicht lädt, sollten Sie die Syntax überprüfen und sicherstellen, dass Ihr Servername für Ihr Netzwerk richtig angegeben ist. Stellen Sie zum Beispiel sicher, dass alle Subnetze enthalten sind, und schließen Sie den Computernamen ein, wenn Sie eine Verbindung zu einer benannten Instanz herstellen. Stellen Sie sicher, dass es sich bei die Anmeldung die Bulk-Uploads führen kann.

### <a name="i-want-to-run-the-script-without-prompts"></a>Ausführen des Skripts ohne Aufforderung

Sie können alle Parameter mithilfe dieser Vorlage mit spezifischen Werten für Ihre Umgebung in einer einzigen Befehlszeile angeben.

```
.\RunSQL_R_Walkthrough.ps1 -server <server address> -dbname <new db name> -u <user name> -p <password> -csvfilepath <path to csv file>
```

Im folgenden Beispiel wird das Skript mit einer SQL-Anmeldung ausgeführt:

```
.\RunSQL_R_Walkthrough.ps1 -server MyServer.subnet.domain.com -dbname MyDB –u SqlUserName –p SqlUsersPassword -csvfilepath C:\temp\nyctaxi1pct.csv
```

-   Stellt eine Verbindung mit der angegebenen Instanz und Datenbank mithilfe der Anmeldeinformationen von *SqlUserName*her.
-   Ruft Daten aus der Datei *C:\temp\nyctaxi1pct.csv*ab.
-   Lädt die Daten in die Tabelle *dbo.nyctaxi_sample*in der Datenbank *MyDB* auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz mit dem Namen *MyServer*.

### <a name="the-data-loaded-but-it-contains-duplicates"></a>Die Daten werden geladen, enthalten aber Duplikate

Wenn die Datenbank auf eine vorhandene Tabelle mit dem gleichen Namen und das gleiche Schema enthält **Bcp** Fügt eine neue Kopie der Daten anstelle von Überschreiben vorhandener Daten.

Um doppelte Daten zu vermeiden, schneiden Sie vorhandenen Tabellen, bevor Sie das Skript erneut ausführen.

## <a name="whats-included-in-the-sample"></a>Was ist im Beispiel enthalten.

Wenn Sie die Dateien aus dem GitHub-Repository herunterladen, erhalten Sie Folgendes:

+ Daten im CSV-format finden Sie unter [Trainings- und Bewertungsdaten](#bkmk_data) Details
+ Ein PowerShell-Skript für die Vorbereitung der Umgebung
+ Eine XML-Formatdatei für das Importieren der Daten mithilfe von bcp in SQL Server
+ Mehrere T-SQL-Skripts
+ Den gesamten R-Code, den Sie in dieser exemplarischen Vorgehensweise ausführen müssen

### <a name="bkmk_data"></a>Trainings- und Bewertungsdaten

Die Daten stellen einen repräsentativen Querschnitt des Datasets New York City Taxi dar, das Datensätze von über 173 Millionen Fahrten aus dem Jahr 2013 enthält, einschließlich der Fahrpreise und Trinkgelder, die für jede Fahrt gezahlt wurden. Damit Sie mit den Daten einfacher arbeiten können, hat das Microsoft Data-Science-Team diese verkleinert, damit nur noch 1 % der Daten abgerufen werden.  Diese Daten wurden in einem öffentlichen Blob-Speichercontainer in Azure im CSV-Format freigegeben. Die Quelldaten ist eine unkomprimierte Datei ganz 350 MB.

+ Öffentliches Dataset: [NYC Taxi and Limousine Commission](https://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)

+ [Erstellen von Azure Machine Learning-Modellen für das NYC Taxi-Dataset](https://blogs.technet.microsoft.com/machinelearning/2015/04/02/building-azure-ml-models-on-the-nyc-taxi-dataset/).

### <a name="powershell-and-r-script-files"></a>PowerShell und R-Skriptdateien

+ **Runsql_r_walkthrough. ps1** Sie führen dieses Skript zuerst, mithilfe von PowerShell. Es ruft die SQL-Skripts zum Laden von Daten in die Datenbank auf.

+ **taxiimportfmt.xml** Eine Formatdefinitionsdatei, die vom Hilfsprogramm bcp zum Laden von Daten in die Datenbank verwendet wird.

+ **RSQL_R_Walkthrough.R** Dies ist das grundlegende R-Skript, das in den übrigen Lektionen für die Datenanalyse und Modellierung verwendet wird. Es stellt den gesamten R-Code bereit, den Sie zum Durchsuchen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten, zum Erstellen des Klassifizierungsmodells und zum Erstellen von Diagrammen benötigen.

### <a name="t-sql-script-files"></a>T-SQL-Skriptdateien

Das PowerShell-Skript führt mehrere [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts auf SQL Server-Instanz. Die folgende Tabelle enthält die [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts und was sie tun.

|Name der SQL-Skriptdatei|Description|
|------------------------|----------------|
|create-db-tb-upload-data.sql|Erstellt die Datenbank und zwei Tabellen:<br /><br /> *nyctaxi_sample*: Tabelle, in der die trainierten Daten gespeichert sind – ein 1 %-Beispiel des Datasets NYC Taxi. Ein gruppierter Columnstore-Index wird der Tabelle hinzugefügt, um die Speicher- und Abfrageleistung zu verbessern.<br /><br /> *Nyc_taxi_models*: eine Tabelle zum Speichern der trainierten Modelle im binären Format verwendet.|
|PredictTipBatchMode.sql|Erstellt eine gespeicherte Prozedur, die ein trainiertes Modell zum Vorhersagen der Bezeichnungen für neue Beobachtungen aufruft. Sie akzeptiert eine Abfrage als Eingabeparameter.|
|PredictTipSingleMode.sql|Erstellt eine gespeicherte Prozedur, die ein trainiertes Klassifizierungsmodell zum Vorhersagen der Bezeichnungen für neue Beobachtungen aufruft. Variablen der neuen Beobachtungen werden als Inlineparameter übergeben.|
|PersistModel.sql|Erstellt eine gespeicherte Prozedur, mit der die binäre Darstellung des Klassifizierungsmodells in eine Tabelle in der Datenbank gespeichert werden kann.|
|fnCalculateDistance.sql|Erstellt eine SQL-Skalarwertfunktion, die die direkte Entfernung zwischen Abhol-und Zielorten berechnet.|
|fnEngineerFeatures.sql|Erstellt eine SQL-Tabellenwertfunktion, die Funktionen zum Trainieren des Klassifizierungsmodells erstellt|

Die T-SQL-Abfragen in dieser exemplarischen Vorgehensweise wurden getestet und als ausgeführt werden können – befindet sich in Ihrem R-Code. Wenn Sie jedoch weiter experimentieren oder Ihre eigene Lösung entwickeln möchten, empfiehlt es sich, eine dedizierte SQL-Entwicklungsumgebung zu verwenden, um Ihre Abfragen zunächst zu testen und zu optimieren, bevor Sie sie Ihrem R-Code hinzufügen.

+ Die [MSSQL-Erweiterung](https://code.visualstudio.com/docs/languages/tsql) für [Visual Studio Code](https://code.visualstudio.com/) ist eine kostenlose, unkomplizierte Umgebung zum Ausführen von Abfragen, die auch die meisten Entwicklungsaufgaben für Datenbanken unterstützt.
+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) ist ein leistungsstarkes und dennoch kostenloses Tool für die Entwicklung und Verwaltung von SQL Server-Datenbanken.

## <a name="next-lesson"></a>Nächste Lektion

[Anzeigen und Durchsuchen von Daten mithilfe von R und SQL](walkthrough-view-and-explore-the-data.md)

## <a name="previous-lesson"></a>Vorherige Lektion

[End-to-End-Data Science Walkthrough für R und SQL Server](walkthrough-data-science-end-to-end-walkthrough.md)

