---
title: sp_fulltext_column (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_column_TSQL
- sp_fulltext_column
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_column
ms.assetid: a84cc45d-1b50-44af-85df-2ea033b8a6a9
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9e17a87a04c8c4286a66c6e7a0746f2d7de48d72
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124342"
---
# <a name="sp_fulltext_column-transact-sql"></a>sp_fulltext_column (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Gibt an, ob eine bestimmte Spalte einer Tabelle bei der Volltextindizierung berücksichtigt werden soll.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [ALTER FULLTEXT Index](../../t-sql/statements/alter-fulltext-index-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_fulltext_column [ @tabname= ] 'qualified_table_name' ,   
     [ @colname= ] 'column_name' ,   
     [ @action= ] 'action'   
     [ , [ @language= ] 'language_term' ]   
     [ , [ @type_colname= ] 'type_column_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @tabname = ] 'qualified_table_name'`Ein ein-oder zweiteilige Tabellenname. Die Tabelle muss in der aktuellen Datenbank vorhanden sein. Die Tabelle muss über einen Volltextindex verfügen. *qualified_table_name* ist vom Datentyp **nvarchar (517)** und hat keinen Standardwert.  
  
`[ @colname = ] 'column_name'`Der Name einer Spalte in *qualified_table_name*. Die Spalte muss eine Zeichen-, eine **varbinary(max)** - oder eine **image** -Spalte sein und darf keine berechnete Spalte sein. *column_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kann Volltextindizes von Textdaten erstellen, die in Spalten mit dem **varbinary (max)** -oder **Image** -Datentyp gespeichert sind. Bilder und Abbildungen werden nicht indiziert.  
  
`[ @action = ] 'action'`Die auszuführende Aktion. *Action* ist vom Datentyp **varchar (20)** und hat keinen Standardwert. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**eren**|Fügt dem inaktiven Volltextindex der Tabelle den *column_name* von *qualified_table_name* hinzu. Durch diese Aktion wird die Volltextindizierung für die Spalte aktiviert.|  
|**Dropdown**|Entfernt *column_name* aus dem inaktiven Volltextindex von *qualified_table_name* .|  
  
`[ @language = ] 'language_term'`Die Sprache der in der Spalte gespeicherten Daten. Eine Liste der Sprachen, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]enthalten sind, finden Sie unter [sys. fulltext_languages &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).  
  
> [!NOTE]  
>  Verwenden Sie 'Neutral', wenn eine Spalte Daten in mehreren Sprachen oder in einer nicht unterstützten Sprache enthält. Die Standardsprache wird mithilfe der Konfigurationsoption 'default full-text language' angegeben.  
  
`[ @type_colname = ] 'type_column_name'`Der Name einer Spalte in *qualified_table_name* , die den Dokumenttyp *column_name*enthält. Diese Spalte muss vom Typ **char**, **nchar**, **varchar**oder **nvarchar**sein. Wird nur verwendet, wenn der Datentyp von *column_name***varbinary(max)** oder **image**ist. *type_column_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der Volltextindex aktiv ist, wird ggf. das derzeit ausgeführte Auffüllen beendet. Wenn für eine Tabelle mit einem aktiven Volltextindex die Änderungsnachverfolgung aktiviert ist, stellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] außerdem sicher, dass der Index aktuell ist. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beendet z. B. das aktuelle Auffüllen der Tabelle, löscht den vorhandenen Index und startet einen neuen Auffüllvorgang.  
  
 Wenn die Änderungsprotokollierung aktiviert ist und Spalten zum Volltextindex hinzugefügt oder aus ihm gelöscht werden sollen, wobei der Index beibehalten werden soll, sollte die Tabelle deaktiviert und dann die erforderlichen Spalten hinzugefügt oder gelöscht werden. Bei diesen Aktionen wird der Index eingefroren. Die Tabelle kann später wieder aktiviert werden, wenn das Auffüllen gestartet werden soll.  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer muss ein Mitglied der festen Datenbankrolle **db_ddladmin** oder ein Mitglied der festen Datenbankrolle **db_owner** bzw. der Besitzer der Tabelle sein.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die `DocumentSummary` -Spalte aus der `Document` -Tabelle dem Volltextindex der Tabelle hinzugefügt.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_column 'Production.Document', DocumentSummary, 'add';  
GO  
```  
  
 Im folgenden Beispiel wird vorausgesetzt, dass Sie einen Volltextindex für die `spanishTbl`-Tabelle erstellt haben. Sie können die `spanishCol` -Spalte dem Volltextindex hinzufügen, indem Sie die folgende gespeicherte Prozedur ausführen:  
  
```  
EXEC sp_fulltext_column 'spanishTbl', 'spanishCol', 'add', 0xC0A;  
GO  
```  
  
 Beim Ausführen der Abfrage:  
  
```  
SELECT *   
FROM spanishTbl   
WHERE CONTAINS(spanishCol, 'formsof(inflectional, trabajar)')  
```  
  
 Das Resultset würde auch Zeilen mit anderen Formen von `trabajar` (arbeiten) einschließen, z. B. `trabajo`, `trabajamos`und `trabajan`.  
  
> [!NOTE]  
>  Alle Spalten, die in einer einzelnen Funktionsklausel für eine Volltextabfrage aufgelistet sind, müssen dieselbe Sprache verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OBJECTPROPERTY &#40;Transact-SQL-&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_help_fulltext_columns &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-transact-sql.md)   
 [sp_help_fulltext_columns_cursor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-cursor-transact-sql.md)   
 [sp_help_fulltext_tables &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-transact-sql.md)   
 [sp_help_fulltext_tables_cursor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-cursor-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Prozeduren für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
