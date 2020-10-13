---
description: sp_columns (Transact-SQL)
title: sp_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/17/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_columns_TSQL
- sp_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sp_columns
ms.assetid: 2dec79cf-2baf-4c0f-8cbb-afb1a8654e1e
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0c7a46f76385a724f1aa8622ac85301cdc7e12b6
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92006506"
---
# <a name="sp_columns-transact-sql"></a>sp_columns (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt Spalteninformationen für die angegebenen, in der aktuellen Umgebung abfragbaren Objekte zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
-- Syntax for SQL Server, Azure SQL Database, Azure Synapse Analytics, Parallel Data Warehouse  
  
sp_columns [ @table_name = ] object  
     [ , [ @table_owner = ] owner ]   
     [ , [ @table_qualifier = ] qualifier ]   
     [ , [ @column_name = ] column ]   
     [ , [ @ODBCVer = ] ODBCVer ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ \@table_name = ] object` Der Name des-Objekts, das verwendet wird, um Katalog Informationen zurückzugeben. bei dem *Objekt* kann es sich um eine Tabelle, eine Sicht oder ein anderes Objekt mit Spalten wie Tabellenwert Funktionen handeln. Das *Objekt* ist vom Datentyp **nvarchar (384)** und hat keinen Standardwert. Mustervergleiche mit Platzhalterzeichen werden unterstützt.  
  
`[ \@table_owner = ] owner` Der Objektbesitzer des-Objekts, das verwendet wird, um Katalog Informationen zurückzugeben. *Owner* ist vom Datentyp **nvarchar (384)** und hat den Standardwert NULL. Mustervergleiche mit Platzhalterzeichen werden unterstützt. Wenn *Owner* nicht angegeben wird, werden die Standardregeln für die Sichtbarkeit des Objekts des zugrunde liegenden DBMS angewendet.  
  
 Wenn der aktuelle Benutzer ein Objekt mit dem angegebenen Namen besitzt, werden die Spalten dieses Objekts zurückgegeben. Wenn *Owner* nicht angegeben wird und der aktuelle Benutzer kein Objekt mit dem angegebenen *Objekt*besitzt, sucht **sp_columns** nach einem Objekt mit dem angegebenen *Objekt* , das im Besitz des Daten Bank Besitzers ist. Sofern ein solches Objekt vorhanden ist, werden dessen Spalten zurückgegeben.  
  
`[ \@table_qualifier = ] qualifier` Der Name des Objekt Qualifizierers. *qualifier* ist vom Datentyp **sysname**und hat den Standardwert NULL. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Benennung für-Objekte (_Qualifizierer_)**.** _Besitzer_**.** _Name_). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Datenbanknamen dar. Bei einigen anderen Produkten stellt sie den Servernamen der Datenbankumgebung für das Objekt dar.  
  
`[ \@column_name = ] column` Bei handelt es sich um eine einzelne Spalte, die verwendet wird, wenn nur eine Spalte mit Katalog Informationen gewünscht wird. die Spalte ist vom *Datentyp* **nvarchar (384)** und hat den Standardwert NULL. Wenn *Column* nicht angegeben wird, werden alle Spalten zurückgegeben. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt *Column* den Spaltennamen dar, der in der **syscolumschlag** -Tabelle aufgelistet ist. Mustervergleiche mit Platzhalterzeichen werden unterstützt. Für eine optimale Interoperabilität sollte der Gatewayclient nur einen SQL-92-Standardmustervergleich voraussetzen (die Platzhalterzeichen % und _).  
  
`[ \@ODBCVer = ] ODBCVer` Die verwendete ODBC-Version. *ODBCVer* ist vom Datentyp **int**. der Standardwert ist 2. Dieser gibt ODBC, Version 2, an. Gültige Werte sind 2 oder 3. Informationen zu den Verhaltens unterschieden zwischen den Versionen 2 und 3 finden Sie in der **SQLColumns** -Spezifikation von ODBC.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
 Die gespeicherte Prozedur **sp_columns** Katalogs entspricht **SQLColumns** in ODBC. Die zurückgegebenen Ergebnisse werden nach **TABLE_QUALIFIER**, **TABLE_OWNER**und **table_name**geordnet.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|Objektqualifizierername. Dieses Feld kann den Wert NULL annehmen.|  
|**TABLE_OWNER**|**sysname**|Objektbesitzername. Dieses Feld gibt immer einen Wert zurück.|  
|**TABLE_NAME**|**sysname**|Objektname Dieses Feld gibt immer einen Wert zurück.|  
|**COLUMN_NAME**|**sysname**|Der Spaltenname für jede Spalte der zurückgegebenen **table_name** . Dieses Feld gibt immer einen Wert zurück.|  
|**DATA_TYPE**|**smallint**|Ganzzahliger Code für den ODBC-Datentyp. Wenn es sich um einen Datentyp handelt, der keinem ODBC-Typ zugeordnet werden kann, ist er NULL. Der Name des systemeigenen Datentyps wird in der **TYPE_NAME** Spalte zurückgegeben.|  
|**TYPE_NAME**|**sysname**|Die Zeichenfolge, die den Datentyp darstellt. Den Datentypnamen stellt das zugrunde liegende DBMS bereit.|  
|**PRECISION**|**int**|Die Anzahl von signifikanten Stellen. Der Rückgabewert für die **Genauigkeits** Spalte ist in Basis 10.|  
|**LENGTH**|**int**|Übertragungs Größe der Daten. <sup>1</sup>|  
|**Migen**|**smallint**|Die Anzahl der Ziffern rechts vom Dezimalzeichen|  
|**RADIX**|**smallint**|Die Basis für numerische Datentypen.|  
|**Werte zulässt**|**smallint**|Gibt die NULL-Zulässigkeit an.<br /><br /> 1 = NULL ist möglich<br /><br /> 0 = NOT NULL|  
|**HINWEISE**|**varchar (254)**|Dieses Feld gibt immer NULL zurück.|  
|**COLUMN_DEF**|**nvarchar(4000)**|Standardwert der Spalte|  
|**SQL_DATA_TYPE**|**smallint**|Der Wert des SQL-Datentyps, wie er im TYPE-Feld des Deskriptors angezeigt wird. Diese Spalte ist identisch mit der **data_type** Spalte, mit Ausnahme der Datentypen **DateTime** und SQL-92 **Interval** . Diese Spalte gibt immer einen Wert zurück.|  
|**SQL_DATETIME_SUB**|**smallint**|Untertyp Code für **DateTime** -und SQL-92 **Interval** -Datentypen. Bei allen anderen Datentypen gibt diese Spalte NULL zurück.|  
|**CHAR_OCTET_LENGTH**|**int**|Die maximale Länge (in Byte) einer Spalte eines Zeichendatentyps oder eines ganzzahligen Datentyps. Für alle anderen Datentypen gibt diese Spalte NULL zurück.|  
|**ORDINAL_POSITION**|**int**|Die Position einer Spalte innerhalb des Objekts. Die erste Spalte im Objekt hat den Wert 1. Diese Spalte gibt immer einen Wert zurück.|  
|**IS_NULLABLE**|**varchar (254)**|Die NULL-Zulässigkeit einer Spalte innerhalb des Objekts. Die NULL-Zulässigkeit wird gemäß den ISO-Regeln bestimmt. Ein DBMS nach ISO SQL kann keine leere Zeichenfolge zurückgeben.<br /><br /> YES = Spalte kann NULL-Werte enthalten.<br /><br /> NO = Spalte kann keine NULL-Werte enthalten.<br /><br /> Die Spalte gibt eine leere Zeichenfolge zurück, wenn die NULL-Zulässigkeit unbekannt ist.<br /><br /> Der für diese Spalte zurückgegebene Wert unterscheidet sich von dem Wert, der für die **Nullable** -Spalte zurückgegeben wird.|  
|**SS_DATA_TYPE**|**tinyint**|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp, der von erweiterten gespeicherten Prozeduren verwendet wird. Weitere Informationen finden Sie unter [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).|  
  
 <sup>1</sup> Weitere Informationen finden Sie in der Microsoft ODBC-Dokumentation.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-und View Definition-Berechtigungen für das Schema.  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_columns** befolgt die Anforderungen für Begrenzungs Bezeichner. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Spalteninformationen für die angegebene Tabelle zurückgegeben.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_columns @table_name = N'Department',  
   @table_owner = N'HumanResources';  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel werden die Spalteninformationen für die angegebene Tabelle zurückgegeben.  
  
```sql  
-- Uses AdventureWorks  
  
EXEC sp_columns @table_name = N'DimEmployee',  
   @table_owner = N'dbo';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_tables &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-tables-transact-sql.md)   
 [Gespeicherte Katalog Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  


