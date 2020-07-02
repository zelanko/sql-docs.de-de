---
title: sp_depends (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_depends
- sp_depends_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_depends
ms.assetid: d9934590-c6ae-4936-91c3-146055ef2c57
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 396e370e7cb271c516033eb160332ac749a27aca
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787005"
---
# <a name="sp_depends-transact-sql"></a>sp_depends (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Zeigt Informationen zu den Abhängigkeiten von Datenbankobjekten an, z. B. die Sichten und Prozeduren, die von einer Tabelle oder Sicht abhängen, und die Tabellen und Sichten, die von der Sicht oder Prozedur abhängen. Verweise auf Objekte außerhalb der aktuellen Datenbank werden nicht angezeigt.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [sys. dm_sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md) und [sys. dm_sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_depends [ @objname = ] '<object>'   
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name.  
    object_name  
}  
```  
  
## <a name="arguments"></a>Argumente  
 *database_name*  
 Der Name der Datenbank.  
  
 *schema_name*  
 Der Name des Schemas, zu dem das Objekt gehört.  
  
 *object_name*  
 Das Datenbankobjekt, das auf Abhängigkeiten untersucht werden soll. Das Objekt kann eine Tabelle, eine Sicht, eine gespeicherte Prozedur, eine benutzerdefinierte Funktion oder ein Trigger sein. o*bject_name* ist vom Datentyp **nvarchar(776)** und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 **sp_depends** zeigt zwei Resultsets an.  
  
 Das folgende Resultset zeigt die Objekte an, *\<object>* von denen abhängt.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar (257** **)**|Der Name des Elements, für das eine Abhängigkeit vorhanden ist.|  
|**type**|**nvarchar (16)**|Der Elementtyp.|  
|**aktualisiert**|**nvarchar (7)**|Gibt an, ob das Element aktualisiert ist.|  
|**gewählte**|**nvarchar (8)**|Gibt an, ob das Element in einer SELECT-Anweisung verwendet wird.|  
|**column**|**sysname**|Spalte oder Parameter, für die bzw. den die Abhängigkeit vorhanden ist.|  
  
 Das folgende Resultset zeigt die Objekte an, die von abhängen *\<object>* .  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar (257** **)**|Der Name des Elements, für das eine Abhängigkeit vorhanden ist.|  
|**type**|**nvarchar (16)**|Der Elementtyp.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-dependencies-on-a-table"></a>A. Auflisten der Abhängigkeiten von einer Tabelle  
 Im folgenden Beispiel werden die Datenbankobjekte aufgelistet, die von der `Sales.Customer` -Tabelle in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank abhängen. Sowohl Schemaname als auch Tabellenname sind angegeben.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_depends @objname = N'Sales.Customer' ;  
```  
  
### <a name="b-listing-dependencies-on-a-trigger"></a>B. Auflisten der Abhängigkeiten für einen Trigger  
 Im folgenden Beispiel werden die Datenbankobjekte aufgelistet, von denen der `iWorkOrder` -Trigger abhängt.  
  
```  
EXEC sp_depends @objname = N'AdventureWorks2012.Production.iWorkOrder' ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys. sql_dependencies &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)  
  
  
