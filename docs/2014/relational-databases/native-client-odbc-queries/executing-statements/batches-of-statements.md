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
ms.openlocfilehash: 8951469279e5c3577aef355e339397b329bb5d63
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206771"
---
# <a name="batches-of-statements"></a>Batches von Anweisungen
  Ein Batch von [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen enthält zwei oder mehr-Anweisungen, getrennt durch ein Semikolon (;), in eine einzelne Zeichenfolge, die an die **SQLExecDirect** -oder [SQLPrepare-Funktion](https://go.microsoft.com/fwlink/?LinkId=59360)weitergegeben wurde. Beispiel:  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 Batches können effizienter als das Senden getrennter Anweisungen sein, da der Netzwerkdatenverkehr dadurch meist reduziert wird. Verwenden Sie [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) , um auf dem nächsten Resultset positioniert zu werden, wenn es mit dem aktuellen Resultset abgeschlossen ist.  
  
 Batches können immer dann verwendet werden, wenn die ODBC-Cursorattribute auf die Standardeinstellungen eines schreibgeschützten Vorwärtscursors mit der Rowsetgröße 1 festgelegt wurden.  
  
 Wenn ein Batch ausgeführt wird und Servercursor für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet werden, dann wird der Servercursor implizit in ein Standardresultset umgewandelt. **SQLExecDirect** oder **SQLExecute** geben SQL_SUCCESS_WITH_INFO zurück, und ein **SQLGetDiagRec** -Befehl gibt Folgendes zurück:  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Anweisungen &#40;ODBC-&#41;](executing-statements-odbc.md)  
  
  
