---
title: Zur Installation herunterladen können Sie
titleSuffix: Azure Data Studio
description: Herunterladen und installieren Sie Azure Data Studio für Windows, MacOS oder Linux
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.custom: seodec18
ms.date: 07/11/2019
ms.reviewer: alayu; sstein
ms.openlocfilehash: a2a4d4e755908d544e79b751d64ee99cad6fc96c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959691"
---
# <a name="download-and-install-azure-data-studio"></a>Herunterladen und Installieren von Azure Data Studio

[!INCLUDE[name-sos](../includes/name-sos.md)] auf Windows, MacOS und Linux ausgeführt wird.


Herunterladen und installieren die neueste Version der *-Release aus Juli*:

> [!NOTE]
> Wenn Sie über SQL Operations Studio aktualisieren und Ihre Einstellungen, Tastenkombinationen in Visual Studio oder Codeausschnitte beibehalten möchten, finden Sie unter [verschieben benutzereinstellungen](#move-user-settings).

|Platform|Herunterladen|Veröffentlichungsdatum| Version |
|:---|:---|:---|:---|
|Windows|[Installationsprogramm für Benutzer (empfohlen)](https://go.microsoft.com/fwlink/?linkid=2098449)<br>[System-Installer](https://go.microsoft.com/fwlink/?linkid=2098450)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2098500)|11 Juli 2019 |1.9.0|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2098501)|11 Juli 2019 |1.9.0|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=2098279)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2098280)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2098197)|11 Juli 2019 |1.9.0|

Weitere Informationen über die neueste Version finden Sie in den [Versionshinweisen](release-notes.md).

## <a name="get-azure-data-studio-for-windows"></a>Azure Data-Studio für Windows herunterladen

Diese Version von [!INCLUDE[name-sos](../includes/name-sos-short.md)] enthält eine standardmäßige Windows Installer-Erfahrung und eine ZIP-Datei.

Die *Installationsprogramm Benutzer* wird empfohlen, da es keine Administratorrechte verfügt, benötigt wird, die sowohl Installationen und Upgrades vereinfacht. Der Benutzer-Installer erfordert keine Administratorberechtigungen, wie der Speicherort befindet sich im lokalen AppData (LOCALAPPDATA) Benutzerordners. Der Benutzer-Installer bietet auch einen möglichst reibungslosen Ablauf der Hintergrund-Update. Weitere Informationen finden Sie unter [benutzereinrichtung für Windows](https://code.visualstudio.com/updates/v1_26#_user-setup-for-windows).


**Installationsprogramm Benutzer** (empfohlen)

1. Herunterladen und Ausführen der [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] *Benutzer* Installer für Windows](https://go.microsoft.com/fwlink/?linkid=2098449).
2. Starten Sie den [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] app.

**System-Installer**

1. Herunterladen und Ausführen der [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] *System* Installer für Windows](https://go.microsoft.com/fwlink/?linkid=2098450 ).
2. Starten Sie den [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] app.


**zip-Datei**

1. Herunterladen [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] ZIP für Windows](https://go.microsoft.com/fwlink/?linkid=2098500).
2. Suchen Sie die heruntergeladene Datei, und extrahieren Sie sie.
3. Ausführen von `\azuredatastudio-windows\azuredatastudio.exe`


## <a name="get-azure-data-studio-for-macos"></a>Abrufen von Azure Data Studio für macOS

1. Herunterladen [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] für MacOS](https://go.microsoft.com/fwlink/?linkid=2098501).
2. Doppelklicken Sie darauf, um den Inhalt der ZIP-Datei zu erweitern.
3. Vornehmen [!INCLUDE[name-sos](../includes/name-sos-short.md)] zur Verfügung, in der *Launchpad*, ziehen Sie *Azure Daten Studio.app* auf die *Anwendungen* Ordner.


## <a name="get-azure-data-studio-for-linux"></a>Azure Data-Studio für Linux herunterladen

1. Herunterladen [!INCLUDE[name-sos](../includes/name-sos-short.md)] für Linux mithilfe eines der Installationsprogramme oder das Archiv für die ".TAR.gz":
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2098279)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2098280)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2098197)
1. Extrahieren Sie die Datei, und starten Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)], öffnen Sie ein neues Terminalfenster, und geben Sie die folgenden Befehle:

   **Debian-Installation:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **u/Min Installation:**
   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **.tar.gz Installation:**
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
## <a name="download-insiders-build-of-azure-data-studio"></a>Herunterladen Sie Insiders-Build von Azure Data Studio
Im Allgemeinen sollten Benutzern die stabile Version von Azure Data Studio höher herunterladen. Allerdings sollten Sie unsere Funktionen der Betaversion ausprobieren und uns Feedback, Sie können eine [Insiders-build von Azure Data Studio.](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master)

## <a name="uninstall-azure-data-studio"></a>Deinstallieren Sie Azure Data Studio

Wenn Sie installiert [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] mit dem Windows-Installer, deinstallieren Sie die gleiche Weise, wie Sie eine Windows-Anwendung entfernen.

Wenn Sie installiert [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] mit ZIP-Datei oder andere archivieren, löschen Sie anschließend einfach die Dateien.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

[!INCLUDE[name-sos](../includes/name-sos-short.md)] unter Windows, MacOS und Linux ausgeführt wird, und wird auf folgenden Plattformen unterstützt:

### <a name="windows"></a>Windows
- Windows 10 (64-Bit)
- Windows 8.1 (64-Bit)
- Windows 8 (64-Bit)
- Erfordert Windows 7 (SP1) (64-Bit) - [KB2533623](https://www.microsoft.com/download/details.aspx?id=26767)
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
Verwenden Sie um eine optimale benutzererfahrung die empfohlenen Systemanforderungen.
[Erforderlich Update hier um Arbeitsspeicher zu quantifizieren.]

|             | CPU-Kerne | Speicher/RAM |
|:-----------|:---------|:----------|
| Empfohlen |     4     |      8 GB    |
|   Minimum   |     2     |      4 GB     |
|             |           |            |

## <a name="check-for-updates"></a>Nach Updates suchen
Um die neuesten Updates zu überprüfen, klicken Sie auf das Zahnradsymbol unten links des Fensters, und klicken Sie auf **nach Updates suchen**

## <a name="supported-sql-offerings"></a>Unterstützte SQL-Angebote

* Diese Version von Azure Data Studio funktioniert mit allen [unterstützten Versionen von SQL Server 2014 - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ](https://support.microsoft.com/lifecycle?C2=1044) und bietet Unterstützung für die Arbeit mit den neuesten cloudfeatures in Azure SQL-Datenbank und Azure SQL Data Warehouse. Azure Data Studio bietet auch vorschauunterstützung für verwaltete Azure SQL-Instanz.

## <a name="upgrade-from-sql-operations-studio"></a>Upgrade von SQL Operations Studio

Wenn Sie SQL Operations Studio weiterhin verwenden möchten, müssen Sie ein Upgrade auf Azure Data Studio durchführen. SQL Operations Studio war die Preview-Namen und die Preview-Version von Azure Data Studio. Im September 2018 wir [den Namen in Azure Data Studio geändert](https://cloudblogs.microsoft.com/sqlserver/2018/09/25/azure-data-studio-for-sql-server/) und der allgemeinen Verfügbarkeit (GA) Version veröffentlicht. Da SQL Operations Studio ist nicht mehr aktualisiert oder unterstützt, bitten wir alle SQL Operations Studio-Benutzer von Azure Data Studio, um die neuesten Features, Sicherheitsupdates, erhalten die neueste Version herunterladen und Korrekturen.
 
Beim Upgrade von der alten Vorschauversion auf die neuesten Studio für Azure Data verlieren Sie Ihre aktuellen Einstellungen und Erweiterungen. Um Ihre Einstellungen zu verschieben, folgen Sie die Anweisungen in der folgenden *verschieben benutzereinstellungen* Abschnitt:


## <a name="move-user-settings"></a>Verschieben von benutzereinstellungen

Wenn Sie Ihre benutzerdefinierten Einstellungen, Tastenkombinationen in Visual Studio oder Codeausschnitte verschieben möchten, führen Sie die folgenden Schritte aus. Dies ist wichtig, wenn Sie SQL Operations Studio-Version auf Azure Data Studio aktualisieren.

*Wenn Sie bereits über Azure Data Studio verfügen oder Sie nicht installiert oder SQL Operations Studio angepasst haben, können Sie diesen Abschnitt ignorieren.*


1. Öffnen Sie Einstellungen, indem Sie auf das Zahnradsymbol auf der linken unteren und auf **Einstellungen.**

   ![Open-Einstellungen](./media/download/open-settings.png)

2. Mit der rechten Maustaste die **Benutzereinstellungen** Registerkarte im Vordergrund, und klicken Sie auf **im Explorer anzeigen**

   ![Anzeigen-in-explorer](./media/download/reveal-in-explorer.png)

3. Kopieren Sie alle Dateien in diesem Ordner, und speichern Sie in einem übersichtlichen Ort auf dem lokalen Laufwerk, z. B. Ihren Dokumentordner finden.

   ![Einstellungen kopieren](./media/download/copy-settings.png)

4. Führen Sie die Schritte, die 1-2, wählen Sie unter Schritt 3 Fügen Sie den Inhalt, die Sie gespeichert, aufgerufen werden, in den Ordner, in Ihrer neuen Version von Azure Data Studio. Sie können auch manuell über die Einstellungen, Keybindings oder Codeausschnitte in ihren entsprechenden Speicherorten kopieren.

5. Wenn eine vorhandene Installation außer Kraft gesetzt werden, löschen Sie das alte Installationsverzeichnis vor der Installation zur Vermeidung von Fehlern, die mit Ihrem Azure-Konto für den Ressourcen-Explorer.

## <a name="next-steps"></a>Nächste Schritte

Finden Sie in der folgenden schnellstartanleitungen für den Einstieg:
- [Verbinden und Abfragen von SQLServer](quickstart-sql-server.md)
- [Verbinden und Abfragen von Azure SQL-Datenbank](quickstart-sql-database.md)
- [Verbinden und Abfragen von Azure Datawarehouse](quickstart-sql-dw.md)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

[Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839) und [Sammlung von Verwendungsdaten](usage-data-collection.md).