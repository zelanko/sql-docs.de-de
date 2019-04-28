---
title: Relatives und absolutes Scrollen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 5ba05cb9079514750cf087149bae476efe0d8d41
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861510"
---
# <a name="relative-and-absolute-scrolling"></a>Relatives und absolutes Scrollen
Der Bildlauf Optionen in den meisten **SQLFetchScroll** positionieren Sie den Cursor relativ zur aktuellen Position oder eine absolute Position. **SQLFetchScroll** unterstützt das Abrufen der nächsten, vorherigen, ersten und letzten Rowsets als auch als relativen abrufen (das Rowset abrufen, *n* Zeilen vom Anfang des aktuellen Rowsets) und absoluten abrufen (Fetch das Rowset starten in Zeile *n*). Wenn *n* ist in einem absoluten Abruf negativ ist, werden Zeilen vom Ende des Resultsets gezählt. Folglich bedeutet, dass ein absoluter Abruf von Zeile-1 das Rowset abzurufen, das mit der letzten Zeile im Resultset beginnt.  
  
 Dynamische Cursor erkennen Zeilen eingefügt und aus dem Resultset gelöscht, es gibt also keine einfache Möglichkeit für dynamic-Cursor, die Zeile an eine bestimmte Anzahl als das Lesen vom Anfang des Resultsets, abzurufen, wodurch der möglicherweise sehr langsam ausgeführt wird. Darüber hinaus ist absoluten abrufen nicht sehr nützlich in dynamischen Cursorn da Zeilennummern ändern, wenn Zeilen eingefügt und gelöscht werden; aus diesem Grund kann nacheinander abrufen die gleiche Anzahl von Zeilen unterschiedliche Zeilen erzielt werden.  
  
 Anwendungen, die **SQLFetchScroll** nur Cursor-Funktionen, z. B. Berichte, sind wahrscheinlich passieren das Resultset auf ein einziges Mal und verwenden die Option zum Abrufen des nächsten Rowsets. Bildschirmbasierte Anwendungen, auf der anderen Seite können nutzen alle Funktionen von **SQLFetchScroll**. Wenn die Anwendung die Rowsetgröße auf die Anzahl der Zeilen, die auf dem Bildschirm angezeigt legt, und die Bildschirmpuffer an das Resultset bindet, kann es Vorgänge der Bildlaufleiste direkt in Aufrufe an übersetzen **SQLFetchScroll**.  
  
|Bildlaufleistenvorgang|SQLFetchScroll-Bildlaufoption|  
|--------------------------|-------------------------------------|  
|Bild auf|SQL_FETCH_PRIOR|  
|Bild ab|SQL_FETCH_NEXT|  
|Zeile auf|SQL_FETCH_RELATIVE mit *FetchOffset* gleich-1|  
|Zeile ab|SQL_FETCH_RELATIVE mit *FetchOffset* gleich 1|  
|Das Bildlauffeld, oben|SQL_FETCH_FIRST|  
|Das Bildlauffeld, unten|SQL_FETCH_LAST|  
|Zufällige Bildlauffeldposition|SQL_FETCH_ABSOLUTE|  
  
 Solche Anwendungen müssen auch das Bildlauffeld nach einem Bildlauf-Vorgang zu positionieren, das die aktuelle Zeilennummer und die Anzahl der Zeilen erforderlich ist. Für die aktuelle Zeilennummer, Anwendungen entweder des nachvollziehen die aktuelle Zeilennummer oder der Aufruf **SQLGetStmtAttr** mit dem SQL_ATTR_ROW_NUMBER-Attribut, um sie abzurufen.  
  
 Die Anzahl der Zeilen im Cursor, der die Größe des Ergebnisses ist festgelegt, wird als Feld SQL_DIAG_CURSOR_ROW_COUNT des Diagnose-Headers zur Verfügung. Der Wert in dieses Feld wird erst nach definiert **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResult** aufgerufen wurde. Diese Anzahl kann es sich um geschätzte Anzahl oder eine genaue Anzahl, abhängig von den Funktionen des Treibers sein. Vom Treiber unterstützt kann bestimmt werden, indem **SQLGetInfo** mit Informationen der Cursortypen-Attribute und überprüft, ob das SQL_CA2_CRC_APPROXIMATE oder SQL_CA2_CRC_EXACT Bit für den Typ des Cursors zurückgegeben wird.  
  
 Eine genaue Zeilenanzahl wird für einen dynamischen Cursor nicht unterstützt. Für andere Typen von Cursorn kann vom Treiber entweder genaue oder Ungefähre Zeilenanzahl, aber nicht beides unterstützt. Wenn der Treiber unterstützt, weder die genaue als auch die ungefähre Zeilenanzahl für einen bestimmten Cursor, der SQL_DIAG_CURSOR_ROW_COUNT-Feld enthält die Anzahl der Zeilen, die bisher abgerufen wurden. Unabhängig davon, welche der Treiber unterstützt **SQLFetchScroll** mit einer *Vorgang* von SQL_FETCH_LAST führt dazu, dass das SQL_DIAG_CURSOR_ROW_COUNT Feld die Anzahl der genauen Zeilen enthalten.
