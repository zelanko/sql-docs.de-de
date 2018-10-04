---
title: Scrollen und fetchen von Zeilen (ODBC) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 884c798e14964fbcaaf3ca9ba6656f4d62738fe8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642748"
---
# <a name="scrolling-and-fetching-rows-odbc"></a>Durchscrollen und Abrufen von Zeilen (ODBC)
Wenn Sie einen bildlauffähigen Cursor verwenden, um Anwendungen Aufrufen **SQLFetchScroll** , positionieren Sie den Cursor und Fetch-Zeilen. **SQLFetchScroll** relative Bildlauf unterstützt (Weiter vor und relativ *n* Zeilen), absolute Bildlauf (Vorname, Nachname und Zeile *n*), und die Positionierung von Lesezeichen. Die *FetchOrientation* und *FetchOffset* Argumente in **SQLFetchScroll** welche Rowset abzurufen, geben Sie wie in den folgenden Diagrammen dargestellt.  
  
 ![Abrufen des nächsten, vorherigen, ersten und letzten Rowsets](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **Abrufen des nächsten, vorherigen, ersten und letzten Rowsets**  
  
 ![Abrufen des absoluten, relativen und mit Lesezeichen markierten Rowsets](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **Abrufen des absoluten, relativen und mit Lesezeichen markierten Rowsets**  
  
 **SQLFetchScroll** platziert den Cursor in die angegebene Zeile und gibt die Zeilen im Rowset ab, die mit dieser Zeile zurück. Wenn das angegebene Rowset, das Ende des Resultsets überlappt, wird eine partielle Rowset zurückgegeben. Wenn das angegebene Rowset der Start des Ergebnisses überlappt festgelegt ist, wird das erste Rowset im Ergebnis wird in der Regel zurückgegeben; Ausführliche Informationen finden Sie unter den [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) funktionsbeschreibung.  
  
 In einigen Fällen kann die Anwendung soll, um den Cursor zu positionieren, ohne das Abrufen von Daten. Beispielsweise möchten sie überprüfen, ob eine Zeile vorhanden ist oder nur das Lesezeichen für die Zeile zu erhalten, ohne die andere Daten über das Netzwerk. Zu diesem Zweck wird das SQL_ATTR_RETRIEVE_DATA-Anweisungsattribut auf SQL_RD_OFF. Die Variable an die Lesezeichenspalte (sofern vorhanden) gebunden werden unabhängig von der Einstellung dieses Attributs Anweisung immer aktualisiert.  
  
 Nach dem das Rowset abgerufen wurde, kann die Anwendung aufrufen **SQLSetPos** zu einer bestimmten Zeile im Rowset oder aktualisieren Sie Zeilen im Rowset zu positionieren. Weitere Informationen zur Verwendung von **SQLSetPos**, finden Sie unter [Aktualisieren von Daten mit SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
> [!NOTE]  
>  Durchführen eines Bildlaufs wird in ODBC 2. unterstützt. *x* Treiber durch **SQLExtendedFetch**. Weitere Informationen finden Sie unter [Blockcursor, scrollbare Cursor und Abwärtskompatibilität](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)in Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität.
