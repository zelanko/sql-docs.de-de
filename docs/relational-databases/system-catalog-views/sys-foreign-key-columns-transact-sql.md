---
title: sys. foreign_key_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.foreign_key_columns
- foreign_key_columns
- sys.foreign_key_columns_TSQL
- foreign_key_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.foreign_key_columns catalog view
ms.assetid: 7247f065-5441-4bcf-9f25-c84a03290dc6
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ad5bd8f5391e5903a6f9fd10e0cfb340cf4952b6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68133981"
---
# <a name="sysforeign_key_columns-transact-sql"></a>sys.foreign_key_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Enthält eine Zeile für jede Spalte oder Spaltengruppe, die einen Fremdschlüssel enthält.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**constraint_object_id**|**int**|ID der FOREIGN KEY-Einschränkung.|  
|**constraint_column_id**|**int**|ID der Spalte oder der Spaltengruppe, die die FOREIGN KEY-Anweisung enthält (*1..n* , wobei n=Anzahl von Spalten).|  
|**parent_object_id**|**int**|Die ID des übergeordneten Objekts der Einschränkung, das das verweisende Objekt darstellt.|  
|**parent_column_id**|**int**|Die ID der übergeordneten Spalte, die die verweisende Spalte darstellt.|  
|**referenced_object_id**|**int**|Die ID des Objekts, auf das verwiesen wird und das den Kandidatenschlüssel aufweist.|  
|**referenced_column_id**|**int**|Die ID der Spalte, auf die verwiesen wird (Kandidatenschlüsselspalte).|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [FAQ: Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
