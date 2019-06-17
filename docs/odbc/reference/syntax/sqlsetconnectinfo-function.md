---
title: SQLSetConnectInfo-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 448b0f5e34a6b7421c23a1267dd9cd68bd93ca6f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537183"
---
# <a name="sqlsetconnectinfo-function"></a>SQLSetConnectInfo-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.81 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLSetConnectInfo** dient zum Festlegen von der Datenquelle, Benutzer-ID und das Kennwort in das Verbindungstoken für die Informationen für einer Anwendung [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) aufrufen.  
  
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
 [Eingabe] Tokenhandle.  
  
 *ServerName*  
 [Eingabe] Datenquellenname. Daten können sich auf demselben Computer wie die Anwendung oder auf einem anderen Computer an einer beliebigen Stelle in einem Netzwerk sein. Weitere Informationen dazu, wie eine Anwendung eine Datenquelle wählt, finden Sie unter [Auswählen einer Datenquelle oder Treiber](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 [Eingabe] Länge der **ServerName* in Zeichen.  
  
 *UserName*  
 [Eingabe] Benutzer-ID.  
  
 *NameLength2*  
 [Eingabe] Länge der **Benutzername* in Zeichen.  
  
 *Authentifizierung*  
 [Eingabe] Zeichenfolge zur cloudauthentifizierung (in der Regel das Kennwort).  
  
 *NameLength3*  
 [Eingabe] Länge der **Authentifizierung* in Zeichen.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Identisch mit [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) für eingabeüberprüfungsfehler, mit dem Unterschied, dass der Treiber-Manager verwendet eine **HandleType** von SQL_HANDLE_DBC_INFO_TOKEN und **behandeln** von *hDbcInfoToken*.  
  
## <a name="remarks"></a>Hinweise  
 Immer ein Treiber SQL_ERROR oder SQL_INVALID_HANDLE zurückgibt, gibt der Treiber-Manager den Fehler an die Anwendung zurück (in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) oder [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Wenn ein Treiber SQL_SUCCESS_WITH_INFO zurückgibt, erhält der Treiber-Manager die Diagnoseinformationen aus *hDbcInfoToken*, und wird SQL_SUCCESS_WITH_INFO zurückgegeben. um die Anwendung im [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)und [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberfähiges Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Umfassen Sie sqlspi.h für die Entwicklung von ODBC-Treiber.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln einen ODBC-Treiber](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiberfähiges Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
