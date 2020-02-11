---
title: sys. masked_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.masked_columns
- masked_columns_tsql
- sys.masked_columns_tsql
- masked_columns
helpviewer_keywords:
- sys.masked_columns catalog view
ms.assetid: 671577e4-d757-4b8d-9aa9-0fc8d51ea9ca
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9e059265dc5f5e0d2e4bc4a3b1396d2401386d7b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68102376"
---
# <a name="sysmasked_columns-transact-sql"></a>sys. masked_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Verwenden Sie die **sys. masked_columns** -Sicht zum Abfragen von Tabellen Spalten, auf die eine dynamische Daten Maskierungs Funktion angewendet wird. Diese Ansicht erbt von der **sys.columns** -Ansicht. Sie gibt alle Spalten in der **sys.columns** -Ansicht sowie die Spalten **is_masked** und **masking_function** zurück, wobei angegeben wird, ob die Spalte maskiert ist. Ist dies der Fall, gibt die Ansicht die definierte Maskierungsfunktion an. Diese Ansicht zeigt nur die Spalten an, auf die eine Maskierungsfunktion angewendet wird.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Die ID des Objekts, zu dem diese Spalte gehört.|  
|name|**sysname**|Name der Spalte. Ist eindeutig innerhalb des Objekts.|  
|column_id|**int**|ID der Spalte. Ist eindeutig innerhalb des Objekts.<br /><br /> Spalten-IDs sind möglicherweise nicht sequenziell.|  
|**sys. masked_columns** gibt viele weitere Spalten zurück, die von **sys. Columns**geerbt wurden.|Verschiedene|Weitere Spaltendefinitionen finden Sie unter [sys. Columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) .|  
|is_masked|**bit**|Gibt an, ob die Spalte maskiert ist. 1 weist auf maskiert hin.|  
|masking_function|**nvarchar(4000)**|Die Maskierungs Funktion für die Spalte.|  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht gibt Informationen zu Tabellen zurück, in denen der Benutzer über eine Berechtigung für die Tabelle verfügt, oder wenn der Benutzer über die VIEW ANY DEFINITION-Berechtigung verfügt.  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage verbindet **sys. masked_columns** mit **sys. Tables** , um Informationen zu allen maskierten Spalten zurückzugeben.  
  
```  
SELECT tbl.name as table_name, c.name AS column_name, c.is_masked, c.masking_function  
FROM sys.masked_columns AS c  
JOIN sys.tables AS tbl   
    ON c.object_id = tbl.object_id  
WHERE is_masked = 1;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [dynamische Datenmaskierung](../../relational-databases/security/dynamic-data-masking.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
