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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 388995cd5cb8a711d72533685c14088a7e908475
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758938"
---
# <a name="using-block-cursors"></a>Verwenden von Blockcursorn
Unterstützung für Blockcursor ist in ODBC 3. integriert. *x*. **SQLFetch** kann nur für die Einfügung mehrerer Zeilen abrufen, die bei Aufruf in ODBC 3. verwendet werden. *X*; Wenn eine ODBC-2. *X* Anwendungsaufrufe **SQLFetch**, nur einen einzelne Zeile, nur vorwärts gerichteten Cursor wird geöffnet. Wenn eine ODBC-3. *x* Anwendungsaufrufe **SQLFetch** in einer ODBC 2. *X* -Treiber verwenden, wird eine einzelne Zeile, wenn der Treiber unterstützt **SQLExtendedFetch**. Weitere Informationen finden Sie unter [Blockcursor, scrollbare Cursor und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität.  
  
 Um Blockcursor verwenden zu können, die Anwendung legt die Größe des Rowsets, bindet der Rowset-Puffer (wie im vorherigen Abschnitt beschrieben) optional legt die Anweisungsattribute SQL_ATTR_ROWS_FETCHED_PTR fest und SQL_ATTR_ROW_STATUS_PTR und Aufrufe **SQLFetch**  oder **SQLFetchScroll** zum Abrufen eines Zeilenblocks. Kann die Anwendung die Rowsetgröße geändert und neue Rowset-Puffer zu binden (durch Aufrufen von **SQLBindCol** oder das Angeben eines Bindung Offsets) auch nach Zeilen abgerufen wurden.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Rowsetgröße](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Anzahl von abgerufenen Zeilen und Status](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData und Blockcursor; Grafikoberfläche zu blockieren](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
