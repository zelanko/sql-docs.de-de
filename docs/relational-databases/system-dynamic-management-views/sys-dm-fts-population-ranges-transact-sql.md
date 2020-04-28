---
title: sys. dm_fts_population_ranges (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_population_ranges
- sys.dm_fts_population_ranges_TSQL
- dm_fts_population_ranges_TSQL
- dm_fts_population_ranges
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_population_ranges dynamic management view
ms.assetid: 58d8564b-9c43-4965-a31c-2893890334ef
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f00de77ef3435bf998f9019fc8b60458594fb0f2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68265905"
---
# <a name="sysdm_fts_population_ranges-transact-sql"></a>sys.dm_fts_population_ranges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen zu den spezifischen Bereichen im Zusammenhang mit einer zurzeit ausgeführten Volltextindexauffüllung zurück.  
   
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**memory_address**|**varbinary(8)**|Adresse der Speicherpuffer, die für die auf diesen Teilbereich einer Volltextindexauffüllung bezogene Aktivität reserviert sind.|  
|**parent_memory_address**|**varbinary(8)**|Adresse der Speicherpuffer, die das übergeordnete Objekt aller Bereiche einer Auffüllung darstellen, die sich auf einen Volltextindex bezieht.|  
|**is_retry**|**bit**|Falls der Wert 1 ist, ist dieser Teilbereich für die Wiederholung von Zeilen verantwortlich, für die Fehler festgestellt wurden.|  
|**session_id**|**smallint**|ID der Sitzung, die diesen Task zurzeit verarbeitet.|  
|**processed_row_count**|**int**|Anzahl der von diesem Bereich verarbeiteten Zeilen. Die Fortschrittsinformationen werden persistent gespeichert und alle 5 Minuten, anstatt mit jedem Batchcommit, gezählt.|  
|**error_count**|**int**|Anzahl der Zeilen, für die von diesem Bereich Fehler erkannt wurden. Die Fortschrittsinformationen werden persistent gespeichert und alle 5 Minuten, anstatt mit jedem Batchcommit, gezählt.|  
  
## <a name="permissions"></a>Berechtigungen  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]ist die `VIEW SERVER STATE` -Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die `VIEW DATABASE STATE` -Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.   
 
## <a name="physical-joins"></a>Physische Joins  
 ![Wesentliche Joins dieser dynamischen Verwaltungssicht](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-population-ranges-1.gif "Wesentliche Joins dieser dynamischen Verwaltungssicht")  
  
## <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|Beschreibung|Beziehung|  
|----------|--------|------------------|  
|dm_fts_population_ranges.parent_memory_address|dm_fts_index_population.memory_address|n:1|  
  
## <a name="see-also"></a>Weitere Informationen  
  [Dynamische Verwaltungs Sichten und Funktionen für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

