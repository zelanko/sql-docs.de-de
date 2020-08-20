---
description: sys.dm_os_memory_pools (Transact-SQL)
title: sys. dm_os_memory_pools (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_pools_TSQL
- dm_os_memory_pools
- dm_os_memory_pools_TSQL
- sys.dm_os_memory_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_pools dynamic management view
ms.assetid: 1ef053f3-c6f3-456e-82b6-26e4bd630d46
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e5108e097ae54800a6a41c99d52af0ca4a92ce5c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493653"
---
# <a name="sysdm_os_memory_pools-transact-sql"></a>sys.dm_os_memory_pools (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt eine Zeile für jeden Objektspeicher in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz zurück. Mit dieser Sicht kann die Cachespeichernutzung überwacht und schlechtes Cacheverhalten identifiziert werden.  
  
> [!NOTE]  
>  Um dies von oder aus aufzurufen [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , verwenden Sie den Namen **sys. dm_pdw_nodes_os_memory_pools**.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**memory_pool_address**|**varbinary(8)**|Speicheradresse des Eintrags, der für den Speicherpool steht. Lässt keine NULL-Werte zu.|  
|**pool_id**|**int**|ID eines bestimmten Pools in einer Gruppe von Pools. Lässt keine NULL-Werte zu.|  
|**type**|**nvarchar(60)**|Typ des Objektpools. Lässt keine NULL-Werte zu. Weitere Informationen finden Sie unter [sys. dm_os_memory_clerks &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**name**|**nvarchar(256)**|Vom System zugewiesener Name des Speicherobjekts. Lässt keine NULL-Werte zu.|  
|**max_free_entries_count**|**bigint**|Maximale Anzahl freier Einträge, die ein Pool haben kann. Lässt keine NULL-Werte zu.|  
|**free_entries_count**|**bigint**|Anzahl der derzeit im Pool befindlichen freien Einträge. Lässt keine NULL-Werte zu.|  
|**removed_in_all_rounds_count**|**bigint**|Anzahl der seit dem Starten der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz aus dem Pool entfernten Einträge. Lässt keine NULL-Werte zu.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] , [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="permissions"></a>Berechtigungen

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ist die- `VIEW SERVER STATE` Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die- `VIEW DATABASE STATE` Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der  **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   

## <a name="remarks"></a>Bemerkungen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten verwenden gelegentlich ein gemeinsames Poolframework zum Zwischenspeichern homogener, statusfreier Datentypen. Das Poolframework ist einfacher als das Cacheframework. Alle Einträge in den Pools werden als gleichwertig betrachtet. Pools sind in interner Hinsicht Arbeitsspeicherclerks und können an den Stellen verwendet werden, an denen Arbeitsspeicherclerks verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 
  [SQL Server dynamischen Verwaltungs Sichten im Zusammenhang mit dem Betriebs System &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


