---
title: ODBC 64-Bit-Informationen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ed9851ce-44ee-4c8e-b626-1d0b52da30fe
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b9cb8e3fc42d0ad71ac83f1432c165f243f39012
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298300"
---
# <a name="odbc-64-bit-information"></a>64-Bit-ODBC-Informationen
Seit Windows Server 2003 unterstützen Microsoft-Betriebssysteme die 64-Bit-ODBC-Bibliotheken. Die ODBC-Header und -Bibliotheken, die zuerst mit MDAC 2.7 SDK ausgeliefert wurden, enthalten Änderungen, die es Programmierern ermöglichen, problemlos Code für die neuen 64-Bit-Plattformen zu schreiben. Indem Sie sicherstellen, dass Ihr Code die unten aufgeführten ODBC-definierten Typen verwendet, können Sie denselben Quellcode sowohl für 64-Bit- als auch für 32-Bit-Plattformen basierend auf den **_WIN64-** oder **WIN32-Makros** kompilieren.  
  
 Bei der Programmierung eines 64-Bit-Prozessors sind mehrere Punkte zu beachten:  
  
-   Obwohl sich die Größe eines Zeigers von 4 Bytes auf 8 Bytes geändert hat, sind ganze Zahlen und Longs immer noch 4 Byte-Werte. Die Typen **INT64** und **UINT64** wurden für 8 Byteganzeger definiert. Die neuen ODBC-Typen **SQLLEN** und **SQLULEN** werden in der ODBC-Headerdatei als **INT64** und **UINT64** definiert, wenn **_WIN64** definiert wurde.  
  
-   Mehrere Funktionen in ODBC werden als Zeigerparameter deklariert. In 32-Bit-ODBC wurden Parameter, die als Zeiger definiert wurden, häufig verwendet, um je nach Kontext des Aufrufs entweder einen Ganzzahlwert oder einen Zeiger an einen Puffer zu übergeben. Dies war natürlich möglich, weil Zeiger und ganze Zahlen die gleiche Größe hatten. In 64-Bit-Windows ist dies nicht der Fall.  
  
-   Einige ODBC-Funktionen, die zuvor mit **den Parametern SQLINTEGER** und **SQLUINTEGER** definiert wurden, wurden entsprechend geändert, um die neuen **SQLLEN-** und **SQLULEN-Typdefs** zu verwenden. Diese Änderungen werden im nächsten Abschnitt Funktionsdeklaration geändert aufgeführt.  
  
-   Einige der Deskriptorfelder, die über die verschiedenen **SQLSet-** und **SQLGet-Funktionen** festgelegt werden können, wurden geändert, um 64-Bit-Werte aufzunehmen, während andere noch 32-Bit-Werte sind. Stellen Sie sicher, dass Sie beim Festlegen und Abrufen dieser Felder die entsprechende Variable in der Größe verwenden. Besonderheiten, deren Deskriptorfelder geändert wurden, werden unter Funktionsdeklarationsänderungen aufgeführt.  
  
## <a name="function-declaration-changes"></a>Funktionsdeklarationsänderungen  
 Die folgenden Funktionssignaturen wurden für die 64-Bit-Programmierung geändert. Die Elemente in Fettdruck sind die spezifischen Parameter, die sich unterscheiden.  
  
```cpp
SQLBindCol (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,  
   SQLSMALLINT TargetType, SQLPOINTER TargetValuePtr, SQLLEN BufferLength,   SQLLEN * StrLen_or_Ind);  
  
SQLBindParam (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,  
   SQLSMALLINT ValueType, SQLSMALLINT ParameterType,   
   SQLULEN ColumnSize, SQLSMALLINT DecimalDigits,   
   SQLPOINTER ParameterValuePtr, SQLLEN *StrLen_or_Ind);  
  
SQLBindParameter (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,   
   SQLSMALLINT InputOutputType, SQLSMALLINT ValueType,   
   SQLSMALLINT ParameterType, SQLULEN ColumnSize, SQLSMALLINT DecimalDigits,   
   SQLPOINTER ParameterValuePtr, SQLLEN BufferLength, SQLLEN *StrLen_or_IndPtr);  
  
SQLColAttribute (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,  
    SQLUSMALLINT FieldIdentifier, SQLPOINTER CharacterAttributePtr,   
   SQLSMALLINT BufferLength, SQLSMALLINT * StringLengthPtr,   
   SQLLEN* NumericAttributePtr)  
  
SQLColAttributes (SQLHSTMT hstmt, SQLUSMALLINT icol,   
   SQLUSMALLINT fDescType, SQLPOINTER rgbDesc,   
   SQLSMALLINT cbDescMax, SQLSMALLINT *pcbDesc, SQLLEN * pfDesc);  
  
SQLDescribeCol (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,   
   SQLCHAR *ColumnName, SQLSMALLINT BufferLength,   
   SQLSMALLINT *NameLengthPtr, SQLSMALLINT *DataTypePtr, SQLULEN *ColumnSizePtr,   
   SQLSMALLINT *DecimalDigitsPtr, SQLSMALLINT *NullablePtr);  
  
SQLDescribeParam (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,   
   SQLSMALLINT *DataTypePtr, SQLULEN *ParameterSizePtr, SQLSMALLINT *DecimalDigitsPtr,   
   SQLSMALLINT *NullablePtr);  
  
SQLExtendedFetch(SQLHSTMT StatementHandle, SQLUSMALLINT FetchOrientation, SQLLEN FetchOffset,   
   SQLULEN * RowCountPtr, SQLUSMALLINT * RowStatusArray);  
  
SQLFetchScroll (SQLHSTMT StatementHandle, SQLSMALLINT FetchOrientation,   
   SQLLEN FetchOffset);  
  
SQLGetData (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,   
   SQLSMALLINT TargetType, SQLPOINTER TargetValuePtr, SQLLEN BufferLength,    SQLLEN *StrLen_or_Ind);  
  
SQLGetDescRec (SQLHDESC DescriptorHandle, SQLSMALLINT RecNumber,   
   SQLCHAR *Name, SQLSMALLINT BufferLength,   
   SQLSMALLINT *StringLengthPtr, SQLSMALLINT *TypePtr,   
   SQLSMALLINT *SubTypePtr, SQLLEN *LengthPtr,   
   SQLSMALLINT *PrecisionPtr, SQLSMALLINT *ScalePtr,   
   SQLSMALLINT *NullablePtr);  
  
SQLParamOptions(SQLHSTMT hstmt, SQLULEN crow, SQLULEN * pirow);  
  
SQLPutData (SQLHSTMT StatementHandle, SQLPOINTER DataPtr,   
   SQLLEN StrLen_or_Ind);  
  
SQLRowCount (SQLHSTMT StatementHandle, SQLLEN* RowCountPtr);  
  
SQLSetConnectOption(SQLHDBC ConnectHandle, SQLUSMALLINT Option,   
   SQLULEN Value);  
  
SQLSetPos (SQLHSTMT StatementHandle, SQLSETPOSIROW RowNumber, SQLUSMALLINT Operation,  
   SQLUSMALLINT LockType);  
  
SQLSetParam (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,   
   SQLSMALLINT ValueType, SQLSMALLINT ParameterType,   
   SQLULEN LengthPrecision, SQLSMALLINT ParameterScale,   
   SQLPOINTER ParameterValue, SQLLEN *StrLen_or_Ind);  
  
SQLSetDescRec (SQLHDESC DescriptorHandle, SQLSMALLINT RecNumber,   
   SQLSMALLINT Type, SQLSMALLINT SubType, SQLLEN Length,   
   SQLSMALLINT Precision, SQLSMALLINT Scale, SQLPOINTER DataPtr,   
   SQLLEN *StringLengthPtr, SQLLEN *IndicatorPtr);  
  
SQLSetScrollOptions (SQLHSTMT hstmt, SQLUSMALLINT fConcurrency,   
   SQLLEN crowKeyset, SQLUSMALLINT crowRowset);  
  
SQLSetStmtOption (SQLHSTMT StatementHandle, SQLUSMALLINT Option,   
   SQLULEN Value);  
```  
  
## <a name="changes-in-sql-data-types"></a>Änderungen in SQL-Datentypen  
 Die folgenden vier SQL-Typen werden weiterhin nur für 32-Bit-Typen unterstützt. Sie sind nicht für 64-Bit-Compiler definiert. Diese Typen werden nicht mehr für Parameter in MDAC 2.7 verwendet; Die Verwendung dieser Typen führt zu Compilerfehlern auf 64-Bit-Plattformen.  
  
```cpp
#ifdef WIN32   
typedef SQLULEN SQLROWCOUNT;   
typedef SQLULEN SQLROWSETSIZE;   
typedef SQLULEN SQLTRANSID;   
typedef SQLLEN SQLROWOFFSET;   
#endif  
```  
  
 Die Definition von SQLSETPOSIROW hat sich sowohl für 32-Bit- als auch für 64-Bit-Compiler geändert:  
  
```cpp
#ifdef _WIN64   
typedef UINT64 SQLSETPOSIROW;   
#else   
#define SQLSETPOSIROW SQLUSMALLINT   
#endif  
```  
  
 Die Definitionen von SQLLEN und SQLULEN haben sich für 64-Bit-Compiler geändert:  
  
```cpp
#ifdef _WIN64   
typedef INT64 SQLLEN;   
typedef UINT64 SQLULEN;   
#else   
#define SQLLEN SQLINTEGER   
#define SQLULEN SQLUINTEGER   
#endif  
```  
  
 Obwohl SQL_C_BOOKMARK in ODBC 3.0 veraltet ist, hat sich für 64-Bit-Compiler auf 2.0-Clients dieser Wert geändert:  
  
```cpp
#ifdef _WIN64   
#define SQL_C_BOOKMARK SQL_C_UBIGINT   
#else   
#define SQL_C_BOOKMARK SQL_C_ULONG   
#endif  
```  
  
 Der BOOKMARK-Typ wird in den neueren Headern unterschiedlich definiert:  
  
```cpp
typedef SQLULEN BOOKMARK;  
```  
  
## <a name="values-returned-from-odbc-api-calls-through-pointers"></a>Werte, die von ODBC-API-Aufrufen über Zeiger zurückgegeben werden  
 Die folgenden ODBC-Funktionsaufrufe nehmen als Eingabeparameter einen Zeiger auf einen Puffer, in dem Daten vom Treiber zurückgegeben werden. Der Kontext und die Bedeutung der zurückgegebenen Daten werden durch andere Eingabeparameter für die Funktionen bestimmt. In einigen Fällen können diese Methoden jetzt 64-Bit-Werte (8-Byte-Ganzzahl) anstelle der typischen 32-Bit-Ganzzahlwerte (4 Byte) zurückgeben. Diese Fälle sind wie folgt:  
  
 **SQLColAttribute**  
  
 Wenn der *FieldIdentifier-Parameter* einen der folgenden Werte hat, wird ein 64-Bit-Wert in **NumericAttribute*zurückgegeben:  
  
 SQL_DESC_AUTO_UNIQUE_VALUE  
  
 SQL_DESC_CASE_SENSITIVE  
  
 SQL_DESC_CONCISE_TYPE  
  
 SQL_DESC_COUNT  
  
 SQL_DESC_DISPLAY_SIZE  
  
 SQL_DESC_FIXED_PREC_SCALE  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_NULLABLE  
  
 SQL_DESC_NUM_PREC_RADIX  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_PRECISION  
  
 SQL_DESC_SCALE  
  
 SQL_DESC_SEARCHABLE  
  
 SQL_DESC_TYPE  
  
 SQL_DESC_UNNAMED  
  
 SQL_DESC_UNSIGNED  
  
 SQL_DESC_UPDATABLE  
  
 **SQLColAttributes**  
  
 Wenn der *fDescType-Parameter* einen der folgenden Werte hat, wird ein 64-Bit-Wert in **pfDesc*zurückgegeben:  
  
 SQL_COLUMN_COUNT  
  
 SQL_COLUMN_DISPLAY_SIZE  
  
 SQL_COLUMN_LENGTH  
  
 SQL_DESC_AUTO_UNIQUE_VALUE  
  
 SQL_DESC_CASE_SENSITIVE  
  
 SQL_DESC_CONCISE_TYPE  
  
 SQL_DESC_FIXED_PREC_SCALE  
  
 SQL_DESC_SEARCHABLE  
  
 SQL_DESC_UNSIGNED  
  
 SQL_DESC_UPDATABLE  
  
 **SQLGetConnectAttr**  
  
 Wenn der *Attributparameter* einen der folgenden Werte hat, wird ein 64-Bit-Wert in *Value*zurückgegeben:  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_ENLIST_IN_DTC  
  
 SQL_ATTR_ODBC_CURSORS  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLGetConnectOption**  
  
 Wenn der *Attributparameter* einen der folgenden Werte hat, wird ein 64-Bit-Wert in *Value*zurückgegeben:  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLGetDescField**  
  
 Wenn der *FieldIdentifier-Parameter* einen der folgenden Werte hat, wird ein 64-Bit-Wert in **ValuePtr*zurückgegeben:  
  
 SQL_DESC_ARRAY_SIZE  
  
 SQL_DESC_ARRAY_STATUS_PTR  
  
 SQL_DESC_BIND_OFFSET_PTR  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_DISPLAY_SIZE  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_ROWS_PROCESSED_PTR  
  
 **SQLGetDiagField**  
  
 Wenn der *Parameter DiagIdentifier* einen der folgenden Werte hat, wird ein 64-Bit-Wert in **DiagInfoPtr*zurückgegeben:  
  
 SQL_DIAG_CURSOR_ROW_COUNT  
  
 SQL_DIAG_ROW_COUNT  
  
 SQL_DIAG_ROW_NUMBER  
  
 **SQLGetInfo**  
  
 Wenn der *InfoType-Parameter* einen der folgenden Werte hat, wird ein 64-Bit-Wert in **InfoValuePtr*zurückgegeben:  
  
 SQL_DRIVER_HDBC  
  
 SQL_DRIVER_HENV  
  
 SQL_DRIVER_HLIB  
  
 Wenn *InfoType* einen der folgenden 2 Werte hat **InfoValuePtr* ist 64-Bit auf Eingang und Ausgang:  
  
 SQL_DRIVER_HDESC  
  
 SQL_DRIVER_HSTMT  
  
 **'SQLGetStmtAttr'**  
  
 Wenn der *Attributparameter* einen der folgenden Werte hat, wird ein 64-Bit-Wert in **ValuePtr*zurückgegeben:  
  
 SQL_ATTR_APP_PARAM_DESC  
  
 SQL_ATTR_APP_ROW_DESC  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_CONCURRENCY  
  
 SQL_ATTR_CURSOR_SCROLLABLE  
  
 SQL_ATTR_CURSOR_SENSITIVITY  
  
 SQL_ATTR_CURSOR_TYPE  
  
 SQL_ATTR_ENABLE_AUTO_IPD  
  
 SQL_ATTR_FETCH_BOOKMARK_PTR  
  
 SQL_ATTR_ROWS_FETCHED_PTR  
  
 SQL_ATTR_IMP_PARAM_DESC  
  
 SQL_ATTR_IMP_ROW_DESC  
  
 SQL_ATTR_KEYSET_SIZE  
  
 SQL_ATTR_MAX_LENGTH  
  
 SQL_ATTR_MAX_ROWS  
  
 SQL_ATTR_METADATA_ID  
  
 SQL_ATTR_NOSCAN  
  
 SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
 SQL_ATTR_PARAM_BIND_TYPE  
  
 SQL_ATTR_PARAM_OPERATION_PTR  
  
 SQL_ATTR_PARAM_STATUS_PTR  
  
 SQL_ATTR_PARAMS_PROCESSED_PTR  
  
 SQL_ATTR_PARAMSET_SIZE  
  
 SQL_ATTR_QUERY_TIMEOUT  
  
 SQL_ATTR_RETRIEVE_DATA  
  
 SQL_ATTR_ROW_ARRAY_SIZE  
  
 SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
 SQL_ATTR_ROW_NUMBER  
  
 SQL_ATTR_ROW_OPERATION_PTR  
  
 SQL_ATTR_ROW_STATUS_PTR  
  
 SQL_ATTR_SIMULATE_CURSOR  
  
 SQL_ATTR_USE_BOOKMARKS  
  
 **SQLGetStmtOption**  
  
 Wenn der *Parameter Option* einen der folgenden Werte hat, wird ein 64-Bit-Wert in **Wert*zurückgegeben:  
  
 SQL_KEYSET_SIZE  
  
 SQL_MAX_LENGTH  
  
 SQL_MAX_ROWS  
  
 SQL_ROWSET_SIZE  
  
 **SQLSetConnectAttr**  
  
 Wenn der *Attributparameter* einen der folgenden Werte hat, wird ein 64-Bit-Wert in *Value*übergeben:  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_ENLIST_IN_DTC  
  
 SQL_ATTR_ODBC_CURSORS  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLSetConnectOption**  
  
 Wenn der *Attributparameter* einen der folgenden Werte hat, wird ein 64-Bit-Wert in *Value*übergeben:  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLSetDescField**  
  
 Wenn der *FieldIdentifier-Parameter* einen der folgenden Werte hat, wird ein 64-Bit-Wert in *ValuePtr*übergeben:  
  
 SQL_DESC_ARRAY_SIZE  
  
 SQL_DESC_ARRAY_STATUS_PTR  
  
 SQL_DESC_BIND_OFFSET_PTR  
  
 SQL_DESC_DATA_PTR  
  
 SQL_DESC_DISPLAY_SIZE  
  
 SQL_DESC_INDICATOR_PTR  
  
 SQL_DESC_LENGTH  
  
 SQL_DESC_OCTET_LENGTH  
  
 SQL_DESC_OCTET_LENGTH_PTR  
  
 SQL_DESC_ROWS_PROCESSED_PTR  
  
 **SQLSetStmtAttr**  
  
 Wenn der *Attributparameter* einen der folgenden Werte hat, wird ein 64-Bit-Wert in *ValuePtr*übergeben:  
  
 SQL_ATTR_APP_PARAM_DESC  
  
 SQL_ATTR_APP_ROW_DESC  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_CONCURRENCY  
  
 SQL_ATTR_CURSOR_SCROLLABLE  
  
 SQL_ATTR_CURSOR_SENSITIVITY  
  
 SQL_ATTR_CURSOR_TYPE  
  
 SQL_ATTR_ENABLE_AUTO_IPD  
  
 SQL_ATTR_FETCH_BOOKMARK_PTR  
  
 SQL_ATTR_IMP_PARAM_DESC  
  
 SQL_ATTR_IMP_ROW_DESC  
  
 SQL_ATTR_KEYSET_SIZE  
  
 SQL_ATTR_MAX_LENGTH  
  
 SQL_ATTR_MAX_ROWS  
  
 SQL_ATTR_METADATA_ID  
  
 SQL_ATTR_NOSCAN  
  
 SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
 SQL_ATTR_PARAM_BIND_TYPE  
  
 SQL_ATTR_PARAM_OPERATION_PTR  
  
 SQL_ATTR_PARAM_STATUS_PTR  
  
 SQL_ATTR_PARAMS_PROCESSED_PTR  
  
 SQL_ATTR_PARAMSET_SIZE  
  
 SQL_ATTR_QUERY_TIMEOUT  
  
 SQL_ATTR_RETRIEVE_DATA  
  
 SQL_ATTR_ROW_ARRAY_SIZE  
  
 SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
 SQL_ATTR_ROW_NUMBER  
  
 SQL_ATTR_ROW_OPERATION_PTR  
  
 SQL_ATTR_ROW_STATUS_PTR  
  
 SQL_ATTR_ROWS_FETCHED_PTR  
  
 SQL_ATTR_SIMULATE_CURSOR  
  
 SQL_ATTR_USE_BOOKMARKS  
  
 **SQLSetStmtOption**  
  
 Wenn der *Parameter Option* einen der folgenden Werte hat, wird ein 64-Bit-Wert in *Value*übergeben:  
  
 SQL_KEYSET_SIZE  
  
 SQL_MAX_LENGTH  
  
 SQL_MAX_ROWS  
  
 SQL_ROWSET_SIZE  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einführung in ODBC](../../odbc/reference/introduction-to-odbc.md)
