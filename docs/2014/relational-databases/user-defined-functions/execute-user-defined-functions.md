---
title: Ausführen von benutzerdefinierten Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-udf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- invoking user-defined functions
- user-defined functions [SQL Server], executing
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6961d8306ff4b5a5f5280d25e3657952d0890063
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050075"
---
# <a name="execute-user-defined-functions"></a>Ausführen von benutzerdefinierten Funktionen
  Sie können in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[tsql](../../includes/tsql-md.md)]eine benutzerdefinierte Funktion ausführen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **Zum Ausführen einer benutzerdefinierten Funktion mit:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 In Transact-SQL können Parameter entweder mit *value* oder mit dem Wert*parameter_name*=*value.* angegeben werden. angegeben werden. Ein Parameter ist nicht Teil einer Transaktion. Deshalb wird der Wert eines Parameters, der in einer Transaktion geändert wird, nicht wieder auf seinen ursprünglichen Wert zurückgesetzt, wenn für diese Transaktion später ein Rollback ausgeführt wird. Der Wert, der an den Aufrufer zurückgegeben wird, ist immer der Wert zu dem Zeitpunkt, zu dem das Modul beendet wird.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Zum Ausführen der EXECUTE-Anweisung sind keine Berechtigungen erforderlich. Es sind jedoch Berechtigungen für die sicherungsfähigen Elemente erforderlich, auf die in der EXECUTE-Zeichenfolge verwiesen wird. Wenn z. B. die Zeichenfolge eine INSERT-Anweisung enthält, benötigt der Aufrufer der EXECUTE-Anweisung die INSERT-Berechtigung für die Zieltabelle. Berechtigungen werden überprüft, wenn die EXECUTE-Anweisung erreicht wird, selbst wenn die EXECUTE-Anweisung innerhalb eines Moduls enthalten ist. Weitere Informationen finden Sie unter [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-execute-a-user-defined-function"></a>So führen Sie eine benutzerdefinierte Funktion aus  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Declares a variable and sets it to zero.  
    -- This variable is used to return the results of the function.  
    DECLARE @ret nvarchar(15)= NULL;   
  
    -- Executes the dbo.ufnGetSalesOrderStatusText function.  
    --The function requires a value for one parameter, @Status.   
    EXEC @ret = dbo.ufnGetSalesOrderStatusText @Status= 5;   
    --Returns the result in the message tab.  
    PRINT @ret;  
    ```  
  
 Weitere Informationen finden Sie unter [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).  
  
  
