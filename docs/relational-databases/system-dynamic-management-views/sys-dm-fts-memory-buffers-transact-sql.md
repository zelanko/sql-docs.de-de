---
title: sys. dm_fts_memory_buffers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_memory_buffers
- dm_fts_memory_buffers_TSQL
- dm_fts_memory_buffers
- sys.dm_fts_memory_buffers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_memory_buffers dynamic management view
ms.assetid: 56895fe5-e8df-4d75-9adc-c1f7757cdef8
author: pmasl
ms.author: pelopes
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fed15fbcfa685bde5d408e799bb605a40380ab5a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68265925"
---
# <a name="sysdm_fts_memory_buffers-transact-sql"></a>sys.dm_fts_memory_buffers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen zu Speicherpuffern zurück, die einem bestimmten Speicherpool angehören, der im Rahmen einer Volltextdurchforstung oder eines Volltext-Durchforstungsbereichs verwendet wird.  
  
> [!NOTE]
> Die folgende Spalte wird in einer zukünftigen Version von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt: **row_count**. Vermeiden Sie diese Spalte bei Neuentwicklungen, und planen Sie die Änderung von Anwendungen, in denen die Spalte derzeit verwendet wird.  

  
|Column|Datentyp|BESCHREIBUNG|  
|------------|---------------|-----------------|  
|**pool_id**|**int**|ID des belegten Speicherpools.<br /><br /> 0 = Kleine Puffer<br /><br /> 1 = Große Puffer|  
|**memory_address**|**varbinary(8)**|Adresse des belegten Speicherpuffers.|  
|**name**|**nvarchar(4000)**|Name des freigegebenen Speicherpuffers, für den die Zuordnung erstellt wurde.|  
|**is_free**|**bit**|Aktueller Status des Speicherpuffers.<br /><br /> 0 = Frei<br /><br /> 1 = Belegt|  
|**row_count**|**int**|Anzahl von Zeilen, die dieser Puffer zurzeit bearbeitet.|  
|**bytes_used**|**int**|Umfang des zurzeit im Puffer belegten Speichers (in Bytes).|  
|**percent_used**|**int**|Prozentsatz des verwendeten belegten Arbeitsspeichers.|  
  
## <a name="permissions"></a>Berechtigungen  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]ist die `VIEW SERVER STATE` -Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die `VIEW DATABASE STATE` -Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   
  
## <a name="physical-joins"></a>Physische Joins  
 ![Wesentliche Joins dieser dynamischen Verwaltungssicht](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-buffers-1.gif "Wesentliche Joins dieser dynamischen Verwaltungssicht")  
  
## <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|Beschreibung|Beziehung|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|n:1|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten und Funktionen für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

