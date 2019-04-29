---
title: Zuordnen von Ersatzfunktionen für die Kompatibilität der Apps – ODBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping replacement functions [ODBC]
- upgrading applications [ODBC], mapping replacement functions
- compatibility [ODBC], mapping replacement functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], mapping replacement functions
- application upgrades [ODBC], mapping replacement functions
- backward compatibility [ODBC], mapping replacement functions
ms.assetid: f5e6d9da-76ef-42cb-b3f5-f640857df732
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6cecc7fcd5ffa7234544dd0a9bc10407b1ea5cb1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63032835"
---
# <a name="mapping-replacement-functions-for-backward-compatibility-of-applications"></a>Zuordnen von Ersatzfunktionen für die Abwärtskompatibilität von Anwendungen
Eine ODBC 3.*.x* Anwendung über die ODBC 3.*.x* -Treiber-Manager funktioniert mit einer ODBC 2. *X* Treiber, solange keine neuen Funktionen verwendet werden. Beide Funktionen dupliziert und Änderungen am Verhalten, allerdings wirken sich die Möglichkeit, die die ODBC 3. *x* Anwendung funktioniert in einer ODBC 2. *X* Treiber. Wenn Sie mit einer ODBC 2. arbeiten zu können. *x* -Treiber verwenden, wird der Treiber-Manager die folgenden ODBC 3. zugeordnet. *X* -Funktionen, die eine oder mehrere ODBC 2. ersetzt haben. *X* -Funktionen in die entsprechenden ODBC 2. *X* Funktionen.  
  
|ODBC 3. *x* Funktion|ODBC-2. *x* Funktion|  
|-------------------------|-------------------------|  
|**SQLAllocHandle**|**SQLAllocEnv**, **SQLAllocConnect**, oder **SQLAllocStmt**|  
|**SQLBulkOperations**|**SQLSetPos**|  
|**SQLColAttribute**|**SQLColAttributes**|  
|**SQLEndTran**|**SQLTransact**|  
|**SQLFetch**|**SQLExtendedFetch**|  
|**SQLFetchScroll**|**SQLExtendedFetch**|  
|**SQLFreeHandle**|**SQLFreeEnv**, **SQLFreeConnect**, oder **SQLFreeStmt**|  
|**SQLGetConnectAttr**|**SQLGetConnectOption**|  
|**SQLGetDiagRec**|**SQLError**|  
|**SQLGetStmtAttr**|**SQLGetStmtOption**[1]|  
|**SQLSetConnectAttr**|**SQLSetConnectOption**|  
|**SQLSetStmtAttr**|**SQLSetStmtOption**[1]|  
  
 [1] anderen Aktionen können vom jeweiligen Attribut angefordert wird auch ausgeführt werden.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
 Der Treiber-Manager zugeordnet wird, diese Option, um **SQLAllocEnv**, **SQLAllocConnect**, oder **SQLAllocStmt**je nach Bedarf. Der folgende Aufruf von **SQLAllocHandle**:  
  
```  
SQLAllocHandle(HandleType, InputHandle, OutputHandlePtr);  
```  
  
 Führt im Treiber-Manager die folgenden ausführen (konzeptionelle und keine fehlerüberprüfung) zuordnen:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLAllocEnv(OutputHandlePtr));  
   case SQL_HANDLE_DBC: return (SQLAllocConnect (InputHandle, OutputHandlePtr));  
   case SQL_HANDLE_STMT: return (SQLAllocStmt (InputHandle, OutputHandlePtr));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
 Der Treiber-Manager zugeordnet wird, diese Option, um **SQLSetPos**. Der folgende Aufruf von **SQLBulkOperations**:  
  
```  
SQLBulkOperations(hstmt, Operation);  
```  
  
 führt die folgende Sequenz von Schritten:  
  
1.  Wenn das Argument der Operation SQL_ADD ist, ruft der Treiber-Manager **SQLSetPos** wie folgt:  
  
    ```  
    SQLSetPos (hstmt, 0, SQL_ADD, SQL_LOCK_NO_CHANGE);  
    ```  
  
2.  Wenn das Argument der Operation nicht SQL_ADD ist, gibt der Treiber SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner).  
  
3.  Wenn die Anwendung versucht, so ändern Sie die SQL_ATTR_ROW_STATUS_PTR zwischen den Aufrufen **SQLFetch** oder **SQLFetchScroll** und **SQLBulkOperations**, wird der Treiber-Manager SQLSTATE HY011 zurück (Attribut kann nicht jetzt festgelegt werden).  
  
4.  Wenn das Argument der Operation SQL_ADD ist, muss die Anwendung aufrufen **SQLBindCol** so binden Sie die Daten eingefügt werden soll. Es kann nicht aufgerufen werden **SQLSetDescField** oder **SQLSetDescRec** so binden Sie die Daten eingefügt werden soll.  
  
5.  Wenn die Operationsargument SQL_ADD und die Anzahl der einzufügenden Zeilen nicht identisch mit der aktuellen Größe des Rowsets ist, **SQLSetStmtAttr** aufgerufen werden, um das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut auf die Anzahl der Zeilen für das Festlegen vor dem Aufruf eingefügt **SQLBulkOperations**. Um die Größe des vorherigen Rowsets wiederherzustellen, legen Sie die Anwendung das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut vor der **SQLFetch**, **SQLFetchScroll**, oder **SQLSetPos**aufgerufen wird.  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
 Der Treiber-Manager zugeordnet wird, diese Option, um **SQLColAttributes**. Der folgende Aufruf von **SQLColAttribute**:  
  
```  
SQLColAttribute(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
```  
  
 führt die folgende Sequenz von Schritten:  
  
1.  Wenn *FieldIdentifier* ist eine der folgenden:  
  
     SQL_DESC_PRECISION SQL_DESC_SCALE, SQL_DESC_LENGTH, SQL_DESC_OCTET_LENGTH, SQL_DESC_UNNAMED, SQL_DESC_BASE_COLUMN_NAME, SQL_DESC_LITERAL_PREFIX, SQL_DESC_LITERAL_SUFFIX oder SQL_DESC_LOCAL_TYPE_NAME  
  
     der Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY091 (Ungültiger Deskriptorfeldbezeichner). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
2.  Der Treiber-Manager ordnet SQL_COLUMN_COUNT SQL_COLUMN_NAME oder SQL_COLUMN_NULLABLE SQL_DESC_COUNT SQL_DESC_NAME oder SQL_DESC_NULLABLE, bzw. (Einer ODBC 2.*.x* Treiber muss nur SQL_COLUMN_COUNT, SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE, nicht SQL_DESC_COUNT, SQL_DESC_NAME, und unterstützen SQL_DESC_NULLABLE.) Der Aufruf von SQLColAttribute zugeordnet ist:  
  
    ```  
    SQLColAttributes(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
    ```  
  
3.  Alle anderen *FieldIdentifier* Werte werden bis an den Treiber übergeben, mit **SQLColAttribute** zugeordnet **SQLColAttributes** wie zuvor gezeigt.  
  
4.  Wenn *Pufferlänge* ist kleiner als 0 (null) der Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY090 (ungültige Zeichenfolgen- oder Pufferlänge Länge). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
5.  Wenn *FieldIdentifier* SQL_DESC_CONCISE_TYPE und des zurückgegebenen Typs präzise Datetime-Datentyp, der Treiber-Manager-Zuordnungen, die die Rückgabe für Datum, Uhrzeit und Timestamp-Codes Werte.  
  
6.  Der Treiber-Manager führt erforderlichen Überprüfungen, um festzustellen, ob Anforderungen von SQLSTATE HY010 (Fehler bei Funktionssequenz) ausgelöst werden soll. Wenn also der Treiber-Manager SQL_ERROR zurück, und SQLSTATE HY010 zurückgibt (Sequenzfehler funktionieren). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
## <a name="sqlendtran"></a>SQLEndTran  
 Der Treiber-Manager zugeordnet wird, diese Option, um **SQLTransact**. Der folgende Aufruf von **SQLEndTran**:  
  
```  
SQLEndTran(HandleType, Handle, CompletionType);  
```  
  
 Führt im Treiber-Manager die folgenden ausführen (konzeptionelle und keine fehlerüberprüfung) zuordnen:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV:return(SQLTransact(Handle, SQL_NULL_HDBC, CompletionType));  
   case SQL_HANDLE_DBC:return(SQLTransact(SQL_NULL_HENV, Handle, CompletionType);  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlfetch"></a>SQLFetch  
 Der Treiber-Manager zugeordnet wird, diese Option, um **SQLExtendedFetch** mit einem *FetchOrientation* Argument sql_fetch_next. Der folgende Aufruf von **SQLFetch**:  
  
```  
SQLFetch (StatementHandle);  
```  
  
 in der aufrufenden-Treiber-Manager führt **SQLExtendedFetch**wie folgt:  
  
```  
rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, &RowCount, RowStatusArray);  
```  
  
 In diesem Aufruf die *PcRow* Argument festgelegt ist, auf den Wert, der die Anwendung das Anweisungsattribut SQL_ATTR_ROWS_FETCHED_PTR fest, durch einen Aufruf von festlegt **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Wenn die Anwendung ruft **SQLSetStmtAttr** um SQL_ATTR_ROW_STATUS_PTR auf ein Statusarray festgelegt, speichert der Treiber-Manager den Zeiger. *RowStatusArray* kann ein null-Zeiger gleich sein.  
  
 Wenn der Treiber nicht unterstützt **SQLExtendedFetch** und die Cursorbibliothek geladen ist, wird der Treiber-Manager der Cursorbibliothek **SQLExtendedFetch** zuordnen **SQLFetch** auf **SQLExtendedFetch**. Wenn der Treiber nicht unterstützt **SQLExtendedFetch** und die Cursorbibliothek nicht geladen wird, wird der Treiber-Manager übergibt, den Aufruf von **SQLFetch** über an den Treiber. Wenn die Anwendung ruft **SQLSetStmtAttr** zum Festlegen von SQL_ATTR_ROW_STATUS_PTR des Treiber-Managers wird sichergestellt, dass das Array aufgefüllt ist. Wenn die Anwendung ruft **SQLSetStmtAttr** um SQL_ATTR_ROWS_FETCHED_PTR festgelegt, legt der Treiber-Manager in diesem Feld auf 1 fest.  
  
## <a name="sqlfetchscroll"></a>SQLFetchScroll  
 Der Treiber-Manager zugeordnet wird, diese Option, um **SQLExtendedFetch**. Der folgende Aufruf von **SQLFetchScroll**:  
  
```  
SQLFetchScroll(StatementHandle, FetchOrientation, FetchOffset);  
```  
  
 führt die folgende Sequenz von Schritten:  
  
1.  Wenn die Anwendung ruft **SQLSetStmtAttr** um lassen Sie SQL_ATTR_ROW_STATUS_PTR (dem Feld SQL_DESC_ARRAY_STATUS_PTR im IRD festgelegt werden soll), zeigen Sie in ein Statusarray von, der Treiber-Manager speichert den this-Zeiger. Lassen Sie diesen Zeiger werden *RowStatusArray*, die andernfalls als auch die Let *RowStatusArray* ein null-Zeiger gleich sein. Wenn die *RowStatusArray* -Argument ein null-Zeiger festgelegt wird, die der Treiber-Manager wird ein Zeilenstatus Array generiert.  
  
2.  Wenn *FetchOrientation* ist keiner der SQL_FETCH_NEXT SQL_FETCH_PRIOR, SQL_FETCH_ABSOLUTE, SQL_FETCH_RELATIVE, SQL_FETCH_FIRST, SQL_FETCH_LAST oder sql_fetch_bookmark auf, der Treiber-Manager gibt SQL_ERROR mit SQLSTATE zurück. HY106 (Fetchtyp außerhalb des gültigen Bereichs). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
3.  Fall:  
  
-   Wenn *FetchOrientation* SQL_FETCH_BOOKMARK, gleich ist:  
  
    -   Wenn **SQLSetStmtAttr** hieß früher legen den Wert der SQL_ATTR_FETCH_BOOKMARK_PTR, und lassen Sie *bak* den Wert, der durch die Dereferenzierung des Zeigers SQL_DESC_FETCH_BOOKMARK_PTR abgerufen werden.  
  
    -   Andernfalls Rückgabe von SQL_ERROR mit SQLSTATE HY111 (Ungültiger Lesezeichenwert). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
     Der Treiber-Manager jetzt ruft **SQLExtendedFetch**wie folgt:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, Bmk, pcRow, RowStatusArray);  
    ```  
  
-   Andernfalls ruft der Treiber-Managers **SQLExtendedFetch**wie folgt:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, pcRow, RowStatusArray);  
    ```  
  
     In diesen Aufrufen die *PcRow* Argument festgelegt ist, auf den Wert, der die Anwendung das Anweisungsattribut SQL_ATTR_ROWS_FETCHED_PTR fest, durch einen Aufruf von festlegt **SQLSetStmtAttr**.  
  
-   SQL_ATTR_ROW_ARRAY_SIZE ist SQL_ROWSET_SIZE setzen zugeordnet.  
  
-   Wenn *rc* ist gleich SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO, und wenn *FetchOrientation* SQL_FETCH_BOOKMARK entspricht und *FetchOffset* ist nicht 0 ist, klicken Sie dann den Treiber gleich Manager sendet eine Warnung, SQLSTATE 01S10 (versuchen, rufen Sie, indem ein Offset von Lesezeichen, Offsetwert ignoriert), und gibt SQL_SUCCESS_WITH_INFO zurück.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 Der Treiber-Manager zugeordnet wird, diese Option, um **SQLFreeEnv**, **SQLFreeConnect**, oder **SQLFreeStmt** je nach Bedarf. Der folgende Aufruf von **SQLFreeHandle**:  
  
```  
SQLFreeHandle(HandleType, Handle);  
```  
  
 Führt im Treiber-Manager die folgenden ausführen (konzeptionelle und keine fehlerüberprüfung) zuordnen:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLFreeEnv(Handle));  
   case SQL_HANDLE_DBC: return (SQLFreeConnect(Handle));  
   case SQL_HANDLE_STMT: return (SQLFreeStmt(Handle, SQL_DROP));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
 Der Treiber-Manager zugeordnet wird, diese Option, um **SQLGetConnectOption**. Der folgende Aufruf von **SQLGetConnectAttr**:  
  
```  
SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 führt die folgende Sequenz von Schritten:  
  
1.  Wenn *Attribut* ist kein treiberdefinierten Verbindung oder Anweisung Attribut und ist kein Attribut in ODBC 2. definiert. *X*, der Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
2.  Wenn *Attribut* ist gleich SQL_ATTR_AUTO_IPD oder SQL_ATTR_METADATA_ID, die Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner).  
  
3.  Der Treiber-Manager führt die erforderlichen Überprüfungen, um festzustellen, ob SQLSTATE 08003 (Verbindung nicht geöffnet) oder SQLSTATE HY010 (Fehler bei Funktionssequenz) ausgelöst werden muss. Wenn dies der Fall ist, wird der Treiber-Manager gibt SQL_ERROR zurück, und sendet die entsprechende Fehlermeldung. Keine weiteren Regeln in diesem Abschnitt gelten.  
  
4.  Der Treiber-Manager ruft **SQLGetConnectOption** wie folgt:  
  
    ```  
    SQLGetConnectOption (ConnectionHandle, Attribute, ValuePtr);  
    ```  
  
     Beachten Sie, dass die *Pufferlänge* und *StringLengthPtr* werden ignoriert.  
  
## <a name="sqlgetdata"></a>SQLGetData  
 Wenn eine ODBC-3. *x* Anwendung mit einer ODBC 2.*.x* Treiber ruft **SQLGetData** mit der *ColumnNumber* Argument ungleich 0 ist, die ODBC 3.*.x* -Treiber-Manager wird hier zugeordnet, für einen Aufruf von **SQLGetStmtOption** mit der *Option* -Attributsatz auf SQL_GET_BOOKMARK.  
  
## <a name="sqlgetstmtattr"></a>'SQLGetStmtAttr'  
 Der Treiber-Manager zugeordnet wird, diese Option, um **SQLGetStmtOption**. Der folgende Aufruf von **SQLGetStmtAttr**:  
  
```  
SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 führt die folgende Sequenz von Schritten:  
  
1.  Wenn *Attribut* ist kein treiberdefinierten Verbindung oder Anweisung Attribut und ist kein Attribut in ODBC 2. definiert. *X*, der Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
2.  Wenn *Attribut* ist eine der folgenden:  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_AUTO_IPD  
  
     SQL_ATTR_ROW_BIND_TYPE  
  
     SQL_ATTR_IMP_ROW_DESC  
  
     SQL_ATTR_IMP_PARAM_DESC  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PREDICATE_PTR  
  
     SQL_ATTR_PREDICATE_OCTET_LENGTH_PTR  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     der Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
3.  Der Treiber-Manager führt erforderlichen Überprüfungen, um festzustellen, ob Anforderungen von SQLSTATE HY010 (Fehler bei Funktionssequenz) ausgelöst werden soll. Wenn also der Treiber-Manager SQL_ERROR zurück, und SQLSTATE HY010 zurückgibt (Sequenzfehler funktionieren). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
4.  Wenn *Attribut* gleich SQL_ATTR_ROWS_FETCHED_PTR fest, der Treiber-Manager gibt ein Zeiger auf die interne-Treiber-Manager-Variable *Luftlinie*, die es verwendet hat, oder verwenden in einem Aufruf von  **SQLExtendedFetch**. Keine weiteren Regeln in diesem Abschnitt gelten.  
  
5.  Wenn *Attribut* entspricht, SQL_DESC_FETCH_BOOKMARK_PTR, gibt der Treiber-Manager den entsprechenden Zeiger, die während eines Aufrufs zwischengespeichert hatten **SQLSetStmtAttr**.  
  
6.  Wenn *Attribut* entspricht, SQL_ATTR_ROW_STATUS_PTR, gibt der Treiber-Manager den entsprechenden Zeiger, die während eines Aufrufs zwischengespeichert hatten **SQLSetStmtAttr**.  
  
7.  Der Treiber-Manager ruft **SQLGetStmtOption** wie folgt:  
  
    ```  
    SQLGetStmtOption (hstmt, fOption, pvParam);  
    ```  
  
     in denen *Befehls beschäftigt*, *fOption*, und *PvParam* festgelegt auf die Werte der *StatementHandle*, *Attribut*, und *ValuePtr*bzw. Die *Pufferlänge* und *StringLengthPtr* werden ignoriert.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 Der Treiber-Manager zugeordnet wird, diese Option, um **SQLSetConnectOption**. Der folgende Aufruf von **SQLSetConnectAttr**:  
  
```  
SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, StringLength);  
```  
  
 führt die folgende Sequenz von Schritten:  
  
1.  Wenn *Attribut* ist kein treiberdefinierten Verbindung oder Anweisung Attribut und ist kein Attribut in ODBC 2. definiert. *X*, der Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
2.  Wenn *Attribut* SQL_ATTR_AUTO_IPD, die Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY092 entspricht (Ungültiger Attribut-/Optionsbezeichner).  
  
3.  Der Treiber-Manager führt die erforderlichen überprüft, ob SQLSTATE 08003 (Verbindung nicht geöffnet) oder SQLSTATE HY010 (Fehler bei Funktionssequenz) erforderlich, die ausgelöst werden. Wenn einer dieser Fehler ausgelöst werden muss, wird der Treiber-Manager gibt SQL_ERROR zurück, und sendet die entsprechende Fehlermeldung. Keine weiteren Regeln in diesem Abschnitt gelten.  
  
4.  Der Treiber-Manager ruft **SQLSetConnectOption** wie folgt:  
  
    ```  
    SQLSetConnectOption (hdbc, fOption, vParam);  
    ```  
  
     in denen *Hdbc*, *fOption*, und *vParam* festgelegt auf die Werte der *ConnectionHandle*, *Attribut*, und *ValuePtr*bzw. *StringLengthPtr* wird ignoriert.  
  
> [!NOTE]  
>  Die Möglichkeit, auf der Verbindungsebene Anweisungsattribute festlegt ist veraltet. Anweisungsattribute sollte nie auf der Verbindungsebene durch ein ODBC-3 festgelegt werden. *x* Anwendung.  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Der Treiber-Manager zugeordnet wird, diese Option, um **SQLSetStmtOption**. Der folgende Aufruf von **SQLSetStmtAttr**:  
  
```  
SQLSetStmtAttr(StatementHandle, Attribute, ValuePtr, StringLength);  
```  
  
 führt die folgende Sequenz von Schritten:  
  
1.  Wenn *Attribut* ist kein treiberdefinierten Verbindung oder Anweisung Attribut und ist kein Attribut in ODBC 2. definiert. *X*, der Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
2.  Wenn *Attribut* ist eine der folgenden:  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_AUTO_IPD  
  
     SQL_ATTR_ROW_BIND_TYPE  
  
     SQL_ATTR_IMP_ROW_DESC  
  
     SQL_ATTR_IMP_PARAM_DESC  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PREDICATE_PTR  
  
     SQL_ATTR_PREDICATE_OCTET_LENGTH_PTR  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     der Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
3.  Der Treiber-Manager führt die erforderlichen überprüft, ob SQLSTATE HY010 (Fehler bei Funktionssequenz) erforderlich, die ausgelöst werden. Wenn also der Treiber-Manager SQL_ERROR zurück, und SQLSTATE HY010 zurückgibt (Sequenzfehler funktionieren). Keine weiteren Regeln in diesem Abschnitt gelten.  
  
4.  Wenn *Attribut* ist gleich verweist SQL_ATTR_PARAMSET_SIZE SQL_ATTR_PARAMS_PROCESSED_PTR, finden Sie im Abschnitt "Zuordnungen für die Behandlung Parameterarrays," weiter unten in diesem Thema. Keine weiteren Regeln in diesem Abschnitt gelten.  
  
5.  Wenn *Attribut* SQL_ATTR_ROWS_FETCHED_PTR fest, die der Zeiger-Wert zur späteren Verwendung mit Treiber-Manager-Caches entspricht **SQLFetchScroll**.  
  
6.  Wenn *Attribut* SQL_ATTR_ROW_STATUS_PTR, die der Zeiger-Wert zur späteren Verwendung mit Treiber-Manager-Caches entspricht **SQLFetchScroll** oder **SQLSetPos**. Keine weiteren Regeln in diesem Abschnitt gelten.  
  
7.  Wenn *Attribut* SQL_ATTR_FETCH_BOOKMARK_PTR, die Treiber-Manager-Caches entspricht *ValuePtr* und verwendet den zwischengespeicherten Wert später in einem Aufruf von **SQLFetchScroll**. Keine weiteren Regeln in diesem Abschnitt gelten.  
  
8.  Der Treiber-Manager ruft **SQLSetStmtOption** wie folgt:  
  
    ```  
    SQLSetStmtOption (hstmt, fOption, vParam);  
    ```  
  
     in denen *Befehls beschäftigt*, *fOption*, und *vParam* festgelegt auf die Werte der *StatementHandle*, *Attribut*, und *ValuePtr*bzw. Die *StringLength* Argument wird ignoriert.  
  
     Wenn eine ODBC-2. *x* -Treiber unterstützt-Zeichenfolge, die treiberspezifische Anweisungsoptionen können nur eine ODBC 3. *X* Anwendung aufrufen sollten **SQLSetStmtOption** um diese Optionen festzulegen.  
  
## <a name="mappings-for-handling-parameter-arrays"></a>Zuordnungen für die Behandlung von Parameterarrays  
 Wenn die Anwendung aufruft:  
  
```  
SQLSetStmtAttr (StatementHandle, SQL_ATTR_PARAMSET_SIZE, Size, StringLength);  
```  
  
 der Treiber-Manager aufruft:  
  
```  
SQLParamOptions (StatementHandle, Size, &RowCount);  
```  
  
 Der Treiber-Manager gibt einen Zeiger später auf diese Variable, wenn die Anwendung aufruft **SQLGetStmtAttr** SQL_ATTR_PARAMS_PROCESSED_PTR abrufen. Der Treiber-Manager können diese internen Variablen nicht ändern, bis das Anweisungshandle auf den vorbereiteten oder zugeordneten Zustand zurückgegeben wird.  
  
 Eine ODBC-3. *x* Anwendung aufrufen kann **SQLGetStmtAttr** um den Wert der SQL_ATTR_PARAMS_PROCESSED_PTR zu erhalten, obwohl sie nicht explizit das Feld SQL_DESC_ARRAY_SIZE im APD festgelegt wurde. Diese Situation kann beispielsweise auftreten, wenn die Anwendung verfügt über eine generische Routine, die prüft, ob die aktuelle "Zeile" der Parameter verarbeitet werden, wenn **SQLExecute** wird SQL_NEED_DATA zurückgegeben. Diese Routine wird aufgerufen, und zwar unabhängig davon, ob die SQL_DESC_ARRAY_SIZE 1 ist, oder größer als 1 ist. Um dies zu berücksichtigen, der Treiber-Manager müssen diese interne Variable definieren, und zwar unabhängig davon, ob die Anwendung aufgerufen hat **SQLSetStmtAttr** Feld SQL_DESC_ARRAY_SIZE im APD festlegen. Wenn SQL_DESC_ARRAY_SIZE nicht festgelegt wurde, wird der Treiber-Manager hat, um sicherzustellen, dass diese Variable den Wert "1" vor der Rückgabe von enthält **SQLExecDirect** oder **SQLExecute**.  
  
## <a name="error-handling"></a>Fehlerbehandlung  
 In ODBC 3. *x*, wird beim Aufruf **SQLFetch** oder **SQLFetchScroll** füllt die SQL_DESC_ARRAY_STATUS_PTR in IRD und das SQL_DIAG_ROW_NUMBER-Feld, der einen bestimmten Datensatz für die Diagnose enthält die Nummer der Zeile im Rowset, dem auf diesen Eintrag bezieht. Die Anwendung kann anhand dieser eine Fehlermeldung mit einer bestimmten Zeilenposition korrelieren.  
  
 Eine ODBC-2. *x* Treiber werden in der Lage, diese Funktion bereitstellen. Sie erhalten jedoch Abgrenzung der Fehler mit SQLSTATE 01 s 01 (Fehler in Zeile). Eine ODBC-3. *x* Anwendung, die **SQLFetch** oder **SQLFetchScroll** mit einer ODBC 2. machen Sie sich beim. *X* Treiber benötigt diese Tatsache berücksichtigen. Beachten Sie, dass eine solche Anwendung kann nicht aufgerufen werden **SQLGetDiagField** um das Feld "SQL_DIAG_ROW_NUMBER" tatsächlich trotzdem zu erhalten. Eine ODBC-3. *x* Anwendung mit einer ODBC 2. *X* Treiber werden in der Lage, rufen Sie **SQLGetDiagField** nur mit einem *DiagIdentifier* Argument SQL_DIAG_MESSAGE_TEXT SQL_DIAG_NATIVE, SQL_DIAG_RETURNCODE oder SQL_DIAG_ SQLSTATE. Die ODBC 3.*.x* -Treiber-Manager verwaltet die Diagnosedaten-Struktur, bei der Arbeit mit einer ODBC 2. *X* Treiber, aber die ODBC 2. *X* Treiber nur diese vier Felder zurückgegeben.  
  
 Wenn eine ODBC-2. *x* Anwendung arbeitet mit einer ODBC 2. *X* -Treiber verwenden, wenn ein Vorgang mehrere Fehler, die vom Treiber-Manager, zurückgegeben werden kann verschiedene Fehler können zurückgegeben werden, indem die ODBC 3.*.x* -Treiber-Manager als durch die ODBC 2. *X* -Treiber-Manager.  
  
## <a name="mappings-for-bookmark-operations"></a>Zuordnungen für die Lesezeichen-Vorgänge  
 Die ODBC 3.*.x* -Treiber-Manager führt die folgenden Zuordnungen, wenn eine ODBC 3. *X* Anwendung mit einer ODBC 2. *X* Treiber führt die Lesezeichen-Vorgänge.  
  
### <a name="sqlbindcol"></a>SQLBindCol  
 Wenn eine ODBC-3. *x* Anwendung mit einer ODBC 2. *X* Treiber ruft **SQLBindCol** zum Binden an die Spalte 0 mit *fCType* gleich SQL_C_VARBOOKMARK, die ODBC 3.*.x* -Treiber-Manager wird überprüft ob die *Pufferlänge* Argument ist kleiner als 4 oder größer als 4, und wenn dies der Fall ist, gibt SQLSTATE HY090 (ungültige Zeichenfolgen- oder Pufferlänge Länge). Wenn die *Pufferlänge* Argument gleich 4 ist, ruft der Treiber-Manager **SQLBindCol** im Treiber, nach dem Ersetzen *fCType* mit SQL_C_BOOKMARK.  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 Wenn eine ODBC-3. *x* Anwendung mit einer ODBC 2. *X* Treiber ruft **SQLColAttribute** mit der *ColumnNumber* Argument auf 0 festgelegt, der Treiber-Manager gibt den *FieldIdentifier* Werte in der folgenden Tabelle aufgeführt.  
  
|*FieldIdentifier*|Wert|  
|-----------------------|-----------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|  
|SQL_DESC_CATALOG_NAME|"" (leere Zeichenfolge)|  
|SQL_DESC_CONCISE_TYPE|SQL_BINARY|  
|SQL_DESC_COUNT|Der gleiche Wert zurückgegeben werden, indem **SQLNumResultCols**|  
|SQL_DESC_DATETIME_INTERVAL_CODE|0|  
|SQL_DESC_DISPLAY_SIZE|8|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|  
|SQL_DESC_LABEL|"" (leere Zeichenfolge)|  
|SQL_DESC_LENGTH|0|  
|SQL_DESC_LITERAL_PREFIX|"" (leere Zeichenfolge)|  
|SQL_DESC_LITERAL_SUFFIX|"" (leere Zeichenfolge)|  
|SQL_DESC_LOCAL_TYPE_NAME|"" (leere Zeichenfolge)|  
|SQL_DESC_NAME|"" (leere Zeichenfolge)|  
|SQL_DESC_NULLABLE|SQL_NO_NULLS|  
|SQL_DESC_OCTET_LENGTH|4|  
|SQL_DESC_PRECISION|4|  
|SQL_DESC_SCALE|0|  
|SQL_DESC_SCHEMA_NAME|"" (leere Zeichenfolge)|  
|SQL_DESC_SEARCHABLE|SQL_PRED_NONE|  
|SQL_DESC_TABLE_NAME|"" (leere Zeichenfolge)|  
|SQL_DESC_TYPE|SQL_BINARY|  
|SQL_DESC_TYPE_NAME|"" (leere Zeichenfolge)|  
|SQL_DESC_UNNAMED|SQL_UNNAMED|  
|SQL_DESC_UNSIGNED|SQL_FALSE|  
|SQL_DESC_UPDATEABLE|SQL_ATTR_READ_ONLY|  
  
### <a name="sqldescribecol"></a>SQLDescribeCol  
 Wenn eine ODBC-3. *x* Anwendung mit einer ODBC 2. *X* Treiber ruft **SQLDescribeCol** mit der *ColumnNumber* Argument auf 0 festgelegt, gibt der Treiber-Manager in der folgenden Tabelle aufgeführten Werte zurück.  
  
|Puffer|Wert|  
|------------|-----------|  
|ColumnName|"" (leere Zeichenfolge)|  
|*NameLengthPtr|0|  
|*DataTypePtr|SQL_BINARY|  
|*ColumnSizePtr|4|  
|*DecimalDigitsPtr|0|  
|*NullablePtr|SQL_NO_NULLS|  
  
### <a name="sqlgetdata"></a>SQLGetData  
 Wenn eine ODBC-3. *x* Anwendung mit einer ODBC 2. *X* Treiber wird den folgenden Aufruf **SQLGetData** ein Lesezeichens abgerufen:  
  
```  
SQLGetData(StatementHandle, 0, SQL_C_VARBOOKMARK, TargetValuePtr, BufferLength, StrLen_or_IndPtr)  
```  
  
 der Aufruf zugeordnet ist **SQLGetStmtOption** mit einer *fOption* von SQL_GET_BOOKMARK, wie folgt:  
  
```  
SQLGetStmtOption(hstmt, SQL_GET_BOOKMARK, TargetValuePtr)  
```  
  
 wo *Befehls beschäftigt* und *PvParam* festgelegt sind, auf die Werte in *StatementHandle* und *TargetValuePtr*bzw. Das Lesezeichen wird zurückgegeben, in den Puffer, der auf die *PvParam* (*TargetValuePtr*) Argument. Der Wert in den Puffer verweist die *StrLen_or_IndPtr* Argument im Aufruf von **SQLGetData** auf 4 festgelegt ist.  
  
 Diese Zuordnung ist notwendig, für den Fall, in dem Konto **SQLFetch** aufgerufen wurde, vor dem Aufruf von **SQLGetData** und die ODBC 2. *X* Treiber nicht **SQLExtendedFetch**. In diesem Fall **SQLFetch** über die ODBC 2. übergeben werden sollen. *X* Treiber, die in der Groß-/Kleinschreibung Lesezeichen abrufen wird nicht unterstützt.  
  
 **SQLGetData** kann nicht mehrere Male aufgerufen werden, in einer ODBC 2. *X* Treiber zum Abrufen eines Lesezeichens in Teilen, daher ist das Aufrufen **SQLGetData** mit der *Pufferlänge* -Argument auf einen Wert kleiner als 4 festgelegt und die *ColumnNumber*SQLSTATE HY090-Argument auf 0 zurück (ungültige Zeichenfolgen- oder Pufferlänge Länge). **SQLGetData** kann jedoch werden mehrere Male abrufen desselben Lesezeichens aufgerufen.  
  
### <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Wenn eine ODBC-3. *x* Anwendung mit einer ODBC 2. *X* Treiber ruft **SQLSetStmtAttr** um das Attribut SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE festzulegen, der Treiber-Manager wird das Attribut auf SQL_UB_ON in die zugrunde liegenden ODBC 2. *X* Treiber.
