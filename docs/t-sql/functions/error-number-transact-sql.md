---
title: ERROR_NUMBER (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ERROR_NUMBER_TSQL
- ERROR_NUMBER
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], line number
- messages [SQL Server], numbers
- TRY...CATCH [SQL Server]
- ERROR_NUMBER function
- CATCH block
ms.assetid: 1de85fff-1ca2-4b31-841b-926e571cb150
caps.latest.revision: 50
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9ae22c38ef34ad8db35c625de80d47f08a0e6073
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2018
ms.locfileid: "35250013"
---
# <a name="errornumber-transact-sql"></a>ERROR_NUMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Diese Funktion gibt die Fehlernummer des Fehlers zurück, der die Ausführung des CATCH-Blocks eines TRY…CATCH-Konstrukts ausgelöst hat.  

 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
ERROR_NUMBER ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
## <a name="return-value"></a>Rückgabewert  
Wenn `ERROR_NUMBER` in einem CATCH-Block aufgerufen wird, wird die Fehlernummer des Fehlers zurückgegeben, der die Ausführung des CATCH-Blocks ausgelöst hat.  

`ERROR_NUMBER` gibt NULL zurück, wenn die Funktion außerhalb des Bereichs eines CATCH-Blocks aufgerufen wird.  
  
## <a name="remarks"></a>Remarks  
`ERROR_NUMBER` kann überall im Bereich eines CATCH-Blocks aufgerufen werden.  
  
`ERROR_NUMBER` gibt unabhängig von der Anzahl der Aufrufe und dem Bereich des `CATCH`-Blocks eine relevante Fehlernummer zurück. Dies steht im Gegensatz zu Funktionen wie @@ERROR, die nur eine Fehlernummer in der Anweisung zurückgeben, die unmittelbar auf der Anweisung folgt, die einen Fehler auslöst.  

`ERROR_NUMBER` gibt in einem geschachtelten `CATCH`-Block die Fehlernummer für den entsprechenden Bereich des `CATCH`-Blocks zurück, der auf den `CATCH`-Block verwiesen hat. Zum Beispiel könnte der `CATCH`-Block eines äußeren TRY...CATCH-Konstrukts ein inneres `TRY...CATCH`-Konstrukt aufweisen. In diesem inneren `CATCH`-Block gibt `ERROR_NUMBER` die Nummer des Fehlers zurück, der den inneren `CATCH`-Block aufgerufen hat. Wenn `ERROR_NUMBER` im äußeren `CATCH`-Block ausgeführt wird, wird die Nummer des Fehlers zurückgegeben, der den äußeren `CATCH`-Block aufgerufen hat.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-errornumber-in-a-catch-block"></a>A. Verwenden von ERROR_NUMBER in einem CATCH-Block  
Das folgende Beispiel zeigt eine `SELECT`-Anweisung, die einen Fehler aufgrund einer Division durch 0 (null) generiert. Der `CATCH`-Block gibt die Fehlernummer zurück.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_NUMBER() AS ErrorNumber;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorNumber
-----------
8134

(1 row(s) affected)

```  
  
### <a name="b-using-errornumber-in-a-catch-block-with-other-error-handling-tools"></a>B. Verwenden von ERROR_NUMBER in einem CATCH-Block mit anderen Fehlerbehandlungstools  
Das folgende Beispiel zeigt eine `SELECT`-Anweisung, die einen Fehler aufgrund einer Division durch 0 (null) generiert. Der `CATCH`-Block gibt zusammen mir der Fehlernummer Informationen zum Fehler zurück.  

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

-----------

(0 row(s) affected)

ErrorNumber ErrorSeverity ErrorState  ErrorProcedure   ErrorLine  ErrorMessage
----------- ------------- ----------- ---------------  ---------- ----------------------------------
8134        16            1           NULL             4          Divide by zero error encountered.

(1 row(s) affected)

```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40;Transact-SQL&#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  

