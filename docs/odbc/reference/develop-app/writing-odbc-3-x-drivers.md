---
title: Schreiben von ODBC 3. x-Treibern | Microsoft-Dokumentation
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
ms.openlocfilehash: fb403cef47f901cdb43bbb32c669ba68aa34913d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078904"
---
# <a name="writing-odbc-3x-drivers"></a>Schreiben von ODBC-3.x-Treibern
In der folgenden Tabelle wird die Funktions Unterstützung in ODBC 3 veranschaulicht. *x* -Treiber und eine ODBC-Anwendung sowie die Zuordnung, die vom Treiber-Manager ausgeführt wird, wenn die Funktionen für einen ODBC 3 aufgerufen werden. *x* -Treiber  
  
|Funktion|Unterstützt<br /><br /> durch einen<br /><br /> ODBC 3. *x*<br /><br /> Trei?|Unterstützt<br /><br /> durch einen<br /><br /> ODBC 3. *x*<br /><br /> Asyl?|Zugeordnet/unterstützt<br /><br /> von ODBC 3. *x*<br /><br /> Treiber-Manager zu<br /><br /> ein ODBC 3. *x* -Treiber?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|Nein|Nein [1]|Ja|  
|**SQLAllocEnv**|Nein|Nein [1]|Ja|  
|**SQLAllocHandle**|Ja|Ja|Nein|  
|**SQLAllocStmt**|Nein|Nein [1]|Ja|  
|**SQLBindCol**|Ja|Ja|Nein|  
|**SQLBindParam**|Nein|Ja [2]|Ja|  
|**SQLBindParameter**|Ja|Ja|Nein|  
|**SQLBrowseConnect**|Ja|Ja|Nein|  
|**SQLBulkOperations**|Ja|Ja|Nein|  
|**SQLCancel**|Ja|Ja|Nein|  
|**SQLCloseCursor**|Ja|Ja|Nein|  
|**SQLColAttribute**|Ja|Ja|Nein|  
|**SQLColAttributes**|Nein [3]|Nein|Ja|  
|**SQLColumnPrivileges**|Ja|Ja|Nein|  
|**SQLColumns**|Ja|Ja|Nein|  
|**SQLConnect**|Ja|Ja|Nein|  
|**Sqlcopyde SC**|Ja|Ja|Ja [4]|  
|**SQLDataSources**|Nein|Ja|Ja|  
|**SQLDescribeCol**|Ja|Ja|Nein|  
|**SQLDescribeParam**|Ja|Ja|Nein|  
|**SQLDisconnect**|Ja|Ja|Nein|  
|**SQLDriverConnect**|Ja|Ja|Nein|  
|**SQLDrivers**|Nein |Ja|Ja|  
|**SQLEndTran**|Ja|Ja|Nein|  
|**SQLError**|Nein|Nein [1]|Ja|  
|**SQLExecDirect**|Ja|Ja|Nein|  
|**SQLExecute**|Ja|Ja|Nein|  
|**SQLExtendedFetch**|Ja|Nein|Nein|  
|**SQLFetch**|Ja|Ja|Nein|  
|**SQLFetchScroll**|Ja|Ja|Nein|  
|**SQLForeignKeys**|Ja|Ja|Nein|  
|**SQLFreeConnect**|Nein|Ja [1]|Ja|  
|**SQLFreeEnv**|Nein|Ja [1]|Ja|  
|**SQLFreeHandle**|Ja|Ja|Nein|  
|**'SQLFreeStmt'**|Ja|Ja|Nein|  
|**SQLGetConnectAttr**|Ja|Ja|Nein|  
|**SQLGetConnectOption**|Nein [5]|Nein [1]|Ja|  
|**SQLGetCursorName**|Ja|Ja|Nein|  
|**SQLGetData**|Ja|Ja|Nein|  
|**SQLGetDescField**|Ja|Ja|Nein|  
|**SQLGetDescRec**|Ja|Ja|Nein|  
|**SQLGetDiagField**|Ja|Ja|Nein|  
|**SQLGetDiagRec**|Ja|Ja|Nein|  
|**SQLGetEnvAttr**|Ja|Ja|Nein|  
|**SQLGetFunctions**|Nein [6]|Ja|Ja|  
|**SQLGetInfo**|Ja|Ja|Nein|  
|**'SQLGetStmtAttr'**|Ja|Ja|Nein|  
|**SQLGetStmtOption**|Nein [5]|Nein [1]|Ja|  
|**SQLGetTypeInfo**|Ja|Ja|Nein|  
|**SQLMoreResults**|Ja|Ja|Nein|  
|**SQLNativeSql**|Ja|Ja|Nein|  
|**SQLNumParams**|Ja|Ja|Nein|  
|**SQLNumResultCols**|Ja|Ja|Nein|  
|**SQLParamData**|Ja|Ja|Nein|  
|**SQLParamOptions**|Nein|Nein |Ja|  
|**SQLPrepare**|Ja|Ja|Nein|  
|**SQLPrimaryKeys**|Ja|Ja|Nein|  
|**SQLProcedureColumns**|Ja|Ja|Nein|  
|**'SQLProcedures'**|Ja|Ja|Nein|  
|**SQLPutData**|Ja|Ja|Nein|  
|**SQLRowCount**|Ja|Ja|Nein|  
|**SQLSetConnectAttr**|Ja|Ja|Nein|  
|**SQLSetConnectOption**|Nein [5]|Nein [1]|Ja|  
|**SQLSetCursorName**|Ja|Ja|Nein|  
|**SQLSetDescField**|Ja|Ja|Nein|  
|**SQLSetDescRec**|Ja|Ja|Nein|  
|**SQLSetEnvAttr**|Ja|Ja|Nein|  
|**SQLSetPos**|Ja|Ja|Nein|  
|**SQLSetParam**|Nein|Nein |Ja|  
|**Sqlsetscrolloption**|Ja|Ja|Nein|  
|**SQLSetStmtAttr**|Ja|Ja|Nein|  
|**SQLSetStmtOption**|Nein [5]|Nein [1]|Ja|  
|**'SQLSpecialColumns'**|Ja|Ja|Nein|  
|**'SQLStatistics'**|Ja|Ja|Nein|  
|**SQLTablePrivileges**|Ja|Ja|Nein|  
|**SQLTables**|Ja|Ja|Nein|  
|**SQLtransact**|Nein|Nein [1]|Ja|  
  
 [1] Diese Funktion ist in ODBC 3 veraltet. *x*. ODBC 3. *x* -Anwendungen sollten diese Funktion nicht verwenden. Diese Funktion kann jedoch von einer Open Group-oder ISO CLI-kompatiblen Anwendung aufgerufen werden.  
  
 [2] ODBC 3. bei *x* -Anwendungen sollte **SQLBindParameter** anstelle von **SQLBindParam**verwendet werden. Diese Funktion kann jedoch von einer Open Group-oder ISO CLI-kompatiblen Anwendung aufgerufen werden.  
  
 [3] Treiber Schreiber sollten beachten, dass ODBC 2. *x* -Spalten Attribute SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE und SQL_COLUMN_LENGTH müssen mit **SQLColAttribute**unterstützt werden.  
  
 [4] **sqlcopyde** wird vom Treiber-Manager teilweise implementiert, wenn ein Deskriptor über Verbindungen kopiert wird, die zu unterschiedlichen Treibern gehören. Treiber sind erforderlich, um **SQLCopyDesc** über zwei ihrer eigenen Verbindungen zu unterstützen. Funktionen wie **SQLDrivers**, die ausschließlich vom Treiber-Manager implementiert werden, werden in dieser Liste nicht angezeigt.  
  
 [5] unter bestimmten Umständen müssen Treiber möglicherweise diese Funktion unterstützen. Weitere Informationen finden Sie auf der Referenzseite der Funktion.  
  
 [6] der Treiber kann **SQLGetFunctions** unterstützen, wenn der vom Treiber unterstützte Funktions Satz von der Verbindung zur Verbindung abweicht.
