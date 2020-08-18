---
description: sys.trace_subclass_values (Transact-SQL)
title: sys. trace_subclass_values (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.trace_subclass_values
- trace_subclass_values_TSQL
- sys.trace_subclass_values_TSQL
- trace_subclass_values
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_subclass_values catalog view
ms.assetid: 542b19ca-61c8-41ca-aa2e-0aba8906cc24
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2c13e9d2f1ce861a2240495f504e945141a01c12
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88400266"
---
# <a name="systrace_subclass_values-transact-sql"></a>sys.trace_subclass_values (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **sys. trace_subclass_values** -Katalog Sicht enthält eine Liste benannter Spaltenwerte. Diese Unterklassenwerte ändern sich für eine bestimmte Version von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nicht.  
  
 Eine vollständige Liste der unterstützten Ablaufverfolgungsereignisse finden Sie unter [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen die Katalogsichten für erweiterte Ereignisse.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**trace_column_id**|**smallint**|ID des Ablaufverfolgungsereignisses. Dieser Parameter befindet sich auch in der Katalog Sicht **sys. trace_events** .|  
|**trace_event_id**|**smallint**|ID der Ablaufverfolgungsspalte, die für die Enumeration verwendet wird. Dieser Parameter befindet sich auch in der Katalog Sicht **sys. trace_columns** .|  
|**subclass_name**|**nvarchar(128)**|Bedeutung des Spaltenwerts.|  
|**subclass_value**|**smallint**|Spaltenwert|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys. Traces &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys. trace_categories &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys. trace_columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys. trace_events &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys. trace_event_bindings &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)  
  
  
