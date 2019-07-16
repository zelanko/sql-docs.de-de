---
title: Schließen des Cursors | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: de22797bdcf4ff526a8c17aee313567da3114b60
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036542"
---
# <a name="closing-the-cursor"></a>Schließen des Cursors
Wenn eine Anwendung mithilfe eines Cursors abgeschlossen hat, ruft er **SQLCloseCursor** Schließen des Cursors. Zum Beispiel:  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 Bis die Anwendung den Cursor geschlossen wurde, kann die Anweisung, die auf der der Cursor geöffnet wird für die meisten anderen Vorgänge, z. B. das Ausführen einer anderen SQL­Anweisung verwendet werden. Eine vollständige Liste der Funktionen, die aufgerufen werden kann, während ein Cursor geöffnet ist, finden Sie unter [Anhang B: ODBC-Übergang Statustabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
> [!NOTE]  
>  Um einen Cursor zu schließen, eine Anwendung aufrufen sollten **SQLCloseCursor**, nicht **SQLCancel**.  
  
 Cursor bleiben geöffnet, bis sie explizit geschlossen werden, außer wenn eine Transaktion ein Commit oder Rollback ausgeführt, wobei einige Datenquellen den Cursor zu schließen. Insbesondere erreichen das Ende des Resultsets festgelegt, wenn **SQLFetch** SQL_NO_DATA zurückgibt, wird einen Cursor nicht geschlossen. Auch Cursor für leere Resultsets (Resultsets erstellt, wenn eine Anweisung erfolgreich ausgeführt wurde, aber die keine Zeilen zurückgegeben), müssen explizit geschlossen werden.
