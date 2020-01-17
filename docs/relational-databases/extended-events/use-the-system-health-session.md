---
title: Verwenden der system_health-Sitzung
ms.date: 11/27/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: tutorial
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ab31461888588ee54f1715f5e98ddb0f3b9aa23b
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246144"
---
# <a name="use-the-system_health-session"></a>Verwenden der system_health-Sitzung

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Bei der system_health-Sitzung handelt es sich um eine standardmäßig in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]enthaltene Sitzung für erweiterte Ereignisse. Diese Sitzung wird automatisch beim Start von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] gestartet und ohne merkliche Auswirkungen auf die Leistung ausgeführt. In der Sitzung werden Systemdaten erfasst, mit deren Hilfe Sie Leistungsprobleme in [!INCLUDE[ssDE](../../includes/ssde-md.md)]beheben können. 

> [!IMPORTANT]
> Es wird empfohlen, die Systemintegritätssitzung (system_health) nicht zu beenden, zu ändern oder zu löschen. Alle Änderungen, die an der system_health-Sitzung vorgenommen werden, können durch ein zukünftiges Produktupdate überschrieben werden.
  
In der Sitzung werden u. a. folgende Informationen erfasst:  
  
-   *sql_text* und *session_id* aller Sitzungen, in denen ein Fehler mit einem Schweregrad >= 20 aufgetreten ist.  
  
-   *sql_text* und *session_id* aller Sitzungen, in denen ein arbeitsspeicherbezogener Fehler aufgetreten ist. Zu diesen Fehlern zählen 17803, 701, 802, 8645, 8651, 8657 und 8902.  
  
-   Aufzeichnungen zu allen nicht gelösten Zeitplanungsproblemen. Diese werden im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll als Fehler 17883 angezeigt.  
  
-   Alle Deadlocks, die erkannt werden, einschließlich des Deadlockdiagramms.  
  
-   *callstack*, *sql_text* und *session_id* aller Sitzungen, die mehr als 15 Sekunden lang auf Latches (oder andere relevante Ressourcen) gewartet haben.  
  
-   *callstack*, *sql_text* und *session_id* aller Sitzungen, die mehr als 30 Sekunden lang auf Sperren gewartet haben.  
  
-   *callstack*, *sql_text* und *session_id* aller Sitzungen, die lange auf präemptive Wartevorgänge gewartet haben. Die Dauer schwankt je nach Wartetyp. Bei einem präemptiven Wartevorgang wartet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf externe API-Aufrufe.  
  
-   *callstack* und *session_id* für Fehler bei der CLR-Belegung und virtuellen Belegung.  
  
-   Die Ringpufferereignisse für den Speicherbroker, die Zeitplanungsmodul-Überwachung, Speicherknoten-OOMs sowie Sicherheit und Konnektivität.  
  
-   Die Systemkomponente ergibt sich aus `sp_server_diagnostics`.  
  
-   Mit *scheduler_monitor_system_health_ring_buffer_recorded* erfasste Integrität der Instanz.  
  
-   CLR-Belegungsfehler.  
  
-   Konnektivitätsfehler mit *connectivity_ring_buffer_recorded*.  
  
-   Sicherheitsfehler mit *security_error_ring_buffer_recorded*.  

> [!NOTE]
> Weitere Informationen zu Deadlocks finden Sie unter dem Stichwort [„Deadlocks“ im Handbuch zu Transaktionssperren und Zeilenversionsverwaltung](../../relational-databases/sql-server-transaction-locking-and-row-versioning-guide.md#deadlocks).   
> Weitere Informationen zu SQL-Fehlermeldungen finden Sie unter [Datenbankenginefehler](../../relational-databases/errors-events/database-engine-events-and-errors.md).

## <a name="viewing-the-session-data"></a>Anzeigen der Sitzungsdaten  
In der Sitzung werden die Daten im Ringpufferziel und Ereignisdateiziel gespeichert. Das Ereignisdateiziel ist mit einer maximalen Größe von 5 MB und einer Richtlinie für die Aufbewahrung von 4 Dateien konfiguriert. 

Um die Sitzungsdaten aus dem Ringpufferziel mit der in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verfügbaren Benutzeroberfläche für erweiterte Ereignisse anzuzeigen, lesen Sie [Erweiterte Ansicht von Zieldaten aus erweiterten Ereignissen in SQL Server: Beobachten von Livedaten](../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md#b3-watch-live-data).

Zum Anzeigen der Sitzungsdaten aus dem Ringpufferziel mit [!INCLUDE[tsql](../../includes/tsql-md.md)] verwenden Sie die folgende Abfrage:  
  
```sql  
SELECT CAST(xet.target_data as xml) 
FROM sys.dm_xe_session_targets xet  
JOIN sys.dm_xe_sessions xe ON (xe.address = xet.event_session_address)  
WHERE xe.name = 'system_health'  
```  
  
Um die Sitzungsdaten aus der Ereignisdatei anzuzeigen, verwenden Sie die in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verfügbare Benutzeroberfläche für erweiterte Ereignisse. Weitere Informationen finden Sie unter [Erweiterte Ansicht von Zieldaten aus erweiterten Ereignissen in SQL Server](../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md).
  
## <a name="restoring-the-system_health-session"></a>Wiederherstellen der system_health-Sitzung  
Wenn Sie die system_health-Sitzung gelöscht haben, können Sie diese wiederherstellen, indem Sie die Datei **u_tables.sql** im Abfrage-Editor ausführen. Diese Datei befindet sich im folgenden Ordner, wobei **C:** dem Laufwerk entspricht, auf dem Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Programmdateien installiert haben, und **MSSQL1x** ist die Hauptversion von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
 `C:\Program Files\Microsoft SQL Server\MSSQL1x.\<*instanceid*>\MSSQL\Install`  
  
Wenn Sie die Sitzung wiederhergestellt haben, müssen Sie die Sitzung mit der `ALTER EVENT SESSION`-Anweisung oder über den Knoten **Erweiterte Ereignisse** im Objekt-Explorer starten. Andernfalls wird die Sitzung beim nächsten Neustart des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Diensts automatisch gestartet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Ereignisse](../../relational-databases/extended-events/extended-events.md)    
 [Tools für erweiterte Ereignisse](../../relational-databases/extended-events/extended-events-tools.md)    
 [Fehler der Datenbank-Engine](../../relational-databases/errors-events/database-engine-events-and-errors.md)    
 [Meldungskatalogsichten (für Fehlermeldungen): sys.messages](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md) 
