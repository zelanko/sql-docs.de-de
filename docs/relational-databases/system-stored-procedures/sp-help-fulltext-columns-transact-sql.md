---
title: Sp_help_fulltext_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_columns
- sp_help_fulltext_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_columns
ms.assetid: 92c8656b-f7fd-4904-9796-acc9ffed4106
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 622a0eafad0c4b029c0fd9512c25defa63229fc0
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169359"
---
# <a name="sphelpfulltextcolumns-transact-sql"></a>sp_help_fulltext_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Spalten zurück, die für die Volltextindizierung angegeben wurden.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden der [fulltext_index_columns](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md) stattdessen-Katalogsicht angezeigt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_fulltext_columns [ [ @table_name = ] 'table_name' ] ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@table_name=**] **"**_Tabelle\_Namen_**"**  
 Der aus einem oder zwei Teilen bestehende Name der Tabelle, für die Informationen zum Volltextindex angefordert werden. *table_name* ist vom Datentyp **nvarchar(517)**. Der Standardwert ist NULL. Wenn *table_name* ausgelassen wird, werden die Volltextindex-Spalteninformationen für jede volltextindizierte Tabelle abgerufen.  
  
 [  **@column_name=**] **"**_Spalte\_Namen_**"**  
 Der Name der Spalte, für die Informationen zum Volltextindex angefordert werden. *Column_name* ist **Sysname**, hat den Standardwert NULL. Wenn *column_name* ausgelassen wird oder den Wert NULL aufweist, werden die Volltextspalteninformationen für jede volltextindizierte Spalte für *table_name*zurückgegeben. Wenn *table_name* ebenfalls ausgelassen wird oder den Wert NULL aufweist, werden die Volltextindex-Spalteninformationen für jede volltextindizierte Spalte aller Tabellen in der Datenbank zurückgegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|Tabellenbesitzer. Der Name des Datenbankbenutzers, der die Tabelle erstellt hat.|  
|**TABLE_ID**|**int**|ID der Tabelle.|  
|**TABLE_NAME**|**sysname**|Der Name der Tabelle.|  
|**FULLTEXT_COLUMN_NAME**|**sysname**|Spalte in einer volltextindizierten Tabelle, die zum Indizieren angegeben ist.|  
|**FULLTEXT_COLID**|**int**|Spalten-ID der volltextindizierten Spalte.|  
|**FULLTEXT_BLOBTP_COLNAME**|**sysname**|Spalte in einer volltextindizierten Tabelle, die den Dokumenttyp der volltextindizierten Spalte angibt. Dieser Wert kann nur angewendet werden, wenn die volltextindizierte Spalte eine **varbinary(max)** - oder **image** -Spalte ist.|  
|**FULLTEXT_BLOBTP_COLID**|**int**|Die Spalten-ID der Dokumenttypspalte. Dieser Wert kann nur angewendet werden, wenn die volltextindizierte Spalte eine **varbinary(max)** - oder **image** -Spalte ist.|  
|**FULLTEXT_LANGUAGE**|**sysname**|Sprache, die für die Volltextsuche der Spalte verwendet wird.|  
  
## <a name="permissions"></a>Berechtigungen  
 Die Ausführungsberechtigungen werden standardmäßig der **public** -Rolle erteilt.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt Informationen zu den Spalten zurück, für die in der `Document`-Tabelle die Volltextindizierung angegeben wurde.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help_fulltext_columns 'Production.Document';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [COLUMNPROPERTY (Transact-SQL)](../../t-sql/functions/columnproperty-transact-sql.md)   
 [sp_fulltext_column &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-column-transact-sql.md)   
 [Sp_help_fulltext_columns_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-cursor-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
