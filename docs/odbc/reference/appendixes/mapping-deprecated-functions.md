---
title: Zuordnung veralteter Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], about mapping deprecated functions
- backward compatibility [ODBC], mapping deprecated functions
- deprecated functions [ODBC]
- compatibility [ODBC], mapping deprecated functions
- functions [ODBC], mapping deprecated functions
- mapping deprecated functions [ODBC]
ms.assetid: ee462617-1d79-4c88-afeb-b129cff34cc6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b59d2604dd9d4b7c3166027c1917dea096b331d9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181314"
---
# <a name="mapping-deprecated-functions"></a>Zuordnen veralteter Funktionen
In diesem Abschnitt wird beschrieben, wie als veraltet markierte Funktionen zugeordnet sind, indem Sie die ODBC 3. *.x* Treiber-Manager zum Gewährleisten der Abwärtskompatibilität von ODBC 3. *.x* Treiber, die mit ODBC 2. verwendet werden. *X* Anwendungen. Der Treiber-Manager führt diese Zuordnung unabhängig von der Version der Anwendung. Da jede der ODBC-2. *x* Funktionen in der folgenden Liste wird zugeordnet, auf die entsprechenden ODBC 3. *.x* Funktion bei Aufruf in einer ODBC 3. *.x* -Treiber verwenden, die ODBC 3. *.x*Treiber muss nicht die ODBC 2. zu implementieren. *x* Funktionen.  
  
 Die Zuordnung in der Liste wird ausgelöst, wenn der Treiber einen ODBC 3. *.x* und den Treiber unterstützt nicht die Funktion, die zugeordnet wird.  
  
 Die folgende Tabelle enthält alle doppelt vorhandenen Funktionen, die in ODBC 3. eingeführte *.x*.  
  
|ODBC-2. *x* Funktion|ODBC 3. *.x* Funktion|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLBindParam**[1]|**SQLBindParameter**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLFreeStmt** mit einer *Option* von SQL_DROP|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**[2]|**SQLBindParameter**|  
|**SQLSetScrollOption**|**SQLSetStmtAttr**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1], obwohl diese Funktion nicht, in ODBC 2. vorhanden war *.x*, es ist in den Open Group und ISO-Standards.  
  
 [2] Dies ist ein ODBC-1.0-Funktion.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [SQLAllocConnect-Zuordnung](../../../odbc/reference/appendixes/sqlallocconnect-mapping.md)  
  
-   [SQLAllocEnv-Zuordnung](../../../odbc/reference/appendixes/sqlallocenv-mapping.md)  
  
-   [SQLAllocStmt-Zuordnung](../../../odbc/reference/appendixes/sqlallocstmt-mapping.md)  
  
-   [SQLBindParam-Zuordnung](../../../odbc/reference/appendixes/sqlbindparam-mapping.md)  
  
-   [SQLColAttributes-Zuordnung](../../../odbc/reference/appendixes/sqlcolattributes-mapping.md)  
  
-   [SQLError-Zuordnung](../../../odbc/reference/appendixes/sqlerror-mapping.md)  
  
-   [SQLFreeConnect-Zuordnung](../../../odbc/reference/appendixes/sqlfreeconnect-mapping.md)  
  
-   [SQLFreeEnv-Zuordnung](../../../odbc/reference/appendixes/sqlfreeenv-mapping.md)  
  
-   [SQLFreeStmt-Zuordnung](../../../odbc/reference/appendixes/sqlfreestmt-mapping.md)  
  
-   [SQLGetConnectOption-Zuordnung](../../../odbc/reference/appendixes/sqlgetconnectoption-mapping.md)  
  
-   [SQLGetStmtOption-Zuordnung](../../../odbc/reference/appendixes/sqlgetstmtoption-mapping.md)  
  
-   [SQLInstallTranslator-Zuordnung](../../../odbc/reference/appendixes/sqlinstalltranslator-mapping.md)  
  
-   [SQLParamOptions-Zuordnung](../../../odbc/reference/appendixes/sqlparamoptions-mapping.md)  
  
-   [SQLSetConnectOption-Zuordnung](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)  
  
-   [SQLSetParam-Zuordnung](../../../odbc/reference/appendixes/sqlsetparam-mapping.md)  
  
-   [SQLSetScrollOptions-Zuordnung](../../../odbc/reference/appendixes/sqlsetscrolloptions-mapping.md)  
  
-   [SQLSetStmtOption-Zuordnung](../../../odbc/reference/appendixes/sqlsetstmtoption-mapping.md)  
  
-   [SQLTransact-Zuordnung](../../../odbc/reference/appendixes/sqltransact-mapping.md)
