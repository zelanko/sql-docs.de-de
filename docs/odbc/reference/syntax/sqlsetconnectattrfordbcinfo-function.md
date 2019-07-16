---
title: SQLSetConnectAttrForDbcInfo-Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67910372"
---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>SQLSetConnectAttrForDbcInfo-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-3,81 Standardkompatibilität: ODBC  
  
 **Zusammenfassung**  
 **SQLSetConnectAttrForDbcInfo** ist identisch mit **SQLSetConnectAttr**, sondern legt das Attribut auf der Verbindung Informationen-Token anstelle von auf dem Verbindungshandle fest.  
  
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
 [Eingabe] Tokenhandle.  
  
 *Attribut*  
 [Eingabe] Attribut, das festgelegt werden soll. Die Liste der gültigen Attribute ist treiberspezifisch und dieselbe wie für [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 *ValuePtr*  
 [Eingabe] Zeiger auf den Wert zugeordnet werden *Attribut*. Abhängig vom Wert *Attribut*, *ValuePtr* ein 32-Bit-Ganzzahl ohne Vorzeichen-Wert oder verweist auf eine Null-terminierte Zeichenfolge. Beachten Sie, dass bei der *Attribut* Argument ist ein Treiber-spezifische-Wert, der Wert in *ValuePtr* möglicherweise eine Ganzzahl mit Vorzeichen.  
  
 *StringLength*  
 [Eingabe] Wenn *Attribut* ist ein ODBC-definierten Attribut und *ValuePtr* zeigt auf eine Zeichenfolge oder ein binärer Puffer, in dieses Argument muss die Länge des **ValuePtr*. Für Zeichenfolgendaten sollte dieses Argument die Anzahl der Bytes in der Zeichenfolge enthalten.  
  
 Wenn *Attribut* ist ein ODBC-definierten Attribut und *ValuePtr* ist eine ganze Zahl, *StringLength* wird ignoriert.  
  
 Wenn *Attribut* ein treiberdefinierten-Attribut, wird die Anwendung zeigt die Art des Attributs auf den Treiber-Manager an, indem die *StringLength* Argument. *StringLength* können die folgenden Werte aufweisen:  
  
-   Wenn *ValuePtr* ist ein Zeiger auf eine Zeichenfolge, *StringLength* ist die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn *ValuePtr* ist ein Zeiger auf ein binärer Puffer, aus, und klicken Sie dann die Anwendung das Ergebnis der SQL_LEN_BINARY_ATTR platziert (*Länge*)-Makro in *StringLength*. Dadurch wird einen negativen Wert im platziert *StringLength*.  
  
-   Wenn *ValuePtr* ist ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine binäre Zeichenfolge *StringLength* Wert SQL_IS_POINTER haben sollte.  
  
-   Wenn *ValuePtr* enthält einen Wert fester Länge *StringLength* ist SQL_IS_INTEGER oder SQL_IS_UINTEGER, nach Bedarf.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Identisch mit [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), mit dem Unterschied, dass der Treiber-Manager verwendet eine **HandleType** von SQL_HANDLE_DBC_INFO_TOKEN und **behandeln** von *hDbcInfoToken* .  
  
## <a name="remarks"></a>Hinweise  
 **SQLSetConnectAttrForDbcInfo** ist identisch mit **SQLSetConnectAttr**, jedoch wird das Attribut für das Verbindungstoken für Informationen nicht auf dem Verbindungshandle. Z. B. wenn **SQLSetConnectAttr** ein Attribut nicht erkennt **SQLSetConnectAttrForDbcInfo** SQL_ERROR sollte auch für dieses Attribut zurück.  
  
 Wenn der Treiber gibt SQL_ERROR oder SQL_INVALID_HANDLE zurück, sollte dieses Attribut, um die Pool-ID zu berechnen der Treiber ignoriert werden. Darüber hinaus erhalten der Treiber-Manager die Diagnoseinformationen aus *hDbcInfoToken*, und wird SQL_SUCCESS_WITH_INFO zurückgegeben. um die Anwendung im [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) und [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md). Daher kann eine Anwendung abrufen, Details, warum einige Attribute können nicht festgelegt werden.  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberfähiges Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Umfassen Sie sqlspi.h für die Entwicklung von ODBC-Treiber.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln einen ODBC-Treiber](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiberfähiges Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
