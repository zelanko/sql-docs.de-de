---
title: Sp_help_fulltext_columns_cursor (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_columns_cursor
- sp_help_fulltext_columns_cursor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_columns_cursor
ms.assetid: 26054e76-53b7-4004-8d48-92ba3435e9d7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6d158c0703190e78209c9a9550040f9bc667b371
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65983056"
---
# <a name="sphelpfulltextcolumnscursor-transact-sql"></a>sp_help_fulltext_columns_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Verwendet einen Cursor, um eine Liste der Spalten zurückzugeben, die für die Volltextindizierung angegeben wurden.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden der [fulltext_index_columns](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md) stattdessen-Katalogsicht angezeigt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_fulltext_columns_cursor [ @cursor_return = ] @cursor_variable OUTPUT   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @cursor_return = ] @cursor_variable OUTPUT` Bezeichnet die Ausgabevariable vom Typ **Cursor**. Bei dem Cursor handelt es sich um einen schreibgeschützten, bildlauffähigen, dynamischen Cursor.  
  
`[ @table_name = ] 'table_name'` Ist der ein- oder zweiteilige Tabellenname, für die Volltextindex-Informationen angefordert werden. *table_name* ist vom Datentyp **nvarchar(517)**. Der Standardwert ist NULL. Wenn *table_name* ausgelassen wird, werden die Volltextindex-Spalteninformationen für jede volltextindizierte Tabelle abgerufen.  
  
`[ @column_name = ] 'column_name'` Ist der Name der Spalte für die Volltextindex-Metadaten erforderlich ist. *column_name* ist vom Datentyp **sysname** . Der Standardwert ist NULL. Wenn *column_name* ausgelassen wird oder den Wert NULL aufweist, werden die Volltextspalteninformationen für jede volltextindizierte Spalte für *table_name*zurückgegeben. Wenn *table_name* ebenfalls ausgelassen wird oder den Wert NULL aufweist, werden die Volltextindex-Spalteninformationen für jede volltextindizierte Spalte aller Tabellen in der Datenbank zurückgegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|Tabellenbesitzer. Der Name des Datenbankbenutzers, der die Tabelle erstellt hat.|  
|**TABLE_ID**|**int**|ID der Tabelle.|  
|**TABLE_NAME**|**sysname**|Tabellenname.|  
|**FULLTEXT_COLUMN_NAME**|**sysname**|Spalte in einer volltextindizierten Tabelle, die zum Indizieren angegeben ist.|  
|**FULLTEXT_COLID**|**int**|Spalten-ID der volltextindizierten Spalte.|  
|**FULLTEXT_BLOBTP_COLNAME**|**sysname**|Spalte in einer volltextindizierten Tabelle, die den Dokumenttyp der volltextindizierten Spalte angibt. Dieser Wert kann nur angewendet werden, wenn die volltextindizierte Spalte eine **varbinary(max)** - oder **image** -Spalte ist.|  
|**FULLTEXT_BLOBTP_COLID**|**int**|Die Spalten-ID der Dokumenttypspalte. Dieser Wert kann nur angewendet werden, wenn die volltextindizierte Spalte eine **varbinary(max)** - oder **image** -Spalte ist.|  
|**FULLTEXT_LANGUAGE**|**sysname**|Sprache, die für die Volltextsuche der Spalte verwendet wird.|  
  
## <a name="permissions"></a>Berechtigungen  
 Die Ausführungsberechtigungen werden standardmäßig der **public** -Rolle erteilt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zu den Spalten zurückgegeben, die in allen Tabellen der Datenbank für die Volltextindizierung angegeben wurden.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @mycursor CURSOR;  
EXEC sp_help_fulltext_columns_cursor @mycursor OUTPUT  
FETCH NEXT FROM @mycursor;  
WHILE (@@FETCH_STATUS <> -1)  
   BEGIN  
      FETCH NEXT FROM @mycursor;  
   END;  
CLOSE @mycursor;  
DEALLOCATE @mycursor;  
GO   
```  
  
## <a name="see-also"></a>Siehe auch  
 [COLUMNPROPERTY (Transact-SQL)](../../t-sql/functions/columnproperty-transact-sql.md)   
 [sp_fulltext_column &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-column-transact-sql.md)   
 [sp_help_fulltext_columns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
