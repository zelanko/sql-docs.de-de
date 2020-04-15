---
title: SQLGetPoolID-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetPoolID function [ODBC]
ms.assetid: 95a8666a-ad68-4d89-bf65-f2cc797f8820
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 32cc973f4dab5bde7bcedade0365d233987dda72
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303317"
---
# <a name="sqlgetpoolid-function"></a>SQLGetPoolID-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.81 Standard-Konformität: ODBC  
  
 **Zusammenfassung**  
 **SQLGetPoolID** ruft die Pool-ID ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>Argumente  
 *hDbcInfoToken*  
 [Eingabe] Tokenhandle, das alle Verbindungsinformationen enthält.  
  
 *pPoolID*  
 [Ausgabe] Die Pool-ID, die verwendet wird, um eine Reihe von Verbindungen zu identifizieren, die austauschbar verwendet werden können (möglicherweise erfordert ein zusätzliches Zurücksetzen).  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetPoolID** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, verwendet der Treiber-Manager einen **HandleType** aus SQL_HANDLE_DBC_INFO_TOKEN und ein **Handle** von *hDbcInfoToken*.  
  
## <a name="remarks"></a>Bemerkungen  
 **SQLGetPoolID** wird verwendet, um die Pool-ID mit einer Reihe von Verbindungsinformationen abzuerhalten (aus **SQLSetConnectAttrForDbcInfo**, **SQLSetDriverConnectInfo**und **SQLSetConnectInfo**). Diese Pool-ID wird verwendet, um eine Reihe von Verbindungen zu identifizieren, die austauschbar verwendet werden können (möglicherweise erfordert ein zusätzliches Zurücksetzen). Die Pool-ID wird verwendet, um den Verbindungspool für diese Gruppe von Verbindungen zu identifizieren.  
  
 Wenn ein Treiber SQL_ERROR oder SQL_INVALID_HANDLE zurückgibt, gibt der Treiber-Manager den Fehler an die Anwendung zurück (in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) oder [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Wenn ein Treiber SQL_SUCCESS_WITH_INFO zurückgibt, ruft der Treiber-Manager die Diagnoseinformationen von *hDbcInfoToken*ab und gibt SQL_SUCCESS_WITH_INFO an die Anwendung in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) und [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)zurück.  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberbewusstes Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Fügen Sie sqlspi.h für die ODBC-Treiberentwicklung ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiber-Aware-Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
