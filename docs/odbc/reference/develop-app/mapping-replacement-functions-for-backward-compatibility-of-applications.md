---
title: Zuordnen von Ersatzfunktionen für die Kompatibilität von Apps - ODBC | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b18669fe9b6edbd39859166e382ad18d1b04a99a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301090"
---
# <a name="mapping-replacement-functions-for-backward-compatibility-of-applications"></a>Zuordnen von Ersatzfunktionen für die Abwärtskompatibilität von Anwendungen
Eine ODBC *3.x-Anwendung,* die über den ODBC *3.x* Driver Manager arbeitet, funktioniert mit einem ODBC *2.x-Treiber,* solange keine neuen Funktionen verwendet werden. Sowohl duplizierte Funktionen als auch Verhaltensänderungen wirken sich jedoch auf die Funktionsweise der ODBC *3.x-Anwendung* auf einem ODBC *2.x-Treiber* aus. Bei der Arbeit mit einem ODBC *2.x-Treiber* ordnet der Treiber-Manager die folgenden ODBC *3.x-Funktionen,* die eine oder mehrere ODBC *2.x-Funktionen* ersetzt haben, den entsprechenden ODBC *2.x-Funktionen* zu.  
  
|ODBC *3.x-Funktion*|ODBC *2.x-Funktion*|  
|-------------------------|-------------------------|  
|**SQLAllocHandle**|**SQLAllocEnv**, **SQLAllocConnect**oder **SQLAllocStmt**|  
|**SQLBulkOperations**|**SQLSetPos**|  
|**SQLColAttribute**|**SQLColAttributes**|  
|**SQLEndTran**|**SQLTransact**|  
|**SQLFetch**|**SQLExtendedFetch**|  
|**SQLFetchScroll**|**SQLExtendedFetch**|  
|**SQLFreeHandle**|**SQLFreeEnv**, **SQLFreeConnect**oder **SQLFreeStmt**|  
|**SQLGetConnectAttr**|**SQLGetConnectOption**|  
|**SQLGetDiagRec**|**Sqlerror**|  
|**'SQLGetStmtAttr'**|**SQLGetStmtOption**[1]|  
|**SQLSetConnectAttr**|**SQLSetConnectOption**|  
|**SQLSetStmtAttr**|**SQLSetStmtOption**[1]|  
  
 [1] Je nach angeforderten Attribut können auch andere Aktionen ausgeführt werden.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
 Der Treiber-Manager ordnet dies **ggf. SQLAllocEnv**, **SQLAllocConnect**oder **SQLAllocStmt**zu. Der folgende Aufruf von **SQLAllocHandle:**  
  
```  
SQLAllocHandle(HandleType, InputHandle, OutputHandlePtr);  
```  
  
 führt dazu, dass der Treiber-Manager die folgende Zuordnung (konzeptionell, keine Fehlerüberprüfung) durchführt:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLAllocEnv(OutputHandlePtr));  
   case SQL_HANDLE_DBC: return (SQLAllocConnect (InputHandle, OutputHandlePtr));  
   case SQL_HANDLE_STMT: return (SQLAllocStmt (InputHandle, OutputHandlePtr));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
 Der Treiber-Manager ordnet dies **SQLSetPos**zu. Der folgende Aufruf von **SQLBulkOperations:**  
  
```  
SQLBulkOperations(hstmt, Operation);  
```  
  
 führt zu der folgenden Abfolge von Schritten:  
  
1.  Wenn das Argument Operation SQL_ADD ist, ruft der Treiber-Manager **SQLSetPos** wie folgt auf:  
  
    ```  
    SQLSetPos (hstmt, 0, SQL_ADD, SQL_LOCK_NO_CHANGE);  
    ```  
  
2.  Wenn das Argument Operation nicht SQL_ADD ist, gibt der Treiber SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurück.  
  
3.  Wenn die Anwendung versucht, die SQL_ATTR_ROW_STATUS_PTR zwischen Aufrufen von **SQLFetch** oder **SQLFetchScroll** und **SQLBulkOperations**zu ändern, gibt der Treiber-Manager SQLSTATE HY011 zurück (Attribut kann jetzt nicht festgelegt werden).  
  
4.  Wenn das Operation-Argument SQL_ADD ist, muss die Anwendung **SQLBindCol** aufrufen, um die einzufügenden Daten zu binden. **SQLSetDescField** oder **SQLSetDescRec** kann nicht aufrufen, um die einzufügenden Daten zu binden.  
  
5.  Wenn das Operation-Argument SQL_ADD ist und die Anzahl der einzufügenden Zeilen nicht mit der aktuellen Rowsetgröße identisch ist, muss **SQLSetStmtAttr** aufgerufen werden, um das Attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung auf die Anzahl der Zeilen festzulegen, die vor dem Aufruf von **SQLBulkOperations**eingefügt werden sollen. Um auf die größe des vorherigen Rowsets zurückzufinden, muss die Anwendung das SQL_ATTR_ROW_ARRAY_SIZE Anweisungsattribut festlegen, bevor **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos** aufgerufen werden.  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
 Der Treiber-Manager ordnet **dies SQLColAttributes**zu. Der folgende Aufruf von **SQLColAttribute:**  
  
```  
SQLColAttribute(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
```  
  
 führt zu der folgenden Abfolge von Schritten:  
  
1.  Wenn *FieldIdentifier* einer der folgenden ist:  
  
     SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH, SQL_DESC_OCTET_LENGTH, SQL_DESC_UNNAMED, SQL_DESC_BASE_COLUMN_NAME, SQL_DESC_LITERAL_PREFIX, SQL_DESC_LITERAL_SUFFIX oder SQL_DESC_LOCAL_TYPE_NAME  
  
     Der Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY091 (Invalid descriptor field identifier) zurück. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
2.  Der Treiber-Manager ordnet SQL_DESC_COUNT, SQL_DESC_NAME oder SQL_DESC_NULLABLE SQL_COLUMN_COUNT, SQL_COLUMN_NAME oder SQL_COLUMN_NULLABLE zu. (Ein ODBC *2.x-Treiber* muss nur SQL_COLUMN_COUNT, SQL_COLUMN_NAME und SQL_COLUMN_NULLABLE und nicht SQL_DESC_COUNT, SQL_DESC_NAME und SQL_DESC_NULLABLE unterstützen.) Der Aufruf von SQLColAttribute ist zugeordnet:  
  
    ```  
    SQLColAttributes(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
    ```  
  
3.  Alle anderen *FieldIdentifier-Werte* werden an den Treiber übergeben, wobei **SQLColAttribute** **SQLColAttributes** zugeordnet ist, wie zuvor gezeigt.  
  
4.  Wenn *BufferLength* kleiner als 0 ist, gibt der Treiber-Manager SQL_ERROR mit SQLSTATE HY090 (Ungültige Zeichenfolge oder Pufferlänge) zurück. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
5.  Wenn *FieldIdentifier* SQL_DESC_CONCISE_TYPE ist und der zurückgegebene Typ ein präziser Datetime-Datentyp ist, ordnet der Treiber-Manager die Rückgabewerte für Datums-, Uhrzeit- und Zeitstempelcodes zu.  
  
6.  Der Treiber-Manager führt die erforderlichen Überprüfungen durch, um festzustellen, ob SQLSTATE HY010 (Funktionssequenzfehler) ausgelöst werden muss. Wenn dies der Fall ist, gibt der Treiber-Manager SQL_ERROR und SQLSTATE HY010 (Funktionssequenzfehler) zurück. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
## <a name="sqlendtran"></a>SQLEndTran  
 Der Treiber-Manager ordnet dies **SQLTransact**zu. Der folgende Aufruf von **SQLEndTran:**  
  
```  
SQLEndTran(HandleType, Handle, CompletionType);  
```  
  
 führt dazu, dass der Treiber-Manager die folgende Zuordnung (konzeptionell, keine Fehlerüberprüfung) durchführt:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV:return(SQLTransact(Handle, SQL_NULL_HDBC, CompletionType));  
   case SQL_HANDLE_DBC:return(SQLTransact(SQL_NULL_HENV, Handle, CompletionType);  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlfetch"></a>SQLFetch  
 Der Treiber-Manager ordnet dies **SQLExtendedFetch** mit dem *FetchOrientation-Argument* von SQL_FETCH_NEXT zu. Der folgende Aufruf von **SQLFetch:**  
  
```  
SQLFetch (StatementHandle);  
```  
  
 führt dazu, dass der Treiber-Manager SQLExtendedFetch wie folgt **aufruft:**  
  
```  
rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, &RowCount, RowStatusArray);  
```  
  
 In diesem Aufruf wird das *argument pcRow* auf den Wert festgelegt, auf den die Anwendung das SQL_ATTR_ROWS_FETCHED_PTR Anweisungsattribut durch einen Aufruf von **SQLSetStmtAttr**setzt.  
  
> [!NOTE]  
>  Wenn die Anwendung **SQLSetStmtAttr** aufruft, um SQL_ATTR_ROW_STATUS_PTR so festzulegen, dass sie auf ein Statusarray zeigt, speichert der Treiber-Manager den Zeiger zwischen. *RowStatusArray* kann gleich einem Nullzeiger sein.  
  
 Wenn der Treiber **SQLExtendedFetch** nicht unterstützt und die Cursorbibliothek geladen wird, verwendet der Treiber-Manager **SQLExtendedFetch** der Cursorbibliothek, um **SQLFetch** **SQLExtendedFetch**zuzuordnen. Wenn der Treiber **SQLExtendedFetch** nicht unterstützt und die Cursorbibliothek nicht geladen ist, übergibt der Treiber-Manager den Aufruf von **SQLFetch** an den Treiber. Wenn die Anwendung **SQLSetStmtAttr** aufruft, um SQL_ATTR_ROW_STATUS_PTR festzulegen, stellt der Treiber-Manager sicher, dass das Array aufgefüllt wird. Wenn die Anwendung **SQLSetStmtAttr** aufruft, um SQL_ATTR_ROWS_FETCHED_PTR festzulegen, legt der Treiber-Manager dieses Feld auf 1 fest.  
  
## <a name="sqlfetchscroll"></a>SQLFetchScroll  
 Der Treiber-Manager ordnet dies **SQLExtendedFetch**zu. Der folgende Aufruf von **SQLFetchScroll:**  
  
```  
SQLFetchScroll(StatementHandle, FetchOrientation, FetchOffset);  
```  
  
 führt zu der folgenden Abfolge von Schritten:  
  
1.  Wenn die Anwendung **SQLSetStmtAttr** aufruft, um SQL_ATTR_ROW_STATUS_PTR festzulegen (wodurch das SQL_DESC_ARRAY_STATUS_PTR Feld in der IRD festgelegt wird), um auf ein Statusarray zu verweisen, speichert der Treiber-Manager diesen Zeiger zwischen. Lassen Sie diesen Zeiger *RowStatusArray*sein; Andernfalls lassen Sie *RowStatusArray* gleich einem Nullzeiger sein. Wenn das *RowStatusArray-Argument* auf einen Nullzeiger festgelegt ist, generiert der Treiber-Manager ein Zeilenstatus-Array.  
  
2.  Wenn *FetchOrientation* nicht zu SQL_FETCH_NEXT, SQL_FETCH_PRIOR, SQL_FETCH_ABSOLUTE, SQL_FETCH_RELATIVE, SQL_FETCH_FIRST, SQL_FETCH_LAST oder SQL_FETCH_BOOKMARK gehört, gibt der Treiber-Manager mit SQL_ERROR und SQLSTATE HY106 (Fetch-Typ a-range) zurück. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
3.  Schreibweise:  
  
-   Wenn *FetchOrientation* gleich SQL_FETCH_BOOKMARK ist, dann:  
  
    -   Wenn **SQLSetStmtAttr** früher aufgerufen wurde, um den Wert von SQL_ATTR_FETCH_BOOKMARK_PTR festzulegen, lassen Sie *Bmk* der Wert sein, der durch Dereferencieren des Zeigers SQL_DESC_FETCH_BOOKMARK_PTR erhalten wird.  
  
    -   Andernfalls geben Sie SQL_ERROR mit SQLSTATE HY111 (Ungültiger Lesezeichenwert) zurück. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
     Der Treiber-Manager ruft jetzt **SQLExtendedFetch**wie folgt auf:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, Bmk, pcRow, RowStatusArray);  
    ```  
  
-   Andernfalls ruft der Treiber-Manager **SQLExtendedFetch**wie folgt auf:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, pcRow, RowStatusArray);  
    ```  
  
     In diesen Aufrufen wird das *argument pcRow* auf den Wert festgelegt, auf den die Anwendung das Attribut SQL_ATTR_ROWS_FETCHED_PTR-Anweisung durch einen Aufruf von **SQLSetStmtAttr**setzt.  
  
-   SQL_ATTR_ROW_ARRAY_SIZE ist SQL_ROWSET_SIZE zugeordnet.  
  
-   Wenn *rc* gleich SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO ist und *FetchOrientation* SQL_FETCH_BOOKMARK und *FetchOffset* nicht gleich 0 ist, gibt der Treiber-Manager eine Warnung, SQLSTATE 01S10 (Versuch, durch einen Lesezeichenversatz abzurufen, Offsetwert ignoriert) und gibt SQL_SUCCESS_WITH_INFO zurück.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 Der Treiber-Manager ordnet dies **SQLFreeEnv**, **SQLFreeConnect**oder **SQLFreeStmt** zu. Der folgende Aufruf von **SQLFreeHandle:**  
  
```  
SQLFreeHandle(HandleType, Handle);  
```  
  
 führt dazu, dass der Treiber-Manager die folgende Zuordnung (konzeptionell, keine Fehlerüberprüfung) durchführt:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLFreeEnv(Handle));  
   case SQL_HANDLE_DBC: return (SQLFreeConnect(Handle));  
   case SQL_HANDLE_STMT: return (SQLFreeStmt(Handle, SQL_DROP));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
 Der Treiber-Manager ordnet dies **SQLGetConnectOption**zu. Der folgende Aufruf von **SQLGetConnectAttr:**  
  
```  
SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 führt zu der folgenden Abfolge von Schritten:  
  
1.  Wenn *Attribute* kein treiberdefiniertes Verbindungs- oder Anweisungsattribut und kein in ODBC *2.x*definiertes Attribut ist, gibt der Treiber-Manager SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurück. Es gelten keine weiteren Regeln in diesem Abschnitt.  
  
2.  Wenn *Attribut* SQL_ATTR_AUTO_IPD oder SQL_ATTR_METADATA_ID entspricht, gibt der Treiber-Manager SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurück.  
  
3.  Der Treiber-Manager führt die erforderlichen Überprüfungen durch, um festzustellen, ob SQLSTATE 08003 (Verbindung nicht geöffnet) oder SQLSTATE HY010 (Funktionssequenzfehler) ausgelöst werden muss. Wenn dies der Fall ist, gibt der Treiber-Manager SQL_ERROR zurück und gibt die entsprechende Fehlermeldung aus. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
4.  Der Treiber-Manager ruft **SQLGetConnectOption** wie folgt auf:  
  
    ```  
    SQLGetConnectOption (ConnectionHandle, Attribute, ValuePtr);  
    ```  
  
     Beachten Sie, dass *BufferLength* und *StringLengthPtr* ignoriert werden.  
  
## <a name="sqlgetdata"></a>SQLGetData  
 Wenn eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, **SQLGetData** mit dem *ColumnNumber-Argument* gleich 0 aufruft, ordnet der ODBC *3.x-Treiber-Manager* dies einem Aufruf von **SQLGetStmtOption** zu, wobei das *Attribut Option* auf SQL_GET_BOOKMARK festgelegt ist.  
  
## <a name="sqlgetstmtattr"></a>'SQLGetStmtAttr'  
 Der Treiber-Manager ordnet dies **SQLGetStmtOption**zu. Der folgende Aufruf von **SQLGetStmtAttr:**  
  
```  
SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 führt zu der folgenden Abfolge von Schritten:  
  
1.  Wenn *Attribute* kein treiberdefiniertes Verbindungs- oder Anweisungsattribut und kein in ODBC *2.x*definiertes Attribut ist, gibt der Treiber-Manager SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurück. Es gelten keine weiteren Regeln in diesem Abschnitt.  
  
2.  Wenn *Attribut* eines der folgenden ist:  
  
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
  
     Der Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurück. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
3.  Der Treiber-Manager führt die erforderlichen Überprüfungen durch, um festzustellen, ob SQLSTATE HY010 (Funktionssequenzfehler) ausgelöst werden muss. Wenn dies der Fall ist, gibt der Treiber-Manager SQL_ERROR und SQLSTATE HY010 (Funktionssequenzfehler) zurück. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
4.  Wenn *Attribut* gleich SQL_ATTR_ROWS_FETCHED_PTR ist, gibt der Treiber-Manager einen Zeiger auf die interne Driver Manager-Variable *cRow*zurück, die er bei einem Aufruf von **SQLExtendedFetch**verwendet hat oder verwendet. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
5.  Wenn *Attribut* gleich SQL_DESC_FETCH_BOOKMARK_PTR ist, gibt der Treiber-Manager den entsprechenden Zeiger zurück, den er während eines Aufrufs von **SQLSetStmtAttr**zwischengespeichert hatte.  
  
6.  Wenn *Attribut* gleich SQL_ATTR_ROW_STATUS_PTR ist, gibt der Treiber-Manager den entsprechenden Zeiger zurück, den er während eines Aufrufs von **SQLSetStmtAttr**zwischengespeichert hatte.  
  
7.  Der Treiber-Manager ruft **SQLGetStmtOption** wie folgt auf:  
  
    ```  
    SQLGetStmtOption (hstmt, fOption, pvParam);  
    ```  
  
     wobei *hstmt*, *fOption*und *pvParam* auf die Werte *von StatementHandle*, *Attribute*und *ValuePtr*festgelegt werden. *BufferLength* und *StringLengthPtr* werden ignoriert.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 Der Treiber-Manager ordnet dies **SQLSetConnectOption**zu. Der folgende Aufruf von **SQLSetConnectAttr:**  
  
```  
SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, StringLength);  
```  
  
 führt zu der folgenden Abfolge von Schritten:  
  
1.  Wenn *Attribute* kein treiberdefiniertes Verbindungs- oder Anweisungsattribut und kein in ODBC *2.x*definiertes Attribut ist, gibt der Treiber-Manager SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurück. Es gelten keine weiteren Regeln in diesem Abschnitt.  
  
2.  Wenn *Attribut* gleich SQL_ATTR_AUTO_IPD ist, gibt der Treiber-Manager SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurück.  
  
3.  Der Treiber-Manager führt die erforderlichen Überprüfungen durch, um festzustellen, ob SQLSTATE 08003 (Verbindung nicht geöffnet) oder SQLSTATE HY010 (Funktionssequenzfehler) ausgelöst werden müssen. Wenn einer dieser Fehler ausgelöst werden muss, gibt der Treiber-Manager SQL_ERROR zurück und gibt die entsprechende Fehlermeldung. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
4.  Der Treiber-Manager ruft **SQLSetConnectOption** wie folgt auf:  
  
    ```  
    SQLSetConnectOption (hdbc, fOption, vParam);  
    ```  
  
     wobei *hdbc*, *fOption*und *vParam* auf die Werte *ConnectionHandle*, *Attribute*und *ValuePtr*festgelegt werden. *StringLengthPtr* wird ignoriert.  
  
> [!NOTE]  
>  Die Möglichkeit, Anweisungsattribute auf Verbindungsebene festzulegen, ist veraltet. Anweisungsattribute sollten niemals auf Verbindungsebene von einer ODBC *3.x-Anwendung* festgelegt werden.  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Der Treiber-Manager ordnet dies **SQLSetStmtOption**zu. Der folgende Aufruf von **SQLSetStmtAttr:**  
  
```  
SQLSetStmtAttr(StatementHandle, Attribute, ValuePtr, StringLength);  
```  
  
 führt zu der folgenden Abfolge von Schritten:  
  
1.  Wenn *Attribute* kein treiberdefiniertes Verbindungs- oder Anweisungsattribut und kein in ODBC *2.x*definiertes Attribut ist, gibt der Treiber-Manager SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurück. Es gelten keine weiteren Regeln in diesem Abschnitt.  
  
2.  Wenn *Attribut* eines der folgenden ist:  
  
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
  
     Der Treiber-Manager gibt SQL_ERROR mit SQLSTATE HY092 (Ungültiger Attribut-/Optionsbezeichner) zurück. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
3.  Der Treiber-Manager führt die erforderlichen Prüfungen durch, um festzustellen, ob SQLSTATE HY010 (Funktionssequenzfehler) ausgelöst werden muss. Wenn dies der Fall ist, gibt der Treiber-Manager SQL_ERROR und SQLSTATE HY010 (Funktionssequenzfehler) zurück. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
4.  Wenn *Attribut* gleich SQL_ATTR_PARAMSET_SIZE oder SQL_ATTR_PARAMS_PROCESSED_PTR ist, lesen Sie den Abschnitt "Mappings for Handling Parameter Arrays" weiter unten in diesem Thema. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
5.  Wenn *Attribut* gleich SQL_ATTR_ROWS_FETCHED_PTR ist, speichert der Treiber-Manager den Zeigerwert für die spätere Verwendung mit **SQLFetchScroll**zwischen.  
  
6.  Wenn *Attribut* gleich SQL_ATTR_ROW_STATUS_PTR ist, speichert der Treiber-Manager den Zeigerwert für die spätere Verwendung mit **SQLFetchScroll** oder **SQLSetPos**zwischen. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
7.  Wenn *Attribut* gleich SQL_ATTR_FETCH_BOOKMARK_PTR ist, speichert der Treiber-Manager *ValuePtr* zwischen und verwendet den zwischengespeicherten Wert später in einem Aufruf von **SQLFetchScroll**. Es gelten keine weiteren Regeln dieses Abschnitts.  
  
8.  Der Treiber-Manager ruft **SQLSetStmtOption** wie folgt auf:  
  
    ```  
    SQLSetStmtOption (hstmt, fOption, vParam);  
    ```  
  
     wobei *hstmt*, *fOption*und *vParam* auf die Werte *von StatementHandle*, *Attribute*und *ValuePtr*festgelegt werden. Das *StringLength-Argument* wird ignoriert.  
  
     Wenn ein ODBC *2.x-Treiber* Zeichenzeichenfolgen-, treiberspezifische Anweisungsoptionen unterstützt, sollte eine ODBC *3.x-Anwendung* **SQLSetStmtOption** aufrufen, um diese Optionen festzulegen.  
  
## <a name="mappings-for-handling-parameter-arrays"></a>Zuordnungen für die Handhabung von Parameter-Arrays  
 Wenn die Anwendung aufruft:  
  
```  
SQLSetStmtAttr (StatementHandle, SQL_ATTR_PARAMSET_SIZE, Size, StringLength);  
```  
  
 der Treiber-Manager ruft auf:  
  
```  
SQLParamOptions (StatementHandle, Size, &RowCount);  
```  
  
 Der Treiber-Manager gibt später einen Zeiger auf diese Variable zurück, wenn die Anwendung **SQLGetStmtAttr** aufruft, um SQL_ATTR_PARAMS_PROCESSED_PTR abzurufen. Der Treiber-Manager kann diese interne Variable erst ändern, wenn das Anweisungshandle in den vorbereiteten oder zugewiesenen Zustand zurückgesendet wurde.  
  
 Eine ODBC *3.x-Anwendung* kann **SQLGetStmtAttr** aufrufen, um den Wert von SQL_ATTR_PARAMS_PROCESSED_PTR zu erhalten, obwohl sie das feld SQL_DESC_ARRAY_SIZE nicht explizit in der APD festgelegt hat. Diese Situation kann z. B. auftreten, wenn die Anwendung über eine generische Routine verfügt, die nach der aktuellen "Zeile" der Parameter sucht, die verarbeitet werden, wenn **SQLExecute** SQL_NEED_DATA zurückgibt. Diese Routine wird aufgerufen, unabhängig davon, ob die SQL_DESC_ARRAY_SIZE 1 oder größer als 1 ist. Um dies zu berücksichtigen, muss der Treiber-Manager diese interne Variable definieren, ob die Anwendung **SQLSetStmtAttr** aufgerufen hat, um das SQL_DESC_ARRAY_SIZE Feld in APD festzulegen. Wenn SQL_DESC_ARRAY_SIZE nicht festgelegt wurde, muss der Treiber-Manager sicherstellen, dass diese Variable den Wert 1 enthält, bevor sie von **SQLExecDirect** oder **SQLExecute**zurückgegeben wird.  
  
## <a name="error-handling"></a>Fehlerbehandlung  
 In ODBC *3.x*füllt das Aufrufen von **SQLFetch** oder **SQLFetchScroll** die SQL_DESC_ARRAY_STATUS_PTR in der IRD aus, und das SQL_DIAG_ROW_NUMBER Feld eines bestimmten Diagnosedatensatzes enthält die Nummer der Zeile im Rowset, auf die sich dieser Datensatz bezieht. Auf diese Weise kann die Anwendung eine Fehlermeldung mit einer bestimmten Zeilenposition korrelieren.  
  
 Ein ODBC *2.x-Treiber* kann diese Funktionalität nicht bereitstellen. Es wird jedoch fehlerabgrenzung mit SQLSTATE 01S01 (Fehler in Zeile) zur Verfügung stellen. Eine ODBC *3.x-Anwendung,* die **SQLFetch** oder **SQLFetchScroll** verwendet, während sie mit einem ODBC *2.x-Treiber* umgeht, muss sich dieser Tatsache bewusst sein. Beachten Sie auch, dass eine solche Anwendung **SQLGetDiagField** nicht aufrufen kann, um das feld SQL_DIAG_ROW_NUMBER trotzdem zu erhalten. Eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, kann **SQLGetDiagField** nur mit einem *DiagIdentifier-Argument* von SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_RETURNCODE oder SQL_DIAG_SQLSTATE aufrufen. Der ODBC *3.x* Treiber-Manager behält die Diagnosedatenstruktur bei der Arbeit mit einem ODBC *2.x-Treiber* bei, aber der ODBC *2.x-Treiber* gibt nur diese vier Felder zurück.  
  
 Wenn eine ODBC *2.x-Anwendung* mit einem ODBC *2.x-Treiber* arbeitet und ein Vorgang dazu führen kann, dass mehrere Fehler vom Treiber-Manager zurückgegeben werden, können vom ODBC *3.x* Driver Manager andere Fehler zurückgegeben werden als vom ODBC *2.x* Driver Manager.  
  
## <a name="mappings-for-bookmark-operations"></a>Zuordnungen für Bookmark-Vorgänge  
 Der ODBC *3.x-Treiber-Manager* führt die folgenden Zuordnungen aus, wenn eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, Lesezeichenvorgänge ausführt.  
  
### <a name="sqlbindcol"></a>SQLBindCol  
 Wenn eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, **SQLBindCol** aufruft, um die Bindung an Spalte 0 mit *fCType* gleich SQL_C_VARBOOKMARK zu binden, überprüft der ODBC *3.x-Treiber-Manager,* ob das Argument *BufferLength* kleiner als 4 oder größer als 4 ist, und gibt in diesem Fall SQLSTATE HY090 (Ungültige Zeichenfolge oder Pufferlänge) zurück. Wenn das *BufferLength-Argument* gleich 4 ist, ruft der Treiber-Manager **SQLBindCol** im Treiber auf, nachdem *fCType* durch SQL_C_BOOKMARK ersetzt wurde.  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 Wenn eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, **SQLColAttribute** aufruft, wobei das *ColumnNumber-Argument* auf 0 festgelegt ist, gibt der Treiber-Manager die in der folgenden Tabelle aufgeführten *FieldIdentifier-Werte* zurück.  
  
|*FieldIdentifier*|Wert|  
|-----------------------|-----------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|  
|SQL_DESC_CATALOG_NAME|"" (leere Zeichenfolge)|  
|SQL_DESC_CONCISE_TYPE|SQL_BINARY|  
|SQL_DESC_COUNT|Derselbe von **SQLNumResultCols** zurückgegebene Wert|  
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
 Wenn eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, **SQLDescribeCol** aufruft, wobei das *ColumnNumber-Argument* auf 0 festgelegt ist, gibt der Treiber-Manager die in der folgenden Tabelle aufgeführten Werte zurück.  
  
|Buffer|Wert|  
|------------|-----------|  
|ColumnName|"" (leere Zeichenfolge)|  
|*NameLengthPtr|0|  
|*DataTypePtr|SQL_BINARY|  
|*ColumnSizePtr|4|  
|*DecimalDigitsPtr|0|  
|*NullablePtr|SQL_NO_NULLS|  
  
### <a name="sqlgetdata"></a>SQLGetData  
 Wenn eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, den folgenden Aufruf an **SQLGetData** ausführt, um ein Lesezeichen abzurufen:  
  
```  
SQLGetData(StatementHandle, 0, SQL_C_VARBOOKMARK, TargetValuePtr, BufferLength, StrLen_or_IndPtr)  
```  
  
 Der Aufruf wird **SQLGetStmtOption** mit einer *fOption* von SQL_GET_BOOKMARK zugeordnet, wie folgt:  
  
```  
SQLGetStmtOption(hstmt, SQL_GET_BOOKMARK, TargetValuePtr)  
```  
  
 wobei *hstmt* und *pvParam* auf die Werte in *StatementHandle* bzw. *TargetValuePtr*festgelegt sind. Die Textmarke wird im Puffer zurückgegeben, auf den das Argument *pvParam* (*TargetValuePtr*) zeigt. Der Wert im Puffer, auf den das *argument StrLen_or_IndPtr* im Aufruf von **SQLGetData** zeigt, ist auf 4 festgelegt.  
  
 Diese Zuordnung ist erforderlich, um den Fall zu berücksichtigen, in dem **SQLFetch** vor dem Aufruf von **SQLGetData** aufgerufen wurde und der ODBC *2.x-Treiber* **SQLExtendedFetch**nicht unterstützt hat. In diesem Fall wird **SQLFetch** an den ODBC *2.x-Treiber* übergeben, in diesem Fall wird der Abruf von Lesezeichen nicht unterstützt.  
  
 **SQLGetData** kann in einem ODBC *2.x-Treiber* nicht mehrmals aufgerufen werden, um eine *BufferLength* Textmarke in Teilen abzurufen. **SQLGetData** *ColumnNumber* **SQLGetData** kann jedoch mehrmals aufgerufen werden, um dieselbe Textmarke abzurufen.  
  
### <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Wenn eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, **SQLSetStmtAttr** aufruft, um das attribut SQL_ATTR_USE_BOOKMARKS auf SQL_UB_VARIABLE festzulegen, legt der Treiber-Manager das Attribut auf SQL_UB_ON im zugrunde liegenden ODBC *2.x-Treiber* fest.
