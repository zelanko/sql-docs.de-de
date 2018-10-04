---
title: Sp_column_privileges_ex (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_column_privileges_ex
- sp_column_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_column_privileges_ex
ms.assetid: 98cb6e58-4007-40fc-b048-449fb2e7e6be
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f9f86f83637cbf71dd128dd262ad1621b2d58270
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47658650"
---
# <a name="spcolumnprivilegesex-transact-sql"></a>sp_column_privileges_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Spaltenprivileginformationen für die angegebene Tabelle auf dem angegebenen Verbindungsserver zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_column_privileges_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@table_server =** ] **"***Table_server***"**  
 Der Name des Verbindungsservers, für den Informationen zurückgegeben werden sollen. *Table_server* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@table_name =** ] **"***Table_name***"**  
 Der Name der Tabelle, die die angegebene Spalte enthält. *TABLE_NAME* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@table_schema =** ] **"***Table_schema***"**  
 Das Tabellenschema. *TABLE_SCHEMA* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@table_catalog =** ] **"***Table_catalog***"**  
 Der Name der Datenbank, in der angegebenen *Table_name* befindet. *TABLE_CATALOG* ist **Sysname**, hat den Standardwert NULL.  
  
 [  **@column_name =** ] **"***Column_name***"**  
 Der Name der Spalte, für die Privilegieninformationen bereitgestellt werden sollen. *Column_name* ist **Sysname**, hat den Standardwert NULL (alle häufigen Spalten).  
  
## <a name="result-sets"></a>Resultsets  
 In der folgenden Tabelle sind die Resultsetspalten aufgeführt. Die zurückgegebenen Ergebnisse sind sortiert nach **TABLE_QUALIFIER**, **TABLE_OWNER**, **TABLE_NAME**, **COLUMN_NAME**, und  **Berechtigung**.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Name des Qualifizierers Tabelle. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Namensgebung für Tabellen (*Qualifizierer ***.*** Besitzer ***.*** Namen*). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Datenbanknamen dar. Bei anderen Produkten stellt sie den Servernamen der Datenbankumgebung für die Tabelle dar. Dieses Feld kann den Wert NULL annehmen.|  
|**NACH "TABLE_SCHEM"**|**sysname**|Name des Tabellenbesitzers. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], diese Spalte dar, den Namen des Datenbankbenutzers, der die Tabelle erstellt hat. Dieses Feld gibt immer einen Wert zurück.|  
|**TABLE_NAME**|**sysname**|Tabellenname. Dieses Feld gibt immer einen Wert zurück.|  
|**COLUMN_NAME**|**sysname**|Name der Spalte für jede Spalte von der **TABLE_NAME** zurückgegeben. Dieses Feld gibt immer einen Wert zurück.|  
|**BERECHTIGENDE (GRANTOR)**|**sysname**|Datenbank-Benutzername, der Berechtigungen für erteilt hat **COLUMN_NAME** aufgeführten **Empfänger**. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], diese Spalte ist immer identisch mit der **TABLE_OWNER**. Dieses Feld gibt immer einen Wert zurück.<br /><br /> Die **GRANTOR** Spalte kann entweder der Datenbankbesitzer sein (**TABLE_OWNER**) oder ein Benutzer, denen die vom Datenbankbesitzer erteilt wurden Berechtigungen mithilfe der WITH GRANT OPTION-Klausel in der GRANT-Anweisung.|  
|**EMPFÄNGER**|**sysname**|Datenbank-Benutzername, dem Berechtigungen für erteilt wurden **COLUMN_NAME** aufgeführte **GRANTOR**. Dieses Feld gibt immer einen Wert zurück.|  
|**BERECHTIGUNGEN**|**Varchar (** 32 **)**|Eine der verfügbaren Spaltenberechtigungen. Spaltenberechtigungen können folgende Werte annehmen (oder auch andere Werte, die von der Datenquelle bei der Definition der Implementierung unterstützt werden):<br /><br /> Wählen Sie = **Empfänger** kann Daten für die Spalten abrufen.<br /><br /> INSERT = **Empfänger** können Daten für diese Spalten bereitstellen, wenn neue Zeilen eingefügt werden (durch die **Empfänger**) in die Tabelle.<br /><br /> UPDATE = **Empfänger** kann vorhandene Daten in der Spalte ändern.<br /><br /> REFERENCES = **Empfänger** können auf eine Spalte in einer Fremdschlüsseltabelle in einer Primärschlüssel/Fremdschlüssel-Beziehung verweisen. Primär-/Fremdschlüssel-Beziehungen werden über Tabelleneinschränkungen definiert.|  
|**IS_GRANTABLE**|**Varchar (** 3 **)**|Gibt an, ob die **Empfänger** ist zulässig, erteilen Sie Berechtigungen für andere Benutzer (häufig als "Berechtigung mit Recht zum Erteilen" bezeichnet). Dieses Feld kann die Werte YES, NO oder NULL annehmen. Ein unbekannter Wert oder NULL-Wert verweist darauf, dass für die entsprechende Datenquelle die "Berechtigung mit Recht zum Erteilen" nicht zutreffend ist.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Spaltenprivileginformationen für die `HumanResources.Department`-Tabelle in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank auf dem Verbindungsserver `Seattle1` zurückgegeben.  
  
```  
EXEC sp_column_privileges_ex @table_server = 'Seattle1',   
   @table_name = 'Department',   
   @table_schema = 'HumanResources',  
   @table_catalog ='AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_table_privileges_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-ex-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
