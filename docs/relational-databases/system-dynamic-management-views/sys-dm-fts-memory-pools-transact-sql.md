---
description: sys.dm_fts_memory_pools (Transact-SQL)
title: sys. dm_fts_memory_pools (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 720c3a3727f332c289b08480f6367babc0213ad4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489877"
---
# <a name="sysdm_fts_memory_pools-transact-sql"></a>sys.dm_fts_memory_pools (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt Informationen zu den Shared Memory-Pools zurück, die für die Volltext-Gatherer-Komponente für einen Volltext-Durchforstungsvorgang oder einen Volltext-Durchforstungsbereich zur Verfügung stehen.  
   
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**pool_id**|**int**|ID des belegten Speicherpools.<br /><br /> 0 = Kleine Puffer<br /><br /> 1 = Große Puffer|  
|**buffer_size**|**int**|Größe der einzelnen zugeordneten Puffer im Speicherpool.|  
|**min_buffer_limit**|**int**|Mindestzahl der zulässigen Puffer im Speicherpool.|  
|**max_buffer_limit**|**int**|Höchstzahl der zulässigen Puffer im Speicherpool.|  
|**buffer_count**|**int**|Derzeitige Anzahl der auf dem freigegebenen Speicherbereich basierenden Puffer im Speicherpool.|  
  
## <a name="permissions"></a>Berechtigungen  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ist die- `VIEW SERVER STATE` Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die- `VIEW DATABASE STATE` Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der  **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   
 
## <a name="physical-joins"></a>Physische Joins  
 ![Wesentliche Joins dieser dynamischen Verwaltungssicht](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-pools-1.gif "Wesentliche Joins dieser dynamischen Verwaltungssicht")  
  
## <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|An|Beziehung|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|n:1|  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das gesamte Shared Memory zurückgegeben, das von der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Volltext-Gatherer-Komponente des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozesses verwendet wird.  
  
```  
SELECT SUM(buffer_size * buffer_count) AS "total memory"   
    FROM sys.dm_fts_memory_pools;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungs Sichten und Funktionen für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  
