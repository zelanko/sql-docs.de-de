---
description: sys.dm_pdw_hadoop_operations (Transact-SQL)
title: sys.dm_pdw_hadoop_operations (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: 25c2e732fea0b92866f233a51a69103028245418
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97472801"
---
# <a name="sysdm_pdw_hadoop_operations-transact-sql"></a>sys.dm_pdw_hadoop_operations (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Enthält eine Zeile für jeden Map-Reduce-Auftrag, der als Teil der Ausführung einer [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Abfrage für eine externe Hadoop-Tabelle an Hadoop übermittelt wird. Jeder Map-Reduce-Auftrag stellt einen der Prädikate in der Abfrage dar. Diese Option wird nur verwendet, wenn die Prädikat Weitergabe für Abfragen für externe Hadoop-Tabellen aktiviert ist.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|ID für diesen externen Hadoop-Vorgang.|Identisch mit der ID in [sys.dm_pdw_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|Index des Abfrage Schritts, der auf diesen Hadoop-Vorgang verweist.|Identisch mit step_index in [sys.dm_pdw_request_steps &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md).|  
|operation_type|**nvarchar(255)**|Beschreibt den Typ des externen Vorgangs.|"Externer Hadoop-Vorgang"|  
|operation_name|**nvarchar(4000)**|Die Auftrags-ID für einen Map-Reduce-Auftrag. Dies wird von Hadoop zurückgegeben, nachdem [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] der Auftrag übermittelt wurde.||  
|map_progress|**float**|Der Prozentsatz der Eingabedaten, die bisher vom Zuordnungs Auftrag verarbeitet wurden.|Eine Gleit Komma Zahl zwischen und einschließlich, 0 und 100.|  
|reduce_progress|**int**|Der Prozentsatz des abgeschlossenen Reduzierungs Auftrags.|Eine Gleit Komma Zahl zwischen und einschließlich, 0 und 100.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [System Sichten &#40;Transact-SQL-&#41;](../../t-sql/language-reference.md)  
  
