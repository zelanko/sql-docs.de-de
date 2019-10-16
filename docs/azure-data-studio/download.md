---
title: Zur Installation herunterladen können Sie
titleSuffix: Azure Data Studio
description: Laden Sie Azure Data Studio für Windows, macOS oder Linux herunter, und installieren Sie es.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.custom: seodec18
ms.date: 10/08/2019
ms.reviewer: alayu; sstein
ms.openlocfilehash: d56bf097bc38670fb7bad83933a1a48800172d5b
ms.sourcegitcommit: 79e6d49ae4632f282483b0be935fdee038f69cc2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2019
ms.locfileid: "72173155"
---
# <a name="download-and-install-azure-data-studio"></a>Herunterladen und Installieren von Azure Data Studio

[!INCLUDE[name-sos](../includes/name-sos.md)] kann unter Windows, macOS und Linux ausgeführt werden.


Laden Sie das neueste *Release vom Oktober* herunter, und installieren Sie es:

> [!NOTE]
> Wie Sie bei einem Update von SQL Operations Studio Ihre Einstellungen, Tastenkombinationen und Codeausschnitte beibehalten können, erfahren Sie unter [Übernehmen von Benutzereinstellungen](#move-user-settings).

|Platform|Herunterladen|Veröffentlichungsdatum| Versionsoptionen |
|:---|:---|:---|:---|
|Windows|[Benutzer-Installationsprogramm (empfohlen)](https://go.microsoft.com/fwlink/?linkid=2105135)<br>[System-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2105134)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2104938)|8\. Oktober 2019 |1.12.1|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2105133)|8\. Oktober 2019 |1.12.1|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=2105131)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2104937)<br>[.tar.gz](https://azuredatastudiobuilds.blob.core.windows.net/releases/1.12.1/azuredatastudio-linux-1.12.1.tar.gz)|8\. Oktober 2019 |1.12.1|

Weitere Informationen über die neueste Version finden Sie in den [Versionshinweisen](release-notes.md).

## <a name="get-azure-data-studio-for-windows"></a>Azure Data Studio für Windows

Dieses Release von [!INCLUDE[name-sos](../includes/name-sos-short.md)] enthält das standardmäßige Windows-Installationsprogramm und eine ZIP-Datei.

Das *Benutzer-Installationsprogramm* wird empfohlen, da dafür keine Administratorrechte erforderlich sind, was Installation und Upgrades vereinfacht. Für das Benutzer-Installationsprogramm sind keine Administratorrechte erforderlich, da sich der Speicherort im lokalen Ordner „AppData“ (LOCALAPPDATA) des Benutzers befindet. Zudem bietet das Benutzer-Installationsprogramm eine einfachere Aktualisierung im Hintergrund. Weitere Informationen finden Sie unter [Benutzersetup für Windows](https://code.visualstudio.com/updates/v1_26#_user-setup-for-windows).

**Benutzer-Installationsprogramm** (empfohlen)

1. Laden Sie das [[!INCLUDE[name-sos](../includes/name-sos-short.md)]-*Benutzer*-Installationsprogramm für Windows](https://go.microsoft.com/fwlink/?linkid=2105135) herunter, und führen Sie es aus.
2. Starten Sie die [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]-App.

**System-Installationsprogramm**

1. Laden Sie das [[!INCLUDE[name-sos](../includes/name-sos-short.md)]-*System*-Installationsprogramm für Windows](https://go.microsoft.com/fwlink/?linkid=2105134) herunter, und führen Sie es aus.
2. Starten Sie die [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]-App.

**zip-Datei**

1. Laden Sie die [[!INCLUDE[name-sos](../includes/name-sos-short.md)]-ZIP-Datei für Windows](https://go.microsoft.com/fwlink/?linkid=2104938) herunter.
2. Navigieren Sie zur heruntergeladenen Datei, und extrahieren Sie sie.
3. Ausführen von `\azuredatastudio-windows\azuredatastudio.exe`


## <a name="get-azure-data-studio-for-macos"></a>Azure Data Studio für macOS

1. Laden Sie [[!INCLUDE[name-sos](../includes/name-sos-short.md)] für macOS](https://go.microsoft.com/fwlink/?linkid=2105133) herunter.
2. Doppelklicken Sie auf die ZIP-Datei, um die Inhalte zu erweitern.
3. Wenn Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)] im *Launchpad* verfügbar machen wollen, können Sie *Azure Data Studio.app* in den Ordner *Programme* ziehen.


## <a name="get-azure-data-studio-for-linux"></a>Azure Data Studio für Linux

1. Laden Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)] für Linux herunter, indem Sie eines der Installationsprogramme oder das Archiv „tar.gz“ verwenden:
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2103004)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2104937)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2105131)
1. Öffnen Sie ein neues Terminalfenster, und geben Sie die folgenden Befehle ein, um die Datei zu extrahieren und [!INCLUDE[name-sos](../includes/name-sos-short.md)] zu starten:

   **Debian-Installation:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **rpm-Installation:**
   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **tar.gz-Installation:**
   ```bash 
   cd ~ 
   cp ~/Downloads/azuredatastudio-linux-<version string>.tar.gz ~ 
   tar -xvf ~/azuredatastudio-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/azuredatastudio-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   azuredatastudio 
   ``` 

   > [!NOTE]
   > Bei Debian, Red hat und Ubuntu fehlen möglicherweise Abhängigkeiten. Verwenden Sie die folgenden Befehle, um diese Abhängigkeiten je nach Ihrer Linux-Version zu installieren:
   

   **Debian:** 
   ```bash
   sudo apt-get install libunwind8
   ```

   **Redhat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```
## <a name="download-insiders-build-of-azure-data-studio"></a>Herunterladen des Insiders-Builds von Azure Data Studio
Im Allgemeinen sollten Benutzer das stabile Release von Azure Data Studio oben herunterladen. Wenn Sie jedoch Betafunktionen testen und uns dazu Feedback geben möchten, können Sie einen [Insiders-Build von Azure Data Studio](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master) herunterladen.

## <a name="uninstall-azure-data-studio"></a>Deinstallieren von Azure Data Studio

Wenn Sie [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] mit dem Windows-Installationsprogramm installiert haben, deinstallieren Sie es auf die gleiche Weise, wie Sie eine Windows-Anwendung entfernen.

Wenn Sie [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] mit einem ZIP- oder anderen Archiv installiert haben, dann löschen Sie einfach die Dateien.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

[!INCLUDE[name-sos](../includes/name-sos-short.md)] kann unter Windows, macOS und Linux ausgeführt werden und wird auf den folgenden Plattformen unterstützt:

### <a name="windows"></a>Windows
- Windows 10 (64-Bit)
- Windows 8.1 (64-Bit)
- Windows 8 (64-Bit)
- Windows 7 (SP1) (64-Bit) – Erfordert [KB2533623](https://www.microsoft.com/download/details.aspx?id=26767)
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2 (64-Bit)
- Windows Server 2012 (64-Bit)
- Windows Server 2008 R2 (64-Bit)

### <a name="macos"></a>macOS
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="recommended-system-requirements"></a>Empfohlene Systemanforderungen

|             | CPU-Kerne | Speicher/RAM |
|:-----------|:---------|:----------|
| Empfohlen |     4     |      8 GB    |
|   Minimum   |     2     |      4 GB     |
|             |           |            |

## <a name="check-for-updates"></a>Suchen nach Updates
Klicken Sie unten links im Fenster auf das Zahnradsymbol und dann auf **Check for Updates** (Nach Updates suchen), um nach aktuellen Updates zu suchen.

## <a name="supported-sql-offerings"></a>Unterstützte SQL-Angebote

* Diese Version von Azure Data Studio funktioniert mit allen [unterstützten Versionen von SQL Server 2014 – [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) und bietet Unterstützung für die Arbeit mit den neuesten Cloudfunktionen in Azure SQL-Datenbank und Azure SQL Data Warehouse. Azure Data Studio bietet auch Unterstützung für die Vorschau der verwalteten Azure SQL-Datenbank-Instanz.

## <a name="upgrade-from-sql-operations-studio"></a>Upgrade von SQL Operations Studio

Wenn Sie noch immer SQL Operations Studio verwenden, müssen Sie ein Upgrade auf Azure Data Studio durchführen. SQL Operations Studio war der Name der Vorschauversion von Azure Data Studio. Im September 2018 haben wir [den Namen in Azure Data Studio](https://cloudblogs.microsoft.com/sqlserver/2018/09/25/azure-data-studio-for-sql-server/) geändert und die allgemein verfügbare Version veröffentlicht. Da SQL Operations Studio nicht länger aktualisiert und unterstützt wird, bitten wir alle Benutzer von SQL Operations Studio, die neueste Version von Azure Data Studio herunterzuladen, um die aktuellen Funktionen, Sicherheitsupdates und Problembehebungen nutzen zu können.
 
Beim Upgrade von der alten Vorschauversion zur neuesten Version von Azure Data Studio gehen Ihre aktuellen Einstellungen und Erweiterungen verloren. Befolgen Sie die Anweisungen im nächsten Abschnitt *Übernehmen von Benutzereinstellungen*, um Ihre Einstellungen zu übernehmen:


## <a name="move-user-settings"></a>Übernehmen von Benutzereinstellungen

Mit den Schritten unten können Sie Ihre benutzerdefinierten Einstellungen, Tastenkombinationen und Codeausschnitte übernehmen. Dies ist wichtig, wenn Sie ein Upgrade von SQL Operations Studio auf Azure Data Studio durchführen.

*Wenn Sie Azure Data Studio bereits nutzen oder SQL Operations Studio nie installiert oder angepasst haben, können Sie diesen Abschnitt ignorieren.*


1. Klicken Sie unten links auf das Zahnradsymbol und dann auf **Settings** (Einstellungen).

   ![open-settings](./media/download/open-settings.png)

2. Klicken Sie mit der rechten Maustaste oben auf die Registerkarte **User Settings** (Benutzereinstellungen) und dann auf **Reveal in Explorer** (Im Explorer anzeigen).

   ![reveal-in-explorer](./media/download/reveal-in-explorer.png)

3. Kopieren Sie alle Dateien in diesem Ordner, und speichern Sie sie an einem leicht zugänglichen Ort auf Ihrem lokalen Laufwerk, z. B. im Ordner „Dokumente“.

   ![copy-settings](./media/download/copy-settings.png)

4. Führen Sie in der neuen Version von Azure Data Studio die Schritte 1-2 durch, und fügen Sie für Schritt 3 die gespeicherten Inhalte in den Ordner ein. Sie können die Einstellungen, Tastenzuordnungen und Codeausschnitte auch manuell an ihre jeweiligen Speicherorte kopieren.

5. Löschen Sie beim Außerkraftsetzen einer vorhandenen Installation zunächst das alte Installationsverzeichnis, um zu verhindern, dass im Ressourcen-Explorer beim Herstellen einer Verbindung mit Ihrem Azure-Konto Fehler auftreten.

## <a name="next-steps"></a>Next Steps

In den folgenden Schnellstarts finden Sie Hinweise zu den ersten Schritten:
- [Herstellen einer Verbindung mit und Abfragen von SQL Server](quickstart-sql-server.md)
- [Herstellen einer Verbindung mit und Abfragen von Azure SQL-Datenbank](quickstart-sql-database.md)
- [Connect & Query Azure Data Warehouse (Herstellen einer Verbindung mit und Abfragen von Azure SQL Data Warehouse)](quickstart-sql-dw.md)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

[Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) und [usage data collection (Erfassung von Nutzungsdaten)](usage-data-collection.md)
