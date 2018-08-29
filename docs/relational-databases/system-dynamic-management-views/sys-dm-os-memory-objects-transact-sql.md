---
title: Sys. dm_os_memory_objects (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_memory_objects
- sys.dm_os_memory_objects
- sys.dm_os_memory_objects_TSQL
- dm_os_memory_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_objects dynamic management view
ms.assetid: 5688bcf8-5da9-4ff9-960b-742b671d7096
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4b48c36183631bfbbf149ff77e8b1c93f0a79fe4
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43068943"
---
# <a name="sysdmosmemoryobjects-transact-sql"></a>sys.dm_os_memory_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt Speicherobjekte, die derzeit von zugeordnet sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können **Sys. dm_os_memory_objects** speicherauslastung zu analysieren und zur Identifizierung möglicher Speicherverluste.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**memory_object_address**|**varbinary(8)**|Adresse des Speicherobjekts. Lässt keine NULL-Werte zu.|  
|**parent_address**|**varbinary(8)**|Adresse des übergeordneten Speicherobjekts. Lässt NULL-Werte zu.|  
|**pages_allocated_count**|**int**|**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Anzahl der von diesem Objekt zugeordneten Seiten. Lässt keine NULL-Werte zu.|  
|**pages_in_bytes**|**bigint**|**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Arbeitsspeicher in Bytes, der von dieser Instanz des Arbeitsspeicherobjekts zugeordnet wird. Lässt keine NULL-Werte zu.|  
|**creation_options**|**int**|Nur interne Verwendung. Lässt NULL-Werte zu.|  
|**bytes_used**|**bigint**|Nur interne Verwendung. Lässt NULL-Werte zu.|  
|**type**|**nvarchar(60)**|Typ des Speicherobjekts:<br /><br /> Dies gibt an, eine Komponente, der dieses Speicherobjekt gehört, oder die Funktion des Speicherobjekts. Lässt NULL-Werte zu.|  
|**name**|**varchar(128)**|Nur interne Verwendung. NULL-Werte sind zulässig.|  
|**memory_node_id**|**smallint**|ID eines Speicherknotens, der von diesem Speicherobjekt verwendet wird. Lässt keine NULL-Werte zu.|  
|**creation_time**|**datetime**|Nur interne Verwendung. Lässt NULL-Werte zu.|  
|**max_pages_allocated_count**|**int**|**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Maximale Anzahl der von diesem Speicherobjekt zugeordneten Seiten. Lässt keine NULL-Werte zu.|  
|**page_size_in_bytes**|**int**|**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Größe der von diesem Objekt zugeordneten Seiten in Bytes. Lässt keine NULL-Werte zu.|  
|**max_pages_in_bytes**|**bigint**|Höchstmenge an Arbeitsspeicher, die je von diesem Arbeitsspeicherobjekt verwendet wurde. Lässt keine NULL-Werte zu.|  
|**page_allocator_address**|**varbinary(8)**|Speicheradresse der Seitenzuordnung. Lässt keine NULL-Werte zu. Weitere Informationen finden Sie unter [Sys. dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**creation_stack_address**|**varbinary(8)**|Nur interne Verwendung. Lässt NULL-Werte zu.|  
|**sequence_num**|**int**|Nur interne Verwendung. Lässt NULL-Werte zu.|  
|**partition_type**|**int**|Der Typ der Partition:<br /><br /> 0 – nicht-partitionierbare Speicherobjekt<br /><br /> 1 – partitionierbare Speicherobjekt, derzeit nicht partitioniert.<br /><br /> 2 – partitionierbare Speicherobjekt, partitioniert nach NUMA-Knoten. In einer Umgebung mit einem einzelnen NUMA-Knoten entspricht dies auf 1.<br /><br /> 3 – partitionierbare Arbeitsspeicher-Objekt, durch die CPU partitioniert.|  
|**contention_factor**|**real**|Ein Wert, der Konflikte für dieses Objekt Arbeitsspeicher angeben, mit 0, d. h. keine Konflikte auftreten. Der Wert wird aktualisiert, wenn eine angegebene Anzahl der speicherbelegungen reflektierenden Konflikte während dieses Zeitraums vorgenommen wurden. Gilt nur für threadsichere Speicherobjekte.|  
|**waiting_tasks_count**|**bigint**|Die Anzahl der Wartevorgänge auf diesem Speicherobjekt. Dieser Indikator wird erhöht, wenn der Arbeitsspeicher von diesem Arbeitsspeicherobjekt zugewiesen ist. Das Inkrement ist die Anzahl der Aufgaben, die derzeit darauf warten, für den Zugriff auf dieses Speicherobjekt an. Gilt nur für threadsichere Speicherobjekte. Dies ist eine bewährte Aufwand Wert ohne Garantie auf Richtigkeit.|  
|**exclusive_access_count**|**bigint**|Gibt an, wie oft dieses Speicherobjekt ausschließlich auf die zugegriffen wurde. Gilt nur für threadsichere Speicherobjekte.  Dies ist eine bewährte Aufwand Wert ohne Garantie auf Richtigkeit.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
 **Partition_type**, **Contention_factor**, **Waiting_tasks_count**, und **Exclusive_access_count** sind noch nicht im implementiert [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   

## <a name="remarks"></a>Hinweise  
 Speicherobjekte sind Heaps. Sie stellen im Vergleich zu den Arbeitsspeicherclerks Zuordnungen mit feinerer Granularität bereit. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten verwenden Arbeitsspeicherobjekte anstelle der Arbeitsspeicherclerks. Speicherobjekte verwenden die Seitenzuordnungsschnittstelle des Arbeitsspeicherclerks für die Zuordnung von Seiten. Speicherobjekte verwenden keine Schnittstellen, die auf virtuellem Speicher oder Shared Memory basieren. Abhängig von den Zuordnungsmustern können Komponenten verschiedene Typen von Speicherobjekten erstellen, um Bereiche zufälliger Größe zuzuordnen.  
  
 Die Standardseitengröße eines Speicherobjekts beträgt 8 kB. Inkrementelle Speicherobjekte können jedoch Seitengrößen zwischen 512 Bytes und 8 kB aufweisen.  
  
> [!NOTE]  
>  Die Seitengröße entspricht nicht der maximalen Zuordnung. Die Seitengröße ist vielmehr eine Zuordnungseinheit, die von einer Seitenzuordnung unterstützt und von einem Arbeitsspeicherclerk implementiert wird. Sie können von Arbeitsspeicherobjekten größere Zuordnungen als 8 KB anfordern.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der von den einzelnen Speicherobjekttypen zugeordnete Speicherumfang zurückgegeben.  
  
```  
SELECT SUM (pages_in_bytes) as 'Bytes Used', type   
FROM sys.dm_os_memory_objects  
GROUP BY type   
ORDER BY 'Bytes Used' DESC;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
  [Dynamische Verwaltungssichten in Verbindung mit SQL Server-Betriebssystem &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)  
  
  


