---
description: sp_pkeys (Transact-SQL)
title: sp_pkeys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_pkeys
- sp_pkeys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_pkeys
ms.assetid: e614c75d-847b-4726-8f6f-cd18de688eda
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ea021b39d01af931a989c55233a7f1cd8fa2cb82
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92004796"
---
# <a name="sp_pkeys-transact-sql"></a>sp_pkeys (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt Primärschlüsselinformationen für eine einzelne Tabelle in der aktuellen Umgebung zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
-- Syntax for SQL Server, Azure SQL Database, Azure Synapse Analytics, Parallel Data Warehouse  
  
sp_pkeys [ @table_name = ] 'name'       
    [ , [ @table_owner = ] 'owner' ]   
    [ , [ @table_qualifier = ] 'qualifier' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @table_name =] '*Name*'  
 Die Tabelle, für die Informationen zurückgegeben werden sollen. *Name ist vom Datentyp* **vom Datentyp sysname**und hat keinen Standardwert. Mustervergleiche mit Platzhalterzeichen werden nicht unterstützt.  
  
 [ @table_owner =] '*Besitzer*'  
 Gibt den Besitzer der angegebenen Tabelle an. *Owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Mustervergleiche mit Platzhalterzeichen werden nicht unterstützt. Wenn *Owner* nicht angegeben wird, werden die Standardregeln für die Tabellen Sichtbarkeit des zugrunde liegenden DBMS angewendet.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden die Spalten einer Tabelle zurückgegeben, wenn der aktuelle Benutzer diese Tabelle mit dem angegebenen Namen besitzt. Wenn der *Besitzer* nicht angegeben wird und der aktuelle Benutzer keine Tabelle mit dem angegebenen *Namen*besitzt, sucht diese Prozedur nach einer Tabelle mit dem angegebenen *Namen* , die im Besitz des Daten Bank Besitzers ist. Wenn eine solche Tabelle vorhanden ist, werden die Spalten dieser Tabelle zurückgegeben.  
  
 [ @table_qualifier =] '*Qualifizierer*'  
 Der Tabellenqualifizierer. *qualifier* ist vom Datentyp **sysname**und hat den Standardwert NULL. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Benennung für Tabellen (_Qualifizierer_)**.** _Besitzer_**.** _Name_). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Datenbanknamen dar. Bei einigen anderen Produkten stellt sie den Servernamen der Datenbankumgebung für die Tabelle dar.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|TABLE_QUALIFIER|**sysname**|Der Name des Tabellen Qualifizierers. Dieses Feld kann den Wert NULL annehmen.|  
|TABLE_OWNER|**sysname**|Der Name des Tabellen Besitzers. Dieses Feld gibt immer einen Wert zurück.|  
|table_name|**sysname**|Der Name der Tabelle. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Tabellennamen dar, der in der sysobjects-Tabelle angegeben ist. Dieses Feld gibt immer einen Wert zurück.|  
|COLUMN_NAME|**sysname**|Der Name der Spalte. Er wird für jede Spalte von TABLE_NAME zurückgegeben. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Spaltennamen dar, der in der sys.columns-Tabelle angegeben ist. Dieses Feld gibt immer einen Wert zurück.|  
|KEY_SEQ|**smallint**|Die Sequenznummer der Spalte in einem mehrspaltigen Primärschlüssel.|  
|PK_NAME|**sysname**|Der Primärschlüsselbezeichner. Gibt NULL zurück, wenn nicht auf die Datenquelle anwendbar|  
  
## <a name="remarks"></a>Bemerkungen  
 sp_pkeys gibt Informationen zu den Spalten zurück, die mit einer PRIMARY KEY-Einschränkung explizit definiert werden. Da nicht alle Systeme explizit benannte Primärschlüssel unterstützen, bestimmt die Gateway-Implementierung, was als Primärschlüssel gilt. Beachten Sie, dass sich der Begriff Primärschlüssel auf einen logischen Primärschlüssel für eine Tabelle bezieht. Es wird davon ausgegangen, dass für jeden als logischen Primärschlüssel aufgeführten Schlüssel ein eindeutiger Index definiert ist. Dieser eindeutige Index wird auch in sp_statistics zurückgegeben.  
  
 Die gespeicherte Prozedur sp_pkeys entspricht in ODBC SQLPrimaryKeys. Die zurückgegebenen Ergebnisse werden folgendermaßen sortiert: TABLE_QUALIFIER, TABLE_OWNER, TABLE_NAME und KEY_SEQ.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Primärschlüssel für die `HumanResources.Department`-Tabelle in der `AdventureWorks2012`-Datenbank abgerufen.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_pkeys @table_name = N'Department'  
    ,@table_owner = N'HumanResources';  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel wird der Primärschlüssel für die `DimAccount`-Tabelle in der `AdventureWorksPDW2012`-Datenbank abgerufen. Null Zeilen werden zurückgegeben, die angeben, dass die Tabelle keinen Primärschlüssel aufweist.  
  
```sql  
-- Uses AdventureWorks  
  
EXEC sp_pkeys @table_name = N'DimAccount';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Katalog Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

