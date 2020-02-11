---
title: Sqlsetconnectinfo-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: e5d8087e7672dd331d0b078cea4930be7582a026
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093003"
---
# <a name="sqlsetconnectinfo-function"></a>SQLSetConnectInfo-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,81 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **Sqlsetconnectinfo** wird verwendet, um die Datenquelle, die Benutzer-ID und das Kennwort in das Verbindungs Informations Token für den [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md) -Befehl einer Anwendung festzulegen.  
  
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
 *Tokenhandle*  
 Der Tokenhandle.  
  
 *Servername*  
 Der Der Name der Datenquelle. Die Daten befinden sich möglicherweise auf demselben Computer wie das Programm oder auf einem anderen Computer in einem Netzwerk. Informationen dazu, wie eine Anwendung eine Datenquelle auswählt, finden Sie unter [Auswählen einer Datenquelle oder eines Treibers](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 *NameLength1*  
 Der Länge von **Servername* in Zeichen.  
  
 *User*  
 Der Benutzer-ID.  
  
 *NameLength2*  
 Der Länge von **Benutzername* in Zeichen.  
  
 *Authentifizierung*  
 Der Authentifizierungs Zeichenfolge (in der Regel das Kennwort)  
  
 *NameLength3*  
 Der Länge der *-*Authentifizierung* in Zeichen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Identisch mit [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md) für Eingabevalidierungsfehler, mit dem Unterschied, dass der Treiber-Manager den **Handlertyp** SQL_HANDLE_DBC_INFO_TOKEN und ein **handle** von *hdbcinfotoken*verwendet.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein Treiber SQL_ERROR oder SQL_INVALID_HANDLE zurückgibt, gibt der Treiber-Manager den Fehler an die Anwendung zurück (in [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md) oder [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Wenn ein Treiber SQL_SUCCESS_WITH_INFO zurückgibt, erhält der Treiber-Manager die Diagnoseinformationen von *hdbcinfotoken*und gibt SQL_SUCCESS_WITH_INFO in [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md) und [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)an die Anwendung zurück.  
  
 Anwendungen sollten diese Funktion nicht direkt aufzurufen. Ein ODBC-Treiber, der Treiber fähiges Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Fügen Sie sqlspi. h für die ODBC-Treiberentwicklung ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiber fähiges Verbindungs Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
