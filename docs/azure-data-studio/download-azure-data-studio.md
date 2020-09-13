---
title: Herunterladen und Installieren von Azure Data Studio
description: Laden Sie Azure Data Studio für Windows, macOS oder Linux herunter, und installieren Sie das Tool. In diesem Artikel finden Sie Veröffentlichungstermine, Versionsnummern, Systemanforderungen und Downloadlinks.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.reviewer: maghan
ms.custom: seodec18
ms.date: 8/12/2020
ms.openlocfilehash: 2e4906ebe22b28a15eb20a182198e6c74853eb18
ms.sourcegitcommit: f7c9e562d6048f89d203d71685ba86f127d8d241
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042731"
---
# <a name="download-and-install-azure-data-studio"></a>Herunterladen und Installieren von Azure Data Studio

Azure Data Studio kann unter Windows, macOS und Linux ausgeführt werden.

Neuestes Release herunterladen und installieren:

> [!NOTE]
> Wie Sie bei einem Update von SQL Operations Studio Ihre Einstellungen, Tastenkombinationen und Codeausschnitte beibehalten können, erfahren Sie unter [Übernehmen von Benutzereinstellungen](#move-user-settings).

|Plattform|Download|Veröffentlichungsdatum| Version |
|:---|:---|:---|:---|
| Windows | [Benutzer-Installationsprogramm (empfohlen)](https://go.microsoft.com/fwlink/?linkid=2138608)<br>[System-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2138704)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2138705) | 12. August 2020 | 1.21.0 |
| macOS | [.zip](https://go.microsoft.com/fwlink/?linkid=2138609) | 12. August 2020 | 1.21.0 |
| Linux | [.deb](https://go.microsoft.com/fwlink/?linkid=2138508)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2138507)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2138706) | 12. August 2020| 1.21.0 |

Weitere Informationen über die neueste Version finden Sie in den [Versionshinweisen](./release-notes-azure-data-studio.md?view=sql-server-ver15).

## <a name="get-azure-data-studio-for-windows"></a>Azure Data Studio für Windows

Dieses Release von Azure Data Studio enthält den standardmäßigen Windows Installer und eine ZIP-Datei.

Das *Benutzer-Installationsprogramm* wird empfohlen, da dafür keine Administratorrechte erforderlich sind, was Installationen und Upgrades vereinfacht. Für das Benutzer-Installationsprogramm sind keine Administratorrechte erforderlich, da sich der Speicherort im lokalen Ordner „AppData“ (LOCALAPPDATA) des Benutzers befindet. Zudem bietet das Benutzer-Installationsprogramm eine einfachere Aktualisierung im Hintergrund. Weitere Informationen finden Sie unter [Benutzersetup für Windows](https://code.visualstudio.com/updates/v1_26#_user-setup-for-windows).

**Benutzer-Installationsprogramm** (empfohlen)

1. Laden Sie das [[!INCLUDE[name-sos](../includes/name-sos-short.md)]-Installationsprogramm für *Benutzer* für Windows](https://go.microsoft.com/fwlink/?linkid=2138608) herunter, und führen Sie es aus.
2. Starten Sie die [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]-App.

**System-Installationsprogramm**

1. Laden Sie das [[!INCLUDE[name-sos](../includes/name-sos-short.md)]-Installationsprogramm für das *System* für Windows](https://go.microsoft.com/fwlink/?linkid=2138704) herunter, und führen Sie es aus.
2. Starten Sie die [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]-App.

**zip-Datei**

1. Laden Sie die [[!INCLUDE[name-sos](../includes/name-sos-short.md)]-ZIP-Datei für Windows](https://go.microsoft.com/fwlink/?linkid=2138705) herunter.
2. Navigieren Sie zur heruntergeladenen Datei, und extrahieren Sie sie.
3. Ausführen von `\azuredatastudio-windows\azuredatastudio.exe`

## <a name="get-azure-data-studio-for-macos"></a>Azure Data Studio für macOS

1. Laden Sie [[!INCLUDE[name-sos](../includes/name-sos-short.md)] für macOS](https://go.microsoft.com/fwlink/?linkid=2138609) herunter.
2. Doppelklicken Sie auf die ZIP-Datei, um die Inhalte zu erweitern.
3. Wenn Sie Azure Data Studio im *Launchpad* zur Verfügung stellen wollen, können Sie *Azure Data Studio.app* in den Ordner *Programme* ziehen.

## <a name="get-azure-data-studio-for-linux"></a>Azure Data Studio für Linux

1. Laden Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)] für Linux herunter, indem Sie eines der Installationsprogramme oder das Archiv „tar.gz“ verwenden:
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2138508)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2138507)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2138706)
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

Im Allgemeinen sollten Benutzer das stabile Release von Azure Data Studio oben herunterladen. Wenn Sie jedoch Betafunktionen testen und uns dazu Feedback geben möchten, können Sie einen [Insiders-Build von Azure Data Studio](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-main) herunterladen.

## <a name="uninstall-azure-data-studio"></a>Deinstallieren von Azure Data Studio

Wenn Sie [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] mit dem Windows Installer installiert haben, deinstallieren Sie das Tool auf die gleiche Weise, wie Sie eine Windows-Anwendung entfernen.

Wenn Sie [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] mit einem ZIP- oder anderen Archiv installiert haben, dann löschen Sie einfach die Dateien.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

Azure Data Studio kann unter Windows, macOS und Linux ausgeführt werden und wird auf den folgenden Plattformen unterstützt:

### <a name="windows"></a>Windows

- Windows 10 (64-Bit)
- Windows 8.1 (64-Bit)
- Windows 8 (64-Bit)
- Windows 7 (SP1)
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2 (64-Bit)
- Windows Server 2012 (64-Bit)
- Windows Server 2008 R2 (64-Bit)

### <a name="macos"></a>macOS

- macOS 10.15 Catalina
- macOS 10.14 Mojave
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="recommended-system-requirements"></a>Empfohlene Systemanforderungen

| Empfohlen/Minimum | CPU-Kerne | Speicher/RAM |
|---------------------|-----------|------------|
| Empfohlen         |     4     |   8 GB     |
|   Minimum           |     2     |   4 GB     |

## <a name="check-for-updates"></a>Suchen nach Updates

Klicken Sie unten links im Fenster auf das Zahnradsymbol und dann auf **Nach Updates suchen**, um nach aktuellen Updates zu suchen.

In einer Offlineumgebung können Updates durch [Installieren der neuesten Version](#download-and-install-azure-data-studio) direkt über eine zuvor installierte Version angewendet werden.  Es ist nicht notwendig, frühere Versionen von Azure Data Studio zu deinstallieren, weil das Installationsprogramm eine installierte Anwendung aktualisiert.

## <a name="supported-sql-offerings"></a>Unterstützte SQL-Angebote

- Diese Version von Azure Data Studio funktioniert mit allen [unterstützten Versionen von SQL Server 2014 – [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) und bietet Unterstützung für die Arbeit mit den neuesten Cloudfunktionen in Azure SQL-Datenbank und Azure SQL Data Warehouse. Azure Data Studio bietet auch Unterstützung für die Vorschau der verwalteten Azure SQL-Datenbank-Instanz.

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

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Schnellstarts finden Sie Hinweise zu den ersten Schritten:

- [Herstellen einer Verbindung mit und Abfragen von SQL Server](quickstart-sql-server.md)
- [Herstellen einer Verbindung mit und Abfragen von Azure SQL-Datenbank](quickstart-sql-database.md)
- [Herstellen einer Verbindung mit und Abfragen von Azure SQL Data Warehouse](quickstart-sql-dw.md)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

[Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) und [usage data collection (Erfassung von Nutzungsdaten)](usage-data-collection.md)
