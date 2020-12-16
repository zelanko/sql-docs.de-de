---
title: Suchen nach Objekten mit den meisten Sperren mithilfe von erweiterten Ereignissen
description: In diesem Artikel wird die Suche nach Objekten mit den meisten Sperren veranschaulicht. Datenbankadministratoren müssen möglicherweise die Objekte mit den meisten Sperren ermitteln, um die Leistung der Datenbank zu verbessern.
ms.date: 10/18/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: tutorial
helpviewer_keywords:
- objects [SQL Server], extended events
- xe
- extended events [SQL Server], locks
- objects [SQL Server], locks
ms.assetid: fcbadbda-c91c-43f0-a1b5-601e40110e07
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 522017d6ced6039cd7e5b9a30cf60404eee9249a
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97465501"
---
# <a name="find-the-objects-that-have-the-most-locks-taken-on-them"></a>Suchen der Objekte, die über die meisten Sperren verfügen

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Datenbankadministratoren müssen oft die Quelle von Sperren identifizieren, die die Datenbankleistung beeinträchtigen.  
  
Sie überwachen z. B. den Produktionsserver auf alle möglichen Engpässe. Sie erwarten einen starken Wettbewerb um die Ressourcen und würden daher gern ermitteln, wie viele Sperren für diese Objekte gelten. Nachdem die am häufigsten gesperrten Objekte ermittelt sind, können Sie Schritte zur Optimierung des Zugangs auf die im Wettbewerb befindlichen Objekte ergreifen.  
  
Verwenden Sie hierzu den Abfrage-Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
### <a name="to-find-the-objects-that-have-the-most-locks"></a>So suchen Sie die Objekte, die über die meisten Sperren verfügen  
  
1. Führen Sie im Abfrage-Editor die folgenden Anweisungen aus.

    ```sql
    -- Find objects in a particular database that have the most
    -- lock acquired. This sample uses AdventureWorksDW2012.
    -- Create the session and add an event and target.
    
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='LockCounts')
        DROP EVENT session LockCounts ON SERVER;
    GO
    DECLARE @dbid int;
  
    SELECT @dbid = db_id('AdventureWorksDW2012');
  
    DECLARE @sql nvarchar(1024);
    SET @sql = '
        CREATE event session LockCounts ON SERVER
            ADD EVENT sqlserver.lock_acquired (WHERE database_id ='
                + CAST(@dbid AS nvarchar) +')
            ADD TARGET package0.histogram(
                SET filtering_event_name=''sqlserver.lock_acquired'',
                    source_type=0, source=''resource_0'')';
  
    EXEC (@sql);
    GO
    ALTER EVENT session LockCounts ON SERVER
        STATE=start;
    GO
    -- Create a simple workload that takes locks.
    
    USE AdventureWorksDW2012;
    GO
    SELECT TOP 1 * FROM dbo.vAssocSeqLineItems;
    GO
    -- The histogram target output is available from the
    -- sys.dm_xe_session_targets dynamic management view in
    -- XML format.
    -- The following query joins the bucketizing target output with
    -- sys.objects to obtain the object names.
    
    SELECT name, object_id, lock_count
        FROM
        (
        SELECT objstats.value('.','bigint') AS lobject_id,
            objstats.value('@count', 'bigint') AS lock_count
            FROM (
                SELECT CAST(xest.target_data AS XML)
                    LockData
                FROM     sys.dm_xe_session_targets xest
                    JOIN sys.dm_xe_sessions        xes  ON xes.address = xest.event_session_address
                    JOIN sys.server_event_sessions ses  ON xes.name    = ses.name
                WHERE xest.target_name = 'histogram' AND xes.name = 'LockCounts'
                 ) Locks
            CROSS APPLY LockData.nodes('//HistogramTarget/Slot') AS T(objstats)
        ) LockedObjects
        INNER JOIN sys.objects o  ON LockedObjects.lobject_id = o.object_id
        WHERE o.type != 'S' AND o.type = 'U'
        ORDER BY lock_count desc;
    GO
    
    -- Stop the event session.
    
    ALTER EVENT SESSION LockCounts ON SERVER
        state=stop;
    GO
    ```

> [!NOTE]
> Das vorangehende Transact-SQL-Codebeispiel wird lokal auf SQL Server ausgeführt, kann jedoch auf _Azure SQL-Datenbank nicht ordnungsgemäß ausgeführt werden._ Die Kernteile des Beispiels, die direkt Ereignisse wie `ADD EVENT sqlserver.lock_acquired` einbeziehen, funktionieren ebenfalls auf Azure SQL-Datenbank. Vorläufige Elemente wie `sys.server_event_sessions` müssen jedoch für die Azure SQL-Datenbank-Pendats wie `sys.database_event_sessions` angepasst werden, damit das Beispiel ausgeführt werden kann.
> Weitere Informationen zu diesen kleinen Unterschieden zwischen einer lokalen SQL Server-Instanz und Azure SQL-Datenbank finden Sie in den folgenden Artikeln:
> - [Erweiterte Ereignisse in Azure SQL-Datenbank](/azure/sql-database/sql-database-xevent-db-diff-from-svr#transact-sql-differences)
> - [Systemobjekte, die erweiterte Ereignisse unterstützen](xevents-references-system-objects.md)

Nach Abschluss der Anweisungen im vorangehenden Transact-SQL-Skript werden auf der Registerkarte **Ergebnisse** des Abfrage-Editors die folgenden Spalten angezeigt:
  
- name
- object_id
- lock_count
  
## <a name="see-also"></a>Weitere Informationen

[CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md)  
[ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)  
[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql.md)  
[sys.dm_xe_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql.md)  
[sys.server_event_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)  
