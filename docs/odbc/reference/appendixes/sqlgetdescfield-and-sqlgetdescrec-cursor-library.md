---
title: SQLGetDescField und SQLGetDescRec (Cursor Bibliothek) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetDescField function [ODBC], Cursor Library
- SQLGetDescRec function [ODBC], Cursor Library
ms.assetid: 1a801f22-6fea-48aa-a723-3187a2ad852b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 49ceea6b6180e1b51f2f103f74412c3e2b4cbe02
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307831"
---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>SQLGetDescField und SQLGetDescRec (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der Funktionen **SQLGetDescField** und **SQLGetDescRec** in der Cursor Bibliothek erläutert. Allgemeine Informationen zu diesen Funktionen finden Sie unter [SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md) und [SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md).  
  
 Die Cursor Bibliothek führt **SQLGetDescRec** aus, um Metadaten für Lesezeichen Spalten zurückzugeben. Die Cursor Bibliothek führt **SQLGetDescField** aus, um dieselben von **SQLGetDescRec**zurückgegebenen Felder zurückzugeben, die SQL_DESC_NAME, SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE und SQL_DESC_NULLABLE sind. Aus Konsistenz Gründen gibt **SQLGetDescField** auch SQL_DESC_UNNAMED zurück.  
  
 Die Cursor Bibliothek führt **SQLGetDescField** aus, wenn Sie aufgerufen wird, um den Wert der folgenden Felder zurückzugeben, die für die Bindung von Lesezeichen Spalten festgelegt sind: SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR und SQL_DESC_LENGTH.  
  
 Die Cursor Bibliothek führt **SQLGetDescField** aus, wenn Sie aufgerufen wird, um den Wert des Felds "SQL_DESC_BIND_OFFSET_PTR", "SQL_DESC_BIND_TYPE", "SQL_DESC_ROW_ARRAY_SIZE" oder "SQL_DESC_ROW_STATUS_PTR" zurückzugeben. Diese Felder können für jede Zeile und nicht nur für die Lesezeichen Zeile zurückgegeben werden.  
  
 Wenn eine Anwendung **SQLGetDescField** aufruft, um den Wert eines anderen Felds als den zuvor erwähnten zurückzugeben, übergibt die Cursor Bibliothek den Aufruf an den Treiber.
