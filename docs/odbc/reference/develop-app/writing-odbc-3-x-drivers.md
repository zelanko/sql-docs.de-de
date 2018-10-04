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
ms.openlocfilehash: 77a94c7505b5ab221fee4896e91f9b26850669df
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795650"
---
# <a name="writing-odbc-3x-drivers"></a>Schreiben von ODBC-3.x-Treibern
Die folgende Tabelle zeigt die funktionsunterstützung in einer ODBC-3. *x* Treiber und eine ODBC-Anwendung und die Zuordnung, die vom Treiber-Manager ausgeführt wird, wenn es sich bei die Funktionen für eine ODBC 3. aufgerufen werden. *X* Treiber.  
  
|Funktion|Supported<br /><br /> durch eine<br /><br /> ODBC 3. *x*<br /><br /> Treiber?|Supported<br /><br /> durch eine<br /><br /> ODBC 3. *x*<br /><br /> Anwendung?|Zugeordnet/unterstützt<br /><br /> der ODBC-3. *x*<br /><br /> Treiber-Manager zu<br /><br /> eine ODBC-3. *x* Treiber?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|nein|Keine [1]|Benutzerkontensteuerung|  
|**SQLAllocEnv**|nein|Keine [1]|Benutzerkontensteuerung|  
|**SQLAllocHandle**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLAllocStmt**|nein|Keine [1]|Benutzerkontensteuerung|  
|**SQLBindCol**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLBindParam**|nein|Ja [2]|Benutzerkontensteuerung|  
|**SQLBindParameter**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLBrowseConnect**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLBulkOperations**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLCancel**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLCloseCursor**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLColAttribute**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLColAttributes**|[3]|nein|Benutzerkontensteuerung|  
|**SQLColumnPrivileges**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLColumns**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLConnect**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLCopyDesc**|Benutzerkontensteuerung|Benutzerkontensteuerung|Ja [4]|  
|**SQLDataSources**|nein|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|**SQLDescribeCol**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLDescribeParam**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLDisconnect**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLDriverConnect**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLDrivers**|nein|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|**SQLEndTran**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLError**|nein|Keine [1]|Benutzerkontensteuerung|  
|**SQLExecDirect**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLExecute**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLExtendedFetch**|Benutzerkontensteuerung|nein|nein|  
|**SQLFetch**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLFetchScroll**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLForeignKeys**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLFreeConnect**|nein|Ja [1]|Benutzerkontensteuerung|  
|**SQLFreeEnv**|nein|Ja [1]|Benutzerkontensteuerung|  
|**SQLFreeHandle**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLFreeStmt**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLGetConnectAttr**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLGetConnectOption**|Keine [5]|Keine [1]|Benutzerkontensteuerung|  
|**SQLGetCursorName**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLGetData**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLGetDescField**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLGetDescRec**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLGetDiagField**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLGetDiagRec**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLGetEnvAttr**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLGetFunctions**|Keine [6]|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|**SQLGetInfo**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLGetStmtAttr**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLGetStmtOption**|Keine [5]|Keine [1]|Benutzerkontensteuerung|  
|**SQLGetTypeInfo**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLMoreResults**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLNativeSql**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLNumParams**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLNumResultCols**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLParamData**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLParamOptions**|nein|nein|Benutzerkontensteuerung|  
|**SQLPrepare**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLPrimaryKeys**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLProcedureColumns**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLProcedures**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLPutData**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLRowCount**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLSetConnectAttr**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLSetConnectOption**|Keine [5]|Keine [1]|Benutzerkontensteuerung|  
|**SQLSetCursorName**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLSetDescField**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLSetDescRec**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLSetEnvAttr**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLSetPos**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLSetParam**|nein|nein|Benutzerkontensteuerung|  
|**SQLSetScrollOption**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLSetStmtAttr**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLSetStmtOption**|Keine [5]|Keine [1]|Benutzerkontensteuerung|  
|**SQLSpecialColumns**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLStatistics**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLTablePrivileges**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLTables**|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|**SQLTransact**|nein|Keine [1]|Benutzerkontensteuerung|  
  
 [1] für diese Funktion ist in ODBC 3. veraltet. *x*. ODBC 3. *x* Anwendungen sollten diese Funktion nicht verwenden. Allerdings kann eine Open Group oder die CLI von ISO-kompatible Anwendung diese Funktion aufrufen.  
  
 [2] ODBC 3. *x* Anwendungen sollten verwenden **SQLBindParameter** anstelle von **SQLBindParam**. Allerdings kann eine Open Group oder die CLI von ISO-kompatible Anwendung diese Funktion aufrufen.  
  
 [3]-Treiber-Writer Beachten Sie, dass die ODBC 2. *x* Spaltenattribute SQL_COLUMN_PRECISION SQL_COLUMN_SCALE und SQL_COLUMN_LENGTH mit unterstützt werden müssen **SQLColAttribute**.  
  
 [4] **SQLCopyDesc** vom Treiber-Manager wird teilweise implementiert werden, wenn ein Deskriptor für Verbindungen kopiert wird, die zu anderen Treibern gehören. Treiber müssen unterstützen **SQLCopyDesc** für zwei der eigene Verbindungen. Funktionen wie **SQLDrivers**, die ausschließlich vom Treiber-Manager implementiert sind, werden in dieser Liste nicht angezeigt.  
  
 [5] unter bestimmten Umständen möglicherweise Treiber zur Unterstützung dieser Funktion. Weitere Informationen finden Sie auf der Referenzseite für diese Funktion.  
  
 [6] der Treiber zur Unterstützung können **SQLGetFunctions** , wenn der Satz von Funktionen, die der Treiber unterstützt in Verbindung, Verbindung variiert.
