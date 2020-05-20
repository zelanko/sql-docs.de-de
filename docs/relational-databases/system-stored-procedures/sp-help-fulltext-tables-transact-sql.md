---
title: sp_help_fulltext_tables (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_tables
- sp_help_fulltext_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_tables
ms.assetid: 86e24a5f-a869-43f6-b83e-c52b7b01b5ff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 30f43a2da32da7984aa4d84aaae259f1e85232fc
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827624"
---
# <a name="sp_help_fulltext_tables-transact-sql"></a>sp_help_fulltext_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Liste der Tabellen zurück, die für die Volltextindizierung registriert sind.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen die **sys. fulltext_indexes** -Katalog Sicht. Weitere Informationen finden Sie unter [sys. fulltext_indexes &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_fulltext_tables [ [ @fulltext_catalog_name = ] 'fulltext_catalog_name' ]   
     [ , [ @table_name = ] 'table_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @fulltext_catalog_name = ] 'fulltext_catalog_name'`Der Name des voll Text Katalogs. *fulltext_catalog_name* ist vom Datentyp **sysname**. Der Standardwert ist NULL. Wenn *fulltext_catalog_name* ausgelassen wird oder den Wert NULL hat, werden alle der Datenbank zugeordneten voll Text indizierten Tabellen zurückgegeben. Wenn *fulltext_catalog_name* angegeben wird, *table_name* aber weggelassen wird oder NULL ist, werden die Volltextindex Informationen für jede voll Text indizierte Tabelle abgerufen, die diesem Katalog zugeordnet ist. Wenn sowohl *fulltext_catalog_name* als auch *table_name* angegeben werden, wird eine Zeile zurückgegeben, wenn *table_name* *fulltext_catalog_name*zugeordnet ist. Andernfalls wird ein Fehler ausgelöst.  
  
`[ @table_name = ] 'table_name'`Der ein-oder zweiteilige Tabellenname, für den die voll Text Metadaten angefordert werden. *table_name* ist vom Datentyp **nvarchar(517)**. Der Standardwert ist NULL. Wenn nur *table_name* angegeben ist, wird nur die Zeile zurückgegeben, die für *table_name* relevant ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|Tabellenbesitzer. Der Name des Datenbankbenutzers, der die Tabelle erstellt hat.|  
|**TABLE_NAME**|**sysname**|Tabellenname.|  
|**FULLTEXT_KEY_INDEX_NAME**|**sysname**|Index, der die UNIQUE-Einschränkung auf die Spalte anwendet, die als die Spalte für den eindeutigen Schlüssel angegeben ist.|  
|**FULLTEXT_KEY_COLID**|**int**|Spalten-ID des durch FULLTEXT_KEY_NAME identifizierten eindeutigen Index.|  
|**FULLTEXT_INDEX_ACTIVE**|**int**|Gibt an, ob die für die Volltextindizierung markierten Spalten in dieser Tabelle bei Abfragen einbezogen werden sollen:<br /><br /> 0 = Inaktiv<br /><br /> 1 = Aktiv|  
|**FULLTEXT_CATALOG_NAME**|**sysname**|Volltextkatalog, in dem sich die Volltextindexdaten der Tabelle befinden.|  
  
## <a name="permissions"></a>Berechtigungen  
 Die Ausführungsberechtigungen werden standardmäßig der **public** -Rolle erteilt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Namen der volltextindizierten Tabellen zurückgegeben, die dem `Cat_Desc`-Volltextkatalog zugeordnet sind.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help_fulltext_tables 'Cat_Desc';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [INDEXPROPERTY &#40;Transact-SQL-&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL-&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_fulltext_table &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-table-transact-sql.md)   
 [sp_help_fulltext_tables_cursor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-cursor-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
