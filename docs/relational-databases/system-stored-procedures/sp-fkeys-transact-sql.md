---
title: sp_fkeys (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fkeys
- sp_fkeys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fkeys
ms.assetid: 18110444-d38d-4cff-90d2-d1fc6236668b
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 18a4a5c25c791122191c07e5bb63a6fc6c32cba0
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180059"
---
# <a name="sp_fkeys-transact-sql"></a>sp_fkeys (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt logische Fremdschlüsselinformationen für die aktuelle Umgebung zurück. Diese Prozedur zeigt Fremdschlüsselbeziehungen an, wobei auch deaktivierte Fremdschlüssel berücksichtigt werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql  
sp_fkeys [ @pktable_name = ] 'pktable_name'   
     [ , [ @pktable_owner = ] 'pktable_owner' ]   
     [ , [ @pktable_qualifier = ] 'pktable_qualifier' ]   
     { , [ @fktable_name = ] 'fktable_name' }   
     [ , [ @fktable_owner = ] 'fktable_owner' ]   
     [ , [ @fktable_qualifier = ] 'fktable_qualifier' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @pktable_name =] '*pktable_name*'  
 Der Name der Tabelle mit dem Primärschlüssel, mit der Kataloginformationen zurückgegeben werden. *pktable_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Mustervergleiche mit Platzhalterzeichen werden nicht unterstützt. Dieser Parameter oder der *fktable_name* Parameter muss angegeben werden.  
  
 [ @pktable_owner =] '*pktable_owner*'  
 Der Name des Besitzers der Tabelle (mit dem Primärschlüssel), die verwendet wird, um Katalog Informationen zurückzugeben. *pktable_owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Mustervergleiche mit Platzhalterzeichen werden nicht unterstützt. Wenn *pktable_owner* nicht angegeben ist, werden die Standardregeln für die Tabellen Sichtbarkeit des zugrunde liegenden DBMS angewendet.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bedeutet dies: Wenn der aktuelle Benutzer eine Tabelle mit dem angegebenen Namen besitzt, werden die Spalten dieser Tabelle zurückgegeben. Wenn *pktable_owner* nicht angegeben wird und der aktuelle Benutzer keine Tabelle mit dem angegebenen *pktable_name*besitzt, sucht die Prozedur nach einer Tabelle mit der angegebenen *pktable_name* , die im Besitz des Daten Bank Besitzers ist. Sofern eine solche Tabelle vorhanden ist, werden die Spalten dieser Tabelle zurückgegeben.  
  
 [ @pktable_qualifier =] '*pktable_qualifier*'  
 Der Name des Qualifizierers der Tabelle (mit dem Primärschlüssel). *pktable_qualifier* ist vom Datentyp sysname und hat den Standardwert NULL. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Benennung für Tabellen (*Qualifier.Owner.Name*). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt der Qualifizierer den Datenbanknamen dar. Bei anderen Produkten stellt sie den Servernamen der Datenbankumgebung für die Tabelle dar.  
  
 [ @fktable_name =] '*fktable_name*'  
 Der Name der Tabelle (mit einem Fremdschlüssel), mit der Kataloginformationen zurückgegeben werden. *fktable_name* ist vom Datentyp sysname und hat den Standardwert NULL. Mustervergleiche mit Platzhalterzeichen werden nicht unterstützt. Dieser Parameter oder der *pktable_name* Parameter muss angegeben werden.  
  
 [ @fktable_owner =] '*fktable_owner*'  
 Der Name des Besitzers der Tabelle (mit einem Fremdschlüssel), mit der Kataloginformationen zurückgegeben werden. *fktable_owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Mustervergleiche mit Platzhalterzeichen werden nicht unterstützt. Wenn *fktable_owner* nicht angegeben ist, werden die Standardregeln für die Tabellen Sichtbarkeit des zugrunde liegenden DBMS angewendet.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bedeutet dies: Wenn der aktuelle Benutzer eine Tabelle mit dem angegebenen Namen besitzt, werden die Spalten dieser Tabelle zurückgegeben. Wenn *fktable_owner* nicht angegeben wird und der aktuelle Benutzer keine Tabelle mit dem angegebenen *fktable_name*besitzt, sucht die Prozedur nach einer Tabelle mit der angegebenen *fktable_name* , die im Besitz des Daten Bank Besitzers ist. Sofern eine solche Tabelle vorhanden ist, werden die Spalten dieser Tabelle zurückgegeben.  
  
 [ @fktable_qualifier =] '*FKTABLE_QUALIFIER*'  
 Der Name des Qualifizierers der Tabelle (mit einem Fremdschlüssel). *FKTABLE_QUALIFIER* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt der Qualifizierer den Datenbanknamen dar. Bei anderen Produkten stellt sie den Servernamen der Datenbankumgebung für die Tabelle dar.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keiner  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|PKTABLE_QUALIFIER|**sysname**|Der Name des Qualifizierers der Tabelle (mit dem Primärschlüssel). Dieses Feld kann den Wert NULL annehmen.|  
|PKTABLE_OWNER|**sysname**|Der Name des Besitzers der Tabelle (mit dem Primärschlüssel). Dieses Feld gibt immer einen Wert zurück.|  
|PKTABLE_NAME|**sysname**|Name der Tabelle (mit dem Primärschlüssel). Dieses Feld gibt immer einen Wert zurück.|  
|PKCOLUMN_NAME|**sysname**|Der Name der Primärschlüsselspalten für jede Spalte des zurückgegebenen TABLE_NAME-Werts. Dieses Feld gibt immer einen Wert zurück.|  
|FKTABLE_QUALIFIER|**sysname**|Der Name des Qualifizierers der Tabelle (mit einem Fremdschlüssel). Dieses Feld kann den Wert NULL annehmen.|  
|FKTABLE_OWNER|**sysname**|Der Name des Besitzers der Tabelle (mit einem Fremdschlüssel). Dieses Feld gibt immer einen Wert zurück.|  
|FKTABLE_NAME|**sysname**|Der Name der Tabelle (mit einem Fremdschlüssel). Dieses Feld gibt immer einen Wert zurück.|  
|FKCOLUMN_NAME|**sysname**|Der Name der Fremdschlüsselspalten für jede Spalte des zurückgegebenen TABLE_NAME-Werts. Dieses Feld gibt immer einen Wert zurück.|  
|KEY_SEQ|**smallint**|Die Sequenznummer der Spalte in einem mehrspaltigen Primärschlüssel. Dieses Feld gibt immer einen Wert zurück.|  
|UPDATE_RULE|**smallint**|Die Aktion, die für den Fremdschlüssel ausgeführt wird, wenn es sich bei dem SQL-Vorgang um ein Update handelt.  Mögliche Werte:<br /> 0=CASCADE; kaskadierende Änderungen am Fremdschlüssel.<br /> 1=NO ACTION; keine Änderungen, wenn der Fremdschlüssel vorhanden ist.<br />   2 = NULL festlegen <br /> 3 = Standard festlegen |  
|DELETE_RULE|**smallint**|Die Aktion, die für den Fremdschlüssel ausgeführt wird, wenn es sich bei dem SQL-Vorgang um eine Löschung handelt. Mögliche Werte:<br /> 0=CASCADE; kaskadierende Änderungen am Fremdschlüssel.<br /> 1=NO ACTION; keine Änderungen, wenn der Fremdschlüssel vorhanden ist.<br />   2 = NULL festlegen <br /> 3 = Standard festlegen |  
|FK_NAME|**sysname**|Der Fremdschlüsselbezeichner. Ist NULL, wenn er auf die Datenquelle nicht anwendbar ist. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt den Namen der FOREIGN KEY-Einschränkung zurück.|  
|PK_NAME|**sysname**|Der Primärschlüsselbezeichner. Ist NULL, wenn er auf die Datenquelle nicht anwendbar ist. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt den Namen der PRIMARY KEY-Einschränkung zurück.|  
  
 Die zurückgegebenen Informationen werden nach folgenden Spalten sortiert: FKTABLE_QUALIFIER, FKTABLE_OWNER, FKTABLE_NAME und KEY_SEQ.  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Anwendungscodierung, die Tabellen mit deaktivierten Fremdschlüsseln enthält, kann folgendermaßen implementiert werden:  
  
-   Deaktivieren Sie bei Verwendung der Tabellen vorübergehend die Überprüfung von Einschränkungen (ALTER TABLE NOCHECK oder CREATE TABLE NOT FOR REPLICATION), und aktivieren Sie sie später wieder.  
  
-   Erzwingen Sie Beziehungen mithilfe von Triggern oder Anwendungscode.  
  
Wenn für die Primärschlüsseltabelle ein Name, für die Fremdschlüsseltabelle jedoch NULL angegeben wurde, gibt sp_fkeys alle Tabellen mit einem Fremdschlüssel für die angegebene Tabelle zurück. Im umgekehrten Fall, d. h., wenn für die Fremdschlüsseltabelle ein Name, für die Primärschlüsseltabelle jedoch NULL angegeben wird, gibt sp_fkeys alle Tabellen zurück, die einen mit der Fremdschlüsseltabelle in Beziehung stehenden Primärschlüssel besitzen.  
  
Die gespeicherte Prozedur sp_fkeys entspricht SQLForeignKeys in ODBC.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert `SELECT` die-Berechtigung für das Schema.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Liste der Fremdschlüssel für die `HumanResources.Department`-Tabelle in der `AdventureWorks2012`-Datenbank abgerufen.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_fkeys @pktable_name = N'Department'  
    ,@pktable_owner = N'HumanResources';  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Im folgenden Beispiel wird eine Liste der Fremdschlüssel für die `DimDate`-Tabelle in der `AdventureWorksPDW2012`-Datenbank abgerufen. Es werden keine Zeilen zurückgegeben, da keine [!INCLUDE[ssDW](../../includes/ssdw-md.md)] Fremdschlüssel unterstützt.  
  
```sql  
EXEC sp_fkeys @pktable_name = N'DimDate;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Katalog Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_pkeys &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-pkeys-transact-sql.md)  
  
  

