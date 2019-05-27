---
title: Erfassen einer Ablaufverfolgung im Datenbank-experimentieren-Assistenten für SQL Server-upgrades
description: Erfassen einer Ablaufverfolgung im Datenbank-experimentieren-Assistenten
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
manager: craigg
ms.openlocfilehash: 822f8d02a9bcaa27a405acdc351646fd63560880
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2019
ms.locfileid: "66015168"
---
# <a name="capture-a-trace-in-database-experimentation-assistant"></a>Erfassen einer Ablaufverfolgung im Datenbank-experimentieren-Assistenten

Können eine Aufzeichnungsinstanz für die Ablaufverfolgung in Datenbank experimentieren-Assistenten (DEA) zum Erstellen einer Ablaufverfolgungsdatei, die über ein Protokoll der aufgezeichnete Serverereignisse verfügt. Ein Serverereignis erfassten handelt es sich um ein Ereignis, das auf einem bestimmten Server in einem bestimmten Zeitraum auftritt. Eine Aufzeichnungsinstanz für die Ablaufverfolgung muss einmal pro Server ausgeführt werden.

Bevor Sie eine Ablaufverfolgung Erfassung beginnen, stellen Sie sicher, dass Sie alle Zieldatenbanken sichern.

Abfrage in SQL Server-Cache kann die auswertungsergebnisse auswirken. Es wird empfohlen, dass Sie die SQL Server-Dienst (MSSQLSERVER) neu starten, in der dienstanwendung, um die Konsistenz der Ergebnisse zu verbessern.

## <a name="create-a-trace-capture"></a>Erstellen Sie eine Ablaufverfolgung erfassen

1. Wählen Sie in DEA das Menüsymbol im im linken Menü aus. Wählen Sie im erweiterten Menü **Erfassen von Ablaufverfolgungen** neben dem Kamerasymbol.

    ![Wählen Sie im Menü Erfassen von Ablaufverfolgungen](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-capture.png)

1. Klicken Sie unter **New Capture**, geben Sie ein oder wählen Sie die folgende Informationen:

    - **SQL Server-Instanzname**: Geben Sie einen Namen für den Computer mit SQL Server auf dem Sie eine serverablaufverfolgung erfassen möchten.
    - **Name der Datenbank**: Geben Sie einen Namen für eine Datenbank, in eine Datenbank-Ablaufverfolgung zu starten. Wenn Sie eine Datenbank nicht angeben, wird die Ablaufverfolgung für alle Datenbanken auf dem Server erfasst.
    - **Name der Ablaufverfolgungsdatei**: Geben Sie einen Namen für die Ablaufverfolgungsdatei für die Erfassung aus.
    - **Maximale Dateigröße (MB)**: Wählen Sie die Rollover-Größe für Dateien. Wie die Größe der Datei benötigt wird, die Sie auswählen, wird eine neue Datei erstellt. Die empfohlene Rollover-Größe beträgt 200 MB.
    - **Dauer (in Minuten)**: Wählen Sie die Zeitdauer (in Minuten) an, die die Ablaufverfolgung Erfassung ausgeführt werden sollen.
    - **Pfad zum Speichern der Datei Ablaufverfolgungsausgabe**: Wählen Sie den Zielpfad für die Ablaufverfolgungsdatei an. 

    > [!NOTE]
    > Der Dateipfad, in die Ablaufverfolgungsdatei muss auf dem Computer, auf denen SQL Server ausgeführt wird. Wenn SQL Server-Dienst nicht für ein bestimmtes Konto festgelegt ist, der Dienst kann Berechtigungen für den angegebenen Ordner für die Ablaufverfolgungsdatei geschrieben werden schreiben müssen.
    >
    >

    ![Seite "neue erfassen"](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-inputs.png)

## <a name="start-the-trace-capture"></a>Starten der Trace-Erfassung

Wählen Sie nach dem eingeben oder der erforderlichen Informationen auswählen, **starten** zum Starten der Erfassung von ablaufverfolgungen. Wenn die Informationen, die Sie eingegeben haben, gültig ist, beginnt der Vorgang der Ablaufverfolgungssammlung. Andernfalls werden die Textfelder, die ungültige Einträge mit roten hervorgehoben. 

Stellen Sie sicher, dass die Werte, die Sie ausgewählt oder eingegeben haben, richtig sind, und Sie dann wählen **starten**.

Nach Abschluss die Ablaufverfolgung Erfassung ausgeführt wird, suchen Sie Ihre neue Ablaufverfolgungsdatei den Speicherort der Datei, die im angegeben **Pfad zum Speichern der Datei Ablaufverfolgungsausgabe**. Wählen Sie das Glockensymbol am unteren Rand im linken Menü den Status der Erfassung überwacht.

![Erfassen von Ablaufverfolgungen wird ausgeführt](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-progress.png)

### <a name="trace-file"></a>Ablaufverfolgungsdatei

Die Erfassung der Ablaufverfolgung einer TRC-Datei am angegebenen Speicherort geschrieben. Die Ablaufverfolgungsdatei enthält Ablaufverfolgungsergebnisse für die Aktivität von einer SQL Server-Datenbank. Um weitere Informationen zu Fehlern bereitzustellen, die erkannt und von SQL Server gemeldeten ist TRC-Dateien dienen.

## <a name="frequently-asked-questions-about-trace-capture"></a>Häufig gestellte Fragen zur Ablaufverfolgung erfassen

Folgenden werden einige häufig gestellte Fragen zur Erfassung der Ablaufverfolgung in DEA.

### <a name="what-events-are-captured-when-i-run-a-trace-capture-on-a-production-database"></a>Welche Ereignisse erfasst werden, wenn ich eine Aufzeichnung der Ablaufverfolgung in einer Produktionsdatenbank ausführen?

Die folgende Tabelle enthält die Liste der Ereignisse und der entsprechenden Spaltendaten, die wir für ablaufverfolgungen zu erfassen:
  
|Ereignisname|Text-Daten (1)|Binäre Daten (2)|Datenbank-ID (3)|Name des Hosts (8)|Anwendungsname (10)|Anmeldename (11)|SPID (12)|Startzeit (14)|Endzeit (15)|Name der Datenbank (35)|Die Sequenz (51)|IsSystem (60)|  
|---|---|---|---|---|---|---|---|---|---|---|---|---|  
|**RPC: abgeschlossen (10)**||*|*|*|*|*|*|*|*|*|*|*|  
|**RPC: Starten (11)**||*|*|*|*|*|*|*||*|*|*|  
|**RPC Output Parameter (100)**|*||*|*|*|*|*|*||*|*|*|  
|**SQL:BatchCompleted (12)**|*||*|*|*|*|*|*|*|*|*|*|  
|**SQL:BatchStarting (13)**|*||*|*|*|*|*|*||*|*|*|  
|**Audit Login (14)**|*|*|*|*|*|*|*|*||*|*|*|  
|**Audit Logout (15)**|*||*|*|*|*|*|*|*|*|*|*|  
|**ExistingConnection (17)**|*|*|*|*|*|*|*|*||*|*|*|  
|**CursorOpen (53)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorPrepare (70)**|*||*|*|*|*|*|*||*|*|*|  
|**Prepare SQL (71)**|||*|*|*|*|*|*||*|*|*|  
|**Exec Prepared SQL (72)**|||*|*|*|*|*|*||*|*|*|  
|**CursorExecute (74)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorUnprepare (77)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorClose (78)**|*||*|*|*|*|*|*||*|*|*|  

### <a name="is-there-a-performance-effect-on-my-production-server-when-trace-capture-is-running"></a>Gibt es eine Auswirkung auf die Leistung auf meinem Produktionsserver bei der Erfassung der Ablaufverfolgung ausgeführt wird?
    
Ja, besteht eine Auswirkung auf die minimale Leistung bei der Ablaufverfolgungssammlung. Wir bei unseren Tests eine arbeitsspeicherauslastung von 3 % gefunden.
    
### <a name="what-kind-of-permissions-are-required-for-capturing-traces-on-a-production-workload"></a>Welche Berechtigungen sind für die Erfassung von ablaufverfolgungen für eine produktionsworkload erforderlich?
    
- Der Windows-Benutzer, der der Trace-Vorgang ausgeführt, in der Anwendung DEA wird benötigen Sysadmin-Rechte auf dem Computer, auf denen SQL Server ausgeführt wird.
- Das Dienstkonto auf dem Computer mit SQL Server verwendet, benötigen Schreibzugriff auf den Dateipfad für die angegebene Ablaufverfolgung.

### <a name="can-i-capture-traces-for-the-entire-server-or-only-on-a-single-database"></a>Kann ich die ablaufverfolgungen für den gesamten Server oder nur für eine einzelne Datenbank erfassen?
    
Sie können die DEA verwenden, zum Erfassen von ablaufverfolgungen für alle Datenbanken auf dem Server oder für eine einzelne Datenbank.
    
### <a name="i-have-a-linked-server-configured-in-my-production-environment-do-those-queries-show-up-in-the-traces"></a>Ich habe einen Verbindungsserver in Meine produktionsumgebung konfiguriert. Werden diese Abfragen in den ablaufverfolgungen angezeigt?
    
Wenn Sie eine Ablaufverfolgung Erfassung für den gesamten Server ausführen, erfasst die Ablaufverfolgung alle Abfragen, einschließlich der Abfragen für Verbindungsserver. Um eine Ablaufverfolgung Erfassung für den gesamten Server auszuführen, lassen Sie die **Datenbanknamen** Feld **New Capture** leer.
    
### <a name="whats-the-minimum-recommended-time-for-production-workload-traces"></a>Was ist die empfohlene minimale Zeit für die Produktion Workload ablaufverfolgungen?
    
Es wird empfohlen, dass Sie eine Uhrzeit auszuwählen, die während des gesamten Entwicklungsprozesses Ihrer Workload am besten darstellt. Auf diese Weise wird die Analyse auf alle Abfragen in Ihrer Workload ausgeführt.
    
### <a name="how-important-is-to-take-a-database-backup-right-before-i-start-a-trace-capture"></a>Wie wichtig ist, eine Datenbank richtige Sicherung vor dem Starten einer Ablaufverfolgung Erfassung?
    
Bevor Sie eine Ablaufverfolgung Erfassung beginnen, stellen Sie sicher, dass Sie alle Ihre Zieldatenbanken sichern. Die aufgezeichnete Ablaufverfolgung in das Ziel 1 und 2 für Ziel wird wiedergegeben. Wenn der Datenbankstatus nicht identisch ist, werden die Ergebnisse der Experimente verzerrt.

### <a name="can-i-collect-xevents-instead-of-traces-and-can-i-replay-xevents"></a>Kann ich anstelle von ablaufverfolgungen XEvents sammeln, und können XEvents wiedergeben?
    
Ja. DEA unterstützt XEvents. Herunterladen der neuesten Version DEA, und versuchen Sie es.

## <a name="troubleshoot-trace-captures"></a>Problembehandlung bei der Ablaufverfolgung erfasst

Wenn Sie eine Fehlermeldung, beim Ausführen einer Ablaufverfolgung erfassen angezeigt, überprüfen Sie die folgenden Voraussetzungen:

- Vergewissern Sie sich, dass der Name der SQL Server-Computers gültig ist. Versuchen Sie es zur Verbindung mit SQL Server-Computers mit SQL Server Management Studio (SSMS), um zu bestätigen.
- Vergewissern Sie sich, dass es sich bei Ihrer Konfiguration der Firewall Verbindungen mit dem Computer mit SQL Server nicht blockiert.
- Vergewissern Sie sich, dass der Benutzer die Berechtigungen, die in dem Blogbeitrag aufgelisteten [Replay – häufig gestellte Fragen](https://blogs.msdn.microsoft.com/datamigration/2017/03/24/dea-2-0-replay-faq/).
- Bestätigen Sie, dass der Name der Ablaufverfolgung nicht die standard-Rollover-Konvention folgt (erfassen\_1). Versuchen Sie stattdessen die Ablaufverfolgung-Namen wie die Erfassung\_1A oder Capture1.

Es folgen einige mögliche Fehler, die unter Umständen und Lösungen zur Fehlerbehebung:

|Mögliche Fehler|Lösung|  
|---|---|  
|Kann nicht gestartet werden die Ablaufverfolgung auf dem Ziel-SQL Server, überprüfen Sie, ob Sie die erforderlichen Berechtigungen verfügen und, dass der SQL Server-Dienstkonto über Schreibzugriff auf den Dateipfad für die angegebene Ablaufverfolgung (53) für Sql-Fehlercode verfügt|Der Benutzer, die Ausführung des Tools DEA benötigen Zugriff auf den Computer, auf denen SQL Server ausgeführt wird. Der Benutzer muss die Sysadmin-Rolle zugewiesen werden.|  
|Kann nicht gestartet werden die Ablaufverfolgung auf dem Ziel-SQL Server, überprüfen Sie, ob Sie die erforderlichen Berechtigungen verfügen und, dass der SQL Server-Dienstkonto über Schreibzugriff auf den Dateipfad für die angegebene Ablaufverfolgung (19062) für Sql-Fehlercode verfügt|Bei der Ablaufverfolgung Pfadangabe möglicherweise nicht vorhanden, oder der Ordner verfügt nicht über Schreibberechtigungen für das Konto, unter denen die SQL, das Server-Dienste (z. B. NETWORK SERVICE) ausgeführt werden. Der Pfad muss vorhanden sein und muss die erforderlichen Berechtigungen für die Ablaufverfolgung zu starten.|  
|Eine Ablaufverfolgung DEA wird derzeit auf dem Zielserver ausgeführt.|Eine aktive Ablaufverfolgung wird bereits auf dem Zielserver ausgeführt. Eine neue Ablaufverfolgung kann nicht gestartet werden, wenn eine Ablaufverfolgung für den serverweiten bereits ausgeführt wird.|  
|Die angeforderte Datenbank für die Erfassung von Ablaufverfolgung kann nicht geöffnet werden. Dieser Fehler kann durch einen Namen für die falsche Datenbank verursacht werden.|Die angegebene Datenbank ist nicht vorhanden oder ist nicht verfügbar. für den aktuellen Benutzer. Verwenden Sie den richtigen Datenbanknamen an.|  

Wenn Sie sehen, dass alle anderen Fehler, die mit der Bezeichnung *Sql-Fehlercode*, finden Sie unter [Systemfehlermeldungen](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/cc645603(v=sql.105)) ausführliche Beschreibungen und Lösungen.
    
## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu den Distributed Replay-Tools in SQL Server konfigurieren, bevor Sie eine aufgezeichnete Ablaufverfolgung wiedergeben, finden Sie unter [konfigurieren Replay](database-experimentation-assistant-configure-replay.md).

- Für einen 19-minütige Einführung in DEA und Demonstrationen im folgenden Video:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
