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
ms.openlocfilehash: f966de4951e5c90dac8d6e48f00f8de6ff067e3c
ms.sourcegitcommit: 82b70c39550402a2b0b327db32bf5ecf88b50d3c
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73033012"
---
# <a name="download-and-install-sqlpackage"></a>Herunterladen und Installieren von „Sqlpackage“

„sqlpackage“ wird auf Windows, macOS und Linux ausgeführt.

Laden Sie die neueste.NET Framework-Version und die MacOS- und Linux-Vorschau herunter und installieren Sie sie:

|Platform|Herunterladen|Veröffentlichungsdatum|Versionsoptionen|Erstellen
|:---|:---|:---|:---|:---|
|Windows (x64)|[MSI-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2108813)|29. Oktober 2019|18.4|15.0.4573.2|
|macOS .net Core (x64)|[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2108815)|29. Oktober 2019| 18.4|15.0.4573.2|
|Linux .net Core (x64) |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2108814)|29. Oktober 2019| 18.4|15.0.4573.2|
|Windows .net Core (x64) |[zip-Datei](https://go.microsoft.com/fwlink/?linkid=2109019)|29. Oktober 2019| 18.4|15.0.4573.2|

Weitere Informationen über die neueste Version finden Sie in den [Versionshinweisen](release-notes-sqlpackage.md). Informationen zum Herunterladen zusätzlicher Sprachen finden Sie im Abschnitt [Verfügbare Sprachen](#available-languages) .

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="get-sqlpackage-for-windows"></a>Abrufen von „sqlpackage“ für Windows

Dieses Release von sqlpackage enthält das standardmäßige Windows Installationsprogramm und ein zip-Datei: 

1. Laden Sie das Installationsprogramm [DacFramework.msi für Windows](https://go.microsoft.com/fwlink/?linkid=2108813) herunter, und führen Sie es aus.
2. Öffnen Sie ein Eingabeaufforderungsfenster, und führen Sie die sqlpackage.exe aus.
    - „sqlpackage“ wird im Ordner ```C:\Program Files\Microsoft SQL Server\150\DAC\bin``` installiert.

## <a name="get-sqlpackage-net-core-for-windows"></a>Get Sqlpackage .net Core für Windows

1. Laden Sie [„sqlpackage“ für Windows](https://go.microsoft.com/fwlink/?linkid=2109019) herunter.
2. Zum Extrahieren der Datei klicken Sie mit der rechten Maustaste auf die Datei in Windows-Explorer, und wählen Sie "Alle extrahieren..." aus, und wählen Sie das Zielverzeichnis aus.
3. Öffnen Sie ein neues Terminal Fenster, und wechseln Sie zu dem Speicherort, an dem Sqlpackage extrahiert wurde:

   ```cmd
   > sqlpackage
   ```

## <a name="get-sqlpackage-net-core-for-macos"></a>Get Sqlpackage .net Core für macOS

1. Laden Sie [„sqlpackage“ für MacOS](https://go.microsoft.com/fwlink/?linkid=2108815) herunter.
2. Um die Datei zu extrahieren und „sqlpackage“ zu starten, öffnen Sie ein neues Terminalfenster und geben Sie die folgenden Befehle ein:

   ```bash
   $ mkdir sqlpackage
   $ unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   $ echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   $ source ~/.bash_profile
   $ sqlpackage
   ```

## <a name="get-sqlpackage-net-core-for-linux"></a>Get Sqlpackage .net Core für Linux

1. Laden Sie [„sqlpackage“ für Linux](https://go.microsoft.com/fwlink/?linkid=2108814) herunter, indem Sie eines der Installationsprogramme oder das tar.gz-Archiv verwenden:
2. Um die Datei zu extrahieren und „sqlpackage“ zu starten, öffnen Sie ein neues Terminalfenster und geben Sie die folgenden Befehle ein:

   ```bash
   cd ~
   $ mkdir sqlpackage
   $ unzip ~/Downloads/sqlpackage-linux-<version string>.zip -d ~/sqlpackage 
   $ echo "export PATH=\"\$PATH:$HOME/sqlpackage\"" >> ~/.bashrc
   $ chmod a+x ~/sqlpackage/sqlpackage
   $ source ~/.bashrc
   $ sqlpackage
   ```

   > [!NOTE]
   > Bei Debian, Red hat und Ubuntu fehlen möglicherweise Abhängigkeiten. Verwenden Sie die folgenden Befehle, um diese Abhängigkeiten je nach Ihrer Linux-Version zu installieren:

   **Debian:**

   ```bash
   $ sudo apt-get install libunwind8
   ```

   **Redhat:**

   ```bash
   $ yum install libunwind
   $ yum install libicu
   ```

   **Ubuntu:**

   ```bash
   $ sudo apt-get install libunwind8

   # install the libicu library based on the Ubuntu version
   $ sudo apt-get install libicu52      # for 14.x
   $ sudo apt-get install libicu55      # for 16.x
   $ sudo apt-get install libicu57      # for 17.x
   $ sudo apt-get install libicu60      # for 18.x
   ```

## <a name="uninstall-sqlpackage-preview"></a>Deinstallieren von „sqlpackage“ (Vorschauversion)

Wenn Sie „sqlpackage“ mit dem Windows-Installationsprogramm installiert haben, deinstallieren Sie es auf die gleiche Weise, wie Sie eine Windows-Anwendung entfernen.

Wenn Sie „sqlpackage“ über eine ZIP-Datei oder ein anderes Archiv installiert haben, dann löschen Sie die Dateien.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

„sqlpackage“ läuft unter Windows, macOS und Linux und wird auf den folgenden Plattformen unterstützt:

### <a name="windows"></a>Windows

- Windows 10
- Windows 8.1
- Windows 7 SP1
- Windows Server 2008 R2
- Windows Server 2012 R2
- Windows Server 2016

### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="available-languages"></a>Verfügbare Sprachen

Diese Version von sqlpackage kann in folgenden Sprachen installiert werden:

Sqlpackage-Fenster:  
[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x40a)

Sqlpackage .net Core-Fenster:  
[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x40a)

Sqlpackage .net Core macOS:  
[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x40a)

Sqlpackage .net Core Linux:  
[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x40a)

## <a name="next-steps"></a>Next Steps

- Weitere Informationen zu [sqlpackage](sqlpackage.md)

[Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
