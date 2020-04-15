---
title: Schließen des Cursors | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], closing
- closing cursors [ODBC]
ms.assetid: 4f19bf5e-6d8c-40ae-a975-cfd62a0790ec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 723e40e6d83eed84ed93ee1eeab3535622ad5f04
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299140"
---
# <a name="closing-the-cursor"></a>Schließen des Cursors
Wenn eine Anwendung mit einem Cursor fertig ist, ruft sie **SQLCloseCursor** auf, um den Cursor zu schließen. Beispiel:  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 Bis die Anwendung den Cursor schließt, kann die Anweisung, auf der der Cursor geöffnet wird, nicht für die meisten anderen Vorgänge verwendet werden, z. B. für das Ausführen einer anderen SQL-Anweisung. Eine vollständige Liste der Funktionen, die aufgerufen werden können, während ein Cursor geöffnet ist, finden Sie in [Anhang B: ODBC-Zustandsübergangstabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
> [!NOTE]  
>  Um einen Cursor zu schließen, sollte eine Anwendung **SQLCloseCursor**aufrufen, nicht **SQLCancel**.  
  
 Cursor bleiben geöffnet, bis sie explizit geschlossen werden, es sei denn, eine Transaktion wird festgeschrieben oder zurückgesetzt, in diesem Fall schließen einige Datenquellen den Cursor. Insbesondere wenn **SQLFetch** das Ende des Resultsets erreicht, wenn SQL_NO_DATA zurückgegeben wird, wird kein Cursor geschlossen. Auch Cursor für leere Resultsets (Ergebnissätze, die erstellt wurden, wenn eine Anweisung erfolgreich ausgeführt wurde, aber keine Zeilen zurückgegeben hat) müssen explizit geschlossen werden.
