---
title: Sp_unbindrule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_unbindrule_TSQL
- sp_unbindrule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unbindrule
ms.assetid: f54ee155-c3c9-4f1a-952e-632a8339f0cc
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d7a014b00a5fba5192e3bd9227f88968980dfd89
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028923"
---
# <a name="spunbindrule-transact-sql"></a>sp_unbindrule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Hebt die Bindung einer Regel an eine Spalte oder einen Aliasdatentyp in der aktuellen Datenbank auf.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Es wird empfohlen, dass Sie Default-Definitionen erstellen, mit dem DEFAULT-Schlüsselwort in der [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) oder [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) Anweisungen stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_unbindrule [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@objname=** ] **"***Object_name***"**  
 Der Name der Tabelle und der Spalte oder der Aliasdatentyp, für die bzw. den die Bindung der Regel aufgehoben wird. *Object_name* ist **nvarchar(776)**, hat keinen Standardwert. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versucht zuerst, zweiteilige Bezeichner für Spaltennamen aufzulösen, und versucht dann, zweiteilige Bezeichner für Aliasdatentypen aufzulösen. Beim Aufheben der Bindung einer Regel an einen Aliasdatentyp wird auch die Bindung für alle Spalten des betreffenden Datentyps, die dieselbe Regel aufweisen, aufgehoben. Spalten dieses Datentyps mit Regeln, die direkt an diese gebunden sind, sind nicht betroffen.  
  
> [!NOTE]  
>  *Object_name* können Klammern enthalten **[]** als begrenzungsbezeichnerzeichen. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md).  
  
 [ **@futureonly=** ] **'***futureonly_flag***'**  
 Wird nur beim Aufheben der Bindung einer Regel an einen Aliasdatentyp verwendet. *Futureonly_flag* ist **varchar(15)**, hat den Standardwert NULL. Wenn *Futureonly_flag* ist **Futureonly**, verlieren vorhandene Spalten dieses Datentyps nicht die angegebene Regel.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie sich den Text der Regel anzeigen lassen möchten, können Sie **sp_helptext** mit dem Regelnamen als Parameter ausführen.  
  
 Wenn eine Regel aufgehoben wird, wird die Informationen über die Bindung von entfernt die **sys.columns** Tabelle, wenn die Regel, auf eine Spalte, und von gebunden wurde der **sys.types** Tabelle, wenn die Regel an einen Aliasdatentyp gebunden wurde.  
  
 Beim Aufheben der Bindung einer Regel an einen Aliasdatentyp wird auch die Bindung an alle Spalten mit diesem Aliasdatentyp aufgehoben. Die Regel kann auch noch gebunden, Spalten, deren Datentypen später durch die ALTER COLUMN-Klausel einer ALTER TABLE-Anweisung geändert wurden, Sie müssen insbesondere die Bindung die Regel aus diesen Spalten aufheben, mithilfe **Sp_unbindrule** und Angeben der Name der Spalte.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Aufheben der Bindung einer Regel an eine Tabellenspalte ist die ALTER-Berechtigung für die Tabelle erforderlich. Zum Aufheben der Bindung einer Regel an einen Aliasdatentyp ist die CONTROL-Berechtigung für den Typ oder die ALTER-Berechtigung für das Schema erforderlich, zu dem der Typ gehört.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-unbinding-a-rule-from-a-column"></a>A. Aufheben der Bindung einer Regel an eine Spalte  
 Das folgende Beispiel hebt die Bindung der Regel an die `startdate`-Spalte einer `employees`-Tabelle auf.  
  
```  
EXEC sp_unbindrule 'employees.startdate';  
```  
  
### <a name="b-unbinding-a-rule-from-an-alias-data-type"></a>B. Aufheben der Bindung einer Regel an einen Aliasdatentyp  
 Das folgende Beispiel hebt die Bindung der Regel an den `ssn`-Aliasdatentyp auf. Die Bindungen der Regel an vorhandene und zukünftige Spalten dieses Typs werden aufgehoben.  
  
```  
EXEC sp_unbindrule ssn;  
```  
  
### <a name="c-using-futureonlyflag"></a>C. Verwenden von futureonly_flag  
 Das folgende Beispiel hebt die Bindung der Regel an den `ssn`-Aliasdatentyp auf, ohne dass vorhandene `ssn`-Spalten davon beeinflusst werden.  
  
```  
EXEC sp_unbindrule 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>D. Verwendung von begrenzungsbezeichnern  
 Das folgende Beispiel zeigt die Verwendung von begrenzungsbezeichnern in die *Object_name* Parameter.  
  
```  
CREATE TABLE [t.4] (c1 int); -- Notice the period as part of the table   
-- name.  
GO  
CREATE RULE rule2 AS @value > 100;  
GO  
EXEC sp_bindrule rule2, '[t.4].c1' -- The object contains two   
-- periods; the first is part of the table name and the second   
-- distinguishes the table name from the column name.  
GO  
EXEC sp_unbindrule '[t.4].c1';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [DROP RULE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-rule-transact-sql.md)   
 [sp_bindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
