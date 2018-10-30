---
title: Herunterladen und Installieren von "Sqlpackage" | Microsoft-Dokumentation
description: Herunterladen und Installieren von "Sqlpackage" für Windows, MacOS oder Linux
ms.custom: tools|sos
ms.date: 06/18/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: craigg
ms.openlocfilehash: 322a9ce1992bb2b4d0215cfefa747ea56e68472f
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050922"
---
# <a name="download-and-install-sqlpackage"></a>Herunterladen und Installieren von "Sqlpackage"

"Sqlpackage", die auf Windows, MacOS und Linux ausgeführt wird.

Herunterladen Sie und installieren Sie die neueste Version von .NET Framework und MacOS und Linux-Vorschau:

|Platform|Herunterladen|Veröffentlichungsdatum|Versionsoptionen|Erstellen
|:---|:---|:---|:---|:---|
|Windows|[MSI-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2033947)|24. Oktober 2018|18.0|15.0.4200.1|
|macOS (Vorschau)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=873927)|9. Mai 2018 |0.0.1|15.0.4057.1|
|Linux (Vorschauversion)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=873926)|9. Mai 2018 |0.0.1|15.0.4057.1|

Weitere Informationen über die neueste Version finden Sie unter den [Anmerkungen zu dieser Version](sqlpackage-release-notes.md).

## <a name="get-sqlpackage-for-windows"></a>Abrufen von "Sqlpackage" für Windows

Diese Version von "Sqlpackage" enthält eine standardmäßige Windows Installer-Erfahrung und ZIP-Datei: 

1. Herunterladen und Ausführen der [DacFramework.msi-Installer für Windows](https://go.microsoft.com/fwlink/?linkid=2033947).
2. Öffnen Sie ein Eingabeaufforderungsfenster, und führen Sie sqlpackage.exe
    - "Sqlpackage" installiert wird, für die ```C:\Program Files\Microsoft SQL Server\150\DAC\bin``` Ordner
    - Installieren die X86-Version auf eine X64-Computer, auf dem "Sqlpackage" installiert ist die ```C:\Program Files (x86)\Microsoft SQL Server\150\DAC\bin``` Ordner

## <a name="get-sqlpackage-preview-for-macos"></a>Abrufen von "Sqlpackage" (Vorschau) für macOS

1. Herunterladen ["Sqlpackage" für MacOS](https://go.microsoft.com/fwlink/?linkid=873927).
2. Zum Extrahieren Sie die Datei, und starten "Sqlpackage", öffnen Sie ein neues Terminalfenster, und geben Sie die folgenden Befehle aus:

   **ZIP-Installation:**

   ```bash
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage
   ```

## <a name="get-sqlpackage-preview-for-linux"></a>Abrufen von "Sqlpackage" (Vorschau) für Linux

1. Herunterladen ["Sqlpackage" für Linux](https://go.microsoft.com/fwlink/?linkid=873926) mithilfe eines der Installationsprogramme oder das Archiv für die ".TAR.gz":
2. Zum Extrahieren Sie die Datei, und starten "Sqlpackage", öffnen Sie ein neues Terminalfenster, und geben Sie die folgenden Befehle aus:

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
   > Für Debian, Red hat und Ubuntu müssen Sie möglicherweise fehlende Abhängigkeiten. Verwenden Sie die folgenden Befehle aus, um diese Abhängigkeiten abhängig von Ihrer Version von Linux zu installieren:

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

## <a name="uninstall-sqlpackage-preview"></a>Deinstallieren von "Sqlpackage" (Vorschau)

Wenn Sie mit dem Windows Installer "Sqlpackage" installiert haben, deinstallieren Sie die gleiche Weise, wie Sie eine Windows-Anwendung entfernen.

Wenn Sie mit einer ZIP- oder andere Archiv "Sqlpackage" installiert haben, klicken Sie dann einfach gelöscht werden.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

"Sqlpackage" unter Windows, MacOS und Linux ausgeführt wird, und es wird auf folgenden Plattformen unterstützt:

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

- MacOS 10.13 High Sierra
- MacOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="next-steps"></a>Next Steps

- Erfahren Sie mehr über ["Sqlpackage"](sqlpackage.md)

[Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
