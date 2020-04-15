---
title: Verwenden von Blockcursorn | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306791"
---
# <a name="using-block-cursors"></a>Verwenden von Blockcursorn
Die Unterstützung für Blockcursor ist in ODBC 3 integriert. *x*. **SQLFetch** kann nur für mehrreihige Abrufe verwendet werden, wenn es in ODBC 3 aufgerufen wird. *x*; wenn ein ODBC 2. *x-Anwendung* ruft **SQLFetch**auf, es wird nur ein einzeiligen, vorwärts gerichteten Cursor geöffnet. Wenn ein ODBC 3. *x-Anwendung* ruft **SQLFetch** in einem ODBC 2 auf. *x-Treiber* gibt er eine einzelne Zeile zurück, es sei denn, der Treiber unterstützt **SQLExtendedFetch**. Weitere Informationen finden Sie unter [Blockcursors, Scrollable Cursors und Backward Compatibility](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiberrichtlinien für Abwärtskompatibilität.  
  
 Um Blockcursor zu verwenden, legt die Anwendung die Rowsetgröße fest, bindet die Rowsetpuffer (wie im vorherigen Abschnitt beschrieben), legt optional die SQL_ATTR_ROWS_FETCHED_PTR- und SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribute fest und ruft **SQLFetch** oder **SQLFetchScroll** auf, um einen Zeilenblock abzurufen. Die Anwendung kann die Rowsetgröße ändern und neue Rowsetpuffer binden (durch Aufrufen von **SQLBindCol** oder Angeben eines Bindungsoffsets), auch nachdem Zeilen abgerufen wurden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Rowsetgröße](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Anzahl von abgerufenen Zeilen und Status](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData- und Blockcursor; Block curso](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
