---
title: Lektion 1-Download-Beispieldaten und Skripts für eingebettete R (SQL Server-Machine Learning) | Microsoft-Dokumentation
description: Veranschaulicht, wie Sie R in SQL Server Einbetten von gespeicherten Prozeduren und T-SQL-Funktionen
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 74a60a95da4fb701f3862c36e35a4bada6ef933b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38030378"
---
# <a name="lesson-1-download-data-and-scripts"></a>Lektion 1: Herunterladen von Daten und Skripts
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Tutorials für SQL-Entwickler zur Verwendung von R in SQL Server.

In diesem Schritt müssen Sie das Beispieldataset herunterladen und die [!INCLUDE[tsql](../../includes/tsql-md.md)] Skriptdateien, die in diesem Tutorial verwendet werden. Die Daten und die Skriptdateien werden auf GitHub freigegeben, aber das PowerShell-Skript Herunterladen der Dateien Daten und Skriptdateien in ein lokales Verzeichnis Ihrer Wahl.

## <a name="download-tutorial-files-from-github"></a>Lernprogrammdateien von Github herunterladen

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

[Lektion 2: Importieren von Daten in SQL Server mithilfe von PowerShell](../r/sqldev-import-data-to-sql-server-using-powershell.md)

## <a name="previous-lesson"></a>Vorherige Lektion

[Eingebettete R-Analysen für SQL-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)
