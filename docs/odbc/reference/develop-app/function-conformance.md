---
title: Funktions Übereinstimmung | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305591"
---
# <a name="function-conformance"></a>Funktionsübereinstimmung
In der folgenden Tabelle ist die Übereinstimmungs Stufe der einzelnen ODBC-Funktionen angegeben, wo diese klar definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|**SQLAllocHandle**|Kernspeicher|  
|**SQLBindCol**|Kernspeicher|  
|**SQLBindParameter**|Kern [1]|  
|**SQLBrowseConnect**|Ebene 1|  
|**SQLBulkOperations**|Ebene 1|  
|**SQLCancel**|Kern [1]|  
|**SQLCloseCursor**|Kernspeicher|  
|**SQLColAttribute**|Kern [1]|  
|**SQLColumnPrivileges**|Ebene 2|  
|**SQLColumns**|Kernspeicher|  
|**SQLConnect**|Kernspeicher|  
|**Sqlcopyde SC**|Kernspeicher|  
|**SQLDataSources**|Kernspeicher|  
|**SQLDescribeCol**|Kern [1]|  
|**SQLDescribeParam**|Ebene 2|  
|**SQLDisconnect**|Kernspeicher|  
|**SQLDriverConnect**|Kernspeicher|  
|**SQLDrivers**|Kernspeicher|  
|**SQLEndTran**|Kern [1]|  
|**SQLExecDirect**|Kernspeicher|  
|**SQLExecute**|Kernspeicher|  
|**SQLFetch**|Kernspeicher|  
|**SQLFetchScroll**|Kern [1]|  
|**SQLForeignKeys**|Ebene 2|  
|**SQLFreeHandle**|Kernspeicher|  
|**'SQLFreeStmt'**|Kernspeicher|  
|**SQLGetConnectAttr**|Kernspeicher|  
|**SQLGetCursorName**|Kernspeicher|  
|**SQLGetData**|Kernspeicher|  
|**SQLGetDescField**|Kernspeicher|  
|**SQLGetDescRec**|Kernspeicher|  
|**SQLGetDiagField**|Kernspeicher|  
|**SQLGetDiagRec**|Kernspeicher|  
|**SQLGetEnvAttr**|Kernspeicher|  
|**SQLGetFunctions**|Kernspeicher|  
|**SQLGetInfo**|Kernspeicher|  
|**'SQLGetStmtAttr'**|Kernspeicher|  
|**SQLGetTypeInfo**|Kernspeicher|  
|**SQLMoreResults**|Ebene 1|  
|**SQLNativeSql**|Kernspeicher|  
|**SQLNumParams**|Kernspeicher|  
|**SQLNumResultCols**|Kernspeicher|  
|**SQLParamData**|Kernspeicher|  
|**SQLPrepare**|Kernspeicher|  
|**SQLPrimaryKeys**|Ebene 1|  
|**SQLProcedureColumns**|Ebene 1|  
|**'SQLProcedures'**|Ebene 1|  
|**SQLPutData**|Kernspeicher|  
|**SQLRowCount**|Kernspeicher|  
|**SQLSetConnectAttr**|Kern [2]|  
|**SQLSetCursorName**|Kernspeicher|  
|**SQLSetDescField**|Kern [1]|  
|**SQLSetDescRec**|Kernspeicher|  
|**SQLSetEnvAttr**|Kern [2]|  
|**SQLSetPos**|Ebene 1 [1]|  
|**SQLSetStmtAttr**|Kern [2]|  
|**'SQLSpecialColumns'**|Kern [1]|  
|**'SQLStatistics'**|Kernspeicher|  
|**SQLTablePrivileges**|Ebene 2|  
|**SQLTables**|Kernspeicher|  
  
 [1] wichtige Features dieser Funktion sind nur bei höheren Konformitätsstufen verfügbar.  
  
 [2] das Festlegen bestimmter Attribute auf nicht standardmäßige Werte hängt vom Konformitäts Grad ab. Weitere Informationen finden Sie im nächsten Abschnitt [Attribut Übereinstimmung](../../../odbc/reference/develop-app/attribute-conformance.md).
