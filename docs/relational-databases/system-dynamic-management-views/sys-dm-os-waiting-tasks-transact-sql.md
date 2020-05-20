---
title: sys. dm_os_waiting_tasks (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_waiting_tasks
- sys.dm_os_waiting_tasks_TSQL
- dm_os_waiting_tasks_TSQL
- sys.dm_os_waiting_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_waiting_tasks dynamic management view
ms.assetid: ca5e6844-368c-42e2-b187-6e5f5afc8df3
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f0efa4a5b5c8144807c27014a96b3fa90ed77971
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82811752"
---
# <a name="sysdm_os_waiting_tasks-transact-sql"></a>sys.dm_os_waiting_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt Informationen zur Warteschlange von Tasks zurück, die auf eine Ressource warten. Weitere Informationen zu Aufgaben finden Sie im [Handbuch zur Thread-und Task Architektur](../../relational-databases/thread-and-task-architecture-guide.md).
   
> [!NOTE]  
>  Um dies von oder aus aufzurufen [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , verwenden Sie den Namen **sys. dm_pdw_nodes_os_waiting_tasks**.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**waiting_task_address**|**varbinary(8)**|Adresse des wartenden Tasks.|  
|**session_id**|**smallint**|ID der Sitzung, die dem Task zugeordnet ist.|  
|**exec_context_id**|**int**|ID des Ausführungskontexts, der dem Task zugeordnet ist.|  
|**wait_duration_ms**|**bigint**|Gesamtwartezeit für diesen Wartetyp (in Millisekunden). Diese Zeit ist **signal_wait_time**.|  
|**wait_type**|**nvarchar(60)**|Der Name des Wartetyps.|  
|**resource_address**|**varbinary(8)**|Adresse der Ressource, auf die der Task wartet.|  
|**blocking_task_address**|**varbinary(8)**|Task, der derzeit diese Ressource verwendet.|  
|**blocking_session_id**|**smallint**|ID der Sitzung, die die Anforderung blockiert. Wenn diese Spalte den Wert NULL aufweist, wird die Anforderung nicht blockiert, oder die Sitzungsinformationen der blockierenden Sitzung sind nicht verfügbar (bzw. können nicht identifiziert werden).<br /><br /> -2 = Der Besitzer der blockierenden Ressource ist eine verwaiste verteilte Transaktion.<br /><br /> -3 = Der Besitzer der blockierenden Ressource ist eine verzögerte Wiederherstellungstransaktion.<br /><br /> -4 = Die Sitzungs-ID des Besitzers des blockierenden Latches konnte aufgrund interner Latchstatusübergänge nicht bestimmt werden.|  
|**blocking_exec_context_id**|**int**|ID des Ausführungskontexts des blockierenden Tasks.|  
|**resource_description**|**nvarchar (3072)**|Beschreibung der verwendeten Ressource. Weitere Informationen finden Sie in der unten stehenden Liste.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ,[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="resource_description-column"></a>resource_description-Spalte  
 Für die resource_description-Spalte sind folgende Werte möglich.  
  
 **Ressourcenbesitzer des Threadpools:**  
  
-   Thread Pool-ID = "Scheduler \< Hex-Address>"  
  
 **Ressourcenbesitzer der parallelen Abfrage:**  
  
-   exchangeevent-ID = {Port | Pipe} \< Hex-Address> waittype = \< Exchange-Wait-Type> NodeId = \< Exchange-Node-ID>  
  
 **Exchange-wait-type:**  
  
-   e_waitNone  
  
-   e_waitPipeNewRow  
  
-   e_waitPipeGetRow  
  
-   e_waitSynchronizeConsumerOpen  
  
-   e_waitPortOpen  
  
-   e_waitPortClose  
  
-   e_waitRange  
  
 **Besitzer der LOCK-Ressource:**  
  
-   \<type-specific-Description> ID = Lock Lock \< -Hex-Address> Mode = \< Mode> AssociatedObjectId = zugeordnete \< -obj-ID>  
  
     **\<Typspezifischer Beschreibung> können folgende sein:**  
  
    -   Für Datenbank: databaselock subresource = \< databaselock-subresource> DBID = \< DB-ID>  
  
    -   Für file: FILELOCK fileid = \< File-ID> subresource = \< FILELOCK-subresource> DBID = \< DB-ID>  
  
    -   Für Objekt: objectlock lockpartition = \< Lock-Partition-ID> objID = \< obj-ID> subresource = \< objectlock-subresource> DBID = \< DB-ID>  
  
    -   Für page: PAGELOCK fleid = \< File-ID> pageID = \< Page-ID> DBID = \< DB-ID> subresource = \< PAGELOCK-subresource>  
  
    -   Für Key: Keylock Hobtid = \< HoBt-ID> DBID = \< DB-ID>  
  
    -   Für Block: extentlock fleid = \< File-ID> pageID = \< Page-ID> DBID = \< DB-ID>  
  
    -   Für RID: ridlock fleid = \< File-ID> pageID = \< Page-ID> DBID = \< DB-ID>  
  
    -   Für Application: applicationlock Hash = \< Hash> databaseprincipalid = \< Role-ID> DBID = \< DB-ID>  
  
    -   Für Metadaten: metadatalock subresource = \< Metadata-subresource> ClassID = \< metadatalock-Description> DBID = \< DB-ID>  
  
    -   Für HoBT: hobtlock Hobtid = \< HoBt-ID> subresource = \< HoBT-subresource> DBID = \< DB-ID>  
  
    -   Für ALLOCATION_UNIT: Zuordnungseinheits Sperr \< -ID = HoBt-ID> subresource = \< Zuordnungseinheits-subresource> DBID = \< DB-ID>  
  
     **\<der Modus> kann sein:**  
  
     Sch-S, Sch-M, S, U, X, IS, IU, IX, SIU, SIX, UIX, BU, RangeS-S, RangeS-U, RangeI-N, RangeI-S, RangeI-U, RangeI-X, RangeX-, RangeX-U, RangeX-X  
  
 **Besitzer der externen Ressource:**  
  
-   Externer ExternalResource = \< Wait-Type>  
  
 **Besitzer der allgemeinen Ressource:**  
  
-   Transaktionmutex transaktioninfo Workspace = \< Workspace-ID>  
  
-   Mutex  
  
-   CLRTaskJoin  
  
-   CLRMonitorEvent  
  
-   CLRRWLockEvent  
  
-   resourceWait  
  
 **Besitzer der Latchressource:**  
  
-   \<DB-ID->: \< Datei-ID->: \< Seite-in-file->  
  
-   \<GUID->  
  
-   \<Latch-Class> ( \< Latch-Address>)  
  
## <a name="permissions"></a>Berechtigungen

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ist die- `VIEW SERVER STATE` Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die- `VIEW DATABASE STATE` Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   
 
## <a name="example"></a>Beispiel
In diesem Beispiel werden blockierte Sitzungen identifiziert. Führen Sie die [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfrage in aus [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .

```sql
SELECT * FROM sys.dm_os_waiting_tasks 
WHERE blocking_session_id IS NOT NULL; 
``` 
  
## <a name="see-also"></a>Weitere Informationen  
[SQL Server dynamischen Verwaltungs Sichten im Zusammenhang mit dem Betriebs System &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)      
[Handbuch zur Thread- und Taskarchitektur](../../relational-databases/thread-and-task-architecture-guide.md)     
   
 
