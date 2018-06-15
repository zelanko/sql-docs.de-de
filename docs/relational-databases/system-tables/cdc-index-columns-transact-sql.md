---
title: index_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- cdc.index_columns_TSQL
- cdc.index_columns
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.index_columns
ms.assetid: 256ec8a5-3031-40a8-9fdb-99db42ea453d
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 631566399cb1489286c36b7af9ed6bbb84e9bb7d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260503"
---
# <a name="cdcindexcolumns-transact-sql"></a>cdc.index_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Indexspalte zurück, die einer Änderungstabelle zugeordnet ist. Die Indexspalten werden von Change Data Capture verwendet, um die Zeilen in der Quelltabelle eindeutig zu identifizieren. Standardmäßig werden die Spalten des Primärschlüssels der Quelltabelle eingeschlossen. Wenn jedoch in der Quelltabelle ein eindeutiger Index angegeben und Change Data Capture in der Quelltabelle aktiviert ist, werden stattdessen die in diesem Index enthaltenen Spalten verwendet. Bei aktivierter Nachverfolgung von Nettoänderungen ist ein Primärschlüssel oder ein eindeutiger Index erforderlich. Weitere Informationen finden Sie unter [sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
 Es wird empfohlen, die Systemtabellen nicht direkt abzufragen. Führen Sie stattdessen die [sp_cdc_help_change_data_capture](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md) gespeicherte Prozedur.  

  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID der Änderungstabelle.|  
|**column_name**|**sysname**|Name der Indexspalte.|  
|**index_ordinal**|**tinyint**|Ordnungszahl (1-basiert) der im Index enthaltenen Spalte.|  
|**column_id**|**int**|ID der Spalte in der Quelltabelle.|  
  
## <a name="see-also"></a>Siehe auch  
 [CDC. change_tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
  
  
