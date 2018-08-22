---
title: Herunterladen und installieren Sie Microsoft SQL Operations Studio (Vorschau) | Microsoft-Dokumentation
description: Herunterladen und installieren Sie Microsoft SQL Operations Studio (Vorschauversion) für Windows, MacOS oder Linux
ms.custom: tools|sos
ms.date: 07/19/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 75879a42e7f9d176e01ae9dffb4bd931154253e3
ms.sourcegitcommit: 489e29bce510fae6d826d5b6548eb9612fc2bd62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393232"
---
# <a name="download-and-install-sql-operations-studio-preview"></a>Herunterladen Sie und installieren Sie SQL Operations Studio (Vorschau)

[!INCLUDE[name-sos](../includes/name-sos.md)] auf Windows, MacOS und Linux ausgeführt wird.

Herunterladen und installieren die neueste Version der *Public Preview von Juli*:

|Platform|Herunterladen|Veröffentlichungsdatum| Version |
|:---|:---|:---|:---|
|Windows|[Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2005949)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2005950)|Am 19. Juli 2018 |0.31.4|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2005959)|Am 19. Juli 2018 |0.31.4|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=2006084)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2006083)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2005960)|Am 19. Juli 2018 |0.31.4|

Weitere Informationen über die neueste Version finden Sie unter den [Anmerkungen zu dieser Version](release-notes.md).

## <a name="get-sql-operations-studio-preview-for-windows"></a>Rufen Sie SQL Operations Studio (Vorschauversion) für Windows

Diese Version von [!INCLUDE[name-sos](../includes/name-sos-short.md)] enthält eine standardmäßige Windows Installer-Erfahrung und ZIP-Datei: 

**Installationsprogramm**

1. Herunterladen und Ausführen der [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] Installer für Windows](https://go.microsoft.com/fwlink/?linkid=2005949).
1. Starten Sie den [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] app.


**ZIP-Datei**

1. Herunterladen [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] ZIP für Windows](https://go.microsoft.com/fwlink/?linkid=2005950).
2. Suchen Sie die heruntergeladene Datei, und extrahieren Sie sie.
3. Ausführen von `\sqlops-windows\sqlops.exe`


## <a name="get-sql-operations-studio-preview-for-macos"></a>Rufen Sie SQL Operations Studio (Vorschauversion) für macOS

1. Herunterladen [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] für MacOS](https://go.microsoft.com/fwlink/?linkid=2005959).
2. Doppelklicken Sie darauf, um den Inhalt der ZIP-Datei zu erweitern.
3. Zu [!INCLUDE[name-sos](../includes/name-sos-short.md)] zur Verfügung, in der *Launchpad*, ziehen Sie *sqlops.app* auf die *Anwendungen* Ordner.


## <a name="get-sql-operations-studio-preview-for-linux"></a>SQL Operations Studio (Vorschauversion) für Linux zu erhalten.

1. Herunterladen [!INCLUDE[name-sos](../includes/name-sos-short.md)] für Linux mithilfe eines der Installationsprogramme oder das Archiv für die ".TAR.gz":
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2006084)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2006083)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2005960)
1. Extrahieren Sie die Datei, und starten Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)], öffnen Sie ein neues Terminalfenster, und geben Sie die folgenden Befehle:

   **Debian-Installation:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
   ```

   **u/Min Installation:**
   ```bash
   cd ~
   yum install ./Downloads/sqlops-linux-<version string>.rpm

   sqlops
   ```

   **.tar.gz Installation:**
   ```bash 
   cd ~ 
   cp ~/Downloads/sqlops-linux-<version string>.tar.gz ~ 
   tar -xvf ~/sqlops-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/sqlops-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   sqlops 
   ``` 

   > [!NOTE]
   > Für Debian, Red hat und Ubuntu müssen Sie möglicherweise fehlende Abhängigkeiten. Verwenden Sie die folgenden Befehle aus, um diese Abhängigkeiten abhängig von Ihrer Version von Linux zu installieren:
   

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


## <a name="uninstall-sql-operations-studio-preview"></a>Deinstallieren Sie SQL Operations Studio (Vorschau)

Wenn Sie installiert [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] mit dem Windows-Installer, deinstallieren Sie die gleiche Weise, wie Sie eine Windows-Anwendung entfernen.

Wenn Sie installiert [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] mit ZIP-Datei oder andere archivieren, löschen Sie anschließend einfach die Dateien.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

[!INCLUDE[name-sos](../includes/name-sos-short.md)] unter Windows, MacOS und Linux ausgeführt wird, und wird auf folgenden Plattformen unterstützt:

### <a name="windows"></a>Windows
- Windows 10 (64-Bit)
- Windows 8.1 (64-Bit)
- Windows 8 (64-Bit)
- Erfordert Windows 7 (SP1) (64-Bit) - [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64-Bit)
- Windows Server 2012 (64-Bit)
- Windows Server 2008 R2 (64-Bit)

### <a name="macos"></a>macOS
- MacOS 10.13 High Sierra
- MacOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="check-for-updates"></a>Nach Updates suchen
Um die neuesten Updates zu überprüfen, klicken Sie auf das Zahnradsymbol unten links des Fensters, und klicken Sie auf **nach Updates suchen**

## <a name="next-steps"></a>Nächste Schritte

Finden Sie in der folgenden schnellstartanleitungen für den Einstieg:
- [Verbinden und Abfragen von SQLServer](quickstart-sql-server.md)
- [Verbinden und Abfragen von Azure SQL-Datenbank](quickstart-sql-database.md)
- [Verbinden und Abfragen von Azure Datawarehouse](quickstart-sql-dw.md)

Mitwirken an [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839) und [Sammlung von Verwendungsdaten](usage-data-collection.md).
