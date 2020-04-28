---
title: sp_indexes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_indexes_TSQL
- sp_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sp_indexes
ms.assetid: 25469e72-9d95-463f-912a-193471c8f5e2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 625b1b5bca3c76a0433e0b887d2c291a714c6f54
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68139917"
---
# <a name="sp_indexes-transact-sql"></a>sp_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Indexinformationen für die angegebene Remotetabelle zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_indexes [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_db' ]   
     [ , [ @index_name = ] 'index_name' ]   
     [ , [ @is_unique = ] 'is_unique' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @table_server= ] "*table_server*"  
 Der Name eines Verbindungsservers, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, und für den Tabelleninformationen angefordert werden. *table_server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
 [ @table_name= ] "*table_name*"  
 Der Name der Remotetabelle, für die Indexinformationen bereitzustellen sind. *table_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn der Wert NULL festgelegt ist, werden alle Tabellen in der angegebenen Datenbank zurückgegeben.  
  
 [ @table_schema= ] "*TABLE_SCHEMA*"  
 Gibt das Tabellenschema an. In der Umgebung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entspricht dies dem Tabellenbesitzer. *TABLE_SCHEMA* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
 [ @table_catalog= ] "*table_db*"  
 Der Name der Datenbank, in der sich *table_name* befindet. *table_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn der Wert NULL ist, *table_db* standardmäßig auf **Master**.  
  
 [ @index_name= ] "*index_name*"  
 Der Name des Indexes, für den Informationen angefordert werden. *Index* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
 [ @is_unique= ] "*is_unique*"  
 Der Typ des Indexes, für den Informationen zurückgegeben werden sollen. *is_unique* ist vom Typ **Bit**und hat den Standardwert NULL. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|1|Gibt Informationen zu eindeutigen Indizes zurück.|  
|0|Gibt Informationen zu Indizes zurück, die nicht eindeutig sind.|  
|NULL|Gibt Informationen zu allen Indizes zurück.|  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|TABLE_CAT|**sysname**|Der Name der Datenbank, in der die angegebene Tabelle gespeichert ist.|  
|TABLE_SCHEM|**sysname**|Das Schema für die Tabelle.|  
|table_name|**sysname**|Der Name der Remotetabelle.|  
|NON_UNIQUE|**smallint**|Gibt an, ob der Index eindeutig oder nicht eindeutig ist:<br /><br /> 0 = Eindeutig<br /><br /> 1 = Nicht eindeutig|  
|INDEX_QUALIFER|**sysname**|Der Name des Indexbesitzers. Verschiedene DBMS-Produkte ermöglichen neben dem Tabellenbesitzer auch anderen Benutzern das Erstellen von Indizes. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist diese Spalte immer identisch mit **table_name**.|  
|INDEX_NAME|**sysname**|Name des Indexes.|  
|TYPE|**smallint**|Typ des Index:<br /><br /> 0 = Statistiken für eine Tabelle<br /><br /> 1 = In einem Cluster gruppiert<br /><br /> 2 = Hash<br /><br /> 3 = Sonstige|  
|ORDINAL_POSITION|**int**|Ordinalposition der Spalte im Index. Die erste Spalte im Index hat den Wert 1. Diese Spalte gibt immer einen Wert zurück.|  
|COLUMN_NAME|**sysname**|Der Name der Spalte; wird für jede Spalte von TABLE_NAME zurückgegeben.|  
|ASC_OR_DESC|**varchar**|Die Sortierreihenfolge:<br /><br /> A = Aufsteigend<br /><br /> D = Absteigend<br /><br /> NULL = Nicht zutreffend<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt immer A zurück.|  
|CARDINALITY|**int**|Die Anzahl der Zeilen in der Tabelle oder der eindeutigen Werte im Index.|  
|PAGES|**int**|Die Anzahl der Seiten, die zum Speichern des Indexes oder der Tabelle benötigt werden.|  
|FILTER_CONDITION|**nvarchar (** 4000 **)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt keinen Wert zurück.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt alle Indexinformationen aus der Tabelle `Employees` der `AdventureWorks2012`-Datenbank auf dem Verbindungsserver `Seattle1` zurück.  
  
```  
EXEC sp_indexes @table_server = 'Seattle1',   
   @table_name = 'Employee',   
   @table_schema = 'HumanResources',  
   @table_catalog = 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für verteilte Abfragen &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
