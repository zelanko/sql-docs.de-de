---
title: Bestimmen der Anzahl der betroffenen Zeilen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], number of rows affected
- number of rows affected by update [ODBC]
- data updates [ODBC], number of rows affected
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 156a5fe41d2c9b57a33bbc2bdb4540d1f5b00340
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305891"
---
# <a name="determining-the-number-of-affected-rows"></a>Bestimmen der Anzahl der betroffenen Zeilen
Nachdem eine Anwendung Zeilen aktualisiert, gelöscht oder eingefügt hat, kann sie **SQLRowCount** aufrufen, um zu bestimmen, wie viele Zeilen betroffen waren. **SQLRowCount** gibt diesen Wert unabhängig davon zurück, ob die Zeilen aktualisiert, gelöscht oder eingefügt wurden, indem eine **UPDATE-,** **DELETE-** oder **INSERT-Anweisung** ausgeführt wurde, indem eine positionierte Aktualisierungs- oder Löschanweisung ausgeführt wird oder **SQLSetPos**aufgerufen wird.  
  
 Wenn ein Batch von SQL-Anweisungen ausgeführt wird, kann die Anzahl der betroffenen Zeilen eine Gesamtanzahl für alle Anweisungen im Batch oder einzelne Zählungen für jede Anweisung im Batch sein. Weitere Informationen finden Sie unter [Batches of SQL Statements](../../../odbc/reference/develop-app/batches-of-sql-statements.md) and [Multiple Results](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Die Anzahl der betroffenen Zeilen wird auch im SQL_DIAG_ROW_COUNT Diagnoseheaderfeld im Diagnosebereich zurückgegeben, der dem Anweisungshandle zugeordnet ist. Die Daten in diesem Feld werden jedoch nach jedem Funktionsaufruf für dasselbe Anweisungshandle zurückgesetzt, während der von **SQLRowCount** zurückgegebene Wert bis zu einem Aufruf von **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**oder **SQLSetPos**gleich bleibt.
