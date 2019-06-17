---
title: Schreiben von ODBC-3.x-Treibern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading drivers [ODBC]
- ODBC drivers [ODBC], upgrading
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 9b75f59b-623f-4711-9ca2-e751b3622e00
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f548e1496ce45d9fdb4677fd9659de349e5c5cc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62636105"
---
# <a name="writing-odbc-3x-drivers"></a>Schreiben von ODBC-3.x-Treibern
Die folgende Tabelle zeigt die funktionsunterstützung in einer ODBC-3. *x* Treiber und eine ODBC-Anwendung und die Zuordnung, die vom Treiber-Manager ausgeführt wird, wenn es sich bei die Funktionen für eine ODBC 3. aufgerufen werden. *X* Treiber.  
  
|Funktion|Supported<br /><br /> durch eine<br /><br /> ODBC 3.*x*<br /><br /> Treiber?|Supported<br /><br /> durch eine<br /><br /> ODBC 3.*x*<br /><br /> application?|Zugeordnet/unterstützt<br /><br /> der ODBC-3. *x*<br /><br /> Treiber-Manager zu<br /><br /> eine ODBC-3. *x* Treiber?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|Nein|Keine [1]|Ja|  
|**SQLAllocEnv**|Nein|Keine [1]|Ja|  
|**SQLAllocHandle**|Ja|Ja|Nein|  
|**SQLAllocStmt**|Nein|Keine [1]|Ja|  
|**SQLBindCol**|Ja|Ja|Nein|  
|**SQLBindParam**|Nein|Ja [2]|Ja|  
|**SQLBindParameter**|Ja|Ja|Nein|  
|**SQLBrowseConnect**|Ja|Ja|Nein|  
|**SQLBulkOperations**|Ja|Ja|Nein|  
|**SQLCancel**|Ja|Ja|Nein|  
|**SQLCloseCursor**|Ja|Ja|Nein|  
|**SQLColAttribute**|Ja|Ja|Nein|  
|**SQLColAttributes**|[3]|Nein|Ja|  
|**SQLColumnPrivileges**|Ja|Ja|Nein|  
|**SQLColumns**|Ja|Ja|Nein|  
|**SQLConnect**|Ja|Ja|Nein|  
|**SQLCopyDesc**|Ja|Ja|Ja [4]|  
|**SQLDataSources**|Nein|Ja|Ja|  
|**SQLDescribeCol**|Ja|Ja|Nein|  
|**SQLDescribeParam**|Ja|Ja|Nein|  
|**SQLDisconnect**|Ja|Ja|Nein|  
|**SQLDriverConnect**|Ja|Ja|Nein|  
|**SQLDrivers**|Nein|Ja|Ja|  
|**SQLEndTran**|Ja|Ja|Nein|  
|**SQLError**|Nein|Keine [1]|Ja|  
|**SQLExecDirect**|Ja|Ja|Nein|  
|**SQLExecute**|Ja|Ja|Nein|  
|**SQLExtendedFetch**|Ja|Nein|Nein|  
|**SQLFetch**|Ja|Ja|Nein|  
|**SQLFetchScroll**|Ja|Ja|Nein|  
|**SQLForeignKeys**|Ja|Ja|Nein|  
|**SQLFreeConnect**|Nein|Ja [1]|Ja|  
|**SQLFreeEnv**|Nein|Ja [1]|Ja|  
|**SQLFreeHandle**|Ja|Ja|Nein|  
|**SQLFreeStmt**|Ja|Ja|Nein|  
|**SQLGetConnectAttr**|Ja|Ja|Nein|  
|**SQLGetConnectOption**|Keine [5]|Keine [1]|Ja|  
|**SQLGetCursorName**|Ja|Ja|Nein|  
|**SQLGetData**|Ja|Ja|Nein|  
|**SQLGetDescField**|Ja|Ja|Nein|  
|**SQLGetDescRec**|Ja|Ja|Nein|  
|**SQLGetDiagField**|Ja|Ja|Nein|  
|**SQLGetDiagRec**|Ja|Ja|Nein|  
|**SQLGetEnvAttr**|Ja|Ja|Nein|  
|**SQLGetFunctions**|Keine [6]|Ja|Ja|  
|**SQLGetInfo**|Ja|Ja|Nein|  
|**SQLGetStmtAttr**|Ja|Ja|Nein|  
|**SQLGetStmtOption**|Keine [5]|Keine [1]|Ja|  
|**SQLGetTypeInfo**|Ja|Ja|Nein|  
|**SQLMoreResults**|Ja|Ja|Nein|  
|**SQLNativeSql**|Ja|Ja|Nein|  
|**SQLNumParams**|Ja|Ja|Nein|  
|**SQLNumResultCols**|Ja|Ja|Nein|  
|**SQLParamData**|Ja|Ja|Nein|  
|**SQLParamOptions**|Nein|Nein|Ja|  
|**SQLPrepare**|Ja|Ja|Nein|  
|**SQLPrimaryKeys**|Ja|Ja|Nein|  
|**SQLProcedureColumns**|Ja|Ja|Nein|  
|**SQLProcedures**|Ja|Ja|Nein|  
|**SQLPutData**|Ja|Ja|Nein|  
|**SQLRowCount**|Ja|Ja|Nein|  
|**SQLSetConnectAttr**|Ja|Ja|Nein|  
|**SQLSetConnectOption**|Keine [5]|Keine [1]|Ja|  
|**SQLSetCursorName**|Ja|Ja|Nein|  
|**SQLSetDescField**|Ja|Ja|Nein|  
|**SQLSetDescRec**|Ja|Ja|Nein|  
|**SQLSetEnvAttr**|Ja|Ja|Nein|  
|**SQLSetPos**|Ja|Ja|Nein|  
|**SQLSetParam**|Nein|Nein|Ja|  
|**SQLSetScrollOption**|Ja|Ja|Nein|  
|**SQLSetStmtAttr**|Ja|Ja|Nein|  
|**SQLSetStmtOption**|Keine [5]|Keine [1]|Ja|  
|**SQLSpecialColumns**|Ja|Ja|Nein|  
|**SQLStatistics**|Ja|Ja|Nein|  
|**SQLTablePrivileges**|Ja|Ja|Nein|  
|**SQLTables**|Ja|Ja|Nein|  
|**SQLTransact**|Nein|Keine [1]|Ja|  
  
 [1] für diese Funktion ist in ODBC 3. veraltet. *x*. ODBC 3. *x* Anwendungen sollten diese Funktion nicht verwenden. Allerdings kann eine Open Group oder die CLI von ISO-kompatible Anwendung diese Funktion aufrufen.  
  
 [2] ODBC 3. *x* Anwendungen sollten verwenden **SQLBindParameter** anstelle von **SQLBindParam**. Allerdings kann eine Open Group oder die CLI von ISO-kompatible Anwendung diese Funktion aufrufen.  
  
 [3]-Treiber-Writer Beachten Sie, dass die ODBC 2. *x* Spaltenattribute SQL_COLUMN_PRECISION SQL_COLUMN_SCALE und SQL_COLUMN_LENGTH mit unterstützt werden müssen **SQLColAttribute**.  
  
 [4] **SQLCopyDesc** vom Treiber-Manager wird teilweise implementiert werden, wenn ein Deskriptor für Verbindungen kopiert wird, die zu anderen Treibern gehören. Treiber müssen unterstützen **SQLCopyDesc** für zwei der eigene Verbindungen. Funktionen wie **SQLDrivers**, die ausschließlich vom Treiber-Manager implementiert sind, werden in dieser Liste nicht angezeigt.  
  
 [5] unter bestimmten Umständen möglicherweise Treiber zur Unterstützung dieser Funktion. Weitere Informationen finden Sie auf der Referenzseite für diese Funktion.  
  
 [6] der Treiber zur Unterstützung können **SQLGetFunctions** , wenn der Satz von Funktionen, die der Treiber unterstützt in Verbindung, Verbindung variiert.
