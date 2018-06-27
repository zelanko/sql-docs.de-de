---
title: ERROR_LINE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ERROR_LINE
- ERROR_LINE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], line number
- messages [SQL Server], line number
- TRY...CATCH [SQL Server]
- line number of error [SQL Server]
- ERROR_LINE function
- CATCH block
ms.assetid: 47335734-0baf-45a6-8b3b-6c4fd80d2cb8
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 347233585a00c73d006fa0115fb703d57fc16ca2
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2018
ms.locfileid: "35249663"
---
# <a name="errorline-transact-sql"></a>ERROR_LINE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion gibt die Zeilennummer des Fehlers zurück, der die Ausführung des CATCH-Blocks eines TRY…CATCH-Konstrukts ausgelöst hat.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
ERROR_LINE ( )  
```  
  
## <a name="return-type"></a>Rückgabetyp  
**int**  
  
## <a name="return-value"></a>Rückgabewert  
Wenn die Funktion in einem CATCH-Block aufgerufen wird, gibt `ERROR_LINE`  
  
-   die Nummer der Zeile zurück, in der der Fehler aufgetreten ist    
-   die Zeilennummer in einer Routine zurück, wenn der Fehler in einer gespeicherten Prozedur oder einem Trigger aufgetreten ist  
-   NULL zurück, wenn sie außerhalb des Bereichs eines CATCH-Blocks aufgerufen wurde.  
  
## <a name="remarks"></a>Remarks  
Ein Aufruf von `ERROR_LINE` kann überall im Bereich eines CATCH-Blocks auftreten.  
  
`ERROR_LINE` gibt die Nummer der Zeile zurück, in der der Fehler aufgetreten ist. Dies geschieht unabhängig davon, wo `ERROR_LINE` innerhalb des Bereichs vom CATCH-Block aufgerufen wurde, und unabhängig davon, wie oft `ERROR_LINE` aufgerufen wurde. Dies steht im Gegensatz zu Funktionen wie @@ERROR. @@ERROR gibt eine Fehlernummer in der Anweisung zurück, die unmittelbar auf die folgt, die einen Fehler verursacht hat sowie in der ersten Anweisung eines CATCH-Blocks.  
  
In geschachtelten CATCH-Blöcken gibt `ERROR_LINE` die für den Bereich des CATCH-Blockes spezifische Fehlerzeilennummer zurück, auf die im Block verwiesen wird. So könnte beispielsweise der CATCH-Block eines TRY…CATCH-Konstrukts ein geschachteltes TRY…CATCH-Konstrukt enthalten. Innerhalb des geschachtelten CATCH-Blocks gibt `ERROR_LINE` die Zeilennummer des Fehlers zurück, der den geschachtelten CATCH-Block aufgerufen hat. Wenn `ERROR_LINE` im äußeren CATCH-Block ausgeführt wird, gibt es die Zeilennummer des Fehlers zurück, der den spezifischen CATCH-Block aufgerufen hat.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-errorline-in-a-catch-block"></a>A. Verwenden von ERROR_LINE in einem CATCH-Block  
In diesem Codebeispiel wird eine `SELECT`-Anweisung dargestellt, die einen Fehler aufgrund einer Division durch 0 (null) generiert. `ERROR_LINE` gibt die Nummer der Zeile zurück, in der der Fehler aufgetreten ist.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_LINE() AS ErrorLine;  
END CATCH;  
GO  
```  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
   
```  
Result 
-----------

(0 row(s) affected)

ErrorLine
-----------
4

(1 row(s) affected)
```  
  
### <a name="b-using-errorline-in-a-catch-block-with-a-stored-procedure"></a>B. Verwenden von ERROR_LINE in einem CATCH-Block mit einer gespeicherten Prozedur  
Dieses Beispiel zeigt eine gespeicherte Prozedur, in der ein Fehler aufgrund einer Division durch 0 (null) generiert wird. `ERROR_LINE` gibt die Nummer der Zeile zurück, in der der Fehler aufgetreten ist.  
  
```  
-- Verify that the stored procedure does not already exist.  
IF OBJECT_ID ( 'usp_ExampleProc', 'P' ) IS NOT NULL   
    DROP PROCEDURE usp_ExampleProc;  
GO  
  
-- Create a stored procedure that  
-- generates a divide-by-zero error.  
CREATE PROCEDURE usp_ExampleProc  
AS  
    SELECT 1/0;  
GO  
  
BEGIN TRY  
    -- Execute the stored procedure inside the TRY block.  
    EXECUTE usp_ExampleProc;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_LINE() AS ErrorLine;  
END CATCH;  
GO  
``` 
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
   
```  
-----------

(0 row(s) affected)

ErrorLine
-----------
7

(1 row(s) affected)  
   
```

### <a name="c-using-errorline-in-a-catch-block-with-other-error-handling-tools"></a>C. Verwenden von ERROR_LINE in einem CATCH-Block mit anderen Tools zur Fehlerbehandlung  
In diesem Codebeispiel wird eine `SELECT`-Anweisung dargestellt, die einen Fehler aufgrund einer Division durch 0 (null) generiert. `ERROR_LINE` gibt die Nummer der Zeile, in der der Fehler aufgetreten ist, sowie Informationen zum Fehler selbst zurück.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_LINE() AS ErrorLine,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
``` 
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
   
```  
-----------

(0 row(s) affected)

ErrorNumber ErrorSeverity ErrorState ErrorProcedure ErrorLine ErrorMessage
----------- ------------- ---------- -------------- --------- ---------------------------------
8134        16            1          NULL           3         Divide by zero error encountered.

(1 row(s) affected)
  
```
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40;Transact-SQL&#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  
