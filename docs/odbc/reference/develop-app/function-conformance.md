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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 45eb427b660496430334633b5d43ee8989211c0f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069756"
---
# <a name="function-conformance"></a>Funktionsübereinstimmung
In der folgenden Tabelle ist die Übereinstimmungs Stufe der einzelnen ODBC-Funktionen angegeben, wo diese klar definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|**SQLAllocHandle**|Core|  
|**SQLBindCol**|Core|  
|**SQLBindParameter**|Kern [1]|  
|**SQLBrowseConnect**|Ebene 1|  
|**SQLBulkOperations**|Ebene 1|  
|**SQLCancel**|Kern [1]|  
|**SQLCloseCursor**|Core|  
|**SQLColAttribute**|Kern [1]|  
|**SQLColumnPrivileges**|Ebene 2|  
|**SQLColumns**|Core|  
|**SQLConnect**|Core|  
|**Sqlcopyde SC**|Core|  
|**SQLDataSources**|Core|  
|**SQLDescribeCol**|Kern [1]|  
|**SQLDescribeParam**|Ebene 2|  
|**SQLDisconnect**|Core|  
|**SQLDriverConnect**|Core|  
|**SQLDrivers**|Core|  
|**SQLEndTran**|Kern [1]|  
|**SQLExecDirect**|Core|  
|**SQLExecute**|Core|  
|**SQLFetch**|Core|  
|**SQLFetchScroll**|Kern [1]|  
|**SQLForeignKeys**|Ebene 2|  
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
|**SQLSetConnectAttr**|Kern [2]|  
|**SQLSetCursorName**|Core|  
|**SQLSetDescField**|Kern [1]|  
|**SQLSetDescRec**|Core|  
|**SQLSetEnvAttr**|Kern [2]|  
|**SQLSetPos**|Ebene 1 [1]|  
|**SQLSetStmtAttr**|Kern [2]|  
|**'SQLSpecialColumns'**|Kern [1]|  
|**'SQLStatistics'**|Core|  
|**SQLTablePrivileges**|Ebene 2|  
|**SQLTables**|Core|  
  
 [1] wichtige Features dieser Funktion sind nur bei höheren Konformitätsstufen verfügbar.  
  
 [2] das Festlegen bestimmter Attribute auf nicht standardmäßige Werte hängt vom Konformitäts Grad ab. Weitere Informationen finden Sie im nächsten Abschnitt [Attribut Übereinstimmung](../../../odbc/reference/develop-app/attribute-conformance.md).
