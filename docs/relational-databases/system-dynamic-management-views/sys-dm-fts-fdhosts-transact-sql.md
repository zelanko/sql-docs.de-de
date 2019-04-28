---
title: sys.dm_fts_fdhosts (Transact-SQL) | Microsoft Docs
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
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: faa79f48a4f3b8ac70984c3b02c8863d7d37e8ac
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026716"
---
# <a name="sysdmftsfdhosts-transact-sql"></a>sys.dm_fts_fdhosts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen über die aktuelle Aktivität des oder der Filterdaemonhosts auf der Serverinstanz zurück.  
  
 
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**fdhost_id**|**int**|ID des Filterdämonhosts.|  
|**fdhost_name**|**nvarchar(120)**|Name des Filterdämonhosts.|  
|**fdhost_process_id**|**int**|Windows-Prozess-ID des Filterdämonhosts.|  
|**fdhost_type**|**nvarchar(120)**|Typ des Dokuments, das vom Filterdämonhost verarbeitet wird. Ist einer der folgenden Typen:<br /><br /> Einzelthread<br /><br /> Multithread<br /><br /> Umfangreiches Dokument|  
|**max_thread**|**int**|Maximale Anzahl von Threads im Filterdämonhost.|  
|**batch_count**|**int**|Anzahl von Batches, die derzeit im Filterdämonhost verarbeitet werden.|  
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   

## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden der Name des Filterdämonhosts und die maximale Anzahl der in ihm enthaltenen Threads zurückgegeben. Außerdem wird überwacht, wie viele Batches derzeit im Filterdämon verarbeitet werden. Diese Informationen können bei der Leistungsdiagnose verwendet werden.  
  
```  
SELECT fdhost_name, batch_count, max_thread FROM sys.dm_fts_fdhosts;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Volltextsuche und semantische Suche, dynamische Verwaltungssichten und Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Volltextsuche](../../relational-databases/search/full-text-search.md)  
  
  
