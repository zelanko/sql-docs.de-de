---
description: ODBC-Funktionen und die Cursorbibliothek
title: ODBC-Funktionen und die Cursor Bibliothek | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c609d0fb-787a-4b39-9673-332d411b3d63
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6aa156a1fe4a6ebecb33b0c0401ae116226a80e9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466125"
---
# <a name="odbc-functions-and-the-cursor-library"></a>ODBC-Funktionen und die Cursorbibliothek
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 Wenn die ODBC-Cursor Bibliothek für eine Verbindung aktiviert ist, ruft der Treiber-Manager Funktionen in der Cursor Bibliothek anstelle des Treibers auf. Die Cursor Bibliothek führt entweder die Funktion aus oder ruft Sie im angegebenen Treiber auf.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [ODBC-Funktionen, die von der Cursorbibliothek ausgeführt](../../../odbc/reference/appendixes/odbc-functions-executed-by-the-cursor-library.md)  
  
-   [ODBC-Funktionen, die von der Cursorbibliothek nicht ausgeführt werden](../../../odbc/reference/appendixes/odbc-functions-not-executed-by-the-cursor-library.md)  
  
-   [SQLBindCol (Cursor Library) (SQLBindCol (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlbindcol-cursor-library.md)  
  
-   [SQLBindParameter (Cursor Library) (SQLBindParameter (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlbindparameter-cursor-library.md)  
  
-   [SQLBulkOperations (Cursor Bibliothek)](../../../odbc/reference/appendixes/sqlbulkoperations-and-the-cursor-library.md)  
  
-   [SQLCloseCursor (Cursor Bibliothek)](../../../odbc/reference/appendixes/sqlclosecursor-odbc.md)  
  
-   [SQLEndTran (Cursor Library) (SQLEndTran (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlendtran-cursor-library.md)  
  
-   [SQLExtendedFetch (Cursor Library) (SQLExtendedFetch (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlextendedfetch-cursor-library.md)  
  
-   [SQLFetch (Cursor Library) (SQLFetch (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlfetch-cursor-library.md)  
  
-   [SQLFetchScroll (Cursor Library) (SQLFetchScroll (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlfetchscroll-cursor-library.md)  
  
-   [SQLFreeStmt (Cursor Library) (SQLFreeStmt (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlfreestmt-cursor-library.md)  
  
-   [SQLGetData (Cursor Library) (SQLGetData (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlgetdata-cursor-library.md)  
  
-   [SQLGetDescField und SQLGetDescRec (Cursorbibliothek)](../../../odbc/reference/appendixes/sqlgetdescfield-and-sqlgetdescrec-cursor-library.md)  
  
-   [SQLGetFunctions (Cursor Library) (SQLGetFunctions (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlgetfunctions-cursor-library.md)  
  
-   [SQLGetInfo (Cursor Library) (SQLGetInfo (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlgetinfo-cursor-library.md)  
  
-   [SQLGetStmtAttr (Cursor Library) (SQLGetStmtAttr (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlgetstmtattr-cursor-library.md)  
  
-   [SQLGetStmtOption (Cursor Library) (SQLGetStmtOption (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlgetstmtoption-cursor-library.md)  
  
-   [SQLNativeSql (Cursor Library) (SQLNativeSql (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlnativesql-cursor-library.md)  
  
-   [SQLRowCount (Cursor Library) (SQLRowCount (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlrowcount-cursor-library.md)  
  
-   [SQLSetConnectAttr (Cursor Library) (SQLSetConnectAttr (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlsetconnectattr-cursor-library.md)  
  
-   [SQLSetDescField und SQLSetDescRec (Cursorbibliothek)](../../../odbc/reference/appendixes/sqlsetdescfield-and-sqlsetdescrec-cursor-library.md)  
  
-   [Sqlsettenvattr (Cursor Bibliothek)](../../../odbc/reference/appendixes/sqlsetenvattr-and-the-cursor-library.md)  
  
-   [SQLSetPos (Cursor Library) (SQLSetPos (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlsetpos-cursor-library.md)  
  
-   [SQLSetScrollOptions (Cursor Library) (SQLSetScrollOptions (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlsetscrolloptions-cursor-library.md)  
  
-   [SQLSetStmtAttr (Cursor Library) (SQLSetStmtAttr (Cursorbibliothek))](../../../odbc/reference/appendixes/sqlsetstmtattr-cursor-library.md)
