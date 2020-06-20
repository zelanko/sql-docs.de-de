---
title: MSSQLSERVER_137 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e0142cd53006609e9274972e4f5964132f5982c2
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967970"
---
# <a name="mssqlserver_137"></a>MSSQLSERVER_137
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|137|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|P_SCALAR_VAR_NOTFOUND|  
|Meldungstext|Die "%.*ls"-Skalarvariable muss deklariert werden.|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler tritt auf, wenn in einem SQL-Skript eine Variable verwendet wird, ohne dass die Variable zuerst deklariert wurde. Im folgenden Beispiel wird der Fehler 137 für die Set-und die SELECT-Anweisung zurückgegeben, da **@mycol** nicht deklariert ist.  
  
 SET @mycol = 'ContactName';  
  
 SELECT @mycol;  
  
 Eine der etwas komplizierteren Ursachen für diesen Fehler ist u. a. die Verwendung einer Variablen, die außerhalb der EXECUTE-Anweisung deklariert wurde. Beispielsweise **@mycol** ist die in der SELECT-Anweisung angegebene Variable für die SELECT-Anweisung lokal. Sie befindet sich daher außerhalb der EXECUTE-Anweisung.  
  
 USE AdventureWorks2012;  
  
 GO  
  
 DECLARE @mycol nvarchar(20);  
  
 SET @mycol = 'Name';  
  
 EXECUTE ('SELECT @mycol FROM Production.Product;');  
  
## <a name="user-action"></a>Benutzeraktion  
 Überprüfen Sie, ob alle in einem SQL-Skript verwendeten Variablen deklariert wurden, bevor sie an anderer Stelle im Skript verwendet werden.  
  
 Schreiben Sie das Skript um, sodass es nicht auf Variablen in der EXECUTE-Anweisung verweist, die außerhalb davon deklariert wurden. Beispiel:  
  
 USE AdventureWorks2012;  
  
 GO  
  
 DECLARE @mycol nvarchar(20) ;  
  
 SET @mycol = 'Name';  
  
 EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;  
  
## <a name="see-also"></a>Weitere Informationen  
 [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)   
 [SET-Anweisungen (Transact-SQL)](/sql/t-sql/statements/set-statements-transact-sql)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql)  
  
  
