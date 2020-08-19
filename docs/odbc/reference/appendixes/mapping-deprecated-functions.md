---
description: Zuordnen veralteter Funktionen
title: Mapping als veraltet markierte Funktionen | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9c990646c54fd0d0698482c5f8dc3f87df80fe93
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429612"
---
# <a name="mapping-deprecated-functions"></a>Zuordnen veralteter Funktionen
In diesem Abschnitt wird beschrieben, wie veraltete Funktionen vom ODBC *3. x* -Treiber-Manager zugeordnet werden, um die Abwärtskompatibilität von ODBC *3. x* -Treibern zu gewährleisten, die mit ODBC *2. x* -Anwendungen verwendet werden. Der Treiber-Manager führt diese Zuordnung unabhängig von der Version der Anwendung aus. Da jede der ODBC *2. x* -Funktionen in der folgenden Liste der entsprechenden ODBC *3. x* -Funktion zugeordnet ist, wenn Sie in einem ODBC *3. x* -Treiber aufgerufen wird, muss der ODBC *3.* x-Treiber die ODBC *2. x* -Funktionen nicht implementieren.  
  
 Die Zuordnung in der Liste wird ausgelöst, wenn der Treiber ein ODBC *3. x* -Treiber ist und der Treiber die zugeordnete Funktion nicht unterstützt.  
  
 In der folgenden Tabelle werden alle duplizierten Funktionen aufgelistet, die in ODBC *3. x*eingeführt wurden.  
  
|ODBC *2. x* -Funktion|ODBC *3. x* -Funktion|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLBindParam**[1]|**SQLBindParameter**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLFreeStmt** mit der *Option* SQL_DROP|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**'SQLGetStmtAttr'**|  
|**SQLParamOptions**|**SQLSetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**[2]|**SQLBindParameter**|  
|**Sqlsetscrolloption**|**SQLSetStmtAttr**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLtransact**|**SQLEndTran**|  
  
 [1] auch wenn diese Funktion in ODBC *2. x*nicht vorhanden ist, ist Sie in den Open Group-und ISO-Standards enthalten.  
  
 [2] Dies ist eine ODBC 1,0-Funktion.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
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
