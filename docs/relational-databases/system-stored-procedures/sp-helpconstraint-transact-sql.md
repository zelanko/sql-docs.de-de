---
description: sp_helpconstraint (Transact-SQL)
title: sp_helpconstraint (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpconstraint
- sp_helpconstraint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpconstraint
ms.assetid: 29d6cd36-535d-4765-bca8-62f9d9886ff5
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7199b56a0bf0c0eb397a061ca366534bdbf9c6ee
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97404181"
---
# <a name="sp_helpconstraint-transact-sql"></a>sp_helpconstraint (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Gibt eine Liste aller Einschränkungstypen zurück, deren benutzerdefinierte oder vom System angegebenen Namen, die Spalten, für die sie definiert wurden, und den Ausdruck, der die Einschränkung definiert (nur bei DEFAULT- und CHECK-Einschränkungen).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpconstraint [ @objname = ] 'table'   
     [ , [ @nomsg = ] 'no_message' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @objname = ] 'table'` Die Tabelle, zu der Einschränkungs Informationen zurückgegeben werden. Die angegebene Tabelle muss für die aktuelle Datenbank lokal sein. *Table ist vom Datentyp* **nvarchar (776)** und hat keinen Standardwert.  
  
`[ @nomsg = ] 'no_message'` Ist ein optionaler Parameter, der den Tabellennamen ausgibt. *no_message* ist vom Datentyp **varchar (5)** und hat den Standardwert **msg**. **nomsg** unterdrückt den Druckvorgang.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 **sp_helpconstraint** zeigt eine absteigende indizierte Spalte an, wenn Sie an Primär Schlüsseln beteiligt ist. Die absteigend indizierte Spalte wird im Resultset mit einem Minuszeichen (-) hinter dem Namen aufgelistet. Standardmäßig werden Spalten aufsteigend indiziert, diese werden nur mit dem Namen aufgelistet.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie **sp_help**_Tabelle_ ausführen, werden alle Informationen über die angegebene Tabelle gemeldet. Verwenden Sie **sp_helpconstraint**, um nur die Einschränkungs Informationen anzuzeigen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt alle Einschränkungen für die Tabelle `Product` an.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helpconstraint 'Production.Product';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.key_constraints &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [sys.check_constraints &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)   
 [sys.default_constraints &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md)  
  
  
