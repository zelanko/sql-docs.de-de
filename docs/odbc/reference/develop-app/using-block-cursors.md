---
title: Verwenden von Blockcursorn | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f5c487bd8b60a83c709399cb9673dc0b015bd79d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306791"
---
# <a name="using-block-cursors"></a>Verwenden von Blockcursorn
Unterstützung für Blockcursorn ist in ODBC 3 integriert. *x*. **SQLFetch** kann nur für Abfragen mit mehreren Zeilen verwendet werden, wenn Sie in ODBC 3 aufgerufen werden. *x*; bei ODBC 2. die *x* -Anwendung ruft **SQLFetch**auf, öffnet nur einen Vorwärts Cursor mit einer einzelnen Zeile. Bei ODBC 3. die *x* -Anwendung ruft **SQLFetch** in einem ODBC 2 auf. *x* -Treiber gibt eine einzelne Zeile zurück, es sei denn, der Treiber unterstützt **SQLExtendedFetch**. Weitere Informationen finden Sie unter [Blockieren von Cursorn, scrollfähigen Cursorn und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiber Richtlinien zur Abwärtskompatibilität.  
  
 Zur Verwendung von Blockcursorn legt die Anwendung die Rowsetgröße fest, bindet die rowsetpuffer (wie im vorherigen Abschnitt beschrieben), legt optional die Attribute SQL_ATTR_ROWS_FETCHED_PTR und SQL_ATTR_ROW_STATUS_PTR Anweisung fest und ruft **SQLFetch** oder **SQLFetchScroll** auf, um einen Zeilen Block abzurufen. Die Anwendung kann die Rowsetgröße ändern und neue rowsetpuffer (durch Aufrufen von **SQLBindCol** oder durch Angeben eines Bindungs Offsets) binden, auch nachdem die Zeilen abgerufen wurden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Rowsetgröße](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Anzahl von abgerufenen Zeilen und Status](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData und Blockcursorn; geschweibs Block](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
