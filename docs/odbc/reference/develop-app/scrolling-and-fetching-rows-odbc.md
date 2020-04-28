---
title: Scrollen und Abrufen von Zeilen (ODBC) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304201"
---
# <a name="scrolling-and-fetching-rows-odbc"></a>Durchscrollen und Abrufen von Zeilen (ODBC)
Wenn Sie einen Bild lauffähigen Cursor verwenden, rufen Anwendungen **SQLFetchScroll** auf, um den Cursor zu positionieren und Zeilen abzurufen. **SQLFetchScroll** unterstützt den relativen Bildlauf (Next, vorherige und relative *n* Zeilen), den absoluten Bildlauf (First, Last und Row *n*) und die Positionierung nach Lesezeichen. Die Argumente " *FetchOrientation* " und " *FetchOffset* " in **SQLFetchScroll** geben an, welches Rowset abgerufen werden soll, wie in den folgenden Diagrammen dargestellt.  
  
 ![Abrufen des nächsten, des vorherigen, des ersten und des letzten Rowsets](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **Abrufen des nächsten, des vorherigen, des ersten und des letzten Rowsets**  
  
 ![Abrufen des absoluten, des relativen und des mit Lesezeichen markierten Rowsets](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **Abrufen von absoluten, relativen und mit Lesezeichen markierten Rowsets**  
  
 **SQLFetchScroll** positioniert den Cursor in die angegebene Zeile und gibt die Zeilen im Rowset zurück, beginnend mit dieser Zeile. Wenn das angegebene Rowset das Ende des Resultsets überlappt, wird ein partielles Rowset zurückgegeben. Wenn das angegebene Rowset den Anfang des Resultsets überlappt, wird normalerweise das erste Rowset im Resultset zurückgegeben. Ausführliche Informationen finden Sie in der Beschreibung der [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) -Funktion.  
  
 In einigen Fällen kann die Anwendung den Cursor positionieren, ohne Daten abzurufen. Beispielsweise kann es sinnvoll sein, zu testen, ob eine Zeile vorhanden ist, oder nur das Lesezeichen für die Zeile zu erhalten, ohne dass andere Daten über das Netzwerk übertragen werden. Zu diesem Zweck wird das Attribut SQL_ATTR_RETRIEVE_DATA Anweisung auf SQL_RD_OFF festgelegt. Die an die Lesezeichen Spalte (falls vorhanden) gebundene Variable wird immer aktualisiert, unabhängig von der Einstellung dieses Anweisungs Attributs.  
  
 Nachdem das Rowset abgerufen wurde, kann die Anwendung **SQLSetPos** aufrufen, um Sie an eine bestimmte Zeile im Rowset zu positionieren oder Zeilen im Rowset zu aktualisieren. Weitere Informationen zur Verwendung von **SQLSetPos**finden Sie unter [Aktualisieren von Daten mit SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
> [!NOTE]  
>  Das Scrollen wird in ODBC 2 unterstützt. *x* -Treiber von **sqlextendecodfetch**. Weitere Informationen finden Sie unter [Blockieren von Cursorn, scrollfähigen Cursorn und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)in Anhang G: Treiber Richtlinien zur Abwärtskompatibilität.
