---
title: SQLSetDescField und SQLSetDescRec (Cursor Bibliothek) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5a21af2a2067498a3ec495013554b70d6a86455a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125572"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField und SQLSetDescRec (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der Funktionen **SQLSetDescField** und **SQLSetDescRec** in der Cursor Bibliothek erläutert. Allgemeine Informationen zu diesen Funktionen finden Sie unter [SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md) und [SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Die Cursor Bibliothek führt **SQLSetDescField** aus, wenn Sie aufgerufen wird, um den Wert der Felder zurückzugeben, die für Lesezeichen Spalten festgelegt wurden:  
  
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
  
 Die Cursor Bibliothek führt Aufrufe von **SQLSetDescRec** für eine Lesezeichen Spalte aus.  
  
 Beim Arbeiten mit einem ODBC *2. x* -Treiber gibt die Cursor Bibliothek SQLSTATE HY090 (ungültige Zeichen folgen-oder Pufferlänge) zurück, wenn **SQLSetDescField** oder **SQLSetDescRec** aufgerufen wird, um das SQL_DESC_OCTET_LENGTH Feld für den Lesezeichen-Datensatz einer ARD auf einen nicht gleich 4-Wert festzulegen. Wenn Sie mit einem ODBC *3. x* -Treiber arbeiten, ermöglicht die Cursor Bibliothek die Größe des Puffers.  
  
 Die Cursor Bibliothek führt **SQLSetDescField** aus, wenn Sie aufgerufen wird, um den Wert des Felds "SQL_DESC_BIND_OFFSET_PTR", "SQL_DESC_BIND_TYPE", "SQL_DESC_ROW_ARRAY_SIZE" oder "SQL_DESC_ROW_STATUS_PTR" zurückzugeben. Diese Felder können für jede Zeile und nicht nur für die Lesezeichen Zeile zurückgegeben werden.  
  
 Die Cursor Bibliothek führt **SQLSetDescField** nicht aus, um ein anderes Deskriptorfeld zu ändern, als die zuvor erwähnten Felder. Wenn eine Anwendung **SQLSetDescField** aufruft, um beim Laden der Cursor Bibliothek ein anderes Feld festzulegen, wird der Aufruf an den Treiber weitergeleitet.  
  
 Die Cursor Bibliothek unterstützt das Ändern der SQL_DESC_DATA_PTR-, SQL_DESC_INDICATOR_PTR-und SQL_DESC_OCTET_LENGTH_PTR Felder beliebiger Zeilen eines Anwendungs Zeilen Deskriptors dynamisch (nach einem-Befehl von **SQLExtendedFetch**, **SQLFetch**oder **SQLFetchScroll**). Das SQL_DESC_OCTET_LENGTH_PTR Feld kann nur in einen NULL-Zeiger geändert werden, um die Bindung des Längen Puffers für eine Spalte aufzuheben.  
  
 Die Cursor Bibliothek bietet keine Unterstützung für das Ändern des SQL_DESC_BIND_TYPE Felds in einer APD oder einer ARD, wenn ein Cursor geöffnet ist. Das SQL_DESC_BIND_TYPE Feld kann nur geändert werden, nachdem der Cursor geschlossen und ein neuer Cursor geöffnet wurde. Die einzigen Deskriptorfelder, die von der Cursor Bibliothek geändert werden, wenn ein Cursor geöffnet ist, sind SQL_DESC_ARRAY_STATUS_PTR, SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR und SQL_DESC_ROWS_PROCESSED_ PTR.  
  
 Die Cursor Bibliothek bietet keine Unterstützung für das Ändern des SQL_DESC_COUNT Felds der ARD, nachdem **SQLExtendedFetch** oder **SQLFetchScroll** aufgerufen wurde und bevor der Cursor geschlossen wurde.
