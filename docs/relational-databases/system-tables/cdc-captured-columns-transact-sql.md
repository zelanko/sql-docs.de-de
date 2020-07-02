---
title: CDC. captured_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.captured_columns
- cdc.captured_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.captured_columns
ms.assetid: 7bb4d408-d764-4ef6-802c-f271c8d39c2a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b4bfba2f8a8512926a42c12236e5baf0d07ceda9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758720"
---
# <a name="cdccaptured_columns-transact-sql"></a>cdc.captured_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Zeile für jede in einer Aufzeichnungsinstanz nachverfolgte Spalte zurück. Standardmäßig werden alle Spalten der Quelltabelle aufgezeichnet. Es können jedoch auch Spalten ein- oder ausgeschlossen werden, wenn die Quelltabelle für Change Data Capture aktiviert ist. Dazu geben Sie eine Spaltenliste an. Weitere Informationen finden Sie unter [sys. sp_cdc_enable_table &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
 Es wird empfohlen, **die Systemtabellen nicht direkt abzufragen**. Führen Sie stattdessen die gespeicherte Prozedur [sys.sp_cdc_get_source_columns](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md) aus.  
   
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID der Quelltabelle, zu der die aufgezeichnete Spalte gehört.|  
|**column_name**|**sysname**|Name der aufgezeichneten Spalte.|  
|**column_id**|**int**|ID der aufgezeichneten Spalte innerhalb der Quelltabelle.|  
|**column_type**|**sysname**|Typ der aufgezeichneten Spalte.|  
|**column_ordinal**|**int**|Spaltenordnungszahl (1-basiert) in der Änderungstabelle. Die Metadatenspalten in der Änderungstabelle werden ausgeschlossen. Der ersten aufgezeichneten Spalte wird die Ordnungszahl 1 zugewiesen.|  
|**is_computed**|**bit**|Gibt an, dass die aufgezeichnete Spalte eine berechnete Spalte in der Quelltabelle ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [CDC. change_tables &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
  
  
