---
title: Aktualisieren der Datenübersicht | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- data updates [ODBC]
- updating data [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 062036a4-cda6-4aaa-9765-f1ec3e0b31b1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9972ab61f041385ae4ca616df093ae63ad7a47d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300386"
---
# <a name="updating-data-overview"></a>Aktualisieren einer Datenübersicht
Anwendungen können Daten aktualisieren, indem sie SQL-Anweisungen ausführen oder **SQLSetPos** oder **SQLBulkOperations**aufrufen. **UPDATE**-, **DELETE-** und **INSERT-Anweisungen** wirken direkt auf die Datenquelle und werden in der Regel von Treibern unterstützt. Gesuchte Aktualisierungs- und Löschanweisungen enthalten eine Spezifikation der zu ändernden Zeilen. Positionierte Update- und Löschanweisungen und **SQLSetPos** wirken über einen Cursor auf die Datenquelle und werden weniger stark unterstützt.  
  
 Ob Cursor Änderungen erkennen können, die mit den in diesem Abschnitt beschriebenen Methoden vorgenommen wurden, hängt vom Typ des Cursors und dessen Implementierung ab. Vorwärtscursor werden keine Zeilen erneut besucht und erkennen daher keine Änderungen. Informationen dazu, ob scrollbare Cursor Änderungen erkennen können, finden Sie [unter Scrollable Cursors](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [UPDATE-, DELETE- und INSERT-Anweisungen](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Positionierte Aktualisierung und DELETE-Anweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Simulieren von positionierten Aktualisierungen und DELETE-Anweisungen](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Bestimmen der Anzahl der betroffenen Zeilen](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Aktualisieren von Daten mit SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Aktualisieren von Daten mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Long-Daten, SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
