---
description: sp_table_privileges (Transact-SQL)
title: sp_table_privileges (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_table_privileges
- sp_table_privileges_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_table_privileges
ms.assetid: 0512e688-4fc0-4557-8dc8-016672c1e3fe
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0ef4f8bb0971c0f594d07d3f8926a6a4cdae8991
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89549521"
---
# <a name="sp_table_privileges-transact-sql"></a>sp_table_privileges (Transact-SQL)

[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt eine Liste der Tabellenberechtigungen (beispielsweise INSERT, DELETE, UPDATE, SELECT, REFERENCES) für die angegebene Tabelle oder Tabellen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_table_privileges [ @table_name = ] 'table_name'     
     [ , [ @table_owner = ] 'table_owner' ]   
     [ , [ @table_qualifier = ] 'table_qualifier' ]   
     [ , [ @fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @table_name =] '*table_name*'  
 Die Tabelle zum Zurückgeben von Kataloginformationen. *table_name* ist vom Datentyp **nvarchar (** 384 **)** und hat keinen Standardwert. Mustervergleiche mit Platzhalterzeichen werden unterstützt.  
  
 [ @table_owner =] '*TABLE_OWNER*'  
 Der Tabellenbesitzer für die Tabelle zum Zurückgeben von Kataloginformationen. *TABLE_OWNER*ist vom Datentyp **nvarchar (** 384 **)** und hat den Standardwert NULL. Mustervergleiche mit Platzhalterzeichen werden unterstützt. Wenn der Besitzer nicht angegeben ist, werden die Standardregeln für die Sichtbarkeit von Tabellen des zugrunde liegenden DBMS angewendet.  
  
 Wenn der aktuelle Benutzer diese Tabelle mit dem angegebenen Namen besitzt, werden die Spalten einer Tabelle zurückgegeben. Wenn *Owner* nicht angegeben wird und der aktuelle Benutzer keine Tabelle mit dem angegebenen *Namen*besitzt, sucht diese Prozedur nach einer Tabelle mit dem angegebenen *table_name* , die dem Datenbankbesitzer gehört. Wenn eine solche Tabelle vorhanden ist, werden die Spalten dieser Tabelle zurückgegeben.  
  
 [ @table_qualifier =] '*TABLE_QUALIFIER*'  
 Der Name des Tabellenqualifizierers. *TABLE_QUALIFIER* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Benennung für Tabellen (*Qualifier.Owner.Name*). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Datenbanknamen dar. Bei anderen Produkten stellt sie den Servernamen der Datenbankumgebung für die Tabelle dar.  
  
 [ @fUsePattern =] '*fUsePattern*'  
 Bestimmt, ob die Zeichen Unterstrich (_), Prozentzeichen (%) und eckige Klammern ([oder]) als Platzhalter Zeichen interpretiert werden. Gültige Werte sind 0 (Mustervergleich ist deaktiviert) und 1 (Mustervergleich ist aktiviert). *fUsePattern* ist vom Datentyp **bit**. Der Standardwert ist 1.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|TABLE_QUALIFIER|**sysname**|Tabellen qualifizierername. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Datenbanknamen dar. Dieses Feld kann den Wert NULL annehmen.|  
|TABLE_OWNER|**sysname**|Der Name des Tabellen Besitzers. Dieses Feld gibt immer einen Wert zurück.|  
|table_name|**sysname**|Tabellenname. Dieses Feld gibt immer einen Wert zurück.|  
|GRANTOR|**sysname**|Der Datenbankbenutzername, der dem aufgelisteten GRANTEE Berechtigungen für TABLE_NAME erteilt hat. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist diese Spalte stets mit dem TABLE_OWNER identisch. Dieses Feld gibt immer einen Wert zurück. Zudem kann die GRANTOR-Spalte entweder der Datenbankbesitzer (TABLE_OWNER) oder ein Benutzer sein, dem der Datenbankbesitzer mithilfe der WITH GRANT OPTION-Klausel in der GRANT-Anweisung die Berechtigung erteilt hat.|  
|GRANTEE|**sysname**|Der Datenbank-Benutzername, dem vom aufgeführten GRANTOR Berechtigungen für TABLE_NAME erteilt wurden. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält diese Spalte immer einen Datenbankbenutzer aus der sys. database_principalssystem-Sicht. Dieses Feld gibt immer einen Wert zurück.|  
|PRIVILEGE|**sysname**|Eine der verfügbaren Tabellenberechtigungen. Tabellenberechtigungen können folgende Werte annehmen (bzw. auch andere Werte, die von der Datenquelle bei der Definition der Implementierung unterstützt werden):<br /><br /> SELECT = GRANTEE kann Daten aus einer oder mehreren Spalten abrufen.<br /><br /> INSERT = GRANTEE kann in einer oder mehreren Spalten Daten für neue Zeilen bereitstellen.<br /><br /> UPDATE = GRANTEE kann vorhandene Daten in einer oder mehreren Spalten ändern.<br /><br /> DELETE = GRANTEE kann Zeilen aus der Tabelle entfernen.<br /><br /> REFERENCES = der Berechtigte (GRANTEE) kann bei einer Primär-/Fremdschlüssel-Beziehung auf eine Spalte in einer Fremdschlüsseltabelle verweisen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden Primär-/Fremdschlüsselbeziehungen über Tabelleneinschränkungen definiert.<br /><br /> Der dem GRANTEE durch ein bestimmtes Tabellenprivileg erteilte Aktionsbereich ist datenquellenabhängig. Beispielsweise kann der GRANTEE mit dem UPDATE-Privileg alle Spalten in einer Tabelle für eine Datenquelle aktualisieren, während er für eine andere Datenquelle nur die Spalten aktualisieren kann, für die der GRANTOR das UPDATE-Privileg besitzt.|  
|IS_GRANTABLE|**sysname**|Zeigt an, ob der GRANTEE anderen Benutzern Berechtigungen erteilen darf (oft als "Berechtigung mit Recht zum Erteilen" bezeichnet). Dieses Feld kann die Werte YES, NO oder NULL annehmen. Ein unbekannter Wert (oder NULL-Wert) verweist auf eine Datenquelle, für die die "Berechtigung mit Recht zum Erteilen" nicht anwendbar ist.|  
  
## <a name="remarks"></a>Hinweise  
 Die gespeicherte Prozedur sp_table_privileges entspricht SQLTablePrivileges in ODBC. Die zurückgegebenen Ergebnisse sind nach TABLE_QUALIFIER, TABLE_OWNER, TABLE_NAME und PRIVILEGE sortiert.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Privileginformationen zu allen Tabellen zurückgegeben, deren Namen mit dem Wort `Contact` beginnen.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_table_privileges   
   @table_name = 'Contact%';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Katalog Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
