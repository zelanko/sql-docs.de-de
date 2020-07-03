---
title: sp_tables_ex (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tables_ex
- sp_tables_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables_ex
ms.assetid: 33755c33-7e1e-4ef7-af14-a9cebb1e2ed4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3e986d5d998864a343eab31e238a8f7df56a5d0c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892624"
---
# <a name="sp_tables_ex-transact-sql"></a>sp_tables_ex (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Tabelleninformationen zu den Tabellen auf dem angegebenen Verbindungsserver zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_tables_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]  
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @table_type = ] 'table_type' ]   
     [ , [@fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @table_server = ] 'table_server'`Der Name des Verbindungs Servers, für den Tabellen Informationen zurückgegeben werden sollen. *table_server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
``[ , [ @table_name = ] 'table_name']``Der Name der Tabelle, für die Datentyp Informationen zurückgegeben werden sollen. *table_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @table_schema = ] 'table_schema']`Das Tabellen Schema. *TABLE_SCHEMA*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @table_catalog = ] 'table_catalog'`Der Name der Datenbank, in der sich die angegebene *table_name* befindet. *TABLE_CATALOG* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @table_type = ] 'table_type'`Der Typ der zurück zugebende Tabelle. *TABLE_TYPE* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL und kann einen der folgenden Werte aufweisen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Alias**|Der Name eines Alias|  
|**GLOBAL TEMPORARY**|Der Name einer systemweit verfügbaren temporären Tabelle|  
|**LOCAL TEMPORARY**|Der Name einer nur für den aktuellen Auftrag verfügbaren temporären Tabelle|  
|**Synonym**|Der Name eines Synonyms|  
|**System Tabelle**|Der Name einer Systemtabelle|  
|**System Ansicht**|Der Name einer Systemsicht|  
|**Glaub**|Der Name einer Benutzertabelle|  
|**Anschauung**|Der Name einer Sicht|  
  
`[ @fUsePattern = ] 'fUsePattern'`Bestimmt, ob die Zeichen **_**, **%** , **[** und **]** als Platzhalter Zeichen interpretiert werden. Gültige Werte sind 0 (Mustervergleich ist deaktiviert) und 1 (Mustervergleich ist aktiviert). *fUsePattern* ist vom Datentyp **bit**. Der Standardwert ist 1.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Tabellen qualifizierername. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Benennung für Tabellen (_Qualifizierer_)**.** _Besitzer_**.** _Name_). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Datenbanknamen dar. In einigen anderen Produkten stellt Sie den Servernamen der Datenbankumgebung der Tabelle dar. Dieses Feld kann den Wert NULL annehmen.|  
|**TABLE_SCHEM**|**sysname**|Der Name des Tabellen Besitzers. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Namen des Daten Bank Benutzers dar, der die Tabelle erstellt hat. Dieses Feld gibt immer einen Wert zurück.|  
|**TABLE_NAME**|**sysname**|Tabellenname. Dieses Feld gibt immer einen Wert zurück.|  
|**TABLE_TYPE**|**varchar(32)**|Tabelle, Systemtabelle oder Sicht.|  
|**HINWEISE**|**varchar (254)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt für diese Spalte keinen Wert zurück.|  
  
## <a name="remarks"></a>Hinweise  
 **sp_tables_ex** wird ausgeführt, indem das TABLES-Rowset der **IDBSchemaRowset** -Schnittstelle des OLE DB Anbieters abgefragt wird, der *table_server*entspricht. Die Parameter *table_name*, *TABLE_SCHEMA*, *TABLE_CATALOG*und *Column* werden an diese Schnittstelle übermittelt, um die zurückgegebenen Zeilen einzuschränken.  
  
 **sp_tables_ex** gibt ein leeres Resultset zurück, wenn der OLE DB Anbieter des angegebenen Verbindungs Servers das TABLES-Rowset der **IDBSchemaRowset** -Schnittstelle nicht unterstützt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zu den Tabellen zurückgegeben, die sich im `HumanResources`-Schema in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank auf dem verknüpften Server `LONDON2` befinden.  
  
```  
EXEC sp_tables_ex @table_server = 'LONDON2',   
@table_catalog = 'AdventureWorks2012',   
@table_schema = 'HumanResources',   
@table_type = 'TABLE';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für verteilte Abfragen &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_columns_ex &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
