---
title: Führen Sie Datenbank-experimentieren-Assistenten aus, an der Eingabeaufforderung für SQL Server-upgrades
description: Führen Sie Datenbank-experimentieren-Assistenten aus, an der Eingabeaufforderung
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: e98863dcdd7f0cac2534f73c8c99b1d38e7b81b0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63273930"
---
# <a name="run-database-experimentation-assistant-at-a-command-prompt"></a>Führen Sie Datenbank-experimentieren-Assistenten aus, an der Eingabeaufforderung

Dieser Artikel beschreibt, wie im Eingabeaufforderungsfenster zum Erfassen einer Ablaufverfolgung in Datenbank experimentieren-Assistenten (DEA), und klicken Sie dann die Ergebnisse analysieren. 

## <a name="start-a-new-workload-capture-by-using-the-dea-command"></a>Starten Sie eine neue arbeitsauslastung Erfassung mithilfe des Befehls DEA

Um eine neue arbeitsauslastung Erfassung zu starten, führen Sie den folgenden Befehl aus:

`Deacmd.exe -o startcapturetrace -s <SQLServerInstance> -e <encryptconnection> -u <trustservercertificate> -d <database name> -p <trace file path> -f <trace file name> -t <Max duration>`

**Beispiel**

`Deacmd.exe -o startcapturetrace -s localhost -e -d adventureworks -p c:\test -f sql2008capture -t 60`

## <a name="replay-a-workload"></a>Eine arbeitsauslastung wiedergegeben

1.  Melden Sie sich mit dem Distributed Replay Controller-Computer.
2.  Konvertieren Sie die Ablaufverfolgung der arbeitsauslastung, die Sie mit dem DEA-Befehl in eine Datei IRF erfasst:

    `DReplay preprocess -m "dreplaycontroller" -i "Path to first trace file" -d "<Folder path on controller>\IrfFolder"`

3.  Starten Sie eine Ablaufverfolgung erfassen, auf dem Zielcomputer mit SQL Server mithilfe von StartReplayCaptureTrace.sql.
       
    a.  Öffnen Sie in die SQL Server Management Studio (SSMS), < Dea_InstallPath\>\Scripts\StartReplayCaptureTrace.sql.
    
    b.  Führen Sie `Set @durationInMins=0` so, dass die Ablaufverfolgung Erfassung automatisch nach einer bestimmten Zeit nicht.
    
    c.  Führen Sie zum Festlegen der maximalen Dateigröße pro Ablaufverfolgungsdatei `Set @maxfilesize`. Die empfohlene Größe beträgt 200 (in MB).
    
    d.  Bearbeiten Sie `@Tracefile` einen eindeutigen Namen für die Ablaufverfolgungsdatei festlegen.
    
    e.  Bearbeiten Sie `@dbname` auf einen Datenbanknamen anzugeben, wenn die arbeitsauslastung nur auf eine bestimmte Datenbank aufgezeichnet werden muss. Standardmäßig wird die arbeitsauslastung auf den gesamten Server erfasst. 
4.  Wiedergegeben Sie die IRF-Datei in der SQL Server-Zielinstanz werden:

    `DReplay replay -m "dreplaycontroller" -d "<Folder Path on Dreplay Controller>\IrfFolder" -o -s "SQL2016Target" -w "dreplaychild1,dreplaychild2,dreplaycild3,dreplaychild4"`
        
    a.  Klicken Sie zum Überwachen des Status, öffnen Sie ein Eingabeaufforderungsfenster, und führen Sie `DReplay status -f 1`.
        
    b.  Um die Wiedergabe zu beenden, z. B., als ob Sie sehen, dass der Pass-% niedriger als erwartet, ist ein Eingabeaufforderungsfenster öffnen und ausführen `DReplay cancel`.

5.  Beenden Sie die Erfassung der Ablaufverfolgung auf der SQL Server-Zielinstanz.
6.  Öffnen Sie in SSMS `<Dea_InstallPath>\Scripts\StopCaptureTrace.sql`.
7.  Bearbeiten Sie `@Tracefile` entsprechend den Trace-Dateipfad auf dem Zielcomputer, die SQL Server ausgeführt wird.
8.  Führen Sie das Skript, mit dem Zielcomputer, die SQL Server ausgeführt wird.

## <a name="analyze-traces-by-using-the-dea-command"></a>Analysieren von ablaufverfolgungen mithilfe des Befehls DEA

Um eine neue Ablaufverfolgungsanalyse zu starten, führen Sie den folgenden Befehl aus:

`Deacmd.exe -o analysis -a <Target1 trace filepath> -b <Target2 trace filepath> -r reportname -s <SQLserverInstance> -e <encryptconnection> -u <trustservercertificate>`

**Beispiel**

`Deacmd.exe -o analysis -a C:\Trace\SQL2008Source\Trace.trc -b C:\ Trace\SQL2014Trace\Trace.trc -r upgrade20082014 -s localhost -e`

## <a name="next-steps"></a>Nächste Schritte

Für einen 19-minütige Einführung in DEA und Demonstrationen im folgenden Video:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
