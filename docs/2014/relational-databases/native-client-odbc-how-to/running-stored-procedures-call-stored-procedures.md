---
title: Aufrufen von gespeicherten Prozeduren (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58e5160065847d5729548702b5f1d65eb31bf694
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200263"
---
# <a name="call-stored-procedures-odbc"></a>Aufrufen von gespeicherten Prozeduren (ODBC)
  Wenn Ruft eine SQL-Anweisung eine gespeicherte Prozedur mithilfe der ODBC CALL Escape-Klausel, die Microsoft?? SqlServer??? Treiber sendet die Prozedur in SQL Server mithilfe des Mechanismus der remote gespeicherten Prozedur Remoteprozeduraufruf (RPC) verwendet wird. RPC-Anforderungen umgehen größtenteils das Analysieren der Anwendungen und die Parameterverarbeitung in SQL Server und sind schneller als die Transact-SQL EXECUTE-Anweisung.  
  
 Eine beispielanwendung, die diese Funktion veranschaulicht wird, finden Sie unter [Prozess Rückgabecodes und Ausgabeparametern &#40;ODBC&#41;](running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>So führen Sie eine Prozedur als RPC aus  
  
1.  Erstellen Sie eine SQL­Anweisung, die die ODBC CALL-Escapesequenz verwendet. Die Anweisung verwendet Parametermarkierungen für jeden Eingabe-, Eingabe/Ausgabe- und Ausgabeparameter sowie für den Prozedurrückgabewert (falls zutreffend):  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Rufen Sie [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) für jeden Eingabe-, Eingabe/Ausgabe- und Ausgabeparameter sowie für den Prozedurrückgabewert (sofern vorhanden) auf.  
  
3.  Führen Sie die Anweisung mit [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)aus.  
  
> [!NOTE]  
>  Wenn eine Anwendung eine Prozedur mit der Transact-SQL EXECUTE-Syntax (statt mit der ODBC CALL-Escapesequenz) übermittelt, gibt der SQL Server ODBC-Treiber den Prozeduraufruf an SQL Server als SQL-Anweisung statt als RPC weiter. Darüber hinaus werden Ausgabeparameter nicht zurückgegeben, wenn die Transact SQL EXECUTE-Anweisung verwendet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von gespeicherten Prozeduren: Themen zur Vorgehensweise &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)   
 [Batchverarbeitung von gespeicherten Prozeduraufrufen](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Ausführen gespeicherter Prozeduren](../native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Aufrufen einer gespeicherten Prozedur](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Vorgehensweisen](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
