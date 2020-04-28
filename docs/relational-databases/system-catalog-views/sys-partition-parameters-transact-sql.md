---
title: sys. partition_parameters (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- partition_parameters_TSQL
- partition_parameters
- sys.partition_parameters_TSQL
- sys.partition_parameters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partition_parameters catalog view
ms.assetid: 2012ed9d-3ea3-4c29-9b78-dfa54a392dce
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 32fe257f14c1e085a43b4150ee933888a83d5d14
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68125340"
---
# <a name="syspartition_parameters-transact-sql"></a>sys.partition_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Enthält eine Zeile für jeden Parameter einer Partitionsfunktion.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**function_id**|**int**|ID der Partitionsfunktion, zu der dieser Parameter gehört|  
|**parameter_id**|**int**|ID des Parameters. Ist innerhalb der Partitionsfunktion eindeutig und beginnt mit 1.|  
|**system_type_id**|**tinyint**|ID des Systemtyps des Parameters. Entspricht der Spalte **system_type_id** der Katalogsicht **sys.types** .|  
|**max_length**|**smallint**|Die maximale Länge des Parameters in Byte.|  
|**precision**|**tinyint**|Genauigkeit des Parameters, wenn dieser numerisch ist. Andernfalls ist der Wert 0.|  
|**scale**|**tinyint**|Dezimalstellen des Parameters, wenn dieser numerisch ist. Andernfalls ist der Wert 0.|  
|**collation_name**|**sysname**|Name der Sortierung des Parameters, wenn dieser auf Zeichen basiert. Andernfalls ist der Wert NULL.|  
|**user_type_id**|**int**|Die ID des Typs. Ist in der Datenbank eindeutig. Für System Datentypen **user_type_id** = **system_type_id**.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Sichten für Partitions Funktionen &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys. partition_functions &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys.partition_range_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)  
  
  
