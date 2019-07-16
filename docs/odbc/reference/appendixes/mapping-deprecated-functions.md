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
ms.openlocfilehash: 307f0f54434fdcb4ebb19c38256a7a04f4a5c46d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67990712"
---
# <a name="mapping-deprecated-functions"></a>Zuordnen veralteter Funktionen
In diesem Abschnitt wird beschrieben, wie als veraltet markierte Funktionen zugeordnet sind, indem Sie die ODBC *3.x* gewährleisten der Abwärtskompatibilität von ODBC-Treiber-Manager *3.x* Treiber, die verwendet werden, mit dem ODBC- *2.x* Anwendungen. Der Treiber-Manager führt diese Zuordnung unabhängig von der Version der Anwendung. Da jede der ODBC- *2.x* Funktionen in der folgenden Liste wird an die entsprechenden ODBC zugeordnet *3.x* bei Aufruf in einer ODBC-Funktion *3.x* ODBC-Treiber*3.x* Treiber keine Implementierung die ODBC *2.x* Funktionen.  
  
 Die Zuordnung in der Liste wird ausgelöst, wenn der Treiber ODBC *3.x* und den Treiber unterstützt nicht die Funktion, die zugeordnet wird.  
  
 Die folgende Tabelle enthält alle doppelt vorhandenen Funktionen, die in ODBC eingeführte *3.x*.  
  
|ODBC *2.x* Funktion|ODBC *3.x* Funktion|  
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
  
 [1], obwohl diese Funktion nicht, in ODBC vorhanden war *2.x*, es ist in den Open Group und ISO-Standards.  
  
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
