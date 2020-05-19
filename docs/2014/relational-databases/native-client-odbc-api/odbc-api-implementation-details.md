---
title: Details zur ODBC-API-Implementierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQL Server Native Client ODBC driver, SQL Server-specific behaviors
- ODBC, SQL Server-specific behaviors
- functions [ODBC]
ms.assetid: dca92489-f179-4b1f-997c-adcc46aa17a3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: dae96ba17ee792b703e96ceff2200d1f8f629a01
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706409"
---
# <a name="odbc-api-implementation-details"></a>ODBC API Implementation Details
  In diesem Abschnitt werden die ODBC-Funktionen dokumentiert, die bei Verwendung mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifisches Verhalten zeigen. Nicht alle ODBC-Funktionen werden hier dokumentiert. In den einzelnen Themen werden nur die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischen Probleme bei ODBC-Funktionen erörtert. Sie stellen keine vollständige Referenz für die ODBC-Funktionen dar.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber entspricht der ODBC 3.51-Spezifikation und bei Verwendung des Windows 7-SDK der ODBC 3.8-Spezifikation. Eine umfassende ODBC-Referenz finden Sie in der [ODBC Programmer es Reference](https://go.microsoft.com/fwlink/?LinkId=45250) online.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [SQLBindCol](sqlbindcol.md)  
  
-   [SQLBindParameter](sqlbindparameter.md)  
  
-   [SQLBrowseConnect](sqlbrowseconnect.md)  
  
-   [SQLCancel](sqlcancel.md)  
  
-   [SQLCloseCursor](sqlclosecursor.md)  
  
-   [SQLColAttribute](sqlcolattribute.md)  
  
-   [SQLColumnPrivileges](sqlcolumnprivileges.md)  
  
-   [SQLColumns](sqlcolumns.md)  
  
-   [SQLConfigDataSource](sqlconfigdatasource.md)  
  
-   [SQLConnect](sqlconnect.md)  
  
-   [SQLDescribeCol](sqldescribecol.md)  
  
-   [SQLDescribeParam](sqldescribeparam.md)  
  
-   [SQLDriverConnect](sqldriverconnect.md)  
  
-   [SQLDrivers](sqldrivers.md)  
  
-   [SQLEndTran](sqlendtran.md)  
  
-   [SQLExecDirect](sqlexecdirect.md)  
  
-   [SQLExecute](sqlexecute.md)  
  
-   [SQLFetch](sqlfetch.md)  
  
-   [SQLFetchScroll](sqlfetchscroll.md)  
  
-   [SQLForeignKeys](sqlforeignkeys.md)  
  
-   [SQLFreeHandle](sqlfreehandle.md)  
  
-   ['SQLFreeStmt'](sqlfreestmt.md)  
  
-   [SQLGetConnectAttr](sqlgetconnectattr.md)  
  
-   [SQLGetCursorName](sqlgetcursorname.md)  
  
-   [SQLGetData](sqlgetdata.md)  
  
-   [SQLGetDescField](sqlgetdescfield.md)  
  
-   [SQLGetDescRec](sqlgetdescrec.md)  
  
-   [SQLGetDiagField](sqlgetdiagfield.md)  
  
-   [SQLGetFunctions](sqlgetfunctions.md)  
  
-   [SQLGetInfo](sqlgetinfo.md)  
  
-   ['SQLGetStmtAttr'](sqlgetstmtattr.md)  
  
-   [SQLGetTypeInfo](sqlgettypeinfo.md)  
  
-   [SQLMoreResults](sqlmoreresults.md)  
  
-   [SQLNativeSql](sqlnativesql.md)  
  
-   [SQLNumParams](sqlnumparams.md)  
  
-   [SQLNumResultCols](sqlnumresultcols.md)  
  
-   [SQLParamData](sqlparamdata.md)  
  
-   [SQLPrimaryKeys](sqlprimarykeys.md)  
  
-   [SQLProcedureColumns](sqlprocedurecolumns.md)  
  
-   ['SQLProcedures'](sqlprocedures.md)  
  
-   [SQLPutData](sqlputdata.md)  
  
-   [SQLRowCount](sqlrowcount.md)  
  
-   [SQLSetConnectAttr](sqlsetconnectattr.md)  
  
-   [SQLSetDescField](sqlsetdescfield.md)  
  
-   [SQLSetDescRec](sqlsetdescrec.md)  
  
-   [SQLSetEnvAttr](sqlsetenvattr.md)  
  
-   [SQLSetStmtAttr](sqlsetstmtattr.md)  
  
-   ['SQLSpecialColumns'](sqlspecialcolumns.md)  
  
-   ['SQLStatistics'](../statistics/statistics.md)  
  
-   [SQLTablePrivileges](sqltableprivileges.md)  
  
-   [SQLTables](sqltables.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC-&#41; Referenz](../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md)   
 [Erstellen von Anwendungen mit SQL Server Native Client](../native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
