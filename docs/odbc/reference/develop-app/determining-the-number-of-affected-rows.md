---
title: Bestimmen der Anzahl der betroffenen Zeilen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99e3676c3b73b177f5e6fc3acef0d93d55cce898
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63262101"
---
# <a name="determining-the-number-of-affected-rows"></a>Bestimmen der Anzahl der betroffenen Zeilen
Nachdem eine Anwendung aktualisieren, löschen oder Einfügen von Zeilen, können sie aufrufen **SQLRowCount** um zu bestimmen, wie viele Zeilen betroffen sind. **SQLRowCount** gibt diesen Wert zurück, unabhängig davon, ob die Zeilen wurden aktualisiert, gelöscht oder, indem Sie Ausführung eingefügt einer **UPDATE**, **löschen**, oder **einfügen** -Anweisung durch Ausführen einer positionierte update oder delete-Anweisung oder durch den Aufruf **SQLSetPos**.  
  
 Wenn ein Batch von SQL-Anweisungen ausgeführt wird, kann die Anzahl der betroffenen Zeilen Gesamtzahl für alle Anweisungen im Batch oder die einzelnen Zählwerte für jede Anweisung im Batch sein. Weitere Informationen finden Sie unter [Batches von SQL-Anweisungen](../../../odbc/reference/develop-app/batches-of-sql-statements.md) und [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Die Anzahl der betroffenen Zeilen wird auch in der SQL_DIAG_ROW_COUNT diagnostische Header-Feld im Bereich diagnostische das Anweisungshandle zugeordnet, zurückgegeben. Jedoch die Daten in dieses Feld werden zurückgesetzt nach jedem Funktionsaufruf auf dasselbe Anweisungshandle, während der Rückgabewert von **SQLRowCount** bleibt unverändert, bis ein Aufruf von **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**, oder **SQLSetPos**.
