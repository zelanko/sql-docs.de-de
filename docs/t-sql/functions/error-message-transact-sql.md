---
title: ERROR_MESSAGE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ERROR_MESSAGE_TSQL
- ERROR_MESSAGE
dev_langs:
- TSQL
helpviewer_keywords:
- ERROR_MESSAGE function
- errors [SQL Server], text of
- messages [SQL Server], text of
- TRY...CATCH [SQL Server]
- CATCH block
ms.assetid: f32877a6-5f17-418c-a32c-5a1a344b3c45
caps.latest.revision: 53
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 839432fa621b81c16627140164549772996cc68d
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39452804"
---
# <a name="errormessage-transact-sql"></a>ERROR_MESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Diese Funktion gibt den Meldungstext des Fehlers zurück, der die Ausführung des CATCH-Blocks eines TRY…CATCH-Konstrukts ausgelöst hat.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
ERROR_MESSAGE ( )   
```  
  
## <a name="return-types"></a>Rückgabetypen  
 **nvarchar(4000)**  
  
## <a name="return-value"></a>Rückgabewert  
Wenn `ERROR_MESSAGE` in einem CATCH-Block aufgerufen wird, wird der vollständige Text der Fehlermeldung zurückgegeben, die die Ausführung des `CATCH`-Blocks ausgelöst hat. Der Text umfasst die Werte, die für alle ersetzbaren Parameter angegeben werden, z.B. Längen, Objektnamen oder Zeitangaben.  
  
`ERROR_MESSAGE` gibt NULL zurück, wenn die Funktion außerhalb des Bereichs eines CATCH-Blocks aufgerufen wird.  
  
## <a name="remarks"></a>Remarks  
`ERROR_MESSAGE` kann überall im Bereich eines CATCH-Blocks aufgerufen werden.  
  
`ERROR_MESSAGE` gibt unabhängig von der Anzahl der Aufrufe und dem Bereich des `CATCH`-Blocks eine relevante Fehlermeldung zurück. Dies steht im Gegensatz zu Funktionen wie @@ERROR, die nur eine Fehlernummer in der Anweisung zurückgeben, die unmittelbar auf der Anweisung folgt, die einen Fehler auslöst.  
  
`ERROR_MESSAGE` gibt in geschachtelten `CATCH`-Blöcken die Fehlermeldung für den entsprechenden Bereich des `CATCH`-Blocks zurück, der auf den `CATCH`-Block verwiesen hat. Zum Beispiel könnte der `CATCH`-Block eines äußeren TRY...CATCH-Konstrukts ein inneres `TRY...CATCH`-Konstrukt aufweisen. In diesem inneren `CATCH`-Block gibt `ERROR_MESSAGE` die Meldung des Fehlers zurück, der den inneren `CATCH`-Block aufgerufen hat. Wenn `ERROR_MESSAGE` im äußeren `CATCH`-Block ausgeführt wird, wird die Meldung des Fehlers zurückgegeben, der den äußeren `CATCH`-Block aufgerufen hat.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-errormessage-in-a-catch-block"></a>A. Verwenden von ERROR_MESSAGE in einem CATCH-Block  
Das folgende Beispiel zeigt eine `SELECT`-Anweisung, die einen Fehler aufgrund einer Division durch 0 (null) generiert. Der `CATCH`-Block gibt die Fehlermeldung zurück.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorMessage
----------------------------------
Divide by zero error encountered.

(1 row(s) affected)

```  
  
### <a name="b-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>B. Verwenden von ERROR_MESSAGE in einem CATCH-Block mit anderen Fehlerbehandlungstools  
Das folgende Beispiel zeigt eine `SELECT`-Anweisung, die einen Fehler aufgrund einer Division durch 0 (null) generiert. Der `CATCH`-Block gibt zusammen mir der Fehlermeldung Informationen zum Fehler zurück.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorNumber ErrorSeverity ErrorState  ErrorProcedure  ErrorLine  ErrorMessage
----------- ------------- ----------- --------------- ---------- ----------------------------------
8134        16            1           NULL            4          Divide by zero error encountered.

(1 row(s) affected)

```
  

