---
title: dm_fts_memory_pools (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_memory_pools_TSQL
- sys.dm_fts_memory_pools_TSQL
- sys.dm_fts_memory_pools
- dm_fts_memory_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_memory_pools dynamic management view
ms.assetid: 24747239-cd78-4d55-a00a-19233a457f42
author: pmasl
ms.author: pelopes
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8af495b77a6a6d1cba9198237a40e87168c16e69
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65947253"
---
# <a name="sysdmftsmemorypools-transact-sql"></a>sys.dm_fts_memory_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen zu den Shared Memory-Pools zurück, die für die Volltext-Gatherer-Komponente für einen Volltext-Durchforstungsvorgang oder einen Volltext-Durchforstungsbereich zur Verfügung stehen.  
   
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**pool_id**|**int**|ID des belegten Speicherpools.<br /><br /> 0 = Kleine Puffer<br /><br /> 1 = Große Puffer|  
|**buffer_size**|**int**|Größe der einzelnen zugeordneten Puffer im Speicherpool.|  
|**min_buffer_limit**|**int**|Mindestzahl der zulässigen Puffer im Speicherpool.|  
|**max_buffer_limit**|**int**|Höchstzahl der zulässigen Puffer im Speicherpool.|  
|**buffer_count**|**int**|Derzeitige Anzahl der auf dem freigegebenen Speicherbereich basierenden Puffer im Speicherpool.|  
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   
 
## <a name="physical-joins"></a>Physische Joins  
 ![Wesentliche Joins dieser dynamischen verwaltungssicht](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-pools-1.gif "wesentliche Joins dieser dynamischen verwaltungssicht")  
  
## <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|Aktion|Beziehung|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|n:1|  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das gesamte Shared Memory zurückgegeben, das von der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Volltext-Gatherer-Komponente des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozesses verwendet wird.  
  
```  
SELECT SUM(buffer_size * buffer_count) AS "total memory"   
    FROM sys.dm_fts_memory_pools;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Volltextsuche und semantische Suche, dynamische Verwaltungssichten und Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  
