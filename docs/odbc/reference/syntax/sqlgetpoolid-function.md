---
title: SQLGetPoolID-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9fc6737530fdf151573a570eb83f777785ddb679
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65538078"
---
# <a name="sqlgetpoolid-function"></a>SQLGetPoolID-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.81 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLGetPoolID** Ruft die Pool-ID  
  
## <a name="syntax"></a>Syntax  
  
```cpp
  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>Argumente  
 *hDbcInfoToken*  
 [Eingabe] Tokenhandle, die alle Verbindungsinformationen enthält.  
  
 *pPoolID*  
 [Ausgabe] Die Pool-ID, die verwendet wird, um eine Gruppe von Verbindungen zu identifizieren, die austauschbar verwendet werden können (möglicherweise muss eine zusätzliche zurückgesetzt).  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Bei der **SQLGetPoolID** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, der Treiber-Manager verwendet eine **HandleType** von SQL_HANDLE_DBC_INFO_TOKEN und ein **behandeln** von *hDbcInfoToken*.  
  
## <a name="remarks"></a>Hinweise  
 **SQLGetPoolID** verwendet, um die Pool-ID, die anhand eines Satzes von Verbindungsinformationen abzurufen (von **SQLSetConnectAttrForDbcInfo**, **SQLSetDriverConnectInfo**, und  **SQLSetConnectInfo**). Dieser Pool-ID wird verwendet, um eine Gruppe von Verbindungen zu identifizieren, die austauschbar verwendet werden können (möglicherweise muss eine zusätzliche zurückgesetzt). Die Pool-ID wird verwendet werden, um den Verbindungspool für diese Gruppe von Verbindungen zu identifizieren.  
  
 Immer ein Treiber SQL_ERROR oder SQL_INVALID_HANDLE zurückgibt, gibt der Treiber-Manager den Fehler an die Anwendung zurück (in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) oder [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Wenn ein Treiber SQL_SUCCESS_WITH_INFO zurückgibt, erhält der Treiber-Manager die Diagnoseinformationen aus *hDbcInfoToken*, und wird SQL_SUCCESS_WITH_INFO zurückgegeben. um die Anwendung im [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)und [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberfähiges Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Umfassen Sie sqlspi.h für die Entwicklung von ODBC-Treiber.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln einen ODBC-Treiber](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiberfähiges Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
