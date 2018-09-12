---
title: Schritt 1 Herunterladen der Beispieldaten | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 07a9b5219649b370b0a5df1e53cf75765f18ec7f
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43888318"
---
# <a name="step-1-download-the-sample-data"></a>Schritt 1: Herunterladen der Beispieldaten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Tutorials, [In-Database Python Analytics für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md). 

Die Daten und die Skripts für dieses Tutorial sind auf Github freigegeben werden. In diesem Schritt verwenden Sie ein PowerShell-Skript zum Herunterladen der Daten und Skript-Dateien in ein lokales Verzeichnis Ihrer Wahl.

## <a name="run-the-script"></a>Führen Sie das Skript

1. Öffnen Sie eine Windows PowerShell-Befehlskonsole.

    Verwenden Sie die Option **als Administrator ausführen**, wenn Administratorrechte erforderlich sind, um das Zielverzeichnis zu erstellen oder zum Schreiben von Dateien in das angegebene Ziel.

2. Führen Sie die folgenden PowerShell-Befehle aus, die den Wert des Parameters *DestDir* auf jedem beliebigen lokalen Verzeichnis ändern.  Der Standardwert, wir haben hier verwendete, ist `C:\temp\pysql`.

    ```ps
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/PythonSQL/Download_Scripts_SQL_Walkthrough.ps1'
    $ps1_dest = "$pwd\Download_Scripts_SQL_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir 'C:\temp\pysql'
    ```
    
    Wenn der von Ihnen angegebene Ordner in *DestDir* nicht existiert, wird er vom PowerShell-Skript erstellt.
    
    Wenn Sie eine Fehlermeldung erhalten, legen Sie vorübergehend die Richtlinie für die Ausführung von PowerShell-Skripts zum **uneingeschränkten** in dieser exemplarischen Vorgehensweise mithilfe der **umgehen** Argument und Einschränken von Änderungen an der aktuellen Sitzung. Das Ausführen dieses Befehls führt zu keiner Konfigurationsänderung.
    
    ```ps
    Set-ExecutionPolicy Bypass -Scope Process
    ```

3. Abhängig von Ihrer Internetverbindung kann der Download eine Weile dauern. 

## <a name="view-results"></a>Anzeigen der Ergebnisse

Wenn alle Dateien heruntergeladen wurden, wechselt PowerShell in das mithilfe des Parameters  *DestDir*angegebene Verzeichnis. 

+ Führen Sie in der PowerShell-Eingabeaufforderung den folgenden Befehl, um die Dateien aufzulisten, die heruntergeladen wurden.

    ```ps
    ls
    ```

![Liste der von PowerShell-Skript heruntergeladenen Dateien](media/sqldev-python-filelist.png "Liste der von PowerShell-Skript heruntergeladenen Dateien")

## <a name="next-step"></a>Nächster Schritt

[Schritt 2: Importieren von Daten nach SQL Server mithilfe von PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="previous-step"></a>Vorheriger Schritt

[In-Database Python Analytics für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md)

## <a name="see-also"></a>Siehe auch

[Python-Erweiterung in SQL Server](../concepts/extension-python.md)


