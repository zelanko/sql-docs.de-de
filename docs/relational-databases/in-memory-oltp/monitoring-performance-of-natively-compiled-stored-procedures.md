---
title: Überwachen der Leistung von systemintern kompilierten gespeicherten Prozeduren
ms.custom: seo-dt-2019
ms.date: 04/03/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 55548cb2-77a8-4953-8b5a-f2778a4f13cf
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b1970c5953373c500f85e82281a69be1d46f1be0
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "78180061"
---
# <a name="monitoring-performance-of-natively-compiled-stored-procedures"></a>Überwachen der Leistung von systemintern kompilierten gespeicherten Prozeduren

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In diesem Artikel wird erläutert, wie Sie die Leistung von nativ kompilierten gespeicherten Prozeduren und anderen nativ kompilierten T-SQL-Modulen überwachen können.  
  
## <a name="using-extended-events"></a>Unter Verwendung erweiterter Ereignisse  
 Verwenden Sie das erweiterte Ereignis **sp_statement_completed** , um die Ausführung einer Abfrage zu verfolgen. Erstellen Sie eine Sitzung für erweiterte Ereignisse mit diesem Ereignis. Optional können Sie für eine bestimmte nativ kompilierte gespeicherte Prozedur nach object_id filtern. Das erweiterte Ereignis wird nach der Ausführung jeder Abfrage ausgelöst. Die vom erweiterten Ereignis angegebene CPU-Zeit und Dauer geben an, wie lange die CPU genutzt und wie lange die Abfrage ausgeführt wurde. Bei einer systemintern kompilierten gespeicherten Prozedur, die viel CPU-Zeit beansprucht, treten u. U. Leistungsprobleme auf.  
  
 Neben**line_number**kann auch **object_id** im erweiterten Ereignis verwendet werden, um die Abfrage zu untersuchen. Mithilfe der folgenden Abfrage kann die Prozedurdefinition abgerufen werden. Anhand der Zeilennummer wird die Abfrage innerhalb der Definition identifiziert:  
  
```sql  
SELECT [definition]
    from sys.sql_modules
    where object_id=object_id;
```  
  
  
## <a name="using-data-management-views-and-query-store"></a>Verwenden von Datenverwaltungsansichten und Abfragespeicher
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssSDS](../../includes/sssds-md.md)] unterstützen Ausführungsstatistiken für nativ kompilierte gespeicherte Prozeduren sowohl auf Prozedur- als auch auf Abfrageebene. Das Sammeln statistischer Ausführungsdaten ist aufgrund der Leistungsauswirkungen standardmäßig nicht aktiviert.  

Ausführungsstatistiken werden in den Systemansichten [sys.dm_exec_procedure_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md) und [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md) sowie im [Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md) wiedergegeben.

## <a name="procedure-level-execution-statistics"></a>Ausführungsstatistiken auf Prozedurebene

**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** : Aktivieren oder Deaktivieren der Sammlung von Statistiken auf nativ kompilierten gespeicherten Prozeduren auf Prozedurebene mithilfe von [sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md).  Die folgende Anweisung aktiviert die Sammlung von Ausführungsstatistiken auf Prozedurebene für alle nativ kompilierten T-SQL-Module auf der aktuellen Instanz:
```sql
EXEC sys.sp_xtp_control_proc_exec_stats 1
```

**[!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]** : Aktivieren oder Deaktivieren der Sammlung von Statistiken auf nativ kompilieren gespeicherten Prozeduren auf Prozedurebene mithilfe der [datenbankweit gültigen Konfigurationsoption](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)`XTP_PROCEDURE_EXECUTION_STATISTICS`. Die folgende Anweisung aktiviert die Sammlung von Ausführungsstatistiken auf Prozedurebene für alle nativ kompilierten T-SQL-Module auf der aktuellen Datenbank:
```sql
ALTER DATABASE
    SCOPED CONFIGURATION
    SET XTP_PROCEDURE_EXECUTION_STATISTICS = ON;
```

## <a name="query-level-execution-statistics"></a>Ausführungsstatistiken auf Abfrageebene

**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** : Aktivieren oder Deaktivieren der Sammlung von Statistiken auf nativ kompilierten gespeicherten Prozeduren auf Abfrageebene mithilfe von [sys.sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md).  Die folgende Anweisung aktiviert die Sammlung von Ausführungsstatistiken auf Abfrageebene für alle nativ kompilierten T-SQL-Module auf der aktuellen Instanz:
```sql
EXEC sys.sp_xtp_control_query_exec_stats 1
```

**[!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]** : Aktivieren oder Deaktivieren der Sammlung von Statistiken auf nativ kompilieren gespeicherten Prozeduren auf Anweisungsebene mithilfe der [datenbankweit gültigen Konfigurationsoption](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)`XTP_QUERY_EXECUTION_STATISTICS`. Die folgende Anweisung aktiviert die Sammlung von Ausführungsstatistiken auf Abfrageebene für alle nativ kompilierten T-SQL-Module auf der aktuellen Datenbank:
```sql
ALTER DATABASE
    SCOPED CONFIGURATION
    SET XTP_QUERY_EXECUTION_STATISTICS = ON;
```

## <a name="sample-queries"></a>Beispielabfragen

 Nachdem die Statistiksammlung abgeschlossen wurde, können die Ausführungsstatistiken zu nativ kompilierten gespeicherten Prozeduren mit [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md) für eine Prozedur und für Abfragen mit [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md) abgefragt werden.  
 
  
 Mit der folgenden Abfrage werden nach der Statistiksammlung die Prozedurnamen und Ausführungsstatistiken für systemintern kompilierte gespeicherte Prozeduren in der aktuellen Datenbank zurückgegeben:  

```sql
SELECT
        object_id,
        object_name(object_id) as 'object name',
        cached_time,
        last_execution_time,  execution_count,
        total_worker_time,    last_worker_time,
        min_worker_time,      max_worker_time,
        total_elapsed_time,   last_elapsed_time,
        min_elapsed_time,     max_elapsed_time
    from
        sys.dm_exec_procedure_stats
    where
        database_id = db_id()
        and
        object_id in
            (
            SELECT object_id
                from sys.sql_modules
                where uses_native_compilation=1
            )
    order by
        total_worker_time desc;
```

Mit der folgenden Abfrage werden der Abfragetext und Ausführungsstatistiken für alle Abfragen in systemintern kompilierten gespeicherten Prozeduren der aktuellen Datenbank zurückgegeben, für die statistische Daten gesammelt wurden. Die Ergebnisse sind nach total_worker_time in absteigender Reihenfolge sortiert:  

```sql
SELECT
        st.objectid,
        object_name(st.objectid) as 'object name',
        SUBSTRING(
            st.text,
            (qs.statement_start_offset/2) + 1,
            ((qs.statement_end_offset-qs.statement_start_offset)/2) + 1
            ) as 'query text',
        qs.creation_time,
        qs.last_execution_time,   qs.execution_count,
        qs.total_worker_time,     qs.last_worker_time,
        qs.min_worker_time,       qs.max_worker_time,
        qs.total_elapsed_time,    qs.last_elapsed_time,
        qs.min_elapsed_time,      qs.max_elapsed_time
    FROM
                    sys.dm_exec_query_stats qs
        cross apply sys.dm_exec_sql_text(sql_handle) st
    WHERE
        st.dbid = db_id()
        and
        st.objectid in
            (SELECT object_id
                from sys.sql_modules
                where uses_native_compilation=1
            )
    ORDER BY
        qs.total_worker_time desc;
```

## <a name="query-execution-plans"></a>Abfragen von Ausführungsplänen

 Systemintern kompilierte gespeicherte Prozeduren unterstützen SHOWPLAN_XML (geschätzter Ausführungsplan). Der geschätzte Ausführungsplan kann verwendet werden, um den Abfrageplan auf Planungsfehler zu überprüfen. Häufige Gründe für fehlerhafte Pläne sind:  
  
-   Statistiken wurden vor der Erstellung der Prozedur nicht aktualisiert.  
  
-   Fehlende Indizes  
  
 Um Showplan XML abzurufen, führen Sie folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code aus:  
  
```sql  
SET SHOWPLAN_XML ON  
GO  
EXEC my_proc   
GO  
SET SHOWPLAN_XML OFF  
GO  
```  
  
 Alternativ können Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Prozedurnamen auswählen und auf **Geschätzten Ausführungsplan anzeigen**klicken.  
  
 Im geschätzten Ausführungsplan für systemintern kompilierte gespeicherte Prozeduren werden die Abfrageoperatoren und Ausdrücke für die Abfragen der Prozedur angezeigt. [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] unterstützt nicht alle SHOWPLAN_XML-Attribute für systemintern kompilierte gespeicherte Prozeduren. Attribute in Zusammenhang mit Kostenberechnungen des Abfrageoptimierers sind nicht Teil der SHOWPLAN_XML für die Prozedur.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Nativ kompilierte gespeicherte Prozeduren](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
