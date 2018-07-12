---
title: Aufrufen von gespeicherten Prozeduren (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37ce27067c4ad30e38b6d3c168b8f676815b693d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411299"
---
# <a name="call-stored-procedures-odbc"></a>Aufrufen von gespeicherten Prozeduren (ODBC)
  Wenn eine SQL-Anweisung eine gespeicherte Prozedur mit der ODBC CALL-Escape-Klausel aufruft, sendet der Microsoft® SQL Server™-Treiber die Prozedur mit dem RPC (Remote Stored Procedure Call)-Mechanismus an SQL Server. RPC-Anforderungen umgehen größtenteils das Analysieren der Anwendungen und die Parameterverarbeitung in SQL Server und sind schneller als die Transact-SQL EXECUTE-Anweisung.  
  
 Eine beispielanwendung, die diese Funktion veranschaulicht wird, finden Sie unter [Prozess Rückgabecodes und Ausgabeparametern &#40;ODBC&#41;](running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>So führen Sie eine Prozedur als RPC aus  
  
1.  Erstellen Sie eine SQL­Anweisung, die die ODBC CALL-Escapesequenz verwendet. Die Anweisung verwendet Parametermarkierungen für jeden Eingabe-, Eingabe/Ausgabe- und Ausgabeparameter sowie für den Prozedurrückgabewert (falls zutreffend):  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Rufen Sie [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) für jeden Eingabe-, Eingabe/Ausgabe- und Ausgabeparameter und für die Prozedur Rückgabewert (sofern vorhanden).  
  
3.  Führen Sie die Anweisung mit [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399).  
  
> [!NOTE]  
>  Wenn eine Anwendung eine Prozedur mit der Transact-SQL EXECUTE-Syntax (statt mit der ODBC CALL-Escapesequenz) übermittelt, gibt der SQL Server ODBC-Treiber den Prozeduraufruf an SQL Server als SQL-Anweisung statt als RPC weiter. Darüber hinaus werden Ausgabeparameter nicht zurückgegeben, wenn die Transact SQL EXECUTE-Anweisung verwendet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von gespeicherten Prozeduren: Themen zur Vorgehensweise &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)   
 [Batchverarbeitung von gespeicherten Prozeduraufrufen](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Ausführen gespeicherter Prozeduren](../native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Aufrufen einer gespeicherten Prozedur](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Vorgehensweisen](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
