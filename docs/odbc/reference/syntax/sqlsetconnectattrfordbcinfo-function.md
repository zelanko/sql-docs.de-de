---
title: SQLSetConnectAttrForDbcInfo-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttrForDbcInfo function [ODBC]
ms.assetid: a28fadb9-b998-472a-b252-709507e92005
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9f43a0fc6cd02fe566579a543667f9a4c4c1a108
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301887"
---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>SQLSetConnectAttrForDbcInfo-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.81 Standard-Konformität: ODBC  
  
 **Zusammenfassung**  
 **SQLSetConnectAttrForDbcInfo** ist identisch mit **SQLSetConnectAttr**, legt jedoch das Attribut für das Verbindungsinformationstoken anstelle des Verbindungshandles fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
  
SQLRETURN  SQLSetConnectAttrForDbcInfo(  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                SQLINTEGER            Attribute,  
                SQLPOINTER            ValuePtr,  
                SQLINTEGER            StringLength );  
```  
  
## <a name="arguments"></a>Argumente  
 *hDbcInfoToken*  
 [Eingabe] Token-Handle.  
  
 *Attribut*  
 [Eingabe] Attribut, das festgelegt werden soll. Die Liste der gültigen Attribute ist treiberspezifisch und identisch mit [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 *ValuePtr*  
 [Eingabe] Zeiger auf den Wert, der *Attribute*zugeordnet werden soll. Abhängig vom Wert von *Attribut*ist *ValuePtr* ein 32-Bit-Ganzzahlwert ohne Vorzeichen oder auf eine null-terminierte Zeichenfolge. Beachten Sie, dass, wenn das *Attributargument* ein treiberspezifischer Wert ist, der Wert in *ValuePtr* eine signierte ganze Zahl sein kann.  
  
 *StringLength*  
 [Eingabe] Wenn *Attribute* ein ODBC-definiertes Attribut ist und *ValuePtr* auf eine Zeichenfolge oder einen Binärpuffer verweist, sollte dieses Argument die Länge von **ValuePtr*sein. Bei Zeichenfolgendaten sollte dieses Argument die Anzahl der Bytes in der Zeichenfolge enthalten.  
  
 Wenn *Attribute* ein ODBC-definiertes Attribut und *ValuePtr* eine ganze Zahl ist, wird *StringLength* ignoriert.  
  
 Wenn *Attribute* ein treiberdefiniertes Attribut ist, gibt die Anwendung die Art des Attributs für den Treiber-Manager an, indem das *StringLength-Argument* festgelegt wird. *StringLength* kann die folgenden Werte haben:  
  
-   Wenn *ValuePtr* ein Zeiger auf eine Zeichenfolge ist, ist *StringLength* die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn *ValuePtr* ein Zeiger auf einen Binärpuffer ist, platziert die Anwendung das Ergebnis des*SQL_LEN_BINARY_ATTR(Länge*) Makros in *StringLength*. Dadurch wird ein negativer Wert in *StringLength*platziert.  
  
-   Wenn *ValuePtr* ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine Binärzeichenfolge ist, sollte *StringLength* den Wert SQL_IS_POINTER haben.  
  
-   Wenn *ValuePtr* einen Wert mit fester Länge enthält, ist *StringLength* entweder SQL_IS_INTEGER oder SQL_IS_UINTEGER.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Genauso wie [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), mit der Ausnahme, dass der Treiber-Manager einen **HandleType** von SQL_HANDLE_DBC_INFO_TOKEN und ein **Handle** von *hDbcInfoToken*verwendet.  
  
## <a name="remarks"></a>Bemerkungen  
 **SQLSetConnectAttrForDbcInfo** ist identisch mit **SQLSetConnectAttr**, legt jedoch das Attribut für das Verbindungsinformationstoken anstelle des Verbindungshandles fest. Wenn **SQLSetConnectAttr** beispielsweise kein Attribut erkennt, sollte **SQLSetConnectAttrForDbcInfo** auch SQL_ERROR für dieses Attribut zurückgeben.  
  
 Wenn der Treiber SQL_ERROR oder SQL_INVALID_HANDLE zurückkehrt, sollte der Treiber dieses Attribut ignorieren, um die Pool-ID zu berechnen. Außerdem ruft der Treiber-Manager die Diagnoseinformationen von *hDbcInfoToken*ab und gibt SQL_SUCCESS_WITH_INFO an die Anwendung in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) und [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)zurück. Daher kann eine Anwendung Details darüber abrufen, warum einige Attribute nicht festgelegt werden können.  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberbewusstes Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Fügen Sie sqlspi.h für die ODBC-Treiberentwicklung ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiber-Aware-Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
