---
title: Sys.partition_functions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.partition_functions_TSQL
- partition_functions
- sys.partition_functions
- partition_functions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partition_functions catalog view
ms.assetid: 96515727-728b-4bea-804a-36ce915b8b75
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 495dd51ede4adf27b488fa35847117fddf64cafc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645128"
---
# <a name="syspartitionfunctions-transact-sql"></a>sys.partition_functions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Enthält eine Zeile für jede Partitionsfunktion in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name der Partitionsfunktion. Ist in der Datenbank eindeutig.|  
|**function_id**|**int**|Die Partitionsfunktions.ID. Ist in der Datenbank eindeutig.|  
|**type**|**char(2)**|Funktionstyp<br /><br /> R = Bereich|  
|**type_desc**|**nvarchar(60)**|Funktionstyp<br /><br /> RANGE|  
|**Anzahl von Verzweigungen angibt**|**int**|Anzahl der von der Funktion erstellten Partitionen|  
|**boundary_value_on_right**|**bit**|Für die Bereichspartitionierung.<br /><br /> 1 = Der Begrenzungswert ist im RIGHT-Bereich der Begrenzung enthalten.<br /><br /> 0 = LEFT.|  
|**is_system**||**Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 1 = Das Objekt wird für Volltextindexfragmente verwendet.<br /><br /> 0 = Das Objekt wird nicht für Volltextindexfragmente verwendet.|  
|**create_date**|**datetime**|Datum, an dem die Funktion erstellt wurde|  
|**modify_date**|**datetime**|Datum, an dem die Funktion zuletzt mithilfe einer ALTER-Anweisung geändert wurde|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Partitionieren von Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.partition_range_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)   
 [Sys. partition_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)  
  
  
