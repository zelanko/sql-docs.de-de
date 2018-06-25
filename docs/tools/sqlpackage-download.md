---
title: Herunterladen und installieren Sie Sqlpackage | Microsoft Docs
description: Herunterladen Sie und installieren Sie Sqlpackage für Windows, Mac OS oder Linux
ms.custom: tools|sos
ms.date: 06/18/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: craigg
ms.openlocfilehash: 4e5528ca046de83385171890fbda389928e41cf3
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2018
ms.locfileid: "35703839"
---
# <a name="download-and-install-sqlpackage"></a>Herunterladen und installieren Sie sqlpackage

Sqlpackage, die unter Windows, Mac OS und Linux ausgeführt wird.

Herunterladen Sie und installieren Sie die neueste Version von .NET Framework und MacOS und Linux-Vorschau:

|Platform|Herunterladen|Veröffentlichungsdatum|Versionsoptionen|Erstellen|
|:---|:---|:---|:---|:---|
|Windows|[Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=875508)|25 Jan 2018|17.4.1|14.0.3917.1|
|MacOS (Vorschau)|[.zip](https://go.microsoft.com/fwlink/?linkid=873927)|9 Mai 2018 |0.0.1|15.0.4057.1|
|Linux (Vorschauversion)|[.zip](https://go.microsoft.com/fwlink/?linkid=873926)|9 Mai 2018 |0.0.1|15.0.4057.1|

## <a name="get-sqlpackage-for-windows"></a>Abrufen von Sqlpackage für Windows

Diese Version des Sqlpackage enthält eine standardmäßige Windows Installer-Umgebung, und eine ZIP: 

**Installationsprogramm**

1. Herunterladen und Ausführen der [DacFramework.msi Installer für Windows](https://go.microsoft.com/fwlink/?linkid=875508).
2. Öffnen Sie ein Eingabeaufforderungsfenster, und führen Sie sqlpackage.exe
    - Sqlpackage ist installiert, um die ```C:\Program Files\Microsoft SQL Server\140\DAC\bin``` Ordner

## <a name="get-sqlpackage-preview-for-macos"></a>Sqlpackage (Vorschau) für MacOS abrufen

1. Herunterladen [Sqlpackage für MacOS](https://go.microsoft.com/fwlink/?linkid=873927).
2. Zum Extrahieren Sie die Datei, und Starten der Sqlpackage, öffnen Sie ein neues Terminal-Fenster, und geben Sie die folgenden Befehle:

   **ZIP-Installation:**
   ```bash 
   mv ~/Downloads/sqlpackage-linux-<version string> ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage 
   ``` 

## <a name="get-sqlpackage-preview-for-linux"></a>Abrufen von Sqlpackage (Vorschau) für Linux

1. Herunterladen [Sqlpackage für Linux](https://go.microsoft.com/fwlink/?linkid=873926) mithilfe einer der Installationsprogramme oder das Archiv weswegen:
2. Zum Extrahieren Sie die Datei, und Starten der Sqlpackage, öffnen Sie ein neues Terminal-Fenster, und geben Sie die folgenden Befehle:

   **ZIP-Installation:**
   ```bash 
   cd ~ 
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-linux-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bashrc
   source ~/.bashrc 
   sqlpackage 
   ``` 

   > [!NOTE]
   > Unter Debian, Redhat und Ubuntu müssen Sie möglicherweise fehlenden Abhängigkeiten. Verwenden Sie die folgenden Befehle aus, um diese Abhängigkeiten abhängig von Ihrer Version von Linux zu installieren:
   

   **Debian:** 
   ```bash
   sudo apt-get install libuwind8
   ```

   **Redhat:** 
   ```bash
   yum install libunwind 
   yum install libicu 
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libunwind8

   # install the libicu library based on the Ubuntu version
   sudo apt-get install libicu52      # for 14.x
   sudo apt-get install libicu55      # for 16.x
   sudo apt-get install libicu57      # for 17.x
   sudo apt-get install libicu60      # for 18.x
   ```


## <a name="uninstall-sqlpackage-preview"></a>Sqlpackage (Vorschau) deinstallieren

Wenn Sie Sqlpackage mit dem Windows Installer installiert haben, deinstallieren Sie die gleiche Weise wie jede Windows-Anwendung zu entfernen.

Wenn Sie mit einem ZIP- oder andere Archiv Sqlpackage installiert haben, klicken Sie dann einfach löschen Sie die Dateien.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

Sqlpackage unter Windows, Mac OS und Linux ausgeführt wird, und es wird auf folgenden Plattformen unterstützt:

### <a name="windows"></a>Windows
- Windows 10
- Windows 8.1 
- Windows 8 
- Windows 7 SP1 
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012 
- Windows Server 2008 R2

### <a name="macos"></a>macOS
- MacOS 10,13 hohe Sierra
- MacOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="next-steps"></a>Next Steps

- Erfahren Sie mehr über [Sqlpackage](sqlpackage.md)

[Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
