---
title: Ausführen von Assistent für Datenbankexperimente an einer Eingabeaufforderung
description: Ausführen von Assistent für Datenbankexperimente an einer Eingabeaufforderung
ms.custom: seo-lt-2019
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
ms.openlocfilehash: c3b87eafa460cfef69666a3837f56626dab81d47
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056571"
---
# <a name="run-database-experimentation-assistant-at-a-command-prompt-sql-server"></a>Ausführen von Assistent für Datenbankexperimente an einer Eingabeaufforderung (SQL Server)

In diesem Artikel wird beschrieben, wie Sie das Eingabe Aufforderungs Fenster verwenden, um eine Ablauf Verfolgung in Assistent für Datenbankexperimente (DEA) aufzuzeichnen und anschließend die Ergebnisse zu analysieren. 

## <a name="start-a-new-workload-capture-by-using-the-dea-command"></a>Starten einer neuen Arbeits Auslastungs Erfassung mit dem Befehl "DEA"

Führen Sie den folgenden Befehl aus, um eine neue Arbeits Auslastungs Erfassung zu starten:

`Deacmd.exe -o startcapturetrace -s <SQLServerInstance> -e <encryptconnection> -u <trustservercertificate> -d <database name> -p <trace file path> -f <trace file name> -t <Max duration>`

**Beispiel**

`Deacmd.exe -o startcapturetrace -s localhost -e -d adventureworks -p c:\test -f sql2008capture -t 60`

## <a name="replay-a-workload"></a>Wiedergeben einer Arbeitsauslastung

1.  Melden Sie sich beim Distributed Replay Controller-Computer an.
2.  Konvertieren Sie die von Ihnen erfasste workloadablauf Verfolgung mit dem Befehl "DEA" in eine UNF-Datei:

    `DReplay preprocess -m "dreplaycontroller" -i "Path to first trace file" -d "<Folder path on controller>\IrfFolder"`

3.  Starten Sie mithilfe von startreplaycapturetrace. SQL eine Ablauf Verfolgungs Erfassung auf dem Zielcomputer, auf dem SQL Server ausgeführt wird.
       
    a.  Öffnen Sie in SQL Server Management Studio (SSMS) < Dea_InstallPath\>\script\startreplaycapturetrace.SQL.
    
    b.  Führen Sie `Set @durationInMins=0` aus, damit die Ablauf Verfolgungs Erfassung nach einem angegebenen Zeitpunkt nicht automatisch beendet wird.
    
    c.  Führen Sie `Set @maxfilesize`aus, um die maximale Dateigröße pro Ablauf Verfolgungs Datei festzulegen. Die empfohlene Größe ist 200 (in MB).
    
    d.  Bearbeiten Sie `@Tracefile`, um einen eindeutigen Namen für die Ablauf Verfolgungs Datei festzulegen.
    
    e.  Bearbeiten Sie `@dbname`, um einen Datenbanknamen anzugeben, wenn die Arbeitsauslastung nur für eine bestimmte Datenbank aufgezeichnet werden muss. Standardmäßig wird die Arbeitsauslastung auf dem gesamten Server aufgezeichnet. 
4.  Wiedergeben der Datei "UNF" für die Ziel SQL Server Instanz:

    `DReplay replay -m "dreplaycontroller" -d "<Folder Path on Dreplay Controller>\IrfFolder" -o -s "SQL2016Target" -w "dreplaychild1,dreplaychild2,dreplaycild3,dreplaychild4"`
        
    a.  Öffnen Sie zum Überwachen des Status ein Eingabe Aufforderungs Fenster, und führen Sie `DReplay status -f 1`aus.
        
    b.  Öffnen Sie ein Eingabe Aufforderungs Fenster, und führen Sie `DReplay cancel`aus, um die Wiedergabe zu verhindern, z. b. Wenn Sie sehen, dass der Durchlauf% niedriger als erwartet ist.

5.  Beendet die Ablauf Verfolgungs Erfassung auf der Ziel SQL Server Instanz.
6.  Öffnen Sie in SSMS `<Dea_InstallPath>\Scripts\StopCaptureTrace.sql`.
7.  Bearbeiten Sie `@Tracefile`, um den Pfad der Ablauf Verfolgungs Datei auf dem Zielcomputer mit SQL Server abzugleichen.
8.  Führen Sie das Skript auf dem Zielcomputer mit SQL Server aus.

## <a name="analyze-traces-by-using-the-dea-command"></a>Analysieren von Ablauf Verfolgungen mit dem Befehl "DEA"

Führen Sie den folgenden Befehl aus, um eine neue Ablauf Verfolgungs Analyse zu starten:

`Deacmd.exe -o analysis -a <Target1 trace filepath> -b <Target2 trace filepath> -r reportname -s <SQLserverInstance> -e <encryptconnection> -u <trustservercertificate>`

**Beispiel**

`Deacmd.exe -o analysis -a C:\Trace\SQL2008Source\Trace.trc -b C:\ Trace\SQL2014Trace\Trace.trc -r upgrade20082014 -s localhost -e`

## <a name="next-steps"></a>Nächste Schritte

Sehen Sie sich das folgende Video an, um die Einführung von DEA und Demo in 19 Minuten zu demonstrieren:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
