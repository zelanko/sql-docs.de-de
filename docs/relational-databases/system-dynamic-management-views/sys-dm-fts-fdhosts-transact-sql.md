---
title: dm_fts_fdhosts (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_fdhosts
- dm_fts_fdhosts_TSQL
- sys.dm_fts_fdhosts
- sys.dm_fts_fdhosts_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_fdhosts dynamic management view
- troubleshooting [SQL Server], full-text search
ms.assetid: d42a6334-4362-4361-83da-f8324fe55ec7
author: pmasl
ms.author: pelopes
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f76ab50987ea8a2e1f2ce6c93e71d2623f532d80
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67951008"
---
# <a name="sysdmftsfdhosts-transact-sql"></a>sys.dm_fts_fdhosts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen über die aktuelle Aktivität des oder der Filterdaemonhosts auf der Serverinstanz zurück.  
  
 
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**fdhost_id**|**int**|ID des Filterdämonhosts.|  
|**fdhost_name**|**nvarchar(120)**|Name des Filterdämonhosts.|  
|**fdhost_process_id**|**int**|Windows-Prozess-ID des Filterdämonhosts.|  
|**fdhost_type**|**nvarchar(120)**|Typ des Dokuments, das vom Filterdämonhost verarbeitet wird. Ist einer der folgenden Typen:<br /><br /> Einzelthread<br /><br /> Multithread<br /><br /> Umfangreiches Dokument|  
|**max_thread**|**int**|Maximale Anzahl von Threads im Filterdämonhost.|  
|**batch_count**|**int**|Anzahl von Batches, die derzeit im Filterdämonhost verarbeitet werden.|  
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] ist die Berechtigung `VIEW DATABASE STATE` in der Datenbank erforderlich.   

## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden der Name des Filterdämonhosts und die maximale Anzahl der in ihm enthaltenen Threads zurückgegeben. Außerdem wird überwacht, wie viele Batches derzeit im Filterdämon verarbeitet werden. Diese Informationen können bei der Leistungsdiagnose verwendet werden.  
  
```  
SELECT fdhost_name, batch_count, max_thread FROM sys.dm_fts_fdhosts;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Volltextsuche und semantische Suche, dynamische Verwaltungssichten und Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Volltextsuche](../../relational-databases/search/full-text-search.md)  
  
  
