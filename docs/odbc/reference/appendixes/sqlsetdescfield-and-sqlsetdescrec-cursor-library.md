---
title: SQLSetDescField und SQLSetDescRec (Cursorbibliothek) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetDescField function [ODBC], Cursor Library
- SQLSetDescRec function [ODBC], Cursor Library
ms.assetid: 4ccff067-85cd-4bfa-a6cd-7f28051fb5b9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b85eb84cdf48a1c2a441b8994076a9023d254f2d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300550"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField und SQLSetDescRec (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der Funktionen **SQLSetDescField** und **SQLSetDescRec** in der Cursorbibliothek erläutert. Allgemeine Informationen zu diesen Funktionen finden Sie unter [SQLSetDescField Function](../../../odbc/reference/syntax/sqlsetdescfield-function.md) und [SQLSetDescRec Function](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Die Cursorbibliothek führt **SQLSetDescField** aus, wenn sie aufgerufen wird, um den Wert der für Lesezeichenspalten festgelegten Felder zurückzugeben:  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_DATETIME_INTERVAL_CODE  
  
 SQL_DESC_SCALE  
  
 SQL_DESC_PRECISION  
  
 SQL_DESC_TYPE  
  
 SQL_DESC_NAME  
  
 SQL_DESC_UNNAMED  
  
 SQL_DESC_NULLABLE  
  
 Die Cursorbibliothek führt Aufrufe von **SQLSetDescRec** für eine Lesezeichenspalte aus.  
  
 Wenn Sie mit einem ODBC *2.x-Treiber* arbeiten, gibt die Cursorbibliothek SQLSTATE HY090 (Ungültige Zeichenfolge oder Pufferlänge) zurück, wenn **SQLSetDescField** oder **SQLSetDescRec** aufgerufen wird, um das SQL_DESC_OCTET_LENGTH Feld für den Lesezeichendatensatz einer ARD auf einen Wert nicht gleich 4 festzulegen. Wenn Sie mit einem ODBC *3.x-Treiber* arbeiten, lässt die Cursorbibliothek zu, dass der Puffer eine beliebige Größe hat.  
  
 Die Cursorbibliothek führt **SQLSetDescField** aus, wenn sie aufgerufen wird, um den Wert des Felds SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE oder SQL_DESC_ROW_STATUS_PTR zurückzugeben. Diese Felder können für jede Zeile zurückgegeben werden, nicht nur für die Lesezeichenzeile.  
  
 Die Cursorbibliothek führt **SQLSetDescField** nicht aus, um ein anderes Deskriptorfeld als die zuvor erwähnten Felder zu ändern. Wenn eine Anwendung **SQLSetDescField** aufruft, um ein anderes Feld festzulegen, während die Cursorbibliothek geladen wird, wird der Aufruf an den Treiber übergeben.  
  
 Die Cursorbibliothek unterstützt das dynamische Ändern der SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR Felder einer Zeile eines Anwendungszeilendeskriptors (nach einem Aufruf von **SQLExtendedFetch**, **SQLFetch**oder **SQLFetchScroll**). Das SQL_DESC_OCTET_LENGTH_PTR Feld kann nur in einen Nullzeiger geändert werden, um die Bindung des Längenpuffers für eine Spalte zu heben.  
  
 Die Cursorbibliothek unterstützt das Ändern des SQL_DESC_BIND_TYPE Feldes in einer APD oder ARD nicht, wenn ein Cursor geöffnet ist. Das SQL_DESC_BIND_TYPE Feld kann erst geändert werden, nachdem der Cursor geschlossen und ein neuer Cursor geöffnet wird. Die einzigen Deskriptorfelder, die die Cursorbibliothek beim Öffnen eines Cursors unterstützt, sind SQL_DESC_ARRAY_STATUS_PTR, SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR und SQL_DESC_ROWS_PROCESSED_PTR.  
  
 Die Cursorbibliothek unterstützt das Ändern des SQL_DESC_COUNT Feldes der ARD nicht, nachdem **SQLExtendedFetch** oder **SQLFetchScroll** aufgerufen wurde und bevor der Cursor geschlossen wurde.
