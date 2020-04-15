---
title: SQLPoolConnect-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPoolConnect function [ODBC]
ms.assetid: 41322737-890d-4a81-aed2-06cc3d546962
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5045fe47683529f858b01e69f6af696e2821ca4c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306901"
---
# <a name="sqlpoolconnect-function"></a>SQLPoolConnect-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.8 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **SQLPoolConnect** wird verwendet, um eine neue Verbindung zu erstellen, wenn keine Verbindung im Pool wiederverwendet werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
  
SQLRETURN  SQLPoolConnect(  
                SQLHDBC              hDbc,  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              wszOutConnectString,  
                SQLSMALLINT          cchConnectStringBuffer,  
                SQLSMALLINT *        cchConnectStringLen );  
```  
  
## <a name="arguments"></a>Argumente  
 *Hdbc*  
 [Eingabe] Das Verbindungshandle.  
  
 *hDbcInfoToken*  
 [Eingabe] Das Tokenhandle für die neue Anwendungsverbindungsanforderung.  
  
 *wszOutConnectString*  
 [Ausgabe] Zeiger auf einen Puffer für die abgeschlossene Verbindungszeichenfolge. Bei erfolgreicher Verbindung mit der Zieldatenquelle enthält dieser Puffer die abgeschlossene Verbindungszeichenfolge. Anwendungen sollten mindestens 1.024 Zeichen für diesen Puffer zuweisen.  
  
 Wenn *wszOutConnectString* NULL ist, gibt *cchConnectStringLen* weiterhin die Gesamtzahl der Zeichen zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), auf die im Puffer von *wszOutConnectString*verwiesen wird.  
  
 *cchConnectStringBuffer*  
 [Eingabe] Länge des **wszOutConnectString-Puffers* in Zeichen.  
  
 *cchConnectStringLen*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Zeichen (mit Ausnahme \*des Null-Beendigungszeichens) zurückgegeben werden soll, die in *wszOutConnectString*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Zeichen größer oder gleich *cchConnectStringBuffer* \*ist, wird die abgeschlossene Verbindungszeichenfolge in *wszOutConnectString* auf *cchConnectStringBuffer* abzüglich der Länge eines Null-Beendigungszeichens abgeschnitten.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Ähnlich wie [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) für jeden Eingabevalidierungsfehler, mit der Ausnahme, dass der Treiber-Manager einen **HandleType** von SQL_HANDLE_DBC_INFO_TOKEN und ein **Handle** von *hDbcInfoToken*verwendet.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Treiber-Manager garantiert, dass das übergeordnete HENV-Handle von *hDbc* und *hDbcInfoToken* identisch ist.  
  
 Im Gegensatz zu [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)gibt es kein *DriverCompletion-Argument,* um Benutzer zur Eingabe von Verbindungsinformationen aufzufordern. Ein Eingabeaufforderungsdialogfeld ist im Pooling-Szenario nicht zulässig.  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberbewusstes Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Wenn ein Treiber SQL_ERROR oder SQL_INVALID_HANDLE zurückgibt, gibt der Treiber-Manager den Fehler an die Anwendung zurück (in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) oder [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Wenn ein Treiber SQL_SUCCESS_WITH_INFO zurückgibt, ruft der Treiber-Manager die Diagnoseinformationen von *hDbcInfoToken*ab und gibt SQL_SUCCESS_WITH_INFO an die Anwendung in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) und [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)zurück.  
  
 Wenn eine Anwendung [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)verwendet, ist *wszOutConnectString* ein NULL-Puffer (die letzten drei Parameter werden alle auf NULL, 0, NULL festgelegt). Andernfalls muss der Treiber die Ausgabeverbindungszeichenfolge zurückgeben, die an den [SQLDriverConnect-Funktionsaufruf](../../../odbc/reference/syntax/sqldriverconnect-function.md) der Anwendung zurückgegeben wird.  
  
 Fügen Sie sqlspi.h für die ODBC-Treiberentwicklung ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiber-Aware-Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
