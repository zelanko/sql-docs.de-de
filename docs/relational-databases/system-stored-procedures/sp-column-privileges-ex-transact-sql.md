---
title: sp_column_privileges_ex (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 46abd2a21441cdf911cecb9b21f02451400258f3
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823987"
---
# <a name="sp_column_privileges_ex-transact-sql"></a>sp_column_privileges_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Spaltenprivileginformationen für die angegebene Tabelle auf dem angegebenen Verbindungsserver zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_column_privileges_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @table_server = ] 'table_server'`Der Name des Verbindungs Servers, für den Informationen zurückgegeben werden sollen. *table_server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @table_name = ] 'table_name'`Der Name der Tabelle, die die angegebene Spalte enthält. *table_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @table_schema = ] 'table_schema'`Das Tabellen Schema. *TABLE_SCHEMA* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @table_catalog = ] 'table_catalog'`Der Name der Datenbank, in der sich die angegebene *table_name* befindet. *TABLE_CATALOG* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @column_name = ] 'column_name'`Der Name der Spalte, für die Berechtigungsinformationen bereitgestellt werden sollen. *column_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL (All Common).  
  
## <a name="result-sets"></a>Resultsets  
 In der folgenden Tabelle sind die Resultsetspalten aufgeführt. Die zurückgegebenen Ergebnisse werden nach **TABLE_QUALIFIER**, **TABLE_OWNER**, **table_name**, **column_name**und **Berechtigungen**geordnet.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Tabellen qualifizierername. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Benennung für Tabellen (_Qualifizierer_)**.** _Besitzer_**.** _Name_). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Datenbanknamen dar. Bei anderen Produkten stellt sie den Servernamen der Datenbankumgebung für die Tabelle dar. Dieses Feld kann den Wert NULL annehmen.|  
|**TABLE_SCHEM**|**sysname**|Der Name des Tabellen Besitzers. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Namen des Daten Bank Benutzers dar, der die Tabelle erstellt hat. Dieses Feld gibt immer einen Wert zurück.|  
|**TABLE_NAME**|**sysname**|Tabellenname. Dieses Feld gibt immer einen Wert zurück.|  
|**COLUMN_NAME**|**sysname**|Der Spaltenname für jede Spalte der zurückgegebenen **table_name** . Dieses Feld gibt immer einen Wert zurück.|  
|**GRANTOR**|**sysname**|Datenbankbenutzer Name, der **dem aufgelisteten Empfänger**Berechtigungen für dieses **column_name** erteilt hat. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist diese Spalte immer identisch mit der **TABLE_OWNER**. Dieses Feld gibt immer einen Wert zurück.<br /><br /> Die **GRANTOR** -Spalte kann entweder der Datenbankbesitzer (**TABLE_OWNER**) oder ein anderer Benutzer sein, dem der Datenbankbesitzer mithilfe der WITH GRANT Option-Klausel in der GRANT-Anweisung Berechtigungen erteilt hat.|  
|**GRANTEE**|**sysname**|Der Name der Datenbank, der von **dem aufgelisteten**Berechtigungs-column_name Berechtigungen für dieses **COLUMN_NAME** erteilt wurden. Dieses Feld gibt immer einen Wert zurück.|  
|**Ehre**|**varchar (** 32 **)**|Eine der verfügbaren Spaltenberechtigungen. Spaltenberechtigungen können folgende Werte annehmen (oder auch andere Werte, die von der Datenquelle bei der Definition der Implementierung unterstützt werden):<br /><br /> Select = **GRANTEE** kann Daten für die Spalten abrufen.<br /><br /> INSERT = **GRANTEE** kann Daten für diese Spalte bereitstellen, wenn neue Zeilen (vom Empfänger **) in**die Tabelle eingefügt werden.<br /><br /> Update = **GRANTEE** kann vorhandene Daten in der Spalte ändern.<br /><br /> References = **GRANTEE** kann in einer Primärschlüssel-/Fremdschlüssel Beziehung auf eine Spalte in einer fremd Tabelle verweisen. Primär-/Fremdschlüssel-Beziehungen werden über Tabelleneinschränkungen definiert.|  
|**IS_GRANTABLE**|**varchar (** 3 **)**|Gibt an, **ob der Empfänger** berechtigt ist, anderen Benutzern Berechtigungen zu erteilen (häufig als "Grant with Grant"-Berechtigung bezeichnet). Dieses Feld kann die Werte YES, NO oder NULL annehmen. Ein unbekannter Wert oder NULL-Wert verweist darauf, dass für die entsprechende Datenquelle die "Berechtigung mit Recht zum Erteilen" nicht zutreffend ist.|  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_table_privileges_ex &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-ex-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
