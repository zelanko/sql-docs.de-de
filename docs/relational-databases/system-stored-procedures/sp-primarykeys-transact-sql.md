---
title: sp_primarykeys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_primarykeys_TSQL
- sp_primarykeys
dev_langs:
- TSQL
helpviewer_keywords:
- sp_primarykeys
ms.assetid: 0f76dd31-5b7b-4209-9e2e-b9ed5cac164d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 05a1563188b5a8332c547901247ef43e07b1efa5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85646129"
---
# <a name="sp_primarykeys-transact-sql"></a>sp_primarykeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt für die angegebene Remotetabelle die Primärschlüsselspalten zurück, wobei pro Schlüsselspalte eine Zeile ausgegeben wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_primarykeys [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @table_server = ] 'table_server'_`Der Name des Verbindungs Servers, von dem Primärschlüssel Informationen zurückgegeben werden sollen. *table_server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @table_name = ] 'table_name'`Der Name der Tabelle, für die Primärschlüssel Informationen bereitgestellt werden sollen. *table_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @table_schema = ] 'table_schema'`Das Tabellen Schema. *TABLE_SCHEMA* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. In der Umgebung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entspricht dies dem Tabellenbesitzer.  
  
`[ @table_catalog = ] 'table_catalog'`Der Name des Katalogs, in dem sich der angegebene *table_name* befindet. In der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Umgebung entspricht dies dem Datenbanknamen. *TABLE_CATALOG* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Der Tabellenkatalog|  
|**TABLE_SCHEM**|**sysname**|Tabellenschema|  
|**TABLE_NAME**|**sysname**|Der Name der Tabelle.|  
|**COLUMN_NAME**|**sysname**|Name der Spalte.|  
|**KEY_SEQ**|**int**|Die Sequenznummer der Spalte in einem mehrspaltigen Primärschlüssel.|  
|**PK_NAME**|**sysname**|Der Primärschlüsselbezeichner. Gibt NULL zurück, wenn nicht auf die Datenquelle anwendbar|  
  
## <a name="remarks"></a>Hinweise  
 **sp_primarykeys** wird ausgeführt, indem das PRIMARY_KEYS Rowset der **IDBSchemaRowset** -Schnittstelle des OLE DB Anbieters abgefragt wird, der *table_server*entspricht. Die Parameter *table_name*, *TABLE_SCHEMA*, *TABLE_CATALOG*und *Column* werden an diese Schnittstelle übermittelt, um die zurückgegebenen Zeilen einzuschränken.  
  
 **sp_primarykeys** gibt ein leeres Resultset zurück, wenn der OLE DB Anbieter des angegebenen Verbindungs Servers das PRIMARY_KEYS-Rowset der **IDBSchemaRowset** -Schnittstelle nicht unterstützt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Primärschlüsselspalten vom Server `LONDON1` für die `HumanResources.JobCandidate`-Tabelle in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank zurückgegeben.  
  
```  
EXEC sp_primarykeys @table_server = N'LONDON1',   
   @table_name = N'JobCandidate',  
   @table_catalog = N'AdventureWorks2012',   
   @table_schema = N'HumanResources';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für verteilte Abfragen &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
