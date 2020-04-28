---
title: Bestimmen der Anzahl betroffener Zeilen | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305891"
---
# <a name="determining-the-number-of-affected-rows"></a>Bestimmen der Anzahl der betroffenen Zeilen
Nachdem eine Anwendung Zeilen aktualisiert, gelöscht oder eingefügt hat, kann Sie **SQLRowCount** aufgerufen werden, um zu bestimmen, wie viele Zeilen betroffen sind. **SQLRowCount** gibt diesen Wert zurück, unabhängig davon, ob die Zeilen aktualisiert, gelöscht oder eingefügt wurden, indem eine **Update**-, **Delete**-oder **Insert** -Anweisung ausgeführt wurde, indem eine positionierte UPDATE-oder DELETE-Anweisung ausgeführt oder **SQLSetPos**aufgerufen werden.  
  
 Wenn ein Batch von SQL-Anweisungen ausgeführt wird, kann die Anzahl der betroffenen Zeilen für alle Anweisungen im Batch oder für jede einzelne Anweisung im Batch die Gesamtzahl sein. Weitere Informationen finden Sie unter [Batches von SQL-Anweisungen](../../../odbc/reference/develop-app/batches-of-sql-statements.md) und [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Die Anzahl der betroffenen Zeilen wird auch im SQL_DIAG_ROW_COUNT Diagnose Header Feld im Diagnose Bereich zurückgegeben, der dem Anweisungs Handle zugeordnet ist. Allerdings werden die Daten in diesem Feld nach jedem Funktions aufrufauf dem gleichen Anweisungs Handle zurückgesetzt, während der von **SQLRowCount** zurückgegebene Wert bis zum Aufrufen von **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**oder **SQLSetPos**unverändert bleibt.
