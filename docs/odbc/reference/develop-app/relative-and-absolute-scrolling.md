---
title: Relativer und absoluter Bildlauf | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e2034a3922dcd3db77113e08a6c48fe7ac39457f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138062"
---
# <a name="relative-and-absolute-scrolling"></a>Relatives und absolutes Scrollen
Die meisten Scrolloptionen in **SQLFetchScroll** positionieren den Cursor relativ zur aktuellen Position oder zu einer absoluten Position. **SQLFetchScroll** unterstützt das Abrufen der nächsten, vorherigen, ersten und letzten Rowsets sowie das relative abrufen (Abrufen der Rowsets *n* Zeilen vom Anfang des aktuellen Rowsets) und das absolute abrufen (Abrufen des Rowsets ab Zeile *n*). Wenn *n* bei einem absoluten Abruf negativ ist, werden Zeilen vom Ende des Resultsets gezählt. Folglich bedeutet das absolute Abrufen von Zeile-1, dass das Rowset, das mit der letzten Zeile im Resultset beginnt, abgerufen wird.  
  
 Dynamische Cursor erkennen Zeilen, die in das Resultset eingefügt und daraus gelöscht werden. es gibt also keine einfache Möglichkeit, die Zeile von dynamischen Cursorn aus dem Anfang des Resultsets abzurufen. Dies ist wahrscheinlich langsam. Außerdem ist das absolute abrufen bei dynamischen Cursorn nicht sehr nützlich, da sich die Zeilennummern ändern, wenn Zeilen eingefügt und gelöscht werden. aus diesem Grund kann das Abrufen der gleichen Zeilennummer zu unterschiedlichen Zeilen führen.  
  
 Anwendungen, die **SQLFetchScroll** nur für Ihre Block Cursor Funktionen verwenden, wie z. b. Berichte, werden das Resultset wahrscheinlich ein einziges Mal durchlaufen, wobei nur die Option zum Abrufen des nächsten Rowsets verwendet wird. Auf der anderen Seite können bildschirmbasierte Anwendungen alle Funktionen von **SQLFetchScroll**nutzen. Wenn die Anwendung die Rowsetgröße auf die auf dem Bildschirm angezeigte Anzahl von Zeilen festlegt und die Bildschirm Puffer an das Resultset bindet, können Schiebe leisten Vorgänge direkt in Aufrufe von **SQLFetchScroll**übersetzt werden.  
  
|Bildlaufleistenvorgang|SQLFetchScroll-Bildlaufoption|  
|--------------------------|-------------------------------------|  
|Bild auf|SQL_FETCH_PRIOR|  
|Bild ab|SQL_FETCH_NEXT|  
|Zeile auf|SQL_FETCH_RELATIVE mit *FetchOffset* gleich-1|  
|Zeile ab|SQL_FETCH_RELATIVE mit *FetchOffset* gleich 1|  
|Bild Lauf Feld oben|SQL_FETCH_FIRST|  
|Bild Lauf Feld unten|SQL_FETCH_LAST|  
|Zufällige Bildlauffeldposition|SQL_FETCH_ABSOLUTE|  
  
 Solche Anwendungen müssen das Bild Lauf Feld auch nach einem scrollvorgang positionieren, für den die aktuelle Zeilennummer und die Anzahl der Zeilen erforderlich sind. Bei der aktuellen Zeilennummer können Anwendungen entweder die aktuelle Zeilennummer nachverfolgen oder **SQLGetStmtAttr** mit dem SQL_ATTR_ROW_NUMBER-Attribut aufrufen, um Sie abzurufen.  
  
 Die Anzahl der Zeilen im Cursor, d. h. die Größe des Resultsets, ist als SQL_DIAG_CURSOR_ROW_COUNT Feld des Diagnose Headers verfügbar. Der Wert in diesem Feld wird erst definiert, nachdem **SQLExecute**, **SQLExecDirect**oder **sqlmoreresult** aufgerufen wurde. Diese Anzahl kann je nach den Funktionen des Treibers entweder eine ungefähre Anzahl oder eine genaue Anzahl sein. Die Unterstützung des Treibers kann durch Aufrufen von **SQLGetInfo** mit den Informationstypen der Cursor Attribute ermittelt werden, und es wird überprüft, ob die SQL_CA2_CRC_APPROXIMATE oder SQL_CA2_CRC_EXACT Bit für den Cursortyp zurückgegeben wird.  
  
 Eine genaue Zeilen Anzahl wird für einen dynamischen Cursor nie unterstützt. Bei anderen Cursor Typen kann der Treiber entweder eine genaue oder ungefähre Zeilen Anzahl unterstützen, aber nicht beides. Wenn der Treiber weder die genaue noch die ungefähre Zeilen Anzahl für einen bestimmten Cursortyp unterstützt, enthält das SQL_DIAG_CURSOR_ROW_COUNT Feld die Anzahl der bisher abgerufenen Zeilen. Unabhängig davon, was der Treiber unterstützt, bewirkt **SQLFetchScroll** mit einem SQL_FETCH_LAST *Vorgang* , dass das SQL_DIAG_CURSOR_ROW_COUNT Feld die genaue Zeilen Anzahl enthält.
