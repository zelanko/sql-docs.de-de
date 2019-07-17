---
title: Sys. dm_db_session_space_usage (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/16/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_session_space_usage_TSQL
- dm_db_session_space_usage
- sys.dm_db_session_space_usage
- sys.dm_db_session_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_session_space_usage dynamic management view
ms.assetid: a67a6045-8e14-460a-9fe3-912b846c08c1
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5e4febf0882f57f7d1545f86cbe4c65e322226dc
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68263973"
---
# <a name="sysdmdbsessionspaceusage-transact-sql"></a>sys.dm_db_session_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt die Anzahl der Seiten zurück, die von jeder Sitzung für die Datenbank zugeordnet werden bzw. deren Zuordnung aufgehoben wird.  
  
> [!NOTE]  
>  Diese Sicht gilt nur für die [Tempdb-Datenbank](../../relational-databases/databases/tempdb-database.md).  
  
> [!NOTE]  
>  Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_db_session_space_usage**.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|Sitzungs-ID.<br /><br /> **Sitzungs-ID** ordnet **Session_id** in [Sys. dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md).|  
|**database_id**|**smallint**|Datenbank-ID|  
|**user_objects_alloc_page_count**|**bigint**|Anzahl der Seiten, die für Benutzerobjekte von dieser Sitzung reserviert oder zugeordnet wurden.|  
|**user_objects_dealloc_page_count**|**bigint**|Anzahl der Seiten, deren Zuordnung für Benutzerobjekte von dieser Sitzung aufgehoben wurde bzw. die nicht mehr reserviert sind.|  
|**internal_objects_alloc_page_count**|**bigint**|Anzahl der Seiten, die für interne Objekte von dieser Sitzung reserviert oder zugeordnet wurden.|  
|**internal_objects_dealloc_page_count**|**bigint**|Anzahl der Seiten, deren Zuordnung für interne Objekte von dieser Sitzung aufgehoben wurde bzw. die nicht mehr reserviert sind.|  
|**user_objects_deferred_dealloc_page_count**|**bigint**|Anzahl der Seiten, die für die verzögerte zuordnungsaufhebung markiert wurden.<br /><br /> **Hinweis**: Eingeführt in Servicepacks für [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarife, erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank. Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard und Basic-Version, erfordert die **Serveradministrator** oder **Azure Active Directory-Administrator** Konto.   

## <a name="remarks"></a>Hinweise  
 IAM-Seiten sind in den in dieser Sicht aufgeführten Zählungen der Zuordnung und Aufhebung der Zuordnung nicht enthalten.  
  
 Die Seitenindikatoren werden mit Null (0) zu Beginn einer Sitzung initialisiert. Mit den Indikatoren wird die Gesamtanzahl der Seiten nachverfolgt, die für bereits in dieser Sitzung abgeschlossene Tasks zugeordnet waren bzw. deren Zuordnung aufgehoben wurde. Die Indikatoren werden nur nach Beendigung eines Tasks aktualisiert. Tasks, die zurzeit ausgeführt werden, sind nicht enthalten.  
  
 Für eine Sitzung können mehrere Anforderungen gleichzeitig aktiv sein. Von einer Anforderung können mehrere Threads oder Tasks gestartet werden, wenn es sich um eine parallele Abfrage handelt.  
  
 Weitere Informationen zu Sitzungen, Anforderungen und Aufgaben finden Sie unter [Sys. dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md), [Sys. dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md), und [Sys. dm_os_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md).  
  
## <a name="user-objects"></a>Benutzerobjekte  
 Die folgenden Objekte sind in den Seitenzählern für Benutzerobjekte enthalten:  
  
-   Benutzerdefinierte Tabellen und Indizes  
  
-   Systemtabellen und -indizes  
  
-   Globale temporäre Tabellen und Indizes  
  
-   Lokale temporäre Tabellen und Indizes  
  
-   Tabellenvariablen  
  
-   In Tabellenwertfunktionen zurückgegebene Tabellen  
  
## <a name="internal-objects"></a>Interne Objekte  
 Interne Objekte gibt es nur in **Tempdb**. Die folgenden Objekte sind in den Seitenzählern für interne Objekte enthalten:  
  
-   Arbeitstabellen für Cursor- oder Spoolvorgänge und temporären LOB-Speicher (Large Object)  
  
-   Arbeitsdateien für Vorgänge wie z. B. Hashjoins  
  
-   Sortierläufe  
  
## <a name="physical-joins"></a>Physische Joins  
 ![Physische Joins für Sys. dm_db_session_space_usage](../../relational-databases/system-dynamic-management-views/media/join-dm-db-session-space-usage-1.gif "physische joins für Sys. dm_db_session_space_usage")  
  
## <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|Beschreibung|Beziehung|  
|----------|--------|------------------|  
|dm_db_session_space_usage.session_id|dm_exec_sessions.session_id|1:1|  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_os_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys.dm_db_task_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
 [sys.dm_db_file_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)  
  
  



