---
title: sys. partition_range_values (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.partition_range_values
- partition_range_values_TSQL
- partition_range_values
- sys.partition_range_values_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partition_range_values catalog view
ms.assetid: 9aee483e-61f3-4613-bec6-f084161f45ac
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 604742cc1c74c3e7ffa472ee1cd37efd1bc98987
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821704"
---
# <a name="syspartition_range_values-transact-sql"></a>sys.partition_range_values (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Enthält für jeden Bereichsbegrenzungswert einer Partitionsfunktion vom Typ R eine Zeile.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**function_id**|**int**|ID der Partitionsfunktion für diesen Bereichsbegrenzungswert.|  
|**boundary_id**|**int**|ID (einsbasierte Ordnungszahl) des Begrenzungswerttupels, wobei die äußerste linke Begrenzung mit einer ID von 1 beginnt.|  
|**parameter_id**|**int**|ID des Parameters der Funktion, der dieser Wert entspricht. Die Werte in dieser Spalte entsprechen den Werten in der **parameter_id** -Spalte der **sys.partition_parameters** -Katalogsicht für eine bestimmte **function_id**.|  
|**value**|**sql_variant**|Der tatsächliche Begrenzungswert.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Sichten für Partitions Funktionen &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys. partition_functions &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys.partition_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)  
  
  
