---
title: Herunterladen und Installieren von „sqlpackage“ | Microsoft-Dokumentation
description: Herunterladen und Installieren von „sqlpackage“ für Windows, MacOS oder Linux
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: craigg
ms.openlocfilehash: 809a78130c5bc015114138e678c55522fa556f01
ms.sourcegitcommit: e2d65828faed6f4dfe625749a3b759af9caa7d91
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59671166"
---
# <a name="download-and-install-sqlpackage"></a>Herunterladen und Installieren von „Sqlpackage“

„sqlpackage“ wird auf Windows, macOS und Linux ausgeführt.

Laden Sie die neueste.NET Framework-Version und die MacOS- und Linux-Vorschau herunter und installieren Sie sie:

|Platform|Herunterladen|Veröffentlichungsdatum|Versionsoptionen|Erstellen
|:---|:---|:---|:---|:---|
|Windows|[MSI-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2087429)|April 15, 2019|18.2|15.0.4384.2|
|macOS .NET Core (Vorschauversion)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2087247)|April 15, 2019 | 18.2 |15.0.4384.2|
|Linux .NET Core (Vorschauversion)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2087431)|April 15, 2019 | 18.2 |15.0.4384.2|

Weitere Informationen über die neueste Version finden Sie in den [Versionshinweisen](release-notes-sqlpackage.md).

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="get-sqlpackage-for-windows"></a>Abrufen von „sqlpackage“ für Windows

Dieses Release von sqlpackage enthält das standardmäßige Windows Installationsprogramm und ein zip-Datei: 

1. Laden Sie das Installationsprogramm [DacFramework.msi für Windows](https://go.microsoft.com/fwlink/?linkid=2087429) herunter, und führen Sie es aus.
2. Öffnen Sie ein Eingabeaufforderungsfenster, und führen Sie die sqlpackage.exe aus.
    - „sqlpackage“ wird im Ordner ```C:\Program Files\Microsoft SQL Server\150\DAC\bin``` installiert.
    - Bei der Installation der x86-Version auf einem x64-Computer wird „sqlpackage“ im Ordner ```C:\Program Files (x86)\Microsoft SQL Server\150\DAC\bin``` installiert.

## <a name="get-sqlpackage-preview-for-macos"></a>Abrufen von „sqlpackage“ (Vorschauversion) für macOS

1. Laden Sie [„sqlpackage“ für MacOS](https://go.microsoft.com/fwlink/?linkid=2087247) herunter.
2. Um die Datei zu extrahieren und „sqlpackage“ zu starten, öffnen Sie ein neues Terminalfenster und geben Sie die folgenden Befehle ein:

   **ZIP-Installation:**

   ```bash
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage
   ```

## <a name="get-sqlpackage-preview-for-linux"></a>Abrufen von „sqlpackage“ (Vorschauversion) für Linux

1. Laden Sie [„sqlpackage“ für Linux](https://go.microsoft.com/fwlink/?linkid=2087431) herunter, indem Sie eines der Installationsprogramme oder das tar.gz-Archiv verwenden:
2. Um die Datei zu extrahieren und „sqlpackage“ zu starten, öffnen Sie ein neues Terminalfenster und geben Sie die folgenden Befehle ein:

   **ZIP-Installation:**

   ```bash
   cd ~
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-linux-<version string>.zip -d ~/sqlpackage 
   echo "export PATH=\"\$PATH:$HOME/sqlpackage\"" >> ~/.bashrc
   chmod a+x ~/sqlpackage/sqlpackage
   source ~/.bashrc
   sqlpackage
   ```

   > [!NOTE]
   > Bei Debian, Red hat und Ubuntu fehlen möglicherweise Abhängigkeiten. Verwenden Sie die folgenden Befehle, um diese Abhängigkeiten je nach Ihrer Linux-Version zu installieren:

   **Debian:**

   ```bash
   sudo apt-get install libunwind8
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

## <a name="uninstall-sqlpackage-preview"></a>Deinstallieren von „sqlpackage“ (Vorschauversion)

Wenn Sie „sqlpackage“ mit dem Windows-Installationsprogramm installiert haben, deinstallieren Sie es auf die gleiche Weise, wie Sie eine Windows-Anwendung entfernen.

Wenn Sie „sqlpackage“ mit einem zip- oder anderen Archiv installiert haben, dann löschen Sie einfach die Dateien.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

„sqlpackage“ läuft unter Windows, macOS und Linux und wird auf den folgenden Plattformen unterstützt:

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

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="next-steps"></a>Next Steps

- Weitere Informationen zu [sqlpackage](sqlpackage.md)

[Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
