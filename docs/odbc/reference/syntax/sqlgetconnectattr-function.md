---
title: SQLGetConnectAttr-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectAttr
helpviewer_keywords:
- SQLGetConnectAttr function [ODBC]
ms.assetid: 2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6076f14ff0c33fec38b99e9c43b8a688970a7a9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285630"
---
# <a name="sqlgetconnectattr-function"></a>SQLGetConnectAttr-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetConnectAttr** gibt die aktuelle Einstellung eines Verbindungsattributs zurück.  
  
> [!NOTE]
>  Weitere Informationen darüber, was der Treiber-Manager dieser Funktion zuordnet, wenn eine ODBC 3 *.x-Anwendung* mit einem ODBC 2 *.x-Treiber* arbeitet, finden Sie unter [Mapping Replacement Functions for Backward Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetConnectAttr(  
     SQLHDBC        ConnectionHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *ConnectionHandle*  
 [Eingabe] Verbindungshandle.  
  
 *Attribut*  
 [Eingabe] Attribut, das abgerufen werden soll.  
  
 *ValuePtr*  
 [Ausgabe] Ein Zeiger auf den Speicher, in dem der aktuelle Wert des von *Attribut*angegebenen Attributs zurückgegeben werden soll. Bei ganzzahligen Attributen können einige Treiber nur das niedrigere 32-Bit- oder 16-Bit-Puffer schreiben und das Bit höherer Ordnung unverändert lassen. Daher sollten Anwendungen einen Puffer von SQLULEN verwenden und den Wert auf 0 initialisieren, bevor diese Funktion aufgerufen wird.  
  
 Wenn *ValuePtr* NULL ist, gibt *StringLengthPtr* weiterhin die Gesamtzahl der Bytes (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten) zurück, auf die im Puffer von *ValuePtr*verwiesen wird.  
  
 *BufferLength*  
 [Eingabe] Wenn *Attribute* ein ODBC-definiertes Attribut ist und *ValuePtr* auf eine Zeichenfolge oder \*einen Binärpuffer verweist, sollte dieses Argument die Länge von *ValuePtr*sein. Wenn *Attribute* ein ODBC-definiertes Attribut und \* *ValuePtr* eine ganze Zahl ist, wird *BufferLength* ignoriert. Wenn der Wert in * \*ValuePtr* eine Unicode-Zeichenfolge ist (beim Aufrufen von **SQLGetConnectAttrW**) muss das *BufferLength-Argument* eine gerade Zahl sein.  
  
 Wenn *Attribute* ein treiberdefiniertes Attribut ist, gibt die Anwendung die Art des Attributs für den Treiber-Manager an, indem das *Argument BufferLength* festgelegt wird. *BufferLength* kann die folgenden Werte haben:  
  
-   Wenn * \*ValuePtr* ein Zeiger auf eine Zeichenfolge ist, ist *BufferLength* die Länge der Zeichenfolge.  
  
-   Wenn * \*ValuePtr* ein Zeiger auf einen Binärpuffer ist, platziert die Anwendung das Ergebnis des*SQL_LEN_BINARY_ATTR(Länge*) -Makros in *BufferLength*. Dadurch wird ein negativer Wert in *BufferLength*platziert.  
  
-   Wenn * \*ValuePtr* ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder Binärzeichenfolge ist, sollte *BufferLength* den Wert SQL_IS_POINTER haben.  
  
-   Wenn * \*ValuePtr* einen Datentyp fester Länge enthält, ist *BufferLength* entweder SQL_IS_INTEGER oder SQL_IS_UINTEGER.  
  
 *StringLengthPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes (mit Ausnahme \*des Null-Beendigungszeichens) zurückgegeben werden soll, die in *ValuePtr*zurückgegeben werden können. Wenn \* *ValuePtr* ein Nullzeiger ist, wird keine Länge zurückgegeben. Wenn der Attributwert eine Zeichenfolge ist und die Anzahl der zurückzugebenden Bytes größer als *BufferLength* abzüglich der Länge des Null-Beendigungszeichens ist, werden die Daten in * \*ValuePtr* auf *BufferLength* abzüglich der Länge des Null-Beendigungszeichens abgeschnitten und vom Treiber null beendet.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetConnectAttr** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert aus der Diagnosedatenstruktur abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DBC und einem *Handle* von *ConnectionHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLGetConnectAttr** zurückgegeben werden, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Die in \* *ValuePtr* zurückgegebenen Daten wurden als *BufferLength* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten. Die Länge des nicht abgeschnittenen Zeichenfolgenwerts wird in **StringLengthPtr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08003|Verbindung nicht geöffnet|(DM) Es wurde ein *Attributwert* angegeben, der eine offene Verbindung erforderte.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die Fehlermeldung, die von der Diagnosedatenstruktur durch das Argument *MessageText* in **SQLGetDiagField** zurückgegeben wird, beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte keinen Speicher zuweisen, der zum Unterstützen der Ausführung oder des Abschlusses der Funktion erforderlich ist.|  
|HY010|Funktionssequenzfehler|(DM) **SQLBrowseConnect** wurde für den *ConnectionHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor **SQLBrowseConnect** SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgegeben wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für den *ConnectionHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) * \*ValuePtr* ist eine Zeichenfolge, und BufferLength war kleiner als Null, aber nicht gleich SQL_NTS.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|Der für das Argument *Attribut* angegebene Wert war für die vom Treiber unterstützte ODBC-Version ungültig.|  
|HY114|Treiber unterstützt keine asynchrone Funktionsausführung auf Verbindungsebene|(DM) Eine Anwendung hat versucht, die asynchrone Funktionsausführung mit SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE für einen Treiber zu aktivieren, der keine asynchronen Verbindungsvorgänge unterstützt.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Der für das Argument *Attribut* angegebene Wert war ein gültiges ODBC-Verbindungsattribut für die vom Treiber unterstützte ODBC-Version, wurde jedoch vom Treiber nicht unterstützt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der Treiber, der dem *ConnectionHandle* entspricht, unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Allgemeine Informationen zu Verbindungsattributen finden Sie unter [Verbindungsattribute](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Eine Liste der Attribute, die festgelegt werden können, finden Sie unter [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md). Wenn *Attribute* ein Attribut angibt, das eine Zeichenfolge zurückgibt, muss *ValuePtr* ein Zeiger auf einen Puffer für die Zeichenfolge sein. Die maximale Länge der zurückgegebenen Zeichenfolge, einschließlich des Null-Beendigungszeichens, ist *BufferLength-Bytes.*  
  
 Je nach Attribut muss eine Anwendung keine Verbindung herstellen, bevor **SQLGetConnectAttr**aufgerufen wird. Wenn **SQLGetConnectAttr** jedoch aufgerufen wird und das angegebene Attribut keinen Standard wert ist und nicht durch einen vorherigen Aufruf von **SQLSetConnectAttr**festgelegt wurde, gibt **SQLGetConnectAttr** SQL_NO_DATA zurück.  
  
 Wenn *Attribut* SQL_ATTR_ TRACE oder SQL_ATTR_ TRACEFILE ist, muss *ConnectionHandle* ungültig sein, und **SQLGetConnectAttr** gibt SQL_ERROR oder SQL_INVALID_HANDLE nicht zurück, wenn *ConnectionHandle* ungültig ist. Diese Attribute gelten für alle Verbindungen. **SQLGetConnectAttr** gibt SQL_ERROR oder SQL_INVALID_HANDLE zurück, wenn ein anderes Argument ungültig ist.  
  
 Obwohl eine Anwendung Anweisungsattribute mithilfe von **SQLSetConnectAttr**festlegen kann, kann eine Anwendung **SQLGetConnectAttr** nicht zum Abrufen von Anweisungsattributwerten verwenden. Es muss **SQLGetStmtAttr** aufrufen, um die Einstellung von Anweisungsattributen abzurufen.  
  
 Sowohl SQL_ATTR_AUTO_IPD- als auch SQL_ATTR_CONNECTION_DEAD-Verbindungsattribute können durch einen Aufruf von **SQLGetConnectAttr** zurückgegeben werden, können jedoch nicht durch einen Aufruf von **SQLSetConnectAttr**festgelegt werden.  
  
> [!NOTE]  
>  Es gibt keine asynchrone Unterstützung für **SQLGetConnectAttr**. Beim Implementieren von **SQLGetConnectAttr**kann ein Treiber die Leistung verbessern, indem er die Häufigkeit minimiert, mit der Informationen vom Server gesendet oder angefordert werden.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben der Einstellung eines Anweisungsattributs|[SQLGetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|Festlegen eines Verbindungsattributs|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Festlegen eines Umgebungsattributs|[SQLSetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Festlegen eines Anweisungsattributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
