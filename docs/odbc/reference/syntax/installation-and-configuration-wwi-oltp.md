---
title: SQLSetDriverConnectInfo-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetDriverConnectInfo function [ODBC]
ms.assetid: bfd4dfc2-fbca-4ef3-81e5-2706f2389256
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10336475e39598161126c13771ad822de0d5f7d8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298799"
---
# <a name="sqlsetdriverconnectinfo-function"></a>SQLSetDriverConnectInfo-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.81 Standard-Konformität: ODBC  
  
 **Zusammenfassung**  
 **SQLSetDriverConnectInfo** wird verwendet, um die Verbindungszeichenfolge im Verbindungsinfotoken für den **SQLDriverConnect-Aufruf** einer Anwendung festzulegen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
  
SQLRETURN SQLSetDriverConnectInfo(  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              InConnectionString,  
                SQLSMALLINT          StringLength1 );  
```  
  
## <a name="arguments"></a>Argumente  
 *TokenHandle*  
 [Eingabe] Token-Handle.  
  
 *InConnectionString*  
 [Eingabe] Eine vollständige Verbindungszeichenfolge (siehe Syntax in "Comments" in [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)), einer partiellen Verbindungszeichenfolge oder einer leeren Zeichenfolge.  
  
 *StringLength1*  
 [Eingabe] Länge von **InConnectionString*, in Zeichen, wenn die Zeichenfolge Unicode ist, oder Bytes, wenn Die Zeichenfolge ANSI oder DBCS ist.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Genauso wie [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) im Zusammenhang mit jedem Eingabevalidierungsfehler, mit der Ausnahme, dass der Treiber-Manager einen **HandleType** von SQL_HANDLE_DBC_INFO_TOKEN und ein **Handle** von *hDbcInfoToken*verwendet.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein Treiber SQL_ERROR oder SQL_INVALID_HANDLE zurückgibt, gibt der Treiber-Manager den Fehler an die Anwendung zurück (in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) oder [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Wenn ein Treiber SQL_SUCCESS_WITH_INFO zurückgibt, ruft der Treiber-Manager die Diagnoseinformationen von *hDbcInfoToken*ab und gibt SQL_SUCCESS_WITH_INFO an die Anwendung in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) und [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)zurück.  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberbewusstes Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Fügen Sie sqlspi.h für die ODBC-Treiberentwicklung ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiber-Aware-Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
