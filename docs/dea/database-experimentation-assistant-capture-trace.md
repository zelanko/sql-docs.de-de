---
title: Aufzeichnen einer Ablauf Verfolgung in Assistent für Datenbankexperimente für SQL Server Upgrades
description: Aufzeichnen einer Ablauf Verfolgung in Assistent für Datenbankexperimente
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
ms.reviewer: mathoma
ms.openlocfilehash: 3887daff7807d57244449d4f35d220bb47b8f10d
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653818"
---
# <a name="capture-a-trace-in-database-experimentation-assistant"></a>Aufzeichnen einer Ablauf Verfolgung in Assistent für Datenbankexperimente

Sie können eine Ablauf Verfolgungs Datei in Assistent für Datenbankexperimente (DEA) verwenden, um eine Ablauf Verfolgungs Datei zu erstellen, die ein Protokoll der aufgezeichneten Server Ereignisse enthält. Ein erfasstes Server Ereignis ist ein Ereignis, das während eines bestimmten Zeitraums auf einem bestimmten Server auftritt. Eine Ablauf Verfolgungs Erfassung muss einmal pro Server ausgeführt werden.

Bevor Sie eine Ablauf Verfolgungs Erfassung starten, müssen Sie sicherstellen, dass Sie alle Ziel Datenbanken sichern.

Das Zwischenspeichern von Abfragen in SQL Server kann sich auf Auswertungs Ergebnisse auswirken Es wird empfohlen, den SQL Server-Dienst (MSSQLSERVER) in der Dienste-Anwendung neu zu starten, um die Konsistenz der Auswertungs Ergebnisse zu verbessern.

## <a name="create-a-trace-capture"></a>Erstellen einer Ablauf Verfolgungs Erfassung

1. Wählen Sie in der DEA im linken Menü das Menü Symbol aus. Wählen Sie im erweiterten Menü Ablauf Verfolgungen **erfassen** neben dem Kamerasymbol aus.

    ![Auswählen von Ablauf Verfolgungen im Menü](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-capture.png)

1. Geben Sie unter **neue Erfassung**die folgenden Informationen ein, oder wählen Sie Sie aus:

    - **SQL Server Instanzname**: Geben Sie einen Namen für den Computer ein, auf dem SQL Server ausgeführt wird, auf dem Sie eine Server Ablauf Verfolgung erfassen möchten.
    - **Datenbankname**: Geben Sie einen Namen für eine Datenbank ein, mit der eine Daten Bank Ablauf Verfolgung gestartet werden soll. Wenn Sie keine Datenbank angeben, wird die Ablauf Verfolgung für alle Datenbanken auf dem Server aufgezeichnet.
    - **Name der Ablauf Verfolgungs Datei**: Geben Sie einen Namen für die Ablauf Verfolgungs Datei für ihre Erfassung ein.
    - **Maximale Dateigröße (MB)** : Wählen Sie die rollovergröße für Dateien aus. Bei Bedarf wird eine neue Datei mit der von Ihnen ausgewählten Dateigröße erstellt. Die empfohlene rollovergröße beträgt 200 MB.
    - **Dauer (in Minuten)** : Wählen Sie die Zeitdauer (in Minuten) aus, für die die Ablauf Verfolgungs Erfassung ausgeführt werden soll.
    - **Pfad zum Speichern der Ausgabedatei**der Ablauf Verfolgung: Wählen Sie den Zielpfad für die Ablauf Verfolgungs Datei aus. 

    > [!NOTE]
    > Der Dateipfad zur Ablauf Verfolgungs Datei muss sich auf dem Computer befinden, auf dem SQL Server ausgeführt wird. Wenn der SQL Server-Dienst nicht für ein bestimmtes Konto festgelegt ist, benötigt der Dienst möglicherweise Schreibberechtigungen für den angegebenen Ordner, damit die Ablauf Verfolgungs Datei geschrieben werden kann.
    >
    >

    ![Neue Erfassungs Seite](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-inputs.png)

## <a name="start-the-trace-capture"></a>Starten der Ablauf Verfolgungs Erfassung

Nachdem Sie die erforderlichen Informationen eingegeben oder ausgewählt haben, wählen Sie **starten** , um die Erfassung von Ablauf Verfolgungen zu starten. Wenn die eingegebenen Informationen gültig sind, beginnt der Ablauf Verfolgungs Erfassungs Vorgang. Andernfalls werden die Textfelder mit ungültigen Einträgen rot hervorgehoben. 

Stellen Sie sicher, dass die Werte, die Sie ausgewählt oder eingegeben haben, richtig sind, und klicken Sie dann auf **starten**.

Wenn die Ausführung der Ablauf Verfolgungs Erfassung abgeschlossen ist, suchen Sie die neue Ablauf Verfolgungs Datei in dem Datei Speicherort, den Sie unter **Pfad zum Speichern der Ausgabedatei**der Ablauf Verfolgung angegeben haben. Wählen Sie das Glocken Symbol unten im linken Menü aus, um den Status der Erfassung zu überwachen.

![Verlauf der Aufzeichnungs Ablauf Verfolgung](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-progress.png)

### <a name="trace-file"></a>Ablaufverfolgungsdatei

Bei der Ablauf Verfolgungs Erfassung wird eine TRC-Datei am angegebenen Speicherort geschrieben. Die Ablauf Verfolgungs Datei enthält Ablauf Verfolgungs Ergebnisse der Aktivität einer SQL Server Datenbank. TRC-Dateien sind so konzipiert, dass Sie weitere Informationen zu Fehlern bereitstellen, die von SQL Server erkannt und gemeldet werden.

## <a name="frequently-asked-questions-about-trace-capture"></a>Häufig gestellte Fragen zur Ablauf Verfolgungs Erfassung

Im folgenden finden Sie einige häufig gestellte Fragen zur Erfassung von Ablauf Verfolgungen in Dea.

### <a name="what-events-are-captured-when-i-run-a-trace-capture-on-a-production-database"></a>Welche Ereignisse werden aufgezeichnet, wenn ich eine Ablauf Verfolgungs Erfassung für eine Produktionsdatenbank führe?

Die folgende Tabelle enthält die Liste der Ereignisse und die entsprechenden Spaltendaten, die wir für Ablauf Verfolgungen sammeln:
  
|Ereignisname|Textdaten (1)|Binärdaten (2)|Datenbank-ID (3)|Hostname (8)|Anwendungs Name (10)|Anmelde Name (11)|SPID (12)|Startzeit (14)|Endzeit (15)|Datenbankname (35)|Ereignis Sequenz (51)|IsSystem (60)|  
|---|---|---|---|---|---|---|---|---|---|---|---|---|  
|**RPC: abgeschlossen (10)**||*|*|*|*|*|*|*|*|*|*|*|  
|**RPC: wird gestartet (11)**||*|*|*|*|*|*|*||*|*|*|  
|**RPC-Ausgabe Parameter (100)**|*||*|*|*|*|*|*||*|*|*|  
|**SQL: batchabgeschlossene (12)**|*||*|*|*|*|*|*|*|*|*|*|  
|**SQL:BatchStarting (13)**|*||*|*|*|*|*|*||*|*|*|  
|**Audit Login (14)**|*|*|*|*|*|*|*|*||*|*|*|  
|**Abmelde protokolerung (15)**|*||*|*|*|*|*|*|*|*|*|*|  
|**ExistingConnection (17)**|*|*|*|*|*|*|*|*||*|*|*|  
|**Cursor Open (53)**|*||*|*|*|*|*|*||*|*|*|  
|**Cursor Vorbereitung (70)**|*||*|*|*|*|*|*||*|*|*|  
|**Prepare SQL (71)**|||*|*|*|*|*|*||*|*|*|  
|**Exec Prepared SQL (72)**|||*|*|*|*|*|*||*|*|*|  
|**Cursor Execute (74)**|*||*|*|*|*|*|*||*|*|*|  
|**Currsorunprepare (77)**|*||*|*|*|*|*|*||*|*|*|  
|**Cursor schließen (78)**|*||*|*|*|*|*|*||*|*|*|  

### <a name="is-there-a-performance-effect-on-my-production-server-when-trace-capture-is-running"></a>Gibt es einen Leistungs Effekt auf dem Produktionsserver, wenn die Ablauf Verfolgungs Erfassung ausgeführt wird?
    
Ja, es gibt eine minimale Leistungs Auswirkung während der Ablauf Verfolgungs Sammlung. In unseren Tests haben wir ungefähr eine Speicherauslastung von 3% festgestellt.
    
### <a name="what-kind-of-permissions-are-required-for-capturing-traces-on-a-production-workload"></a>Welche Art von Berechtigungen ist für die Erfassung von Ablauf Verfolgungen für eine produktionsworkloads erforderlich?
    
- Der Windows-Benutzer, der den Ablauf Verfolgungs Vorgang in der DEA-Anwendung ausführt, muss auf dem Computer, auf dem SQL Server ausgeführt wird, über Systemadministrator Rechte verfügen.
- Das Dienst Konto, das auf dem Computer verwendet wird, auf dem SQL Server ausgeführt wird, muss Schreibzugriff auf den angegebenen Pfad der Ablauf Verfolgungs Datei

### <a name="can-i-capture-traces-for-the-entire-server-or-only-on-a-single-database"></a>Kann ich Ablauf Verfolgungen für den gesamten Server oder nur für eine einzelne Datenbank erfassen?
    
Mithilfe von DEA können Sie Ablauf Verfolgungen für alle Datenbanken auf dem Server oder für eine einzelne Datenbank erfassen.
    
### <a name="i-have-a-linked-server-configured-in-my-production-environment-do-those-queries-show-up-in-the-traces"></a>In meiner Produktionsumgebung ist ein Verbindungs Server konfiguriert. Werden diese Abfragen in den Ablauf Verfolgungen angezeigt?
    
Wenn Sie eine Ablauf Verfolgungs Erfassung für den gesamten Server ausführen, erfasst die Ablauf Verfolgung alle Abfragen, einschließlich der verknüpften Server Abfragen. Wenn Sie eine Ablauf Verfolgungs Erfassung für den gesamten Server ausführen möchten, lassen Sie das Feld **Datenbankname** unter **neue Erfassung** leer.
    
### <a name="whats-the-minimum-recommended-time-for-production-workload-traces"></a>Was ist die empfohlene mindestanzeit für Ablauf Verfolgungen für die Arbeitsauslastung?
    
Es wird empfohlen, dass Sie eine Zeit auswählen, die die gesamte Arbeitsauslastung am besten repräsentiert. Auf diese Weise wird die Analyse für alle Abfragen in Ihrer Arbeitsauslastung ausgeführt.
    
### <a name="how-important-is-to-take-a-database-backup-right-before-i-start-a-trace-capture"></a>Wie wichtig ist es, eine Datenbanksicherung zu erstellen, bevor Sie eine Ablauf Verfolgungs Erfassung starten?
    
Bevor Sie eine Ablauf Verfolgungs Erfassung starten, müssen Sie sicherstellen, dass Sie alle Ihre Ziel Datenbanken sichern. Die erfasste Ablauf Verfolgung in Ziel 1 und Ziel 2 wird wiedergegeben. Wenn der Daten Bank Status nicht identisch ist, werden die Ergebnisse der Experimente verzerrt.

### <a name="can-i-collect-xevents-instead-of-traces-and-can-i-replay-xevents"></a>Kann ich xevents anstelle von Ablauf Verfolgungen erfassen, und kann ich xevents wiedergeben?
    
Ja. "DEA" unterstützt xevents. Laden Sie die neueste Version von DEA herunter, und probieren Sie Sie aus.

## <a name="troubleshoot-trace-captures"></a>Problembehandlung bei Ablauf Verfolgungs Aufzeichnungen

Wenn beim Ausführen einer Ablauf Verfolgungs Erfassung ein Fehler angezeigt wird, überprüfen Sie die folgenden Voraussetzungen:

- Vergewissern Sie sich, dass der Name des Computers, der SQL Server ausgeführt wird, gültig ist. Versuchen Sie, eine Verbindung mit dem Computer herzustellen, auf dem SQL Server ausgeführt wird, indem Sie SQL Server Management Studio (SSMS) verwenden.
- Vergewissern Sie sich, dass Ihre Firewallkonfiguration keine Verbindungen mit dem Computer blockiert, der SQL Server ausgeführt wird
- Vergewissern Sie sich, dass der Benutzer über die Berechtigungen verfügt, die im Blogbeitrag [Replay Replay FAQ](https://blogs.msdn.microsoft.com/datamigration/2017/03/24/dea-2-0-replay-faq/)aufgeführt sind.
- Vergewissern Sie sich, dass der Ablauf Verfolgungs Name nicht der standardrolloverkonvention (Erfassung\_1) folgt. Versuchen Sie stattdessen, Namen von Ablauf\_Verfolgungen wie z. b. Capture 1A oder Capture1

Im folgenden finden Sie einige mögliche Fehler, die möglicherweise angezeigt werden, und Lösungen für deren Behebung:

|Mögliche Fehler|Lösung|  
|---|---|  
|Die Ablauf Verfolgung kann nicht auf dem Ziel SQL Server gestartet werden. Überprüfen Sie, ob Sie über die erforderlichen Berechtigungen verfügen und dass das SQL Server Konto Schreibzugriff auf den angegebenen Pfad für die Ablauf Verfolgungs Datei hat SQL-Fehler Code (53).|Der Benutzer, der das Tool "DEA" ausgeführt hat, muss Zugriff auf den Computer mit SQL Server haben. Dem Benutzer muss die sysadmin-Rolle zugewiesen werden.|  
|Die Ablauf Verfolgung kann nicht auf dem Ziel SQL Server gestartet werden. Überprüfen Sie, ob Sie über die erforderlichen Berechtigungen verfügen und dass das SQL Server Konto Schreibzugriff auf den angegebenen Pfad für die Ablauf Verfolgungs Datei hat SQL-Fehler Code (19062).|Der angegebene Ablauf Verfolgungs Pfad ist möglicherweise nicht vorhanden, oder der Ordner verfügt nicht über Schreibberechtigungen für das Konto, unter dem SQL Server-Dienste ausgeführt werden (z. b. Netzwerkdienst). Der Pfad muss vorhanden sein und muss über die erforderlichen Berechtigungen verfügen, damit die Ablauf Verfolgung gestartet werden kann.|  
|Auf dem Zielserver wird derzeit eine DEA-Ablauf Verfolgung ausgeführt.|Eine aktive Ablauf Verfolgung wird bereits auf dem Zielserver ausgeführt. Eine neue Ablauf Verfolgung kann nicht gestartet werden, wenn bereits eine Server weite Ablauf Verfolgung ausgeführt wird.|  
|Die angeforderte Datenbank kann nicht zum Erfassen der Ablauf Verfolgung geöffnet werden. Dieser Fehler kann durch einen falschen Datenbanknamen verursacht werden.|Die angegebene Datenbank ist nicht vorhanden, oder der aktuelle Benutzer ist nicht verfügbar. Verwenden Sie den richtigen Datenbanknamen.|  

Wenn Sie andere Fehler mit der Bezeichnung *SQL-Fehler Code*sehen, finden Sie unter [Datenbank-Engine Fehler](https://docs.microsoft.com/sql/relational-databases/errors-events/database-engine-events-and-errors) ausführliche Beschreibungen.

## <a name="next-steps"></a>Nächste Schritte

- Informationen zum Konfigurieren der Distributed Replay Tools in SQL Server vor der Wiedergabe einer aufgezeichneten Ablauf Verfolgung finden Sie unter Konfigurieren der wieder [Gabe](database-experimentation-assistant-configure-replay.md).

- Sehen Sie sich das folgende Video an, um die Einführung von DEA und Demo in 19 Minuten zu demonstrieren:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
