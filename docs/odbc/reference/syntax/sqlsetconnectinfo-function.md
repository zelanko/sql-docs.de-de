---
title: SQLSetConnectInfo-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectInfo function [ODBC]
ms.assetid: 0782a1c3-c5d1-499b-a8ba-134162db9990
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b575e0d09f87ad21e1190b8081b6604349a98263
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301851"
---
# <a name="sqlsetconnectinfo-function"></a>SQLSetConnectInfo-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.81 Standard-Konformität: ODBC  
  
 **Zusammenfassung**  
 **SQLSetConnectInfo** wird verwendet, um die Datenquelle, die Benutzer-ID und das Kennwort in das Verbindungsinfotoken für den [SQLConnect-Aufruf](../../../odbc/reference/syntax/sqlconnect-function.md) einer Anwendung festzulegen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
  
SQLRETURN  SQLSetConnectInfo(  
                SQLHDBC_INFO_TOKEN   TokenHandle,  
                WCHAR *              ServerName,  
                SQLSMALLINT          NameLength1,  
                WCHAR *              UserName,  
                SQLSMALLINT          NameLength2,  
                WCHAR *              Authentication,  
                SQLSMALLINT          NameLength3 );  
```  
  
## <a name="arguments"></a>Argumente  
 *TokenHandle*  
 [Eingabe] Token-Handle.  
  
 *ServerName*  
 [Eingabe] Datenquellenname. Die Daten befinden sich möglicherweise auf demselben Computer wie das Programm oder auf einem anderen Computer irgendwo in einem Netzwerk. Informationen dazu, wie eine Anwendung eine Datenquelle auswählt, finden Sie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 [Eingabe] Länge von **ServerName* in Zeichen.  
  
 *Nutzername*  
 [Eingabe] Benutzerkennung.  
  
 *NameLength2*  
 [Eingabe] Länge von **UserName* in Zeichen.  
  
 *Authentifizierung*  
 [Eingabe] Authentifizierungszeichenfolge (in der Regel das Kennwort).  
  
 *NameLength3*  
 [Eingabe] Länge der **Authentifizierung* in Zeichen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Genauso wie [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) für Eingabevalidierungsfehler, mit der Ausnahme, dass der Treiber-Manager einen **HandleType** von SQL_HANDLE_DBC_INFO_TOKEN und ein **Handle** von *hDbcInfoToken*verwendet.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein Treiber SQL_ERROR oder SQL_INVALID_HANDLE zurückgibt, gibt der Treiber-Manager den Fehler an die Anwendung zurück (in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) oder [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Wenn ein Treiber SQL_SUCCESS_WITH_INFO zurückgibt, ruft der Treiber-Manager die Diagnoseinformationen von *hDbcInfoToken*ab und gibt SQL_SUCCESS_WITH_INFO an die Anwendung in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) und [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)zurück.  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberbewusstes Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Fügen Sie sqlspi.h für die ODBC-Treiberentwicklung ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiber-Aware-Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
