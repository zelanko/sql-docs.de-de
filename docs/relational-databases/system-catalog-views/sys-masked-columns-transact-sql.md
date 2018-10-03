---
title: masked_columns (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e5e90fb00a74324cce6267e372199153707ca7ee
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47726108"
---
# <a name="sysmaskedcolumns-transact-sql"></a>masked_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Verwenden der **masked_columns** -Ansicht zum Abfragen von Tabellenspalten, die eine dynamische datenmaskierung-Funktion, die angewendet werden. Diese Ansicht erbt von der **sys.columns** -Ansicht. Sie gibt alle Spalten in der **sys.columns** -Ansicht sowie die Spalten **is_masked** und **masking_function** zurück, wobei angegeben wird, ob die Spalte maskiert ist. Ist dies der Fall, gibt die Ansicht die definierte Maskierungsfunktion an. Diese Ansicht zeigt nur die Spalten an, auf die eine Maskierungsfunktion angewendet wird.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Die ID des Objekts, zu dem diese Spalte gehört.|  
|NAME|**sysname**|Der Name der Spalte. Ist eindeutig innerhalb des Objekts.|  
|column_id|**int**|ID der Spalte. Ist eindeutig innerhalb des Objekts.<br /><br /> Spalten-IDs sind möglicherweise nicht sequenziell.|  
|**masked_columns** gibt viele weitere Spalten geerbt von **sys.columns**.|verschiedene|Finden Sie unter [sys.columns &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) für weitere Spaltendefinitionen.|  
|is_masked|**bit**|Gibt an, ob die Spalte maskiert ist. 1 gibt verdeckter Form an.|  
|masking_function|**nvarchar(4000)**|Die Maskierungsfunktion für die Spalte.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="permissions"></a>Berechtigungen  
 In dieser Ansicht werden Informationen zu Tabellen zurückgegeben, in denen der Benutzer eine Art der Berechtigung für die Tabelle verfügt, oder wenn der Benutzer die VIEW ANY DEFINITION-Berechtigung verfügt.  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage Joins **masked_columns** zu **sys.tables** zum Zurückgeben von Informationen zu allen maskiert Spalten.  
  
```  
SELECT tbl.name as table_name, c.name AS column_name, c.is_masked, c.masking_function  
FROM sys.masked_columns AS c  
JOIN sys.tables AS tbl   
    ON c.object_id = tbl.object_id  
WHERE is_masked = 1;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Datenmaskierung](../../relational-databases/security/dynamic-data-masking.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
