---
title: Scrollen und Abrufen von Zeilen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a0c0f7f2cad7eaecc212e2283fab7fc7d69f2ee7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63207126"
---
# <a name="scrolling-and-fetching-rows"></a>Bildläufe und Abrufen von Zeilen
  Um einen bildlauffähigen Cursor zu verwenden, muss eine ODBC-Anwendung folgende Bedingungen erfüllen:  
  
-   Legen Sie die Cursor Funktionen mithilfe von [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)fest.  
  
-   Öffnen Sie den Cursor mithilfe von **SQLExecute** oder **SQLExecDirect**.  
  
-   Scrollen und Abrufen von Zeilen mithilfe von **SQLFetch** oder [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).  
  
 Sowohl **SQLFetch** als auch **sqlfetchsroll** können Zeilen Blöcke gleichzeitig abrufen. Die Anzahl der zurückgegebenen Zeilen wird mithilfe von **SQLSetStmtAttr** festgelegt, um den SQL_ATTR_ROW_ARRAY_SIZE-Parameter festzulegen.  
  
 ODBC-Anwendungen können **SQLFetch** zum Abrufen über einen Vorwärts Cursor verwenden.  
  
 **SQLFetchScroll** wird verwendet, um einen Bildlauf um einen Cursor durchführen. **SQLFetchScroll** unterstützt das Abrufen der nächsten, vorherigen, ersten und letzten Rowsets zusätzlich zum relativen Abrufen (Abrufen der Rowsets *n* Zeilen vom Anfang des aktuellen Rowsets) und das absolute abrufen (Abrufen des Rowsets ab Zeile *n*). Wenn *n* bei einem absoluten Abruf negativ ist, werden Zeilen vom Ende des Resultsets gezählt. Ein absoluter Abruf von Zeile -1 bedeutet den Abruf des Rowsets, das mit der letzten Zeile im Resultset beginnt.  
  
 Anwendungen, die **SQLFetchScroll** nur für Ihre Block Cursor Funktionen verwenden, wie z. b. Berichte, werden das Resultset wahrscheinlich ein einziges Mal durchlaufen, wobei nur die Option zum Abrufen des nächsten Rowsets verwendet wird. Auf der anderen Seite können bildschirmbasierte Anwendungen alle Funktionen von **SQLFetchScroll**nutzen. Wenn die Anwendung die Rowsetgröße auf die auf dem Bildschirm angezeigte Anzahl von Zeilen festlegt und die Bildschirm Puffer an das Resultset bindet, können Schiebe leisten Vorgänge direkt in Aufrufe von **SQLFetchScroll**übersetzt werden.  
  
|Bildlaufleistenvorgang|SQLFetchScroll-Bildlaufoption|  
|--------------------------|-------------------------------------|  
|Bild auf|SQL_FETCH_PRIOR|  
|Bild ab|SQL_FETCH_NEXT|  
|Zeile auf|SQL_FETCH_RELATIVE mit FetchOffset gleich-1|  
|Zeile ab|SQL_FETCH_RELATIVE mit FetchOffset gleich 1|  
|Bildlauffeld nach oben|SQL_FETCH_FIRST|  
|Bildlauffeld nach unten|SQL_FETCH_LAST|  
|Zufällige Bildlauffeldposition|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Kennzeichnen von Zeilen in ODBC](scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Cursorn &#40;ODBC-&#41;](using-cursors-odbc.md)  
  
  
