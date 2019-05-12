---
title: SQLGetStmtAttr-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6edec1b341855154e6df6ef24abb7da3d93ffc2
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65538004"
---
# <a name="sqlgetstmtattr-function"></a>SQLGetStmtAttr-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetStmtAttr** die aktuelle Einstellung eines Anweisung-Attributs zurück.  
  
> [!NOTE]  
>  Weitere Informationen über welche des Treiber-Managers ordnet diese Funktion zu, wenn eine ODBC-3. *x* Anwendung arbeitet mit einer ODBC 2. *X* -Treiber verwenden, finden Sie unter [Zuordnen von Ersatzfunktionen für Abwärtskompatibilität-Kompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
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
 [Eingabe] Attribut, das abgerufen werden.  
  
 *ValuePtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem den Wert des Attributs im angegebenen zurückgegeben *Attribut*.  
  
 Wenn *ValuePtr* NULL ist, *StringLengthPtr* gibt die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer, der auf zurückgegeben *ValuePtr*.  
  
 *BufferLength*  
 [Eingabe] Wenn *Attribut* ist ein ODBC-definierten Attribut und *ValuePtr* zeigt auf eine Zeichenfolge oder ein binärer Puffer, in dieses Argument muss die Länge des \* *ValuePtr*. Wenn *Attribut* ist ein ODBC-definierten Attribut und \* *ValuePtr* ist eine ganze Zahl, *Pufferlänge* wird ignoriert. Wenn der Rückgabewert in  *\*ValuePtr* ist eine Unicodezeichenfolge (beim Aufrufen von **SQLGetStmtAttrW**), wird die *Pufferlänge* Argument muss eine gerade Zahl sein.  
  
 Wenn *Attribut* ein treiberdefinierten-Attribut, wird die Anwendung zeigt die Art des Attributs auf den Treiber-Manager an, indem die *Pufferlänge* Argument. *BufferLength* können die folgenden Werte aufweisen:  
  
-   Wenn  *\*ValuePtr* ist ein Zeiger auf eine Zeichenfolge, *Pufferlänge* ist die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn  *\*ValuePtr* ist ein Zeiger auf ein binärer Puffer, aus, und klicken Sie dann die Anwendung das Ergebnis der SQL_LEN_BINARY_ATTR platziert (*Länge*)-Makro in *Pufferlänge*. Dadurch wird einen negativen Wert im platziert *Pufferlänge*.  
  
-   Wenn  *\*ValuePtr* ist ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder Binärzeichenfolge, *Pufferlänge* Wert SQL_IS_POINTER haben sollte.  
  
-   Wenn  *\*ValuePtr* ist einen Datentyp fester Länge enthält *Pufferlänge* ist SQL_IS_INTEGER oder SQL_IS_UINTEGER, nach Bedarf.  
  
 *StringLengthPtr*  
 [Ausgabe] Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen) zurückgegeben. verfügbar für die zurückzugebenden in  *\*ValuePtr*. Wenn *ValuePtr* ist ein null-Zeiger wird keine Länge zurückgegeben. Wenn Sie den Wert des Attributs ist eine Zeichenfolge, und die Anzahl der Bytes, die für die Rückgabe verfügbar ist, größer als oder gleich *Pufferlänge*, die Daten in  *\*ValuePtr* auf abgeschnitten*Pufferlänge* abzüglich der Länge des ein Null-Terminierungszeichen und Null-terminiert ist vom Treiber.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetStmtAttr** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* SQL _HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLGetStmtAttr** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Die Daten im zurückgegebenen  *\*ValuePtr* wurde abgeschnitten, um werden *Pufferlänge* abzüglich der Länge des ein Null-Terminierungszeichen. Die Länge des Werts den ungekürzten Zeichenfolge wird zurückgegeben, **StringLengthPtr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|24000|Ungültiger Cursorstatus|Das Argument *Attribut* SQL_ATTR_ROW_NUMBER wurde und der Cursor konnte nicht geöffnet werden, oder der Cursor vor dem Start des Resultsets oder nach dem Ende des Resultsets positioniert wurde.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** im Argument *MessageText* beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLGetStmtAttr** Funktion aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|*(DM) \*ValuePtr* ist eine Zeichenfolge, und die Pufferlänge war kleiner als 0 (null), aber ungleich SQL_NTS.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|Der angegebene Wert für das Argument *Attribut* war nicht gültig für die Version von ODBC, die vom Treiber unterstützt werden.|  
|HY109|Ungültige Cursorposition|Die *Attribut* Argument war SQL_ATTR_ROW_NUMBER und die Zeile wurde gelöscht haben oder konnte nicht abgerufen werden.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Optionales Feature nicht implementiert.|Der angegebene Wert für das Argument *Attribut* wurde ein gültiger ODBC-Anweisungsattribut, für die ODBC-Version vom Treiber unterstützt werden, jedoch wurde vom Treiber nicht unterstützt.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber entspricht der *StatementHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Allgemeine Informationen zu Anweisungsattribute, finden Sie unter [Anweisungsattribute](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 Ein Aufruf von **SQLGetStmtAttr** gibt  *\*ValuePtr* den Wert des Attributs im angegebenen Anweisung *Attribut*. Dieser Wert kann es sich entweder um einen Wert SQLULEN erstellt wurde oder ein Null-terminierte Zeichenfolge sein. Wenn der Wert einen SQLULEN-Wert ist, einige Treiber können nur die untere 32-Bit-schreiben oder 16-Bit, der einen Puffer und eine verlassen Bits höherer Ordnung unverändert. Anwendungen sollten daher verwendet einen Puffer mit SQLULEN erstellt wurde, und initialisieren den Wert auf 0 vor dem Aufrufen dieser Funktion. Darüber hinaus die *Pufferlänge* und *StringLengthPtr* Argumente werden nicht verwendet. Wenn der Wert ein Null-terminierte Zeichenfolge ist, handelt es sich bei der Anwendung wird die maximale Länge der Zeichenfolge in die *Pufferlänge* Argument und der Treiber gibt die Länge der Zeichenfolge in die  *\* StringLengthPtr* Puffer.  
  
 Damit Anwendungen Aufrufen **SQLGetStmtAttr** zum Arbeiten mit ODBC 2. *X* Treiber, die einen Aufruf von **SQLGetStmtAttr** zugeordnet ist, in der Treiber-Manager **SQLGetStmtOption**.  
  
 Die folgenden Anweisungsattribute sind schreibgeschützt, sodass abgerufen werden kann **SQLGetStmtAttr**, jedoch nicht von festgelegt **SQLSetStmtAttr**:  
  
-   SQL_ATTR_IMP_PARAM_DESC  
  
-   SQL_ATTR_IMP_ROW_DESC  
  
-   SQL_ATTR_ROW_NUMBER  
  
 Eine Liste der Attribute, die festgelegt und abgerufen werden können, finden Sie unter [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Die Einstellung ein Verbindungsattribut zurückgeben|[SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Ein Verbindungsattribut festlegen|[SQLSetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Wenn eine Anweisungsattribut|[SQLSetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
