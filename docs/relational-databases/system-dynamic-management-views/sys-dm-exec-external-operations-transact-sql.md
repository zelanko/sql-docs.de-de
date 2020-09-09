---
description: sys. dm_exec_external_operations (Transact-SQL)
title: sys. dm_exec_external_operations (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_EXTERNAL_OPERATIONS_TSQL
- DM_EXEC_EXTERNAL_OPERATIONS
- SYS.DM_EXEC_EXTERNAL_OPERATIONS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- sys.dm_exec_external_operations management view
- dm_exec_external_operations management view
ms.assetid: d268217a-85b8-4b7f-9cd1-87865eba2be1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cfb27c27e680e253cbafc0d30a4e4db0cd6d9ed4
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548533"
---
# <a name="sysdm_exec_external_operations-transact-sql"></a>sys. dm_exec_external_operations (Transact-SQL)
[!INCLUDE [sqlserver2016-asa-pdw](../../includes/applies-to-version/sqlserver2016-asa-pdw.md)]

  Erfasst Informationen über externe polybase-Vorgänge.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|Eindeutige Abfrage-ID, die polybase-Abfrage zugeordnet ist|Siehe ID in [sys. dm_exec_requests &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)|  
|step_index|**int**|Index des Abfrage Schritts|Weitere Informationen finden Sie unter step_index in [sys. dm_exec_distributed_request_steps &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md)|  
|operation_-Typ|**nvarchar(128)**|Beschreibt einen Hadoop-Vorgang oder einen anderen externen Vorgang.|"Externer Hadoop-Vorgang"|  
|operation_ Name|**nvarchar(4000)**|Gibt an, wie der Status des Auftrags in Prozent (wie viel die Eingabe verbraucht) ist.|0-1-multipliziert mit Faktor 100 (abgeschlossen)|  
|map_ Status|**float**|Gibt an, wie der Status eines Reduzierungs Auftrags in Prozent (falls vorhanden) reduziert wird.|0-1-multipliziert mit Faktor 100 (abgeschlossen)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei polybase mit dynamischen Verwaltungs Sichten](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungs Sichten im Zusammenhang mit der Datenbank &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
