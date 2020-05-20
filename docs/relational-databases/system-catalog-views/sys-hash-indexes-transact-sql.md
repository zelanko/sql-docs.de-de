---
title: sys. hash_indexes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.hash_indexes_TSQL
- hash_indexes
- sys.hash_indexes
- hash_indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.hash_indexes catalog view
ms.assetid: d9e230fb-d3ff-486f-86ef-44898f0a703e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7090c0ac52f82c0840c7bc36f91d146a121b1854
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828485"
---
# <a name="syshash_indexes-transact-sql"></a>sys.hash_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt aktuelle Hashindizes und die Hashindexeigenschaften an. Hash Indizes werden nur für [in-Memory-OLTP &#40;in-Memory-Optimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)unterstützt.  
  
 Die sys. hash_indexes-Sicht enthält dieselben Spalten wie die sys. Indexes-Sicht und eine zusätzliche Spalte mit dem Namen **bucket_count**. Weitere Informationen zu den anderen Spalten in der sys. hash_indexes-Sicht finden Sie unter [sys. Indexes &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**\<geerbte Spalten>**||Erbt Spalten von [sys. Indexes &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).|  
|**bucket_count**|**int**|Anzahl der Hashbuckets für Hashindizes.<br /><br /> Weitere Informationen zum bucket_count-Wert, einschließlich Richtlinien zum Festlegen des Werts, finden Sie unter [CREATE TABLE &#40;Transact-SQL-&#41;](../../t-sql/statements/create-table-transact-sql.md).|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)].  Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
  
```  
SELECT object_name([object_id]) AS 'table_name', [object_id],  
     [name] AS 'index_name', [type_desc], [bucket_count]   
FROM sys.hash_indexes   
WHERE OBJECT_NAME([object_id]) = 'T1';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
