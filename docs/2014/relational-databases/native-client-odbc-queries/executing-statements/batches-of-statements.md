---
title: Batches von Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aa97baae4ad6331193cab16ae2609212753c5be0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051936"
---
# <a name="batches-of-statements"></a>Batches von Anweisungen
  Ein Batch von [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen enthält zwei oder mehr Anweisungen, getrennt durch ein Semikolon (;), in einer einzelnen Zeichenfolge, die an **SQLExecDirect** oder [SQLPrepare-Funktion](http://go.microsoft.com/fwlink/?LinkId=59360). Zum Beispiel:  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 Batches können effizienter als das Senden getrennter Anweisungen sein, da der Netzwerkdatenverkehr dadurch meist reduziert wird. Verwendung [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) , positioniert wird, auf das nächste Resultset, wenn das aktuelle Resultset beendet.  
  
 Batches können immer dann verwendet werden, wenn die ODBC-Cursorattribute auf die Standardeinstellungen eines schreibgeschützten Vorwärtscursors mit der Rowsetgröße 1 festgelegt wurden.  
  
 Wenn ein Batch ausgeführt wird und Servercursor für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet werden, dann wird der Servercursor implizit in ein Standardresultset umgewandelt. **SQLExecDirect** oder **SQLExecute** SQL_SUCCESS_WITH_INFO und ein Aufruf zurück **SQLGetDiagRec** zurückgibt:  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Anweisungen &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  
