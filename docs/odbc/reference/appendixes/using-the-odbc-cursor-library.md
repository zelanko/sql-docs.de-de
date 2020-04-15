---
title: Verwenden der ODBC-Cursorbibliothek | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], using cursor library
- cursor library [ODBC], using cursor library
ms.assetid: 9653f2f8-ccfc-4220-99ef-601dc0fa641c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c740ed78de51684eac38ad0c54ab2224986018d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301401"
---
# <a name="using-the-odbc-cursor-library"></a>Verwenden der ODBC-Cursorbibliothek
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Um die ODBC-Cursorbibliothek zu verwenden, eine Anwendung:  
  
1.  Ruft **SQLSetConnectAttr** mit einem *Attribut* von SQL_ATTR_ODBC_CURSORS auf, um anzugeben, wie die Cursorbibliothek mit einer bestimmten Verbindung verwendet werden soll. Die Cursorbibliothek kann immer verwendet werden (SQL_CUR_USE_ODBC), die nur verwendet wird, wenn der Treiber keine scrollbaren Cursor (SQL_CUR_USE_IF_NEEDED) unterstützt oder nie verwendet wird (SQL_CUR_USE_DRIVER).  
  
2.  Ruft **SQLConnect**, **SQLDriverConnect**oder **SQLBrowseConnect** auf, um eine Verbindung mit der Datenquelle herzustellen.  
  
3.  Ruft **SQLSetStmtAttr** auf, um den Cursortyp (SQL_ATTR_CURSOR_TYPE), die Parallelität (SQL_ATTR_CONCURRENCY) und die Rowsetgröße (SQL_ATTR_ROW_ARRAY_SIZE) anzugeben. Die Cursorbibliothek unterstützt vorwärts- und statische Cursor. Vorwärtscursor müssen schreibgeschützt sein, während statische Cursor schreibgeschützt sein oder optimistische Parallelitätssteuerelemente verwenden können, die Werte vergleichen.  
  
4.  Ordnet einen oder mehrere Rowsetpuffer zu und ruft **SQLBindCol** ein oder mehrere Male auf, um diese Puffer an Resultsetspalten zu binden.  
  
5.  Generiert ein Resultset, indem eine **SELECT-Anweisung** oder eine Prozedur ausgeführt oder eine Katalogfunktion aufgerufen wird. Wenn die Anwendung positionierte Aktualisierungsanweisungen ausführt, sollte sie eine **SELECT FOR UPDATE-Anweisung** ausführen, um das Resultset zu generieren.  
  
6.  Ruft **SQLFetch** oder **SQLFetchScroll** ein oder mehrere Male auf, um durch das Resultset zu scrollen.  
  
 Die Anwendung kann Datenwerte in den Rowsetpuffern ändern. Um die Rowsetpuffer mit Daten aus dem Cache der Cursorbibliothek zu aktualisieren, ruft eine Anwendung **SQLFetchScroll** auf, wobei das *Argument FetchOrientation* auf SQL_FETCH_RELATIVE und das *FetchOffset-Argument* auf 0 festgelegt ist.  
  
 Um Daten aus einer ungebundenen Spalte abzurufen, ruft die Anwendung **SQLSetPos** auf, um den Cursor in der gewünschten Zeile zu positionieren. Anschließend wird **SQLGetData** zum Abrufen der Daten auf.  
  
 Um die Anzahl der Zeilen zu ermitteln, die aus der Datenquelle abgerufen wurden, ruft die Anwendung **SQLRowCount**auf.
