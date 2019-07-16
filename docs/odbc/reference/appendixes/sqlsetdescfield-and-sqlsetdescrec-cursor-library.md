---
title: SQLSetDescField und SQLSetDescRec (Cursorbibliothek) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125572"
---
# <a name="sqlsetdescfield-and-sqlsetdescrec-cursor-library"></a>SQLSetDescField und SQLSetDescRec (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLSetDescField** und **SQLSetDescRec** Funktionen in der Cursorbibliothek. Allgemeine Informationen zu diesen Funktionen finden Sie unter [SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md) und [SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Führt die Cursorbibliothek **SQLSetDescField** für Lesezeichenspalten festzulegen wenn er aufgerufen wird, um den Wert der Felder zurückzugeben:  
  
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
  
 Die Cursorbibliothek führt Aufrufe **SQLSetDescRec** für eine Lesezeichenspalte.  
  
 Bei der Arbeit mit einer ODBC- *2.x* -Treiber verwenden, gibt die Cursorbibliothek SQLSTATE HY090 zurück (ungültige Zeichenfolgen- oder Pufferlänge.) Wenn **SQLSetDescField** oder **SQLSetDescRec** aufgerufen wird Das SQL_DESC_OCTET_LENGTH-Feld für die Lesezeichen-Datensatz, der eine ARD auf einen Wert nicht gleich 4 festgelegt. Beim Arbeiten mit ODBC *3.x* -Treiber die Cursorbibliothek ermöglicht den Puffer, in eine beliebige Größe aufweisen.  
  
 Führt die Cursorbibliothek **SQLSetDescField** wenn er aufgerufen wird, um den Wert des Felds SQL_DESC_BIND_OFFSET_PTR SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE oder SQL_DESC_ROW_STATUS_PTR zurückzugeben. Diese Felder können für jede Zeile wird nicht nur die Lesezeichen-Zeile zurückgegeben werden.  
  
 Die Cursorbibliothek wird nicht ausgeführt, **SQLSetDescField** alle Deskriptorfeld als die zuvor aufgeführten Felder ändern. Wenn eine Anwendung ruft **SQLSetDescField** um jedes andere Feld festzulegen, während die Cursorbibliothek geladen ist, der Aufruf über an den Treiber übergeben wird.  
  
 Die Cursorbibliothek unterstützt die SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR Felder einer Zeile, der einen Anwendungsdienst-Deskriptor Zeile dynamisch ändern (nach einem Aufruf von **SQLExtendedFetch**, **SQLFetch**, oder **SQLFetchScroll**). Das Feld SQL_DESC_OCTET_LENGTH_PTR kann ein null-Zeiger nur für den Puffer der Länge für eine Spalte aufheben der Bindung geändert werden.  
  
 Die Cursorbibliothek unterstützt nicht das SQL_DESC_BIND_TYPE-Feld in einem APD oder ARD ändern, wenn ein Cursor geöffnet ist. Das Feld SQL_DESC_BIND_TYPE kann geändert werden, nur, wenn der Cursor geschlossen ist, und bevor Sie ein neuer Cursor geöffnet wird. Die einzige deskriptorfelder, dass die Cursorbibliothek ändern unterstützt, wenn ein Cursor geöffnet ist sind SQL_DESC_ARRAY_STATUS_PTR SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR und SQL_DESC_ROWS_PROCESSED_ PTR-WERT.  
  
 Die Cursorbibliothek ändern das Feld SQL_DESC_COUNT der ARD nach wird nicht unterstützt. **SQLExtendedFetch** oder **SQLFetchScroll** aufgerufen wurde und bevor der Cursor geschlossen wurde.
