---
title: SQLPoolConnect-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c390dacb5072c5d516e95b4fe6b789bfffbbd2d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68005802"
---
# <a name="sqlpoolconnect-function"></a>SQLPoolConnect-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: Einhaltung von ODBC 3.8-Standards: ODBC  
  
 **Zusammenfassung**  
 **SQLPoolConnect** wird verwendet, um eine neue Verbindung erstellen, wenn keine Verbindung im Pool wiederverwendet werden kann.  
  
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
 *hDbc*  
 [Eingabe] Der Verbindungs-Handle.  
  
 *hDbcInfoToken*  
 [Eingabe] Das Tokenhandle für die neue verbindungsanforderung für die Anwendung.  
  
 *wszOutConnectString*  
 [Ausgabe] Zeiger auf einen Puffer für die vollständige Verbindungszeichenfolge. Bei erfolgreicher Verbindung auf die Datenquelle enthält dieser Puffer vervollständigte Verbindungszeichenfolge. Anwendungen sollten mindestens 1.024 Zeichen für diesen Puffer zuordnen.  
  
 Wenn *WszOutConnectString* NULL ist, *CchConnectStringLen* gibt immer noch die Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) zur zurück in die Puffer verweist *WszOutConnectString*.  
  
 *cchConnectStringBuffer*  
 [Eingabe] Länge der **WszOutConnectString* Puffers in Zeichen.  
  
 *cchConnectStringLen*  
 [Ausgabe] Zeiger auf einen Puffer für die Rückgabe der Gesamtzahl der Zeichen, die (mit Ausnahme der Null-Terminierungszeichen) zur Verfügung, die in zurückgegeben \* *WszOutConnectString*. Wenn die Anzahl der zurückzugebenden verfügbaren Zeichen ist größer als oder gleich ist *CchConnectStringBuffer*, wird die Verbindungszeichenfolge zumeist im abgeschlossen \* *WszOutConnectString* auf abgeschnitten*CchConnectStringBuffer* abzüglich der Länge eines Zeichens Null-Terminierung vorliegt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or, SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Ähnlich wie [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) für alle Überprüfungsfehler, Eingabe, mit dem Unterschied, dass der Treiber-Manager verwendet eine **HandleType** von SQL_HANDLE_DBC_INFO_TOKEN und ein **behandeln** von *hDbcInfoToken*.  
  
## <a name="remarks"></a>Hinweise  
 Der Treiber-Manager wird sichergestellt, dass das übergeordnete Element HENV Handles aus *hDbc* und *hDbcInfoToken* sind identisch.  
  
 Im Gegensatz zu [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md), gibt es keine *DriverCompletion* Argument, um Benutzer zur Eingabe von Verbindungsinformationen aufzufordern. Ein Dialogfeld aufgefordert wird, ist im Lightweightpooling-Szenario nicht zulässig.  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberfähiges Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Immer ein Treiber SQL_ERROR oder SQL_INVALID_HANDLE zurückgibt, gibt der Treiber-Manager den Fehler an die Anwendung zurück (in [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) oder [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Wenn ein Treiber SQL_SUCCESS_WITH_INFO zurückgibt, erhält der Treiber-Manager die Diagnoseinformationen aus *hDbcInfoToken*, und wird SQL_SUCCESS_WITH_INFO zurückgegeben. um die Anwendung im [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)und [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Wenn eine Anwendung verwendet [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md), *WszOutConnectString* wird ein NULL-Puffer (die letzten drei Parameter werden alle NULL festgelegt werden, 0, NULL) sein. Andernfalls muss der Treiber die ausgegebene Verbindungszeichenfolge, die die Anwendung zurückgegeben wird, zurückgeben [SQLDriverConnect-Funktion](../../../odbc/reference/syntax/sqldriverconnect-function.md) aufrufen.  
  
 Umfassen Sie sqlspi.h für die Entwicklung von ODBC-Treiber.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln einen ODBC-Treiber](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiberfähiges Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
