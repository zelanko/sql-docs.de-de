---
title: sys. DM _os_waiting_tasks (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c0a89a48fa960812ee955cd3b7ecb30069161f61
ms.sourcegitcommit: aece9f7db367098fcc0c508209ba243e05547fe1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72260382"
---
# <a name="sysdm_os_waiting_tasks-transact-sql"></a>sys.dm_os_waiting_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt Informationen zur Warteschlange von Tasks zurück, die auf eine Ressource warten. Weitere Informationen zu Aufgaben finden Sie im [Handbuch zur Thread-und Task Architektur](../../relational-databases/thread-and-task-architecture-guide.md).
   
> [!NOTE]  
>  Verwenden Sie den Namen **sys. DM _pdw_nodes_os_waiting_tasks**, um dies von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] aus aufzurufen.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**waiting_task_address**|**varbinary(8)**|Adresse des wartenden Tasks.|  
|**session_id**|**smallint**|ID der Sitzung, die dem Task zugeordnet ist.|  
|**exec_context_id**|**int**|ID des Ausführungskontexts, der dem Task zugeordnet ist.|  
|**wait_duration_ms**|**bigint**|Gesamtwartezeit für diesen Wartetyp (in Millisekunden). Dieses Mal ist **signal_wait_time**inbegriffen.|  
|**wait_type**|**nvarchar(60)**|Name des Wartetyps.|  
|**resource_address**|**varbinary(8)**|Adresse der Ressource, auf die der Task wartet.|  
|**blocking_task_address**|**varbinary(8)**|Task, der derzeit diese Ressource verwendet.|  
|**blocking_session_id**|**smallint**|ID der Sitzung, die die Anforderung blockiert. Wenn diese Spalte den Wert NULL aufweist, wird die Anforderung nicht blockiert, oder die Sitzungsinformationen der blockierenden Sitzung sind nicht verfügbar (bzw. können nicht identifiziert werden).<br /><br /> -2 = Der Besitzer der blockierenden Ressource ist eine verwaiste verteilte Transaktion.<br /><br /> -3 = Der Besitzer der blockierenden Ressource ist eine verzögerte Wiederherstellungstransaktion.<br /><br /> -4 = Die Sitzungs-ID des Besitzers des blockierenden Latches konnte aufgrund interner Latchstatusübergänge nicht bestimmt werden.|  
|**blocking_exec_context_id**|**int**|ID des Ausführungskontexts des blockierenden Tasks.|  
|**resource_description**|**nvarchar(3072)**|Beschreibung der verwendeten Ressource. Weitere Informationen finden Sie in der unten stehenden Liste.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="resource_description-column"></a>resource_description-Spalte  
 Die resource_description-Spalte verfügt über die folgenden möglichen Werte.  
  
 **Besitzer der Thread Pool Ressource:**  
  
-   threadpool id=scheduler\<hex-address>  
  
 **Besitzer der parallelen Abfrage Ressource:**  
  
-   exchangeevent-ID = {Port | Pipe} \<hex-Address > waittype = \<exchange-Wait-Type > NodeId = \<exchange-Node-ID >  
  
 **Exchange-Wait-Type:**  
  
-   e_waitNone  
  
-   e_waitPipeNewRow  
  
-   e_waitPipeGetRow  
  
-   e_waitSynchronizeConsumerOpen  
  
-   e_waitPortOpen  
  
-   e_waitPortClose  
  
-   e_waitRange  
  
 **Sperren des Ressourcen Besitzers:**  
  
-   \<type-Specific-Description > ID = Lock @ no__t-1lock-Hex-Address > Mode = \<mode > AssociatedObjectId = \<associated-obj-ID >  
  
     **\<type-Specific-Description > können folgende sein:**  
  
    -   Für Datenbank: databaselock subresource = \<databaselock-subresource > DBID = \<dB-ID >  
  
    -   Für file: FILELOCK fileid = \<file-ID > subresource = \<filelock-subresource > DBID = \<dB-ID >  
  
    -   Für Objekt: objectlock lockpartition = \<lock-Partition-ID > objID = \<obj-ID > subresource = \<objectlock-subresource > DBID = \<dB-ID >  
  
    -   Für page: PAGELOCK fleid = \<file-ID > pageID = \<page-ID > DBID = \<dB-ID > subresource = \<pagelock-subresource >  
  
    -   Für Key: Keylock Hobtid = \<hobt-ID > DBID = \<dB-ID >  
  
    -   Für Block: extentlock fleid = \<file-ID > pageID = \<page-ID > DBID = \<dB-ID >  
  
    -   Für RID: ridlock fleid = \<file-ID > pageID = \<page-ID > DBID = \<dB-ID >  
  
    -   Für Application: applicationlock Hash = \<hash > databaseprincipalid = \<role-ID > DBID = \<dB-ID >  
  
    -   Für Metadaten: metadatalock subresource = \<metadata-subresource > ClassID = \<metadatalock-Description > DBID = \<dB-ID >  
  
    -   Für HoBT: hobtlock Hobtid = \<hobt-ID > subresource = \<hobt-subresource > DBID = \<dB-ID >  
  
    -   Für ALLOCATION_UNIT: zuordcunitlock Hobtid = \<hobt-ID > subresource = \<zuordc-Unit-subresource > DBID = \<dB-ID >  
  
     **\<mode > können folgende sein:**  
  
     Sch-S, Sch-M, S, U, X, IS, IU, IX, SIU, SIX, UIX, BU, RangeS-S, RangeS-U, RangeI-N, RangeI-S, RangeI-U, RangeI-X, RangeX-, RangeX-U, RangeX-X  
  
 **Besitzer externer Ressourcen:**  
  
-   Externer ExternalResource = \<wait-Type >  
  
 **Besitzer der generischen Ressource:**  
  
-   Transaktionmutex transaktioninfo Workspace = \<workspace-ID >  
  
-   Mutex  
  
-   CLRTaskJoin  
  
-   CLRMonitorEvent  
  
-   CLRRWLockEvent  
  
-   resourceWait  
  
 **Latchressourcenbesitzer:**  
  
-   \<db-id>:\<file-id>:\<page-in-file>  
  
-   \<GUID>  
  
-   \<latch-Klasse > (\<latch-Address >)  
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ist `VIEW SERVER STATE`-Berechtigung erforderlich.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Ebenen ist die `VIEW DATABASE STATE`-Berechtigung in der Datenbank erforderlich. Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]-Tarifen (Standard und Basic) ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   
 
## <a name="example"></a>Beispiel
In diesem Beispiel werden blockierte Sitzungen identifiziert. Führen Sie die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Abfrage in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] aus.

```sql
SELECT * FROM sys.dm_os_waiting_tasks 
WHERE blocking_session_id IS NOT NULL; 
``` 
  
## <a name="see-also"></a>Siehe auch  
[SQL Server mit dem Betriebs System verbundene dynamische &#40;Verwaltungs Sichten Transact&#41;-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)      
[Handbuch zur Thread- und Taskarchitektur](../../relational-databases/thread-and-task-architecture-guide.md)     
   
 
