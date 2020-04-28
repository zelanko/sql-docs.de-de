---
title: Ausführen von Assistent für Datenbankexperimente an einer Eingabeaufforderung
description: Ausführen von Assistent für Datenbankexperimente an einer Eingabeaufforderung
ms.custom: seo-lt-2019
ms.date: 02/25/2020
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.openlocfilehash: f2640e9018f29385851839932572aeaa3ee91ad9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "77600130"
---
# <a name="run-database-experimentation-assistant-at-a-command-prompt"></a>Ausführen von Assistent für Datenbankexperimente an einer Eingabeaufforderung

In diesem Artikel wird beschrieben, wie Sie eine Ablauf Verfolgung in Assistent für Datenbankexperimente (DEA) erfassen und dann die Ergebnisse über eine Eingabeaufforderung analysieren.

   > [!NOTE]
   > Wenn Sie mehr über jeden DEA-Vorgang erfahren möchten, führen Sie den folgenden Befehl aus:
   >
   > `Deacmd.exe -o <operation> --help`
   >
   > Ein Vorgangs Name ist erforderlich. gültige Vorgänge sind **Analysis**, **startcapture**und **stopcapture**.

## <a name="start-a-new-workload-capture-by-using-the-dea-command"></a>Starten einer neuen Arbeits Auslastungs Erfassung mit dem Befehl "DEA"

Führen Sie an einer Eingabeaufforderung den folgenden Befehl aus, um eine neue Arbeits Auslastungs Erfassung zu starten:

`Deacmd.exe -o StartCapture -h <SQLServerInstance> -e <encryptconnection> -u <trustservercertificate> -d <database name> -p <trace file path> -f <trace file name> -t <Max duration>`

**Beispiel**

`Deacmd.exe -o StartCapture -h localhost -e -d adventureworks -p c:\test -f sql2008capture -t 60`

**Zusätzliche Optionen**

Beim Starten einer neuen Arbeits Auslastungs `Deacmd.exe` Erfassung mit dem Befehl können Sie die folgenden zusätzlichen Optionen verwenden:

| Option| BESCHREIBUNG |  
| --- | --- |
| -n, --name | Benötigten Name der Ablauf Verfolgungs Datei |
| -x,--Format | Benötigten Format der Ablauf Verfolgung (Trace = 0, xevents = 1) |
| -d,--Dauer | Benötigten maximale Dauer für die Erfassung (in Minuten) |
| -l, --location | Benötigten Speicherort des Ausgabe Ordners zum Speichern von Trace/XEvent-Dateien auf dem Host Computer |
| -t,--Typ | (Standard: 0) Typ/Edition von SQL Server (SQLServer = 0, azuresqldb = 1, Azure SQL verwaltete Instanz = 2) |
| -h, --host | Benötigten SQL Server Hostnamen und/oder Instanzname zum Starten der Erfassung |
| -e,--verschlüsseln | (Standardwert: true) Verschlüsseln Sie die Verbindung mit SQL Server-Instanz. Die Standardeinstellung ist „true“. |
| --Vertrauensstellung | (Standardwert: false) Vertrauenswürdiges Serverzertifikat beim Herstellen einer Verbindung mit SQL Server-Instanz. Die Standardeinstellung ist „false“. |
| -f,--DatabaseName | (Standard:) Der Name der Datenbank, in der die Ablauf Verfolgungen gefiltert werden sollen. Falls nicht angegeben, wird die Erfassung für alle Datenbanken gestartet. |
| -m,--authmode | (Standard: 0) Authentifizierungsmodus (Windows = 0, SQL-Authentifizierung = 1) |
| -u,--username | Benutzername für die Verbindung mit der SQL Server |
| -p,--Kennwort | Kennwort für das Herstellen einer Verbindung mit dem SQL Server |

## <a name="replay-a-workload-capture"></a>Wiedergeben einer workloaderfassung

**Verwenden von Distributed Replay**

Wenn Sie Distributed Replay verwenden, führen Sie die folgenden Schritte aus.

1. Melden Sie sich beim Distributed Replay Controller-Computer an.
2. Führen Sie an einer Eingabeaufforderung den folgenden Befehl aus, um die Arbeits Auslastungs Ablauf Verfolgung, die Sie mit dem Befehl "DEA" erfasst haben, in eine UNF-Datei umzuwandeln

    `DReplay preprocess -m "dreplaycontroller" -i "Path to first trace file" -d "<Folder path on controller>\IrfFolder"`

3. Starten Sie auf dem Zielcomputer, auf dem SQL Server ausgeführt wird, eine Ablauf Verfolgungs Erfassung mit startreplaycapturetrace. SQL.

    a.  Öffnen Sie in SQL Server Management Studio (SSMS) <Dea_InstallPath\>\script\startreplaycapturetrace.SQL.

    b.  Führen `Set @durationInMins=0` Sie aus, damit die Ablauf Verfolgungs Erfassung nach einem angegebenen Zeitpunkt nicht automatisch beendet wird.

    c.  Führen Sie aus, um die maximale Dateigröße pro Ablauf `Set @maxfilesize`Verfolgungs Datei festzulegen. Die empfohlene Größe ist 200 (in MB).

    d.  Bearbeiten `@Tracefile` Sie, um einen eindeutigen Namen für die Ablauf Verfolgungs Datei festzulegen.

    e.  Bearbeiten `@dbname` Sie, um einen Datenbanknamen anzugeben, wenn die Arbeitsauslastung nur für eine bestimmte Datenbank aufgezeichnet werden muss. Standardmäßig wird die Arbeitsauslastung auf dem gesamten Server aufgezeichnet.

4. Führen Sie an einer Eingabeaufforderung den folgenden Befehl aus, um die UNF-Datei für die Ziel SQL Server Instanz wiederzugeben:

    `DReplay replay -m "dreplaycontroller" -d "<Folder Path on Dreplay Controller>\IrfFolder" -o -s "SQL2016Target" -w "dreplaychild1,dreplaychild2,dreplaycild3,dreplaychild4"`

    a.  Führen `DReplay status -f 1`Sie an einer Eingabeaufforderung aus, um den Status zu überwachen.

    b.  Um die Wiedergabe anzuhalten, z. b. Wenn Sie sehen, dass der Durchlauf% niedriger als erwartet ist, führen `DReplay cancel`Sie an einer Eingabeaufforderung aus.

5. Beendet die Ablauf Verfolgungs Erfassung auf der Ziel SQL Server Instanz.
6. Öffnen `<Dea_InstallPath>\Scripts\StopCaptureTrace.sql`Sie in SSMS.
7. Bearbeiten `@Tracefile` Sie, um den Pfad der Ablauf Verfolgungs Datei auf dem Zielcomputer mit SQL Server abzugleichen.
8. Führen Sie das Skript auf dem Zielcomputer mit SQL Server aus.

**Verwenden der integrierten Wiedergabe**

Wenn Sie die integrierte Wiedergabe verwenden, müssen Sie Distributed Replay nicht einrichten. Die Möglichkeit, die integrierte Wiedergabe über die Befehlszeile zu verwenden, ist auf dem Weg, aber in der Zwischenzeit können Sie die Benutzeroberfläche verwenden, um die Wiedergabe mit integrierter Wiedergabe auszuführen.

## <a name="analyze-traces-using-the-dea-command"></a>Analysieren von Ablauf Verfolgungen mit dem Befehl "DEA"

Führen Sie an einer Eingabeaufforderung den folgenden Befehl aus, um eine neue Ablauf Verfolgungs Analyse zu starten:

`Deacmd.exe -o analysis -a <Target1 trace filepath> -b <Target2 trace filepath> -r reportname -h <SQLserverInstance> -e <encryptconnection> -u <trustservercertificate>`

**Beispiel**

`Deacmd.exe -o analysis -a C:\Trace\SQL2008Source\Trace.trc -b C:\ Trace\SQL2014Trace\Trace.trc -r upgrade20082014 -s localhost -e`

Zum Anzeigen der Analyseberichte dieser Ablauf Verfolgungs Dateien müssen Sie die GUI zum Anzeigen von Diagrammen und organisierten Metriken verwenden.  Die Analysedatenbank wird jedoch in die angegebene SQL Server Instanz geschrieben, sodass Sie die generierten Analyse Tabellen auch direkt abfragen können.

**Zusätzliche Optionen**

Beim Analysieren von Ablauf Verfolgungen mit dem Befehl "DEA" können Sie die folgenden zusätzlichen Optionen verwenden:

| Option| BESCHREIBUNG |  
| --- | --- |
| -a,--tracea | Benötigten Dateipfad zur Ereignis Datei für eine-Instanz. Beispiel: c:\traces\sql2008trace.trc.  Wenn es einen Batch von Dateien gibt, wählen Sie die erste Datei aus, und die DEA überprüft automatisch, ob Rolloverdateien vorhanden sind. Wenn sich Dateien im BLOB befinden, geben Sie den Ordner Pfad an, in dem die Ereignis Dateien lokal gespeichert werden sollen.  Beispiel: c:\traces\ |
| -b,--traceb | Benötigten Dateipfad zur Ereignis Datei für die B-Instanz. Beispiel: c:\traces\sql2014trace.trc. Wenn es einen Batch von Dateien gibt, wählen Sie die erste Datei aus, und die DEA überprüft automatisch, ob Rolloverdateien vorhanden sind. Wenn sich Dateien im BLOB befinden, geben Sie den Ordner Pfad an, in dem die Ereignis Dateien lokal gespeichert werden sollen.  Beispiel: c:\traces\ |
| -r,--Report Name | Benötigten der Name für die aktuelle Analyse. Der Analysebericht, der generiert wird, wird anhand dieses Namens identifiziert. |
| -t,--Typ | (Standard: 0) Typ/Edition von SQL Server (SQLServer = 0, azuresqldb = 1, Azure SQL verwaltete Instanz = 2) |
| -h, --host | Benötigten SQL Server Hostname und/oder Instanzname |
| -e,--verschlüsseln | (Standardwert: true) Verschlüsseln Sie die Verbindung mit SQL Server-Instanz. Die Standardeinstellung ist „true“. |
| --Vertrauensstellung | (Standardwert: false) Vertrauenswürdiges Serverzertifikat beim Herstellen einer Verbindung mit SQL Server-Instanz. Die Standardeinstellung ist „false“. |
| -m,--authmode | (Standard: 0) Authentifizierungsmodus (Windows = 0, SQL-Authentifizierung = 1) |
| -u,--username | Benutzername für die Verbindung mit der SQL Server |
| --p | Kennwort für das Herstellen einer Verbindung mit dem SQL Server |
| --ab | (Standardwert: false) Der Speicherort der Ablauf Verfolgung A befindet sich im BLOB. Bei Verwendung von muss auch--Abu (Trace A BLOB URL) angegeben werden. |
| --BB | (Standardwert: false) Der Speicherort der Ablauf Verfolgung B befindet sich im BLOB. Bei Verwendung von muss auch--BBU (Trace B-BLOB-URL) angegeben werden. |
| --Abu | BLOB-URL für eine-Instanz mit einem SAS-Schlüssel |
| --BBU | BLOB-URL für B-Instanz mit SAS-Schlüssel |

## <a name="see-also"></a>Weitere Informationen:

- Weitere Informationen zur Verwendung von DEA finden Sie unter [Übersicht über Assistent für Datenbankexperimente](database-experimentation-assistant-overview.md).
