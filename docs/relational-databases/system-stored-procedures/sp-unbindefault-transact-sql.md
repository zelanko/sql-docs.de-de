---
title: sp_unbindefault (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_unbindefault_TSQL
- sp_unbindefault
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unbindefault
ms.assetid: c96a6c5e-f3ca-4c1e-b64b-0d8ef6986af8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cc3e3af8e1b2333f68ea43fe9cacdfb4c3d39e40
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762776"
---
# <a name="sp_unbindefault-transact-sql"></a>sp_unbindefault (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Hebt die Bindung eines Standardwerts an eine Spalte oder einen Aliasdatentyp in der aktuellen Datenbank auf.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]Es wird empfohlen, stattdessen mithilfe des Default-Schlüssel Worts in den [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) -oder [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) -Anweisungen Standarddefinitionen zu erstellen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_unbindefault [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @objname = ] 'object_name'`Der Name der Tabelle und Spalte oder der Alias Datentyp, von dem aus der Standardwert für die Bindung aufgehoben wird. *object_name* ist vom Datentyp **nvarchar (776)** und hat keinen Standardwert. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versucht zuerst, zweiteilige Bezeichner für Spaltennamen aufzulösen, und versucht dann, zweiteilige Bezeichner für Aliasdatentypen aufzulösen.  
  
 Beim Aufheben der Bindung eines Standardwerts an einen Aliasdatentyp wird auch die Bindung für alle Spalten dieses Datentyps, die denselben Standardwert aufweisen, aufgehoben. Spalten dieses Datentyps mit Standardwerten, die direkt an diese gebunden sind, sind nicht betroffen.  
  
> [!NOTE]  
>  *object_name* können eckige Klammern **[]** als Begrenzungs Bezeichner enthalten. Weitere Informationen finden Sie unter [Datenbankbezeichner](../../relational-databases/databases/database-identifiers.md).  
  
`[ @futureonly = ] 'futureonly_flag'`Wird nur beim Aufheben der Bindung eines standardmäßigen von einem Alias Datentyp verwendet. *futureonly_flag* ist vom Datentyp **varchar (15)** und hat den Standardwert NULL. Wenn *futureonly_flag* **futureonly**ist, verlieren vorhandene Spalten des-Datentyps nicht den angegebenen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Um den Text eines Standard-anzuzeigen, führen Sie **sp_helptext** mit dem Namen des Standardwerts als Parameter aus.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Aufheben der Bindung eines Standardwerts an eine Tabellenspalte ist die ALTER-Berechtigung für die Tabelle erforderlich. Zum Aufheben der Bindung eines Standardwerts an einen Aliasdatentyp ist für den Datentyp die CONTROL-Berechtigung bzw. für das Schema, zu dem der Datentyp gehört, die ALTER-Berechtigung erforderlich.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-unbinding-a-default-from-a-column"></a>A. Aufheben der Bindung eines Standardwerts an eine Spalte  
 Im folgenden Beispiel wird die Bindung des an die `hiredate`-Spalte der `employees`-Tabelle gebundenen Standardwerts aufgehoben.  
  
```  
EXEC sp_unbindefault 'employees.hiredate';  
```  
  
### <a name="b-unbinding-a-default-from-an-alias-data-type"></a>B. Aufheben der Bindung eines Standardwerts an einen Aliasdatentyp  
 Im folgenden Beispiel wird die Bindung des an den `ssn`-Aliasdatentyp gebundenen Standardwerts aufgehoben. Die Bindungen aller vorhandenen und zukünftigen Spalten dieses Typs werden aufgehoben.  
  
```  
EXEC sp_unbindefault 'ssn';  
```  
  
### <a name="c-using-the-futureonly_flag"></a>C. Verwenden des futureonly_flag  
 Im folgenden Beispiel wird die Bindung zukünftiger Verwendungen des Aliasdatentyps `ssn` aufgehoben, ohne dass vorhandene `ssn`-Spalten davon betroffen sind.  
  
```  
EXEC sp_unbindefault 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>D: Verwenden von Begrenzungs Bezeichnerzeichen  
 Das folgende Beispiel zeigt die Verwendung von Begrenzungs bezeichnerbezeichern in *object_name* Parameter.  
  
```  
CREATE TABLE [t.3] (c1 int); -- Notice the period as part of the table   
-- name.  
CREATE DEFAULT default2 AS 0;  
GO  
EXEC sp_bindefault 'default2', '[t.3].c1' ;  
-- The object contains two periods;  
-- the first is part of the table name and the second   
-- distinguishes the table name from the column name.  
EXEC sp_unbindefault '[t.3].c1';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [Drop default &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-default-transact-sql.md)   
 [sp_bindefault &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
