---
title: Scrollen und Abrufen von Zeilen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0ae9f1079f329951045d4b3f61b39c12efc153fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302490"
---
# <a name="scrolling-and-fetching-rows"></a>Bildläufe und Abrufen von Zeilen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Um einen bildlauffähigen Cursor zu verwenden, muss eine ODBC-Anwendung folgende Bedingungen erfüllen:  
  
-   Legen Sie die Cursorfunktionen mit [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)fest.  
  
-   Öffnen Sie den Cursor mit **SQLExecute** oder **SQLExecDirect**.  
  
-   Scrollen und Abrufen von Zeilen mit **SQLFetch** oder [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md).  
  
 Sowohl **SQLFetch als** auch **SQLFetchSroll** können Zeilenblöcke gleichzeitig abrufen. Die Anzahl der zurückgegebenen Zeilen wird mithilfe von **SQLSetStmtAttr** angegeben, um den Parameter SQL_ATTR_ROW_ARRAY_SIZE festzulegen.  
  
 ODBC-Anwendungen können **SQLFetch** verwenden, um über einen Vorwärtscursor abzurufen.  
  
 **SQLFetchScroll** wird verwendet, um einen Cursor zu scrollen. **SQLFetchScroll** unterstützt das Abrufen der nächsten, vorherigen, ersten und letzten Rowsets zusätzlich zum relativen Abrufen (Abrufen des Rowsets *n* Zeilen vom Anfang des aktuellen Rowsets) und absolutes Abrufen (Abrufen des Rowsets ab Zeile *n*). Wenn *n* in einem absoluten Abruf negativ ist, werden Zeilen vom Ende des Resultsets gezählt. Ein absoluter Abruf von Zeile -1 bedeutet den Abruf des Rowsets, das mit der letzten Zeile im Resultset beginnt.  
  
 Anwendungen, die **SQLFetchScroll** nur für seine Blockcursorfunktionen verwenden, z. B. Berichte, durchlaufen das Resultset wahrscheinlich ein einziges Mal, indem sie nur die Option zum Abrufen des nächsten Rowsets verwenden. Bildschirmbasierte Anwendungen hingegen können alle Funktionen von **SQLFetchScroll**nutzen. Wenn die Anwendung die Rowsetgröße auf die Anzahl der auf dem Bildschirm angezeigten Zeilen festlegt und die Bildschirmpuffer an das Resultset bindet, kann sie Bildlaufleistenoperationen direkt in Aufrufe von **SQLFetchScroll**übersetzen.  
  
|Bildlaufleistenvorgang|SQLFetchScroll-Bildlaufoption|  
|--------------------------|-------------------------------------|  
|Bild auf|SQL_FETCH_PRIOR|  
|Bild ab|SQL_FETCH_NEXT|  
|Zeile auf|SQL_FETCH_RELATIVE mit FetchOffset gleich -1|  
|Zeile ab|SQL_FETCH_RELATIVE mit FetchOffset gleich 1|  
|Bildlauffeld nach oben|SQL_FETCH_FIRST|  
|Bildlauffeld nach unten|SQL_FETCH_LAST|  
|Zufällige Bildlauffeldposition|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Kennzeichnen von Zeilen in ODBC](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Cursorn &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
