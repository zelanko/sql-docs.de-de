---
title: sp_table_privileges_ex (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_table_privileges_ex
- sp_table_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_table_privileges_ex
ms.assetid: b58d4a07-5c40-4f17-b66e-6d6b17188dda
author: stevestein
ms.author: sstein
ms.openlocfilehash: b40f7233bb3c50203a68c0b01cfcbdaf631e0098
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68096172"
---
# <a name="sp_table_privileges_ex-transact-sql"></a>sp_table_privileges_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Privileginformationen zu der angegebenen Tabelle vom angegebenen Verbindungsserver zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_table_privileges_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]  
     [ , [@fUsePattern =] 'fUsePattern']  
```  
  
## <a name="arguments"></a>Argumente  
`[ @table_server = ] 'table_server'`Der Name des Verbindungs Servers, für den Informationen zurückgegeben werden sollen. *table_server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @table_name = ] 'table_name']`Der Name der Tabelle, für die Tabellen Berechtigungsinformationen bereitgestellt werden sollen. *table_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @table_schema = ] 'table_schema'`Das Tabellen Schema. Dies ist in einigen DBMS-Umgebungen der Tabellenbesitzer. *TABLE_SCHEMA* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @table_catalog = ] 'table_catalog'`Der Name der Datenbank, in der sich die angegebene *table_name* befindet. *TABLE_CATALOG* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @fUsePattern = ] 'fUsePattern'`Bestimmt, ob die Zeichen "_", "%", "[" und "]" als Platzhalter Zeichen interpretiert werden. Gültige Werte sind 0 (Mustervergleich ist deaktiviert) und 1 (Mustervergleich ist aktiviert). *fUsePattern* ist vom Datentyp **bit**. Der Standardwert ist 1.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Tabellen qualifizierername. Verschiedene DBMS-Produkte unterstützen eine dreiteilige Benennung für Tabellen (_Qualifizierer_)**.** _Besitzer_**.** _Name_). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt diese Spalte den Datenbanknamen dar. Bei anderen Produkten stellt sie den Servernamen der Datenbankumgebung für die Tabelle dar. Dieses Feld kann den Wert NULL annehmen.|  
|**TABLE_SCHEM**|**sysname**|Der Name des Tabellen Besitzers. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]stellt diese Spalte den Namen des Daten Bank Benutzers dar, der die Tabelle erstellt hat. Dieses Feld gibt immer einen Wert zurück.|  
|**TABLE_NAME**|**sysname**|Tabellenname. Dieses Feld gibt immer einen Wert zurück.|  
|**GRANTOR**|**sysname**|Datenbank-Benutzername, der **dem aufgelisteten Empfänger**Berechtigungen für dieses **table_name** erteilt hat. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist diese Spalte immer identisch mit der **TABLE_OWNER**. Dieses Feld gibt immer einen Wert zurück. Außerdem kann die GRANTOR-Spalte entweder der Datenbankbesitzer (**TABLE_OWNER**) oder ein Benutzer sein, dem der Datenbankbesitzer mithilfe der WITH GRANT Option-Klausel in der GRANT-Anweisung die Berechtigung erteilt hat.|  
|**GRANTEE**|**sysname**|Datenbank-Benutzername, dem **vom aufgelisteten**Berechtigungs Element Berechtigungen für dieses **table_name** erteilt wurden. Dieses Feld gibt immer einen Wert zurück.|  
|**Ehre**|**varchar (** 32 **)**|Eine der verfügbaren Tabellenberechtigungen. Tabellenberechtigungen können folgende Werte annehmen bzw. auch andere Werte, die von der Datenquelle bei der Definition der Implementierung unterstützt werden.<br /><br /> Select = **GRANTEE** kann Daten für eine oder mehrere Spalten abrufen.<br /><br /> INSERT = **GRANTEE** kann für eine oder mehrere Spaltendaten für neue Zeilen bereitstellen.<br /><br /> Update = **GRANTEE** kann vorhandene Daten für eine oder mehrere Spalten ändern.<br /><br /> DELETE = **GRANTEE** kann Zeilen aus der Tabelle entfernen.<br /><br /> References = **GRANTEE** kann in einer Primärschlüssel-/Fremdschlüssel Beziehung auf eine Spalte in einer fremd Tabelle verweisen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden Primär-/Fremdschlüsselbeziehungen mithilfe von Tabelleneinschränkungen definiert.<br /><br /> Der **dem Empfänger durch ein** bestimmtes Tabellen Privileg erteilte Aktionsbereich ist Datenquellen abhängig. Beispielsweise **kann die Berechtigung** aktualisieren dem Empfänger ermöglichen, alle Spalten in einer Tabelle in einer Datenquelle zu aktualisieren, und nur die Spalten, für die der **GRANTOR** über die Berechtigung aktualisieren für eine andere Datenquelle verfügt.|  
|**IS_GRANTABLE**|**varchar (** 3 **)**|Gibt an, **ob der Empfänger** berechtigt ist, anderen Benutzern Berechtigungen zu erteilen. Dies wird häufig als "Berechtigung mit Recht zum Erteilen" bezeichnet. Dieses Feld kann die Werte YES, NO oder NULL annehmen. Ein unbekannter Wert oder NULL-Wert verweist auf eine Datenquelle, für die die "Berechtigung mit Recht zum Erteilen" nicht anwendbar ist.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die zurückgegebenen Ergebnisse werden nach **TABLE_QUALIFIER**, **TABLE_OWNER**, **table_name**und **Berechtigungen**geordnet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigung für das Schema.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel werden die Privileginformationen zu Tabellen zurückgegeben, deren Namen in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank des angegebenen Verbindungsservers `Product` mit `Seattle1` beginnen. ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird als Verbindungs Server angenommen).  
  
```  
EXEC sp_table_privileges_ex @table_server = 'Seattle1',   
   @table_name = 'Product%',   
   @table_schema = 'Production',  
   @table_catalog ='AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_column_privileges_ex &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-ex-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Prozeduren für verteilte Abfragen &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)  
  
  
