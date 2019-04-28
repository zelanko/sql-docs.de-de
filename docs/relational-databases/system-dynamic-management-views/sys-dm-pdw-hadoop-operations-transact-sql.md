---
title: Sys.dm_pdw_hadoop_operations (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d2337d4-e2c7-48de-9c26-cdc7e6eb5d55
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 11c8cc0797bafff6cc8c38bffb55023be00003a9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62690424"
---
# <a name="sysdmpdwhadoopoperations-transact-sql"></a>sys.dm_pdw_hadoop_operations (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jedes map-reduce-Auftrags, der als Teil der Ausführung an Hadoop weitergegeben wird eine [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Abfrage einer externen Hadoop-Tabelle. Jeder map-reduce-Auftrag stellt eines der Prädikate in der Abfrage dar. Dies wird nur verwendet, wenn die prädikatweitergabe für Abfragen für Hadoop externe Tabellen aktiviert ist.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|Die ID für diesen externen Hadoop-Vorgang.|Identisch mit der ID in der [dm_pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Der Index des abfrageschritts, die auf diesen Hadoop-Vorgang verweist.|Identisch mit Step_index in [dm_pdw_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|operation_type|**nvarchar(255)**|Beschreibt den Typ externer Vorgang.|"Externen Hadoop-Operation"|  
|operation_name|**nvarchar(4000)**|Die Auftrags-ID für einen map-reduce-Auftrag. Dies wird zurückgegeben, von Hadoop nach [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] sendet den Auftrag.||  
|map_progress|**float**|Der Prozentsatz der Daten, die bisher durch die Map-Auftrag verbraucht wurde.|Eine Gleitkommazahl zwischen und einschließlich 0 und 100 liegen.|  
|reduce_progress|**int**|Der Prozentsatz des Reduce-Auftrags, der abgeschlossen ist...|Eine Gleitkommazahl zwischen und einschließlich 0 und 100 liegen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Systemsichten &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
