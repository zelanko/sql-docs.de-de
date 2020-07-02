---
title: sp_indexoption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_indexoption
- sp_indexoption_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_indexoption
ms.assetid: 75f836be-d322-4a53-a45d-25bee6b42a52
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2dc82e34234082013b1c590008ef610f1492f9a2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733069"
---
# <a name="sp_indexoption-transact-sql"></a>sp_indexoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Legt Werte für Sperrenoptionen für benutzerdefinierte gruppierte und nicht gruppierte Indizes oder Tabellen ohne gruppierten Index fest.  
  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] wählt automatisch zwischen Sperren auf Seitenebene, Zeilenebene und Tabellenebene aus. Sie müssen diese Optionen nicht manuell festlegen. **sp_indexoption** wird für erfahrene Benutzer bereitgestellt, die mit Sicherheit sicher sind, dass eine bestimmte Art von Sperre immer geeignet ist.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]Verwenden Sie stattdessen [Alter Index &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-index-transact-sql.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_indexoption [ @IndexNamePattern = ] 'table_or_index_name'   
    , [ @OptionName = ] 'option_name'   
    , [ @OptionValue = ] 'value'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @IndexNamePattern = ] 'table_or_index_name'`Der qualifizierte oder nicht qualifizierte Name einer benutzerdefinierten Tabelle oder eines benutzerdefinierten Indexes. *table_or_index_name* ist vom Datentyp **nvarchar (1035)** und hat keinen Standardwert. Anführungszeichen sind nur erforderlich, wenn ein qualifizierter Index- oder Tabellenname angegeben wird. Bei Angabe eines voll gekennzeichneten Tabellennamens (einschließlich eines Datenbanknamens) muss der Datenbankname der Name der aktuellen Datenbank sein. Wenn ein Tabellenname ohne Index angegeben wird, wird der angegebene Optionswert für alle Indizes dieser Tabelle und für die Tabelle selbst, falls kein gruppierter Index vorhanden ist, festgelegt.  
  
`[ @OptionName = ] 'option_name'`Ist ein Index Options Name. *option_name* ist vom Datentyp **varchar (35)** und hat keinen Standardwert. *option_name* kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**AllowRowLocks**|Mit TRUE sind Zeilensperren beim Zugriff auf den Index zulässig. Das [!INCLUDE[ssDE](../../includes/ssde-md.md)] bestimmt, wann Zeilensperren verwendet werden. Mit FALSE werden keine Zeilensperren verwendet. Der Standardwert ist TRUE.|  
|**AllowPageLocks**|Mit TRUE sind Seitensperren beim Zugriff auf den Index zulässig. Das [!INCLUDE[ssDE](../../includes/ssde-md.md)] bestimmt, wann Seitensperren verwendet werden. Mit FALSE werden keine Seitensperren verwendet. Der Standardwert ist TRUE.|  
|**DisAllowRowLocks**|Mit TRUE werden keine Zeilensperren verwendet. Mit FALSE sind Zeilensperren beim Zugriff auf den Index zulässig. Das [!INCLUDE[ssDE](../../includes/ssde-md.md)] bestimmt, wann Zeilensperren verwendet werden.|  
|**DisAllowPageLocks**|Mit TRUE werden keine Seitensperren verwendet. Mit FALSE sind Seitensperren beim Zugriff auf den Index zulässig. Das [!INCLUDE[ssDE](../../includes/ssde-md.md)] bestimmt, wann Seitensperren verwendet werden.|  
  
`[ @OptionValue = ] 'value'`Gibt an, ob die *option_name* Einstellung aktiviert ist (true, on, yes oder 1) oder deaktiviert (false, Off, No oder 0). der Wert ist vom Datentyp **varchar (12)** und hat keinen Standard *Wert* .  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder größer als 0 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 XML-Indizes werden nicht unterstützt. Wenn Sie einen XML-Index angeben oder einen Tabellennamen ohne Indexnamen angeben und die Tabelle einen XML-Index enthält, wird für die Anweisung ein Fehler gemeldet. Verwenden Sie stattdessen [Alter Index](../../t-sql/statements/alter-index-transact-sql.md) , um diese Optionen festzulegen.  
  
 Verwenden Sie [INDEXPROPERTY](../../t-sql/functions/indexproperty-transact-sql.md) oder die [sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) -Katalog Sicht, um die aktuellen Zeilen-und Seiten Sperr Eigenschaften anzuzeigen.  
  
-   Sperren auf Zeilen-, Seiten-und Tabellenebene sind beim Zugriff auf den Index zulässig, wenn **AllowRowLocks** = true oder **DisAllowRowLocks** = false und **AllowPageLocks** = true oder **DisAllowPageLocks** = false. Das [!INCLUDE[ssDE](../../includes/ssde-md.md)] wählt die geeignete Sperre aus und kann die Sperre von einer Zeilen- oder Seitensperre auf eine Tabellensperre ausweiten.  
  
 Beim Zugriff auf den Index ist nur eine Sperre auf Tabellenebene zulässig, wenn **AllowRowLocks** = false oder **DisAllowRowLocks** = true und **AllowPageLocks** = false oder **DisAllowPageLocks** = true ist.  
  
 Wenn ein Tabellenname ohne Index angegeben wird, werden die Einstellungen auf alle Indizes dieser Tabelle angewendet. Wenn die zugrunde liegende Tabelle keinen gruppierten Index aufweist (d. h., es handelt sich um einen Heap), werden die Einstellungen wie folgt angewendet:  
  
-   Wenn **AllowRowLocks** oder **DisAllowRowLocks** auf "true" oder "false" festgelegt ist, wird die Einstellung auf den Heap und alle zugehörigen nicht gruppierten Indizes angewendet.  
  
-   Wenn die Option **AllowPageLocks** auf true oder **DisAllowPageLocks** auf false festgelegt ist, wird die Einstellung auf den Heap und alle zugehörigen nicht gruppierten Indizes angewendet.  
  
-   Wenn die **AllowPageLocks** -Option auf false festgelegt ist oder **DisAllowPageLocks** auf true festgelegt ist, wird die Einstellung vollständig auf die nicht gruppierten Indizes angewendet. Das heißt, alle Seitensperren sind für die nicht gruppierten Indizes nicht zulässig. Auf dem Heap sind nur freigegebene Sperren (S), Updatesperren (U) und exklusive Sperren (X) für die Seite nicht zulässig. Das [!INCLUDE[ssDE](../../includes/ssde-md.md)] kann weiterhin eine beabsichtigte Seitensperre (IS, IU oder IX) für interne Zwecke abrufen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-setting-an-option-on-a-specific-index"></a>A. Festlegen einer Option auf einen bestimmten Index  
 Im folgenden Beispiel werden Seiten Sperren für den Index der-Tabelle nicht zugelassen `IX_Customer_TerritoryID` `Customer` .  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_indexoption N'Sales.Customer.IX_Customer_TerritoryID',  
    N'disallowpagelocks', TRUE;  
```  
  
### <a name="b-setting-an-option-on-all-indexes-on-a-table"></a>B. Festlegen einer Option auf alle Indizes in einer Tabelle  
 Im folgenden Beispiel werden Zeilensperren für alle Indizes der `Product`-Tabelle nicht zugelassen. Die `sys.indexes`-Katalogsicht wird vor und nach dem Ausführen der gespeicherten Prozedur `sp_indexoption` abgefragt, um die Ergebnisse der Anweisung anzuzeigen.  
  
```sql  
USE AdventureWorks2012;  
GO  
--Display the current row and page lock options for all indexes on the table.  
SELECT name, type_desc, allow_row_locks, allow_page_locks   
FROM sys.indexes  
WHERE object_id = OBJECT_ID(N'Production.Product');  
GO  
-- Set the disallowrowlocks option on the Product table.   
EXEC sp_indexoption N'Production.Product',  
    N'disallowrowlocks', TRUE;  
GO  
--Verify the row and page lock options for all indexes on the table.  
SELECT name, type_desc, allow_row_locks, allow_page_locks   
FROM sys.indexes  
WHERE object_id = OBJECT_ID(N'Production.Product');  
GO  
```  
  
### <a name="c-setting-an-option-on-a-table-with-no-clustered-index"></a>C. Festlegen einer Option für eine Tabelle ohne gruppierten Index  
 Im folgenden Beispiel werden Seitensperren für eine Tabelle ohne gruppierten Index (ein Heap) nicht zugelassen. Die `sys.indexes` -Katalog Sicht wird vor und nach dem Ausführen der `sp_indexoption` Prozedur abgefragt, um die Ergebnisse der Anweisung anzuzeigen.  
  
```sql  
USE AdventureWorks2012;  
GO  
--Display the current row and page lock options of the table.   
SELECT OBJECT_NAME (object_id) AS [Table], type_desc, allow_row_locks, allow_page_locks   
FROM sys.indexes  
WHERE OBJECT_NAME (object_id) = N'DatabaseLog';  
GO  
-- Set the disallowpagelocks option on the table.   
EXEC sp_indexoption DatabaseLog,  
    N'disallowpagelocks', TRUE;  
GO  
--Verify the row and page lock settings of the table.  
SELECT OBJECT_NAME (object_id) AS [Table], allow_row_locks, allow_page_locks   
FROM sys.indexes  
WHERE OBJECT_NAME (object_id) = N'DatabaseLog';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [INDEXPROPERTY &#40;Transact-SQL-&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
  
