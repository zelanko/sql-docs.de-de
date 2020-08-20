---
description: sp_foreignkeys (Transact-SQL)
title: sp_foreignkeys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_foreignkeys_TSQL
- sp_foreignkeys
dev_langs:
- TSQL
helpviewer_keywords:
- sp_foreignkeys
ms.assetid: 935fe385-19ff-41a4-8d0b-30618966991d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8f7d3fe93965bcfcb516e79452b6725940c1e68c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481285"
---
# <a name="sp_foreignkeys-transact-sql"></a>sp_foreignkeys (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt die Fremdschlüssel zurück, die auf Primärschlüssel in der Tabelle auf dem Verbindungsserver verweisen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_foreignkeys [ @table_server = ] 'table_server'   
     [ , [ @pktab_name = ] 'pktab_name' ]   
     [ , [ @pktab_schema = ] 'pktab_schema' ]   
     [ , [ @pktab_catalog = ] 'pktab_catalog' ]   
     [ , [ @fktab_name = ] 'fktab_name' ]   
     [ , [ @fktab_schema = ] 'fktab_schema' ]   
     [ , [ @fktab_catalog = ] 'fktab_catalog' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @table_server = ] 'table_server'` Der Name des Verbindungs Servers, für den Tabellen Informationen zurückgegeben werden sollen. *table_server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @pktab_name = ] 'pktab_name'` Der Name der Tabelle mit einem Primärschlüssel. *pktab_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @pktab_schema = ] 'pktab_schema'` Der Name des Schemas mit einem Primärschlüssel. *pktab_schema*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält dies den Namen des Besitzers.  
  
`[ @pktab_catalog = ] 'pktab_catalog'` Der Name des Katalogs mit einem Primärschlüssel. *pktab_catalog*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält dies den Namen der Datenbank.  
  
`[ @fktab_name = ] 'fktab_name'` Der Name der Tabelle mit einem Fremdschlüssel. *fktab_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @fktab_schema = ] 'fktab_schema'` Der Name des Schemas mit einem Fremdschlüssel. *fktab_schema*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @fktab_catalog = ] 'fktab_catalog'` Der Name des Katalogs mit einem Fremdschlüssel. *fktab_catalog*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
 Verschiedene DBMS-Produkte unterstützen eine dreiteilige Benennung für Tabellen (_catalog_**.** _Schema_**.** _Tabelle_), die im Resultset dargestellt wird.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**PKTABLE_CAT**|**sysname**|Katalog für die Tabelle, in der sich der Primärschlüssel befindet|  
|**PKTABLE_SCHEM**|**sysname**|Schema für die Tabelle, in der sich der Primärschlüssel befindet|  
|**PKTABLE_NAME**|**sysname**|Name der Tabelle (mit dem Primärschlüssel). Dieses Feld gibt immer einen Wert zurück.|  
|**PKCOLUMN_NAME**|**sysname**|Der Name der Primärschlüssel Spalte oder-Spalten für jede Spalte des zurückgegebenen **table_name** . Dieses Feld gibt immer einen Wert zurück.|  
|**FKTABLE_CAT**|**sysname**|Katalog für die Tabelle, in der sich der Fremdschlüssel befindet|  
|**FKTABLE_SCHEM**|**sysname**|Schema für die Tabelle, in der sich der Fremdschlüssel befindet|  
|**FKTABLE_NAME**|**sysname**|Der Name der Tabelle (mit einem Fremdschlüssel). Dieses Feld gibt immer einen Wert zurück.|  
|**FKCOLUMN_NAME**|**sysname**|Name der Fremdschlüssel Spalten für jede Spalte des zurückgegebenen TABLE_NAME. Dieses Feld gibt immer einen Wert zurück.|  
|**KEY_SEQ**|**smallint**|Die Sequenznummer der Spalte in einem mehrspaltigen Primärschlüssel. Dieses Feld gibt immer einen Wert zurück.|  
|**UPDATE_RULE**|**smallint**|Die Aktion, die für den Fremdschlüssel ausgeführt wird, wenn es sich bei dem SQL-Vorgang um ein Update handelt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt 0, 1 oder 2 für diese Spalten zurück:<br /><br /> 0=CASCADE; kaskadierende Änderungen am Fremdschlüssel.<br /><br /> 1=NO ACTION; keine Änderungen, wenn der Fremdschlüssel vorhanden ist.<br /><br /> 2=SET_NULL; Fremdschlüssel auf NULL festlegen.|  
|**DELETE_RULE**|**smallint**|Die Aktion, die für den Fremdschlüssel ausgeführt wird, wenn es sich bei dem SQL-Vorgang um eine Löschung handelt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt 0, 1 oder 2 für diese Spalten zurück:<br /><br /> 0=CASCADE; kaskadierende Änderungen am Fremdschlüssel.<br /><br /> 1=NO ACTION; keine Änderungen, wenn der Fremdschlüssel vorhanden ist.<br /><br /> 2=SET_NULL; Fremdschlüssel auf NULL festlegen.|  
|**FK_NAME**|**sysname**|Der Fremdschlüsselbezeichner. Ist NULL, wenn er auf die Datenquelle nicht anwendbar ist. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt den Namen der FOREIGN KEY-Einschränkung zurück.|  
|**PK_NAME**|**sysname**|Der Primärschlüsselbezeichner. Ist NULL, wenn er auf die Datenquelle nicht anwendbar ist. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt den Namen der PRIMARY KEY-Einschränkung zurück.|  
|**DEFERRABILITY**|**smallint**|Gibt an, ob die Einschränkungsüberprüfung verzögert werden kann.|  
  
 Im Resultset geben die Spalten FK_NAME und PK_NAME immer NULL zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_foreignkeys** fragt das FOREIGN_KEYS Rowset der **IDBSchemaRowset** -Schnittstelle des OLE DB Anbieters ab, der *table_server*entspricht. Die Parameter *table_name*, *TABLE_SCHEMA*, *TABLE_CATALOG*und *Column* werden an diese Schnittstelle übermittelt, um die zurückgegebenen Zeilen einzuschränken.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt Fremdschlüsselinformationen zur `Department`-Tabelle in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank auf dem Verbindungsserver `Seattle1` zurück.  
  
```  
EXEC sp_foreignkeys @table_server = N'Seattle1',   
   @pktab_name = N'Department',   
   @pktab_catalog = N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_catalogs &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_primarykeys &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
