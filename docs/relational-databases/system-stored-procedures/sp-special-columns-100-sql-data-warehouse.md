---
description: sp_special_columns_100 (SQL Data Warehouse)
title: sp_special_columns_100 (SQL Data Warehouse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.subservice: design
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5774fadc-77cc-46f8-8f9f-a0f9efe95e21
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 002524d834b8036c353b096b0a4fa1fa37875b4e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473793"
---
# <a name="sp_special_columns_100-sql-data-warehouse"></a>sp_special_columns_100 (SQL Data Warehouse)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Gibt die optimale Gruppe von Spalten zurück, die eine Zeile in der Tabelle eindeutig identifizieren. Außerdem werden Spalten zurückgegeben, die automatisch aktualisiert werden, wenn ein Wert in der Zeile durch eine Transaktion aktualisiert wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_special_columns_100 [ @table_name = ] 'table_name'     
     [ , [ @table_owner = ] 'table_owner' ]   
     [ , [ @qualifier = ] 'qualifier' ]   
     [ , [ @col_type = ] 'col_type' ]   
     [ , [ @scope = ] 'scope' ]  
     [ , [ @nullable = ] 'nullable' ]   
     [ , [ @ODBCVer = ] 'ODBCVer' ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @table_name =] '*table_name*'  
 Der Name der Tabelle zur Rückgabe von Kataloginformationen. *Name ist vom Datentyp* **vom Datentyp sysname**und hat keinen Standardwert. Mustervergleiche mit Platzhalterzeichen werden nicht unterstützt.  
  
 [ @table_owner =] '*TABLE_OWNER*'  
 Der Tabellenbesitzer für die Tabelle zum Zurückgeben von Kataloginformationen. *Owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Mustervergleiche mit Platzhalterzeichen werden nicht unterstützt. Wenn *Owner* nicht angegeben wird, werden die Standardregeln für die Tabellen Sichtbarkeit des zugrunde liegenden DBMS angewendet.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden die Spalten einer Tabelle zurückgegeben, wenn der aktuelle Benutzer diese Tabelle mit dem angegebenen Namen besitzt. Wenn *Owner* nicht angegeben wird und der aktuelle Benutzer keine Tabelle mit dem angegebenen *Namen*besitzt, wird nach einer Tabelle mit dem angegebenen *Namen* gesucht, die im Besitz des Daten Bank Besitzers ist. Wenn die Tabelle vorhanden ist, werden die zugehörigen Spalten zurückgegeben.  
  
 [ @qualifier =] '*Qualifizierer*'  
 Der Name des Tabellenqualifizierers. *qualifier* ist vom Datentyp **sysname**und hat den Standardwert NULL. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Benennung für Tabellen (*Qualifier.Owner.Name*). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Datenbanknamen dar. Bei einigen anderen Produkten stellt sie den Servernamen der Datenbankumgebung für die Tabelle dar.  
  
 [ @col_type =] '*col_type*'  
 Der Spaltentyp. *col_type* ist vom Datentyp **char (** 1 **)**. der Standardwert ist R. Type R gibt die optimale Spalte oder Gruppe von Spalten zurück, die durch Abrufen von Werten aus der Spalte oder den Spalten eine eindeutige Identifizierung der Zeilen in der angegebenen Tabelle ermöglicht. Bei einer Spalte kann es sich entweder um eine Pseudospalte handeln, die speziell zu diesem Zweck erstellt wurde, oder um die Spalte(n) eines eindeutigen Index für die Tabelle. Der Typ "V" gibt ggf. die Spalte(n) in der angegebenen Tabelle zurück, die automatisch von der Datenquelle aktualisiert werden, sobald ein Wert in der Zeile durch eine Transaktion aktualisiert wird.  
  
 [ @scope =] '*Bereich*'  
 Der mindestens erforderliche Bereich der ROWID. *Scope* ist vom Typ **char (** 1 **)** und hat den Standardwert T. der Bereich C gibt an, dass die ROWID nur gültig ist, wenn Sie in dieser Zeile positioniert ist. Der Bereich "T" gibt an, dass die ROWID für die Transaktion gültig ist.  
  
 [ @nullable =] '*Werte zulässt*'  
 Gibt an, ob die speziellen Spalten einen NULL-Wert akzeptieren können. *null* -Werte sind vom Typ **char (** 1 **)**. der Standardwert ist U. O gibt spezielle Spalten an, die keine NULL-Werte zulassen. "U" definiert Spalten, die teilweise NULL zulassen.  
  
 [ @ODBCVer =] '*ODBCVer*'  
 Die verwendete ODBC-Version. *ODBCVer* ist vom Datentyp **int (** 4 **)** und hat den Standardwert 2. Dieser gibt ODBC, Version 2.0, an. Weitere Informationen zu den Unterschieden zwischen ODBC, Version 2.0, und ODBC, Version 3.0, finden Sie in der SQLSpecialColumns-ODBC-Spezifikation für ODBC, Version 3.0.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|SCOPE|**smallint**|Der Bereich der Zeilen-ID. Kann 0, 1 oder 2 sein. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt immer 0 zurück. Dieses Feld gibt immer einen Wert zurück.<br /><br /> 0 = SQL_SCOPE_CURROW. Die Zeilen-ID ist nur garantiert gültig, wenn sie sich in dieser Zeile befindet. Eine spätere erneute Auswahl mit dieser Zeilen-ID gibt möglicherweise keine Zeile zurück, wenn die Zeile durch eine andere Transaktion aktualisiert oder gelöscht wurde.<br /><br /> 1 = SQL_SCOPE_TRANSACTION. Die Zeilen-ID ist für die Dauer der aktuellen Transaktion garantiert gültig.<br /><br /> 2 = SQL_SCOPE_SESSION. Die Zeilen-ID ist für die Dauer der Sitzung garantiert gültig (über Transaktionsgrenzen hinweg).|  
|COLUMN_NAME|**sysname**|Der Spaltenname für jede Spalte der zurückgegebenen *Tabelle*. Dieses Feld gibt immer einen Wert zurück.|  
|DATA_TYPE|**smallint**|ODBC-SQL-Datentyp.|  
|TYPE_NAME|**sysname**|Datenquellen abhängiger Datentyp Name; beispielsweise " **char**", " **varchar**", " **Money**" oder " **Text**".|  
|PRECISION|**Int**|Die Genauigkeit der Spalte bezüglich der Datenquelle. Dieses Feld gibt immer einen Wert zurück.|  
|LENGTH|**Int**|Die Länge in Bytes, die für den Datentyp in der Binär Form in der Datenquelle erforderlich ist, z. b. 10 für **char (** 10 **)**, 4 für **Integer**und 2 für **smallint**.|  
|SCALE|**smallint**|Die Dezimalstellen der Spalte bezüglich der Datenquelle. NULL wird für Datentypen zurückgegeben, auf die Dezimalstellen nicht anwendbar sind.|  
|PSEUDO_COLUMN|**smallint**|Gibt an, ob es sich bei der Spalte um eine Pseudospalte handelt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt immer 1 zurück:<br /><br /> 0 = SQL_PC_UNKNOWN<br /><br /> 1 = SQL_PC_NOT_PSEUDO<br /><br /> 2 = SQL_PC_PSEUDO|  
  
## <a name="remarks"></a>Bemerkungen  
 sp_special_columns entspricht SQLSpecialColumns in ODBC. Die zurückgegebenen Ergebnisse sind nach der SCOPE-Spalte geordnet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel werden Informationen zu der Spalte zurückgegeben, die Zeilen in der `FactFinance`-Tabelle eindeutig identifiziert.  
  
```sql  
-- Uses AdventureWorks  
  
EXEC sp_special_columns_100 @table_name = 'FactFinance';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren SQL Data Warehouse](../../relational-databases/system-stored-procedures/sql-data-warehouse-stored-procedures.md)  
  
  

