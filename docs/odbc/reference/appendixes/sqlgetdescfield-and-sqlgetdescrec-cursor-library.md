---
title: SQLGetDescField und SQLGetDescRec (Cursorbibliothek) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307831"
---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>SQLGetDescField und SQLGetDescRec (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der Funktionen **SQLGetDescField** und **SQLGetDescRec** in der Cursorbibliothek erläutert. Allgemeine Informationen zu diesen Funktionen finden Sie unter [SQLGetDescField Function](../../../odbc/reference/syntax/sqlgetdescfield-function.md) und [SQLGetDescRec Function](../../../odbc/reference/syntax/sqlgetdescrec-function.md).  
  
 Die Cursorbibliothek führt **SQLGetDescRec** aus, um Metadaten für Lesezeichenspalten zurückzugeben. Die Cursorbibliothek führt **SQLGetDescField** aus, um dieselben Felder zurückzugeben, die von **SQLGetDescRec**zurückgegeben werden, die SQL_DESC_NAME, SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE und SQL_DESC_NULLABLE sind. Aus Gründen der Konsistenz gibt **SQLGetDescField** auch SQL_DESC_UNNAMED zurück.  
  
 Die Cursorbibliothek führt **SQLGetDescField** aus, wenn sie aufgerufen wird, um den Wert der folgenden Felder zurückzugeben, die für die Bindung von Lesezeichenspalten festgelegt sind: SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR und SQL_DESC_LENGTH.  
  
 Die Cursorbibliothek führt **SQLGetDescField** aus, wenn sie aufgerufen wird, um den Wert des Felds SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE oder SQL_DESC_ROW_STATUS_PTR zurückzugeben. Diese Felder können für jede Zeile zurückgegeben werden, nicht nur für die Lesezeichenzeile.  
  
 Wenn eine Anwendung **SQLGetDescField** aufruft, um den Wert eines anderen Felds als des zuvor genannten zurückzugeben, übergibt die Cursorbibliothek den Aufruf an den Treiber.
