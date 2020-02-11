---
title: Sqlsetconnectattrfordbcinfo-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f16cac6a715716dcef0a1c2b337716835c14b2b7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67910372"
---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>SQLSetConnectAttrForDbcInfo-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,81 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **Sqlsetconnectattrfordbcinfo** ist identisch mit **SQLSetConnectAttr**, aber das-Attribut wird auf das Verbindungs Informations Token festgelegt, anstatt auf das Verbindungs Handle.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
  
SQLRETURN  SQLSetConnectAttrForDbcInfo(  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                SQLINTEGER            Attribute,  
                SQLPOINTER            ValuePtr,  
                SQLINTEGER            StringLength );  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbcinfotoken*  
 Der Tokenhandle.  
  
 *Attribut*  
 Der Das festzulegende Attribut. Die Liste der gültigen Attribute ist Treiber spezifisch und identisch mit denen für [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 *ValuePtr*  
 Der Zeiger auf den Wert, der dem *Attribut*zugeordnet werden soll. Abhängig vom Wert des *Attributs*ist *ValuePtr* ein ganzzahliger Wert von 32-Bit-Ganzzahl ohne Vorzeichen oder zeigt auf eine mit NULL endende Zeichenfolge. Beachten Sie, dass der Wert in *ValuePtr* eine Ganzzahl mit Vorzeichen sein kann, wenn das *Attribut* Argument ein Treiber spezifischer Wert ist.  
  
 *StringLength*  
 Der Wenn *Attribute* ein ODBC-definiertes Attribut ist und *ValuePtr* auf eine Zeichenfolge oder einen binären Puffer zeigt, sollte dieses Argument die Länge von **ValuePtr*aufweisen. Für Zeichen folgen Daten sollte dieses Argument die Anzahl der Bytes in der Zeichenfolge enthalten.  
  
 Wenn *Attribute* ein ODBC-definiertes Attribut und *ValuePtr* eine ganze Zahl ist, wird *StringLength* ignoriert.  
  
 Wenn *Attribute* ein Treiber definiertes Attribut ist, gibt die Anwendung die Art des Attributs für den Treiber-Manager an, indem das *StringLength* -Argument festgelegt wird. *StringLength* kann die folgenden Werte aufweisen:  
  
-   Wenn *ValuePtr* ein Zeiger auf eine Zeichenfolge ist, ist *StringLength* die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn *ValuePtr* ein Zeiger auf einen binären Puffer ist, platziert die Anwendung das Ergebnis des SQL_LEN_BINARY_ATTR (*length*)-Makros in *StringLength*. Dadurch wird ein negativer Wert in *StringLength*platziert.  
  
-   Wenn *ValuePtr* ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine binäre Zeichenfolge ist, sollte *StringLength* den Wert SQL_IS_POINTER haben.  
  
-   Wenn *ValuePtr* einen Wert mit fester Länge enthält, ist *StringLength* entweder SQL_IS_INTEGER oder SQL_IS_UINTEGER.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Identisch mit [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), mit dem Unterschied, dass der Treiber-Manager den **Handlertyp** SQL_HANDLE_DBC_INFO_TOKEN und ein **handle** von *hdbcinfotoken*verwendet.  
  
## <a name="remarks"></a>Bemerkungen  
 **Sqlsetconnectattrfordbcinfo** ist identisch mit **SQLSetConnectAttr**, legt jedoch das-Attribut für das Verbindungs Informations Token und nicht für das Verbindungs Handle fest. Wenn **SQLSetConnectAttr** z. b. ein Attribut nicht erkennt, sollte **sqlsetconnectattrfordbcinfo** auch SQL_ERROR für dieses Attribut zurückgeben.  
  
 Wenn der Treiber SQL_ERROR oder SQL_INVALID_HANDLE zurückgibt, sollte der Treiber dieses Attribut ignorieren, um die Pool-ID zu berechnen. Außerdem erhält der Treiber-Manager die Diagnoseinformationen von *hdbcinfotoken*und gibt SQL_SUCCESS_WITH_INFO an die Anwendung in [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md) und [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)zurück. Aus diesem Grund kann eine Anwendung Details dazu abrufen, warum einige Attribute nicht festgelegt werden können.  
  
 Anwendungen sollten diese Funktion nicht direkt aufzurufen. Ein ODBC-Treiber, der Treiber fähiges Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Fügen Sie sqlspi. h für die ODBC-Treiberentwicklung ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiber fähiges Verbindungs Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
