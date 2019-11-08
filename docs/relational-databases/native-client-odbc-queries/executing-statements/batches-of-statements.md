---
title: Batches von Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 19efcc8b4381694177d0ec3d64376368e8d23a7d
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73779766"
---
# <a name="batches-of-statements"></a>Batches von Anweisungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Ein Batch von [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen enthält zwei oder mehr-Anweisungen, getrennt durch ein Semikolon (;), in eine einzelne Zeichenfolge, die an die **SQLExecDirect** -oder [SQLPrepare-Funktion](https://go.microsoft.com/fwlink/?LinkId=59360)weitergegeben wurde. Beispiel:  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 Batches können effizienter als das Senden getrennter Anweisungen sein, da der Netzwerkdatenverkehr dadurch meist reduziert wird. Verwenden Sie [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) , um auf dem nächsten Resultset positioniert zu werden, wenn es mit dem aktuellen Resultset abgeschlossen ist.  
  
 Batches können immer dann verwendet werden, wenn die ODBC-Cursorattribute auf die Standardeinstellungen eines schreibgeschützten Vorwärtscursors mit der Rowsetgröße 1 festgelegt wurden.  
  
 Wenn ein Batch ausgeführt wird und Servercursor für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet werden, dann wird der Servercursor implizit in ein Standardresultset umgewandelt. **SQLExecDirect** oder **SQLExecute** geben SQL_SUCCESS_WITH_INFO zurück, und ein **SQLGetDiagRec** -Befehl gibt Folgendes zurück:  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von &#40;Anweisungen (ODBC)&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
