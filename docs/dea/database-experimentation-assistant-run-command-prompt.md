---
title: Ausführen von Assistent für Datenbankexperimente an einer Eingabeaufforderung
description: Ausführen von Assistent für Datenbankexperimente an einer Eingabeaufforderung
ms.custom: seo-lt-2019
ms.date: 11/22/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.openlocfilehash: f5a0f7441dd17aec2587c772a678a3681fd3b423
ms.sourcegitcommit: 9e026cfd9f2300f106af929d88a9b43301f5edc2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74317719"
---
# <a name="run-database-experimentation-assistant-at-a-command-prompt"></a>Ausführen von Assistent für Datenbankexperimente an einer Eingabeaufforderung

In diesem Artikel wird beschrieben, wie Sie eine Ablauf Verfolgung in Assistent für Datenbankexperimente (DEA) erfassen und dann die Ergebnisse über eine Eingabeaufforderung analysieren.

## <a name="start-a-new-workload-capture-by-using-the-dea-command"></a>Starten einer neuen Arbeits Auslastungs Erfassung mit dem Befehl "DEA"

Führen Sie an einer Eingabeaufforderung den folgenden Befehl aus, um eine neue Arbeits Auslastungs Erfassung zu starten:

`Deacmd.exe -o startcapturetrace -s <SQLServerInstance> -e <encryptconnection> -u <trustservercertificate> -d <database name> -p <trace file path> -f <trace file name> -t <Max duration>`

**Beispiel**

`Deacmd.exe -o startcapturetrace -s localhost -e -d adventureworks -p c:\test -f sql2008capture -t 60`

## <a name="replay-a-workload-capture"></a>Wiedergeben einer workloaderfassung

1. Melden Sie sich beim Distributed Replay Controller-Computer an.
2. Führen Sie an einer Eingabeaufforderung den folgenden Befehl aus, um die Arbeits Auslastungs Ablauf Verfolgung, die Sie mit dem Befehl "DEA" erfasst haben, in eine UNF-Datei umzuwandeln

    `DReplay preprocess -m "dreplaycontroller" -i "Path to first trace file" -d "<Folder path on controller>\IrfFolder"`

3. Starten Sie auf dem Zielcomputer, auf dem SQL Server ausgeführt wird, eine Ablauf Verfolgungs Erfassung mit startreplaycapturetrace. SQL.

    ein.  Öffnen Sie in SQL Server Management Studio (SSMS) <Dea_InstallPath\>\script\startreplaycapturetrace.SQL.

    b.  Führen `Set @durationInMins=0` Sie aus, damit die Ablauf Verfolgungs Erfassung nach einem angegebenen Zeitpunkt nicht automatisch beendet wird.

    c.  Führen Sie aus, um die maximale Dateigröße pro Ablauf `Set @maxfilesize`Verfolgungs Datei festzulegen. Die empfohlene Größe ist 200 (in MB).

    d.  Bearbeiten `@Tracefile` Sie, um einen eindeutigen Namen für die Ablauf Verfolgungs Datei festzulegen.

    e.  Bearbeiten `@dbname` Sie, um einen Datenbanknamen anzugeben, wenn die Arbeitsauslastung nur für eine bestimmte Datenbank aufgezeichnet werden muss. Standardmäßig wird die Arbeitsauslastung auf dem gesamten Server aufgezeichnet.

4. Führen Sie an einer Eingabeaufforderung den folgenden Befehl aus, um die UNF-Datei für die Ziel SQL Server Instanz wiederzugeben:

    `DReplay replay -m "dreplaycontroller" -d "<Folder Path on Dreplay Controller>\IrfFolder" -o -s "SQL2016Target" -w "dreplaychild1,dreplaychild2,dreplaycild3,dreplaychild4"`

    ein.  Führen `DReplay status -f 1`Sie an einer Eingabeaufforderung aus, um den Status zu überwachen.

    b.  Um die Wiedergabe anzuhalten, z. b. Wenn Sie sehen, dass der Durchlauf% niedriger als erwartet ist, führen `DReplay cancel`Sie an einer Eingabeaufforderung aus.

5. Beendet die Ablauf Verfolgungs Erfassung auf der Ziel SQL Server Instanz.
6. Öffnen `<Dea_InstallPath>\Scripts\StopCaptureTrace.sql`Sie in SSMS.
7. Bearbeiten `@Tracefile` Sie, um den Pfad der Ablauf Verfolgungs Datei auf dem Zielcomputer mit SQL Server abzugleichen.
8. Führen Sie das Skript auf dem Zielcomputer mit SQL Server aus.

## <a name="analyze-traces-using-the-dea-command"></a>Analysieren von Ablauf Verfolgungen mit dem Befehl "DEA"

Führen Sie an einer Eingabeaufforderung den folgenden Befehl aus, um eine neue Ablauf Verfolgungs Analyse zu starten:

`Deacmd.exe -o analysis -a <Target1 trace filepath> -b <Target2 trace filepath> -r reportname -s <SQLserverInstance> -e <encryptconnection> -u <trustservercertificate>`

**Beispiel**

`Deacmd.exe -o analysis -a C:\Trace\SQL2008Source\Trace.trc -b C:\ Trace\SQL2014Trace\Trace.trc -r upgrade20082014 -s localhost -e`

## <a name="see-also"></a>Siehe auch

- Weitere Informationen zur Verwendung von DEA finden Sie unter [Übersicht über Assistent für Datenbankexperimente](database-experimentation-assistant-overview.md).
