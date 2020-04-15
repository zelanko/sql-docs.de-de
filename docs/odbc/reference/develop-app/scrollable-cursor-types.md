---
title: Scrollbare Cursortypen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: dbd32576-0453-4e90-ae45-1a81cee8259d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 63f29269ea209875a2e775cf8d523302fcb9a976
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304231"
---
# <a name="scrollable-cursor-types"></a>Scrollbare Cursortypen
Die vier Typen von scrollbaren Cursorn sind statisch, dynamisch, Keyset-gesteuert und gemischt. Statische Cursor erkennen nur wenige oder keine Änderungen, sind aber relativ kostengünstig zu implementieren. Dynamische Cursor erkennen alle Änderungen, sind jedoch teuer zu implementieren. Keyset-gesteuerte und gemischte Cursor liegen dazwischen und erkennen die meisten Änderungen, jedoch mit weniger Kosten als dynamische Cursor.  
  
 Die folgenden Begriffe werden verwendet, um die Eigenschaften der einzelnen Scroll-Cursortypen zu definieren:  
  
-   **Eigene Aktualisierungen, Löschungen und Einfügungen.** Aktualisierungen, Löschungen und Einfügungen, die über den Cursor erstellt werden, entweder mit einem Aufruf von **SQLBulkOperations** oder **SQLSetPos** oder mit einer positionierten Aktualisierungs- oder Löschanweisung.  
  
-   **Andere Aktualisierungen, Löschungen und Einfügungen.** Aktualisierungen, Löschungen und Einfügungen, die nicht vom Cursor vorgenommen wurden, einschließlich der Vorgänge, die von anderen Vorgängen in derselben Transaktion, von anderen Transaktionen und von anderen Anwendungen vorgenommen wurden.  
  
-   **Mitgliedschaft.** Der Satz von Zeilen im Resultset.  
  
-   **Bestellung.** Die Reihenfolge, in der Zeilen vom Cursor zurückgegeben werden.  
  
-   **Werte.** Die Werte in jeder Zeile im Resultset.  
  
 Informationen zum Aktualisieren, Löschen und Einfügen von Daten finden Sie unter Aktualisieren der [Datenübersicht](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Statische ODBC-Cursor](../../../odbc/reference/develop-app/odbc-static-cursors.md)  
  
-   [Dynamische ODBC-Cursor](../../../odbc/reference/develop-app/odbc-dynamic-cursors.md)  
  
-   [Keysetgesteuerte Cursor](../../../odbc/reference/develop-app/keyset-driven-cursors.md)  
  
-   [Gemischte Cursor](../../../odbc/reference/develop-app/mixed-cursors.md)
