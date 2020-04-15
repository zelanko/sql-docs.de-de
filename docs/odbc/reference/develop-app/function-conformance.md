---
title: Funktionskonformität | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], function
- function conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: bb5d68cf-d238-481e-babc-2e9401b4700e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 33cd0ad4269ed59e31c8ab343ddbb01806afce04
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305591"
---
# <a name="function-conformance"></a>Funktionsübereinstimmung
Die folgende Tabelle gibt die Konformitätsstufe jeder ODBC-Funktion an, wobei diese gut definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|**SQLAllocHandle**|Core|  
|**SQLBindCol**|Core|  
|**SQLBindParameter**|Kern[1]|  
|**SQLBrowseConnect**|Ebene 1|  
|**SQLBulkOperations**|Ebene 1|  
|**SQLCancel**|Kern[1]|  
|**SQLCloseCursor**|Core|  
|**SQLColAttribute**|Kern[1]|  
|**SQLColumnPrivileges**|Ebene 2|  
|**SQLColumns**|Core|  
|**SQLConnect**|Core|  
|**SQLCopyDesc**|Core|  
|**SQLDataSources**|Core|  
|**SQLDescribeCol**|Kern[1]|  
|**SQLDescribeParam**|Ebene 2|  
|**SQLDisconnect**|Core|  
|**SQLDriverConnect**|Core|  
|**SQLDrivers**|Core|  
|**SQLEndTran**|Kern[1]|  
|**SQLExecDirect**|Core|  
|**SQLExecute**|Core|  
|**SQLFetch**|Core|  
|**SQLFetchScroll**|Kern[1]|  
|**SQLForeignKeys**|Ebene 2|  
|**SQLFreeHandle**|Core|  
|**'SQLFreeStmt'**|Core|  
|**SQLGetConnectAttr**|Core|  
|**SQLGetCursorName**|Core|  
|**SQLGetData**|Core|  
|**SQLGetDescField**|Core|  
|**SQLGetDescRec**|Core|  
|**SQLGetDiagField**|Core|  
|**SQLGetDiagRec**|Core|  
|**SQLGetEnvAttr**|Core|  
|**SQLGetFunctions**|Core|  
|**SQLGetInfo**|Core|  
|**'SQLGetStmtAttr'**|Core|  
|**SQLGetTypeInfo**|Core|  
|**SQLMoreResults**|Ebene 1|  
|**SQLNativeSql**|Core|  
|**SQLNumParams**|Core|  
|**SQLNumResultCols**|Core|  
|**SQLParamData**|Core|  
|**SQLPrepare**|Core|  
|**SQLPrimaryKeys**|Ebene 1|  
|**SQLProcedureColumns**|Ebene 1|  
|**'SQLProcedures'**|Ebene 1|  
|**SQLPutData**|Core|  
|**SQLRowCount**|Core|  
|**SQLSetConnectAttr**|Kern[2]|  
|**SQLSetCursorName**|Core|  
|**SQLSetDescField**|Kern[1]|  
|**SQLSetDescRec**|Core|  
|**SQLSetEnvAttr**|Kern[2]|  
|**SQLSetPos**|Stufe 1[1]|  
|**SQLSetStmtAttr**|Kern[2]|  
|**'SQLSpecialColumns'**|Kern[1]|  
|**'SQLStatistics'**|Core|  
|**SQLTablePrivileges**|Ebene 2|  
|**SQLTables**|Core|  
  
 [1] Wesentliche Merkmale dieser Funktion sind nur bei höheren Konformitätsstufen verfügbar.  
  
 [2] Das Festlegen bestimmter Attribute auf nicht standardmäßige Werte hängt von der Konformitätsstufe ab. Weitere Informationen finden Sie im nächsten [Abschnitt, Attributkonformität](../../../odbc/reference/develop-app/attribute-conformance.md).
