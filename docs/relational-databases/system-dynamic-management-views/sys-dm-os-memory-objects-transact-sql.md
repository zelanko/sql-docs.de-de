---
title: sys. dm_os_memory_objects (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a3d0691a82607a207a64f4a6c7ed8c937f052abc
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983076"
---
# <a name="sysdm_os_memory_objects-transact-sql"></a>sys.dm_os_memory_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt Speicher Objekte zurück, die derzeit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zugeordnet sind. Sie können **sys. dm_os_memory_objects** verwenden, um die Speicherauslastung zu analysieren und mögliche Speicher Verluste zu identifizieren.  
  
|Spaltenname|Datentyp|und Beschreibung|  
|-----------------|---------------|-----------------|  
|**memory_object_address**|**varbinary(8)**|Adresse des Speicherobjekts. Lässt keine NULL-Werte zu.|  
|**parent_address**|**varbinary(8)**|Adresse des übergeordneten Speicherobjekts. Lässt NULL-Werte zu.|  
|**pages_allocated_count**|**int**|**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Anzahl der von diesem Objekt zugeordneten Seiten. Lässt keine NULL-Werte zu.|  
|**pages_in_bytes**|**bigint**|**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher.<br /><br /> Arbeitsspeicher in Bytes, der von dieser Instanz des Arbeitsspeicherobjekts zugeordnet wird. Lässt keine NULL-Werte zu.|  
|**creation_options**|**int**|Nur interne Verwendung. Lässt NULL-Werte zu.|  
|**bytes_used**|**bigint**|Nur interne Verwendung. Lässt NULL-Werte zu.|  
|**Typ**|**nvarchar(60)**|Typ des Speicherobjekts:<br /><br /> Dies gibt eine Komponente an, zu der dieses Speicher Objekt gehört, oder die Funktion des Speicher Objekts. Lässt NULL-Werte zu.|  
|**name**|**varchar(128)**|Nur interne Verwendung. NULL-Werte sind zulässig.|  
|**memory_node_id**|**smallint**|ID eines Speicherknotens, der von diesem Speicherobjekt verwendet wird. Lässt keine NULL-Werte zu.|  
|**creation_time**|**datetime**|Nur interne Verwendung. Lässt NULL-Werte zu.|  
|**max_pages_allocated_count**|**int**|**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Maximale Anzahl der von diesem Speicherobjekt zugeordneten Seiten. Lässt keine NULL-Werte zu.|  
|**page_size_in_bytes**|**int**|**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher.<br /><br /> Größe der von diesem Objekt zugeordneten Seiten in Bytes. Lässt keine NULL-Werte zu.|  
|**max_pages_in_bytes**|**bigint**|Höchstmenge an Arbeitsspeicher, die je von diesem Arbeitsspeicherobjekt verwendet wurde. Lässt keine NULL-Werte zu.|  
|**page_allocator_address**|**varbinary(8)**|Speicheradresse der Seitenzuordnung. Lässt keine NULL-Werte zu. Weitere Informationen finden Sie unter [sys. dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**creation_stack_address**|**varbinary(8)**|Nur interne Verwendung. Lässt NULL-Werte zu.|  
|**sequence_num**|**int**|Nur interne Verwendung. Lässt NULL-Werte zu.|  
|**partition_type**|**int**|Der Typ der Partition:<br /><br /> 0-nicht Partitionier bares Speicher Objekt<br /><br /> 1-partitionierbares Speicher Objekt, derzeit nicht partitioniert<br /><br /> 2-partitionierbares Speicher Objekt, partitioniert durch den NUMA-Knoten. In einer Umgebung mit einem einzelnen NUMA-Knoten entspricht dies 1.<br /><br /> 3-partitionierbares Speicher Objekt, partitioniert nach CPU.|  
|**contention_factor**|**real**|Ein-Wert, der Konflikte für dieses Speicher Objekt angibt, wobei 0 kein Konflikt ist. Der-Wert wird immer dann aktualisiert, wenn eine angegebene Anzahl von Speicher Belegungen während dieses Zeitraums zu Konflikten geführt hat. Gilt nur für Thread sichere Speicher Objekte.|  
|**waiting_tasks_count**|**bigint**|Anzahl der Warte Vorgänge für dieses Speicher Objekt. Dieser Wert wird jedes Mal inkrementiert, wenn Speicher von diesem Speicher Objekt belegt wird. Das Inkrement ist die Anzahl der Tasks, die zurzeit auf den Zugriff auf dieses Speicher Objekt warten. Gilt nur für Thread sichere Speicher Objekte. Dies ist ein bestmögliche Wert ohne Richtigkeit der Garantie.|  
|**exclusive_access_count**|**bigint**|Gibt an, wie oft ausschließlich auf dieses Speicher Objekt zugegriffen wurde. Gilt nur für Thread sichere Speicher Objekte.  Dies ist ein bestmögliche Wert ohne Richtigkeit der Garantie.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)][!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
 **partition_type**, **contention_factor**, **waiting_tasks_count**und **exclusive_access_count** sind noch nicht in [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]implementiert.  
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]ist `VIEW SERVER STATE` Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die `VIEW DATABASE STATE`-Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard-und Basic-Tarifen ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   

## <a name="remarks"></a>Remarks  
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
  [SQL Server mit dem Betriebs System verbundene dynamische &#40;Verwaltungs Sichten Transact&#41; -SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)  
  
  


