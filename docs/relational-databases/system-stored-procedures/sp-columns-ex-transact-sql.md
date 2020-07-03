---
title: sp_columns_ex (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_columns_ex
- sp_columns_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_columns_ex
ms.assetid: c12ef6df-58c6-4391-bbbf-683ea874bd81
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 77608294b06025d5c265e67f71f9b0b228732729
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85871106"
---
# <a name="sp_columns_ex-transact-sql"></a>sp_columns_ex (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt die Spalteninformationen (eine Zeile pro Spalte) für die angegebenen Verbindungsservertabellen zurück. **sp_columns_ex** gibt Spalten Informationen nur für die jeweilige Spalte zurück, wenn *Column* angegeben wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_columns_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @column_name = ] 'column' ]   
     [ , [ @ODBCVer = ] 'ODBCVer' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @table_server = ] 'table_server'`Der Name des Verbindungs Servers, für den Spalten Informationen zurückgegeben werden sollen. *table_server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @table_name = ] 'table_name'`Der Name der Tabelle, für die Spalten Informationen zurückgegeben werden sollen. *table_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @table_schema = ] 'table_schema'`Der Schema Name der Tabelle, für die Spalten Informationen zurückgegeben werden sollen. *TABLE_SCHEMA* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @table_catalog = ] 'table_catalog'`Der Katalog Name der Tabelle, für die Spalten Informationen zurückgegeben werden sollen. *TABLE_CATALOG* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @column_name = ] 'column'`Der Name der Daten Bank Spalte, für die Informationen bereitgestellt werden sollen. *Column* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @ODBCVer = ] 'ODBCVer'`Die verwendete ODBC-Version. *ODBCVer* ist vom Datentyp **int**. der Standardwert ist 2. Dieser gibt ODBC, Version 2, an. Gültige Werte sind 2 oder 3. Informationen zu den Verhaltensunterschieden zwischen den Versionen 2 und 3 finden Sie in der SQLColumns-Spezifikation von ODBC.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Der Name des Qualifizierers für die Tabelle oder Sicht. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Benennung für Tabellen (_Qualifizierer_)**.** _Besitzer_**.** _Name_). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte dem Datenbanknamen dar. Bei anderen Produkten stellt sie den Servernamen der Datenbankumgebung für die Tabelle dar. Dieses Feld kann den Wert NULL annehmen.|  
|**TABLE_SCHEM**|**sysname**|Der Name des Besitzers der Tabelle oder Sicht. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Namen des Datenbankbenutzers dar, der die Tabelle erstellt hat. Dieses Feld gibt immer einen Wert zurück.|  
|**TABLE_NAME**|**sysname**|Der Name der Tabelle oder Sicht. Dieses Feld gibt immer einen Wert zurück.|  
|**COLUMN_NAME**|**sysname**|Der Spaltenname für jede Spalte der zurückgegebenen **table_name** . Dieses Feld gibt immer einen Wert zurück.|  
|**DATA_TYPE**|**smallint**|Ein Wert für eine ganze Zahl, der den ODBC-Datentypbezeichnern entspricht. Bei einem Datentyp, der keinem ODBC-Datentyp zugeordnet werden kann, wird der Wert NULL zurückgegeben. Der Name des systemeigenen Datentyps wird in der **TYPE_NAME** Spalte zurückgegeben.|  
|**TYPE_NAME**|**varchar (** 13 **)**|Die Zeichenfolge, die den Datentyp darstellt. Den Datentypnamen stellt das zugrunde liegende DBMS bereit.|  
|**COLUMN_SIZE**|**int**|Die Anzahl von signifikanten Stellen. Der Rückgabewert für die **Genauigkeits** Spalte ist in Basis 10.|  
|**BUFFER_LENGTH**|**int**|Die Übertragungsgröße der Daten.1|  
|**DECIMAL_DIGITS**|**smallint**|Die Anzahl der Ziffern rechts vom Dezimalzeichen|  
|**NUM_PREC_RADIX**|**smallint**|Ist die Basis für numerische Datentypen.|  
|**Werte zulässt**|**smallint**|Gibt die NULL-Zulässigkeit an.<br /><br /> 1 = NULL ist möglich<br /><br /> 0 = NOT NULL|  
|**HINWEISE**|**varchar (** 254 **)**|Dieses Feld gibt immer NULL zurück.|  
|**COLUMN_DEF**|**varchar (** 254 **)**|Standardwert der Spalte|  
|**SQL_DATA_TYPE**|**smallint**|Der Wert des SQL-Datentyps, wie er im TYPE-Feld des Deskriptors angezeigt wird. Diese Spalte ist identisch mit der **data_type** Spalte, mit Ausnahme der Datentypen **DateTime** und SQL-92 **Interval** . Diese Spalte gibt immer einen Wert zurück.|  
|**SQL_DATETIME_SUB**|**smallint**|Untertyp Code für **DateTime** -und SQL-92 **Interval** -Datentypen. Bei allen anderen Datentypen gibt diese Spalte NULL zurück.|  
|**CHAR_OCTET_LENGTH**|**int**|Die maximale Länge (in Byte) einer Spalte eines Zeichendatentyps oder eines ganzzahligen Datentyps. Für alle anderen Datentypen gibt diese Spalte NULL zurück.|  
|**ORDINAL_POSITION**|**int**|Die Position einer Spalte innerhalb der Tabelle. Die erste Spalte in der Tabelle ist "1". Diese Spalte gibt immer einen Wert zurück.|  
|**IS_NULLABLE**|**varchar (** 254 **)**|NULL-Zulässigkeit der Spalte in der Tabelle. Die NULL-Zulässigkeit wird gemäß den ISO-Regeln bestimmt. Ein DBMS nach ISO SQL kann keine leere Zeichenfolge zurückgeben.<br /><br /> YES = Spalte kann NULL-Werte enthalten.<br /><br /> NO = Spalte kann keine NULL-Werte enthalten.<br /><br /> Die Spalte gibt eine leere Zeichenfolge zurück, wenn die NULL-Zulässigkeit unbekannt ist.<br /><br /> Der für diese Spalte zurückgegebene Wert unterscheidet sich von dem Wert, der für die **Nullable** -Spalte zurückgegeben wird.|  
|**SS_DATA_TYPE**|**tinyint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp, der von erweiterten gespeicherten Prozeduren verwendet wird.|  
  
 Weitere Informationen finden Sie in der Microsoft ODBC-Dokumentation.  
  
## <a name="remarks"></a>Hinweise  
 **sp_columns_ex** wird ausgeführt, indem das COLUMNS-Rowset der **IDBSchemaRowset** -Schnittstelle des OLE DB Anbieters abgefragt wird, der *table_server*entspricht. Die Parameter *table_name*, *TABLE_SCHEMA*, *TABLE_CATALOG*und *Column* werden an diese Schnittstelle übermittelt, um die zurückgegebenen Zeilen einzuschränken.  
  
 **sp_columns_ex** gibt ein leeres Resultset zurück, wenn der OLE DB Anbieter des angegebenen Verbindungs Servers das COLUMNS-Rowset der **IDBSchemaRowset** -Schnittstelle nicht unterstützt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="remarks"></a>Hinweise  
 **sp_columns_ex** befolgt die Anforderungen für Begrenzungs Bezeichner. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Datentyp der `JobTitle`-Spalte der `HumanResources.Employee`-Tabelle in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank auf dem `Seattle1`-Verbindungsserver zurückgegeben.  
  
```  
EXEC sp_columns_ex 'Seattle1',   
   'Employee',   
   'HumanResources',   
   'AdventureWorks2012',   
   'JobTitle';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_catalogs &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_primarykeys &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
