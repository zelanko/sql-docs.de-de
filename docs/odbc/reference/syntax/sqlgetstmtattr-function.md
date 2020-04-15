---
title: SQLGetStmtAttr-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetStmtAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetStmtAttr
helpviewer_keywords:
- SQLGetStmtAttr function [ODBC]
ms.assetid: e321d460-e997-4527-aee6-207cf5a498e9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89e7c75b412a6358806017102915989a8370dd43
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303304"
---
# <a name="sqlgetstmtattr-function"></a>SQLGetStmtAttr-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetStmtAttr** gibt die aktuelle Einstellung eines Anweisungsattributs zurück.  
  
> [!NOTE]  
>  Weitere Informationen darüber, was der Treiber-Manager dieser Funktion zuordnet, wenn ein ODBC 3. *x-Anwendung* arbeitet mit einem ODBC 2. *x-Treiber,* siehe [Mapping-Ersatzfunktionen für die Abwärtskompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetStmtAttr(  
     SQLHSTMT        StatementHandle,  
     SQLINTEGER      Attribute,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *Attribut*  
 [Eingabe] Attribut, das abgerufen werden soll.  
  
 *ValuePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem der Wert des in *Attribut*angegebenen Attributs zurückgegeben werden soll.  
  
 Wenn *ValuePtr* NULL ist, gibt *StringLengthPtr* weiterhin die Gesamtzahl der Bytes (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten) zurück, auf die im Puffer von *ValuePtr*verwiesen wird.  
  
 *BufferLength*  
 [Eingabe] Wenn *Attribute* ein ODBC-definiertes Attribut ist und *ValuePtr* auf eine Zeichenfolge oder \*einen Binärpuffer verweist, sollte dieses Argument die Länge von *ValuePtr*sein. Wenn *Attribute* ein ODBC-definiertes Attribut und \* *ValuePtr* eine ganze Zahl ist, wird *BufferLength* ignoriert. Wenn der in * \*ValuePtr* zurückgegebene Wert eine Unicode-Zeichenfolge ist (beim Aufrufen von **SQLGetStmtAttrW**), muss das *BufferLength-Argument* eine gerade Zahl sein.  
  
 Wenn *Attribute* ein treiberdefiniertes Attribut ist, gibt die Anwendung die Art des Attributs für den Treiber-Manager an, indem das *Argument BufferLength* festgelegt wird. *BufferLength* kann die folgenden Werte haben:  
  
-   Wenn * \*ValuePtr* ein Zeiger auf eine Zeichenfolge ist, ist *BufferLength* die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn * \*ValuePtr* ein Zeiger auf einen Binärpuffer ist, platziert die Anwendung das Ergebnis des Makros*SQL_LEN_BINARY_ATTR(Länge*) in *BufferLength*. Dadurch wird ein negativer Wert in *BufferLength*platziert.  
  
-   Wenn * \*ValuePtr* ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder Binärzeichenfolge ist, sollte *BufferLength* den Wert SQL_IS_POINTER haben.  
  
-   Wenn * \*ValuePtr* einen Datentyp fester Länge enthält, wird *BufferLength* entweder SQL_IS_INTEGER oder SQL_IS_UINTEGER.  
  
 *StringLengthPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes (mit Ausnahme des Null-Beendigungszeichens) zurückgegeben werden soll, die in * \*ValuePtr*zurückgegeben werden können. Wenn *ValuePtr* ein Nullzeiger ist, wird keine Länge zurückgegeben. Wenn der Attributwert eine Zeichenfolge ist und die Anzahl der zurückzugebenden Bytes größer oder gleich *BufferLength*ist, werden die Daten in * \*ValuePtr* auf *BufferLength* abzüglich der Länge eines Null-Beendigungszeichens abgeschnitten und vom Treiber null beendet.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetStmtAttr** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die normalerweise von **SQLGetStmtAttr** zurückgegeben werden, und es werden die SQLSTATE-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Die in * \*ValuePtr* zurückgegebenen Daten wurden als *BufferLength* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten. Die Länge des nicht abgeschnittenen Zeichenfolgenwerts wird in **StringLengthPtr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|24.000|Ungültiger Cursorstatus|Das Argument *Attribut* wurde SQL_ATTR_ROW_NUMBER und der Cursor wurde nicht geöffnet, oder der Cursor wurde vor dem Anfang des Resultsets oder nach dem Ende des Resultsets positioniert.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im Argument *MessageText* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLGetStmtAttr-Funktion** aufgerufen wurde.<br /><br /> (DM) Eine asynchron ausgeführte Funktion wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|*(DM) \*ValuePtr* ist eine Zeichenfolge, und BufferLength war kleiner als Null, aber nicht gleich SQL_NTS.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|Der für das Argument *Attribut* angegebene Wert war für die vom Treiber unterstützte ODBC-Version ungültig.|  
|HY109|Ungültige Cursorposition|Das *Attributargument* wurde SQL_ATTR_ROW_NUMBER, und die Zeile wurde gelöscht oder konnte nicht abgerufen werden.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionale Funktion nicht implementiert|Der für das Argument *Attribut* angegebene Wert war ein gültiges ODBC-Anweisungsattribut für die vom Treiber unterstützte ODBC-Version, wurde jedoch vom Treiber nicht unterstützt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* entsprechende Treiber unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Allgemeine Informationen zu Anweisungsattributen finden Sie unter [Anweisungsattribute](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 Ein Aufruf von **SQLGetStmtAttr** gibt in * \*ValuePtr* den Wert des in *Attribut*angegebenen Anweisungsattributs zurück. Dieser Wert kann entweder ein SQLULEN-Wert oder eine null-terminierte Zeichenfolge sein. Wenn es sich bei dem Wert um einen SQLULEN-Wert handelt, schreiben einige Treiber möglicherweise nur das niedrigere 32-Bit- oder 16-Bit-Puffer und lassen das Bit höherer Ordnung unverändert. Daher sollten Anwendungen einen Puffer von SQLULEN verwenden und den Wert auf 0 initialisieren, bevor diese Funktion aufgerufen wird. Außerdem werden die Argumente *BufferLength* und *StringLengthPtr* nicht verwendet. Wenn der Wert eine null-terminierte Zeichenfolge ist, gibt die Anwendung die maximale Länge dieser Zeichenfolge im *BufferLength-Argument* an, und der Treiber gibt die Länge dieser Zeichenfolge im * \*StringLengthPtr-Puffer* zurück.  
  
 So ermöglichen Anwendungen, die **SQLGetStmtAttr** aufrufen, mit ODBC 2 zu arbeiten. *x-Treiber* wird ein Aufruf von **SQLGetStmtAttr** im Treiber-Manager **SQLGetStmtOption**zugeordnet.  
  
 Die folgenden Anweisungsattribute sind schreibgeschützt und können daher von **SQLGetStmtAttr**abgerufen werden, aber nicht von **SQLSetStmtAttr**festgelegt:  
  
-   SQL_ATTR_IMP_PARAM_DESC  
  
-   SQL_ATTR_IMP_ROW_DESC  
  
-   SQL_ATTR_ROW_NUMBER  
  
 Eine Liste der Attribute, die festgelegt und abgerufen werden können, finden Sie unter [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben der Einstellung eines Verbindungsattributs|[SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Festlegen eines Verbindungsattributs|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Festlegen eines Anweisungsattributs|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
