---
title: SQLSetDriverConnectInfo-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c344315764eac32e2e63663f07b7f797571a0e6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63233438"
---
# <a name="sqlsetdriverconnectinfo-function"></a>SQLSetDriverConnectInfo-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.81 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLSetDriverConnectInfo** dient zum Festlegen der Verbindungszeichenfolge in das Verbindungstoken für die Informationen für einer Anwendung **SQLDriverConnect** aufrufen.  
  
## <a name="syntax"></a>Syntax  
  
```  
SQLRETURN SQLSetDriverConnectInfo(  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              InConnectionString,  
                SQLSMALLINT          StringLength1 );  
```  
  
## <a name="arguments"></a>Argumente  
 *TokenHandle*  
 [Eingabe] Tokenhandle.  
  
 *InConnectionString*  
 [Eingabe] Eine vollständige Verbindungszeichenfolge (finden Sie in der Syntax "Kommentare" unter [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)), ein Teil der Verbindungszeichenfolge oder eine leere Zeichenfolge.  
  
 *StringLength1*  
 [Eingabe] Länge der **InConnectionString*, in Zeichen, wenn die Zeichenfolge Unicode oder Bytes ist, wenn die Zeichenfolge ANSI oder DBCS ist.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Identisch mit [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) Bezug auf alle Fehler eingabeüberprüfung, mit dem Unterschied, dass der Treiber-Manager verwendet eine **HandleType** von SQL_HANDLE_DBC_INFO_TOKEN und ein **behandeln** von *hDbcInfoToken*.  
  
## <a name="remarks"></a>Hinweise  
 Immer ein Treiber SQL_ERROR oder SQL_INVALID_HANDLE zurückgibt, gibt der Treiber-Manager den Fehler an die Anwendung zurück (in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) oder [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Wenn ein Treiber SQL_SUCCESS_WITH_INFO zurückgibt, erhält der Treiber-Manager die Diagnoseinformationen aus *hDbcInfoToken*, und wird SQL_SUCCESS_WITH_INFO zurückgegeben. um die Anwendung im [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)und [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberfähiges Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Umfassen Sie sqlspi.h für die Entwicklung von ODBC-Treiber.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln einen ODBC-Treiber](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiberfähiges Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
