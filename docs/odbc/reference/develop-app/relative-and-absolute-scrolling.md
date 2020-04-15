---
title: Relative und absolute Scrolling | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- absolute scrolling [ODBC]
- relative scrolling [ODBC]
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: 3d0ff48d-fef5-4c01-bb1d-a583e6269b66
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae0ed5af8d116a3038b55b1e3d68231154c2a35c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300100"
---
# <a name="relative-and-absolute-scrolling"></a>Relatives und absolutes Scrollen
Die meisten Bildlaufoptionen in **SQLFetchScroll** positionieren den Cursor relativ zur aktuellen Position oder zu einer absoluten Position. **SQLFetchScroll** unterstützt das Abrufen der nächsten, vorherigen, ersten und letzten Rowsets sowie das relative Abrufen (Abrufen des Rowsets *n* Zeilen vom Anfang des aktuellen Rowsets) und absolutes Abrufen (Abrufen des Rowsets ab Zeile *n*). Wenn *n* in einem absoluten Abruf negativ ist, werden Zeilen vom Ende des Resultsets gezählt. Daher bedeutet ein absoluter Abruf von Zeile -1, das Rowset abzurufen, das mit der letzten Zeile im Resultset beginnt.  
  
 Dynamische Cursor erkennen Zeilen, die in das Resultset eingefügt und aus diesem gelöscht wurden, sodass es für dynamische Cursor keine einfache Möglichkeit gibt, die Zeile unter einer bestimmten Zahl abzurufen, die nicht vom Anfang des Resultsets aus gelesen wird, was wahrscheinlich langsam ist. Darüber hinaus ist absolutes Abrufen bei dynamischen Cursorn nicht sehr nützlich, da sich Zeilennummern ändern, wenn Zeilen eingefügt und gelöscht werden. Daher kann das sukzessive Abrufen derselben Zeilennummer zu unterschiedlichen Zeilen führen.  
  
 Anwendungen, die **SQLFetchScroll** nur für seine Blockcursorfunktionen verwenden, z. B. Berichte, durchlaufen das Resultset wahrscheinlich ein einziges Mal, indem sie nur die Option zum Abrufen des nächsten Rowsets verwenden. Bildschirmbasierte Anwendungen hingegen können alle Funktionen von **SQLFetchScroll**nutzen. Wenn die Anwendung die Rowsetgröße auf die Anzahl der auf dem Bildschirm angezeigten Zeilen festlegt und die Bildschirmpuffer an das Resultset bindet, kann sie Bildlaufleistenoperationen direkt in Aufrufe von **SQLFetchScroll**übersetzen.  
  
|Bildlaufleistenvorgang|SQLFetchScroll-Bildlaufoption|  
|--------------------------|-------------------------------------|  
|Bild auf|SQL_FETCH_PRIOR|  
|Bild ab|SQL_FETCH_NEXT|  
|Zeile auf|SQL_FETCH_RELATIVE mit *FetchOffset* gleich -1|  
|Zeile ab|SQL_FETCH_RELATIVE mit *FetchOffset* gleich 1|  
|Scroll-Box oben|SQL_FETCH_FIRST|  
|Scroll-Box unten|SQL_FETCH_LAST|  
|Zufällige Bildlauffeldposition|SQL_FETCH_ABSOLUTE|  
  
 Solche Anwendungen müssen auch das Bildlauffeld nach einem Bildlaufvorgang positionieren, der die aktuelle Zeilennummer und die Anzahl der Zeilen erfordert. Für die aktuelle Zeilennummer können Anwendungen entweder die aktuelle Zeilennummer nachverfolgen oder **SQLGetStmtAttr** mit dem attribut SQL_ATTR_ROW_NUMBER aufrufen, um sie abzurufen.  
  
 Die Anzahl der Zeilen im Cursor, die die Größe des Resultsets darstellt, ist als SQL_DIAG_CURSOR_ROW_COUNT Feld des Diagnoseheaders verfügbar. Der Wert in diesem Feld wird erst definiert, nachdem **SQLExecute**, **SQLExecDirect**oder **SQLMoreResult** aufgerufen wurden. Diese Anzahl kann je nach den Fähigkeiten des Treibers entweder eine ungefähre Anzahl oder eine exakte Anzahl sein. Die Unterstützung des Treibers kann bestimmt werden, indem **SQLGetInfo** mit den Cursorattributen Informationstypen aufgerufen und überprüft wird, ob die SQL_CA2_CRC_APPROXIMATE oder SQL_CA2_CRC_EXACT Bit für den Cursortyp zurückgegeben wird.  
  
 Eine genaue Zeilenanzahl wird für einen dynamischen Cursor nie unterstützt. Bei anderen Cursortypen kann der Treiber entweder exakte oder ungefähre Zeilenanzahlen unterstützen, jedoch nicht beides. Wenn der Treiber für einen bestimmten Cursortyp weder genaue noch ungefähre Zeilenanzahlen unterstützt, enthält das Feld SQL_DIAG_CURSOR_ROW_COUNT die Anzahl der Zeilen, die bisher abgerufen wurden. Unabhängig davon, was der Treiber unterstützt, bewirkt **SQLFetchScroll** mit einem *Vorgang* von SQL_FETCH_LAST, dass das feld SQL_DIAG_CURSOR_ROW_COUNT die genaue Zeilenanzahl enthält.
