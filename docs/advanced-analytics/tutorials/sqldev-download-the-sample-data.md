---
title: Lektion 1-Download-Beispieldaten und Skripts für eingebettete R (SQL Server-Machine Learning) | Microsoft Docs
description: Lernprogramm zur Einbettung von R in SQL Server gespeicherte Prozeduren und Funktionen des T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 74a60a95da4fb701f3862c36e35a4bada6ef933b
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2018
ms.locfileid: "35249833"
---
# <a name="lesson-1-download-data-and-scripts"></a>Lektion 1: Herunterladen von Daten und Skripts
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Lernprogramms für SQL-Entwicklern zum Verwenden von R in SQL Server.

In diesem Schritt fügen Sie das Beispieldataset herunterladen und die [!INCLUDE[tsql](../../includes/tsql-md.md)] Skriptdateien, die in diesem Lernprogramm verwendet werden. Die Daten und die Skriptdateien auf GitHub freigegeben werden, aber das PowerShell-Skript Daten-und Skripts auf Ihrer Wahl ein lokales Verzeichnis herunter.

## <a name="download-tutorial-files-from-github"></a>Herunterladen der Lernprogrammdateien von Github

1.  Öffnen Sie eine Windows PowerShell-Befehlskonsole.
  
    Verwenden Sie die Option **Als Administrator ausführen**, wenn Administratorrechte erforderlich sind, um das Zielverzeichnis zu erstellen oder Dateien in das angegebene Ziel zu schreiben.
  
2.  Führen Sie die folgenden PowerShell-Befehle aus, die den Wert des Parameters *DestDir* auf jedem beliebigen lokalen Verzeichnis ändern.  Wir haben in diesem Fall **TempRSQL**verwendet.
  
    ```ps
    $source = ‘https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_SQL_Walkthrough.ps1’  
    $ps1_dest = “$pwd\Download_Scripts_SQL_Walkthrough.ps1”
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir ‘C:\tempRSQL’
    ```
  
    Wenn der von Ihnen angegebene Ordner in *DestDir* nicht existiert, wird er vom PowerShell-Skript erstellt.
  
    > [!TIP]
    > Wenn Sie eine Fehlermeldung erhalten, können Sie für diese exemplarische Vorgehensweise die Richtlinie für die Ausführung von PowerShell-Skripts auf **Uneingeschränkt** festlegen, indem Sie das Bypass-Argument verwenden, und die Gültigkeit der Änderungen auf die aktuelle Sitzung beschränken.
    >   
    >````
    > Set\-ExecutionPolicy Bypass \-Scope Process
    >````
    > Das Ausführen dieses Befehls führt zu keiner Konfigurationsänderung.
  
    Abhängig von Ihrer Internetverbindung kann der Download eine Weile dauern.
  
3.  Wenn alle Dateien heruntergeladen wurden, wechselt PowerShell in das mithilfe des Parameters  *DestDir*angegebene Verzeichnis. Führen Sie den folgenden Befehl in der PowerShell-Eingabeaufforderung aus, und überprüfen Sie die Dateien, die heruntergeladen wurden.
  
    ```
    ls
    ```
  
    **Ergebnisse:**
  
    ![Liste der von PowerShell-Skript heruntergeladenen Dateien](media/rsql-devtut-filelist.png "Liste der von PowerShell-Skript heruntergeladenen Dateien")
  
## <a name="next-lesson"></a>Nächste Lektion

[Lektion 2: Importieren von Daten in SQL Server mit PowerShell](../r/sqldev-import-data-to-sql-server-using-powershell.md)

## <a name="previous-lesson"></a>Vorherige Lektion

[Eingebetteten R-Analyse für SQL-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)
