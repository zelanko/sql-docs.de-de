---
title: Scrollen und Abrufen von Zeilen (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- fetches [ODBC], scrollable cursors
- cursors [ODBC], scrollable
- scrolling rows [ODBC]
ms.assetid: c43764cb-5841-4b89-9dc0-984a7488b3c1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 72d262bf73e69388f65ff281e62235d2d831669e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304201"
---
# <a name="scrolling-and-fetching-rows-odbc"></a>Durchscrollen und Abrufen von Zeilen (ODBC)
Wenn Sie einen scrollbaren Cursor verwenden, rufen Anwendungen **SQLFetchScroll** auf, um den Cursor zu positionieren und Zeilen abzurufen. **SQLFetchScroll** unterstützt relatives Scrollen (nächste, vorherige und relative *n* Zeilen), absolutes Scrollen (erste, letzte und Zeile *n)* und Positionierung nach Lesezeichen. Die *Argumente FetchOrientation* und *FetchOffset* in **SQLFetchScroll** geben an, welches Rowset abgerufen werden soll, wie in den folgenden Diagrammen gezeigt.  
  
 ![Abrufen des nächsten, des vorherigen, des ersten und des letzten Rowsets](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **Abrufen des nächsten, des vorherigen, des ersten und des letzten Rowsets**  
  
 ![Abrufen des absoluten, des relativen und des mit Lesezeichen markierten Rowsets](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **Abrufen von absoluten, relativen und lesezeichenmarkierten Rowsets**  
  
 **SQLFetchScroll** positioniert den Cursor in der angegebenen Zeile und gibt die Zeilen im Rowset zurück, die mit dieser Zeile beginnen. Wenn das angegebene Rowset das Ende des Resultsets überlappt, wird ein teiles Rowset zurückgegeben. Wenn das angegebene Rowset den Anfang des Resultsets überlappt, wird in der Regel das erste Rowset im Resultset zurückgegeben. Ausführliche Informationen finden Sie in der [SQLFetchScroll-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlfetchscroll-function.md)  
  
 In einigen Fällen möchte die Anwendung den Cursor möglicherweise positionieren, ohne Daten abzurufen. Sie kann z. B. testen, ob eine Zeile vorhanden ist, oder einfach das Lesezeichen für die Zeile abrufen, ohne andere Daten über das Netzwerk zu bringen. Dazu wird das Attribut SQL_ATTR_RETRIEVE_DATA-Anweisung auf SQL_RD_OFF festgelegt. Die an die Lesezeichenspalte gebundene Variable (falls vorhanden) wird immer aktualisiert, unabhängig von der Einstellung dieses Anweisungsattributs.  
  
 Nachdem das Rowset abgerufen wurde, kann die Anwendung **SQLSetPos** aufrufen, um es in einer bestimmten Zeile im Rowset zu positionieren oder Zeilen im Rowset zu aktualisieren. Weitere Informationen zur Verwendung von **SQLSetPos**finden Sie unter [Aktualisieren von Daten mit SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
> [!NOTE]  
>  Scrollen wird in ODBC 2 unterstützt. *x-Treiber* von **SQLExtendedFetch**. Weitere Informationen finden Sie unter [Blockcursors, Scrollable Cursors und Backward Compatibility](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)in Anhang G: Treiberrichtlinien für Abwärtskompatibilität.
