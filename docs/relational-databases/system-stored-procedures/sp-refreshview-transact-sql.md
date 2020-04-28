---
title: sp_refreshview (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_refreshview
- sp_refreshview_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_refreshview
ms.assetid: 9ce1d07c-ee66-4a83-8c73-cd2cc104dd08
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b8c1b95d8d04e2b11982af14971e43e83db146f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68075776"
---
# <a name="sp_refreshview-transact-sql"></a>sp_refreshview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aktualisiert die Metadaten für die angegebene nicht schemagebundene Sicht. Persistente Metadaten für eine Sicht sind möglicherweise aufgrund von Änderungen an den zugrunde liegenden Objekten, von denen die Sicht abhängt, nicht mehr aktuell.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_refreshview [ @viewname = ] 'viewname'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @viewname = ] 'viewname'`Der Name der Ansicht. *viewName ist vom Datentyp* **nvarchar**und hat keinen Standardwert. *viewName* kann ein mehrteilige Bezeichner sein, kann jedoch nur auf Sichten in der aktuellen Datenbank verweisen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Sicht nicht mit SCHEMABINDING erstellt wird, sollten **sp_refreshview** ausgeführt werden, wenn Änderungen an den Objekten vorgenommen werden, die der Sicht zugrunde liegen, die sich auf die Definition der Sicht auswirken. Andernfalls liefert die Abfrage der Sicht möglicherweise unerwartete Ergebnisse.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Sicht und die REFERENCES-Berechtigung für CLR-benutzerdefinierte (Common Language Runtime) Typen und XML-Schemaauflistungen, auf die durch die Sichtspalten verwiesen wird.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-updating-the-metadata-of-a-view"></a>A. Aktualisieren der Metadaten einer Sicht  
 Im folgenden Beispiel werden die Metadaten für die Sicht `Sales.vIndividualCustomer` aktualisiert.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sp_refreshview N'Sales.vIndividualCustomer';  
```  
  
### <a name="b-creating-a-script-that-updates-all-views-that-have-dependencies-on-a-changed-object"></a>B. Erstellen eines Skripts, das alle Sichten aktualisiert, die Abhängigkeiten von einem geänderten Objekt aufweisen  
 Angenommen, die `Person.Person`-Tabelle wurde auf eine Weise geändert, die sich auf die Definition von Sichten auswirkt, die für die Tabelle erstellt wurden. Im folgenden Beispiel wird ein Skript erstellt, das die Metadaten aller Sichten aktualisiert, die eine Abhängigkeit von der `Person.Person`-Tabelle aufweisen.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT DISTINCT 'EXEC sp_refreshview ''' + name + ''''   
FROM sys.objects AS so   
INNER JOIN sys.sql_expression_dependencies AS sed   
    ON so.object_id = sed.referencing_id   
WHERE so.type = 'V' AND sed.referenced_id = OBJECT_ID('Person.Person');  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [sp_refreshsqlmodule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-refreshsqlmodule-transact-sql.md)  
  
  
