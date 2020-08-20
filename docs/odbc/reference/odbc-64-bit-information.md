---
description: 64-Bit-ODBC-Informationen
title: ODBC 64-Bit-Informationen | Microsoft-Dokumentation
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
ms.openlocfilehash: 791bb54481ae5844061852f5321bdf07fc027b1a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461282"
---
# <a name="odbc-64-bit-information"></a>64-Bit-ODBC-Informationen
Ab Windows Server 2003 haben die Microsoft-Betriebssysteme die 64-Bit-ODBC-Bibliotheken unterstützt. Die ODBC-Header und-Bibliotheken, die zum ersten Mal mit dem MDAC 2,7 SDK ausgeliefert wurden, enthalten Änderungen, damit Programmierer problemlos Code für die neuen 64-Bit-Plattformen schreiben Indem Sie sicherstellen, dass der Code die unten aufgeführten ODBC-Typen verwendet, können Sie den gleichen Quellcode sowohl für 64-Bit-als auch 32-Bit-Plattformen kompilieren, die auf den **_WIN64** -oder **Win32** -Makros basieren.  
  
 Beim Programmieren für einen 64-Bit-Prozessor sind einige Punkte zu beachten:  
  
-   Obwohl sich die Größe eines Zeigers von 4 Bytes in 8 Bytes geändert hat, sind ganze Zahlen und Long weiterhin 4-Byte-Werte. Die Typen **Int64** und **UINT64** wurden für ganze Zahlen von 8 Byte definiert. Die neuen ODBC-Typen **sqllen** und **SQLULEN** werden in der ODBC-Header Datei als **Int64** und **UINT64** definiert, wenn **_WIN64** definiert wurde.  
  
-   Mehrere Funktionen in ODBC werden so deklariert, dass ein Zeiger Parameter übernommen wird. In 32-Bit-ODBC wurden Parameter, die als Zeiger definiert sind, häufig verwendet, um entweder einen ganzzahligen Wert oder einen Zeiger auf einen Puffer zu übergeben, abhängig vom Kontext des Aufrufes. Dies war natürlich aufgrund der Tatsache möglich, dass Zeiger und ganze Zahlen dieselbe Größe aufwiesen. In 64-Bit-Fenstern ist dies nicht der Fall.  
  
-   Einige ODBC-Funktionen, die zuvor mit **SQLINTEGER** -und **SQLUINTEGER** -Parametern definiert wurden, wurden geändert, wenn Sie sich für die Verwendung der neuen **sqllen** -und **SQLULEN** -Typedefs eignen. Diese Änderungen werden im nächsten Abschnitt, Änderungen der Funktionsdeklaration, aufgeführt.  
  
-   Einige der Deskriptorfelder, die über die verschiedenen **SQLSET** -und **SQLGET** -Funktionen festgelegt werden können, wurden so geändert, dass Sie 64-Bit-Werte unterstützen, während andere noch 32-Bit-Werte sind. Stellen Sie sicher, dass Sie die entsprechende Größen Variable verwenden, wenn Sie diese Felder festlegen und abrufen. Einzelheiten darüber, welche Deskriptorfelder geändert wurden, werden unter Funktionsdeklaration Änderungen aufgelistet.  
  
## <a name="function-declaration-changes"></a>Funktionsdeklaration ändern  
 Die folgenden Funktions Signaturen haben sich für die 64-Bit-Programmierung geändert. Bei den fett formatierten Text handelt es sich um die spezifischen Parameter, die unterschiedlich sind.  
  
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
 Die folgenden vier SQL-Typen werden immer noch auf 32-Bit unterstützt. Sie sind nicht für 64-Bit-Compiler definiert. Diese Typen werden nicht mehr für Parameter in MDAC 2,7 verwendet. die Verwendung dieser Typen führt zu Compilerfehlern auf 64-Bit-Plattformen.  
  
```cpp
#ifdef WIN32   
typedef SQLULEN SQLROWCOUNT;   
typedef SQLULEN SQLROWSETSIZE;   
typedef SQLULEN SQLTRANSID;   
typedef SQLLEN SQLROWOFFSET;   
#endif  
```  
  
 Die Definition von sqlsetposirow wurde für 32-Bit-und 64-Bit-Compiler geändert:  
  
```cpp
#ifdef _WIN64   
typedef UINT64 SQLSETPOSIROW;   
#else   
#define SQLSETPOSIROW SQLUSMALLINT   
#endif  
```  
  
 Die Definitionen von sqllen und SQLULEN haben sich für 64-Bit-Compiler geändert:  
  
```cpp
#ifdef _WIN64   
typedef INT64 SQLLEN;   
typedef UINT64 SQLULEN;   
#else   
#define SQLLEN SQLINTEGER   
#define SQLULEN SQLUINTEGER   
#endif  
```  
  
 Obwohl SQL_C_BOOKMARK in ODBC 3,0 als veraltet markiert ist, wurde dieser Wert für 64-Bit-Compiler auf 2,0-Clients geändert:  
  
```cpp
#ifdef _WIN64   
#define SQL_C_BOOKMARK SQL_C_UBIGINT   
#else   
#define SQL_C_BOOKMARK SQL_C_ULONG   
#endif  
```  
  
 Der Lese Zeichentyp wird in den neueren Headern anders definiert:  
  
```cpp
typedef SQLULEN BOOKMARK;  
```  
  
## <a name="values-returned-from-odbc-api-calls-through-pointers"></a>Von ODBC-API-Aufrufen durch Zeiger zurückgegebene Werte  
 Die folgenden ODBC-Funktionsaufrufe akzeptieren als Eingabeparameter einen Zeiger auf einen Puffer, in dem Daten vom Treiber zurückgegeben werden. Der Kontext und die Bedeutung der zurückgegebenen Daten werden durch andere Eingabeparameter für die Funktionen bestimmt. In einigen Fällen können diese Methoden jetzt 64-Bit-Werte (8-Byte-Ganzzahl) anstelle der typischen ganzzahligen Werte von 32 Bit (4 Bytes) zurückgeben. Diese Fälle lauten wie folgt:  
  
 **SQLColAttribute**  
  
 Wenn der *fieldidentifier* -Parameter einen der folgenden Werte aufweist, wird in **numerigattribute*ein 64-Bit-Wert zurückgegeben:  
  
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
  
 Wenn der Parameter " *atdesctype* " einen der folgenden Werte aufweist, wird in **pfdesc*ein 64-Bit-Wert zurückgegeben:  
  
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
  
 Wenn der *Attribut* Parameter einen der folgenden Werte aufweist, wird ein 64-Bit-Wert als *Wert*zurückgegeben:  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_ENLIST_IN_DTC  
  
 SQL_ATTR_ODBC_CURSORS  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLGetConnectOption**  
  
 Wenn der *Attribut* Parameter einen der folgenden Werte aufweist, wird ein 64-Bit-Wert als *Wert*zurückgegeben:  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLGetDescField**  
  
 Wenn der *fieldidentifier* -Parameter einen der folgenden Werte aufweist, wird in **ValuePtr*ein 64-Bit-Wert zurückgegeben:  
  
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
  
 Wenn der *DiagIdentifier* -Parameter einen der folgenden Werte aufweist, wird in **diaginfoptr*ein 64-Bit-Wert zurückgegeben:  
  
 SQL_DIAG_CURSOR_ROW_COUNT  
  
 SQL_DIAG_ROW_COUNT  
  
 SQL_DIAG_ROW_NUMBER  
  
 **SQLGetInfo**  
  
 Wenn der *InfoType* -Parameter einen der folgenden Werte aufweist, wird in **infovalueptr*ein 64-Bit-Wert zurückgegeben:  
  
 SQL_DRIVER_HDBC  
  
 SQL_DRIVER_HENV  
  
 SQL_DRIVER_HLIB  
  
 Wenn *InfoType* einen der beiden folgenden Werte aufweist **infovalueptr* ist 64-Bits sowohl für die Eingabe als auch für die Ausgabe:  
  
 SQL_DRIVER_HDESC  
  
 SQL_DRIVER_HSTMT  
  
 **'SQLGetStmtAttr'**  
  
 Wenn der *Attribut* Parameter einen der folgenden Werte aufweist, wird in **ValuePtr*ein 64-Bit-Wert zurückgegeben:  
  
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
  
 Wenn der *Option* -Parameter einen der folgenden Werte aufweist, wird ein 64-Bit-Wert im *-*Wert*zurückgegeben:  
  
 SQL_KEYSET_SIZE  
  
 SQL_MAX_LENGTH  
  
 SQL_MAX_ROWS  
  
 SQL_ROWSET_SIZE  
  
 **SQLSetConnectAttr**  
  
 Wenn der *Attribut* Parameter einen der folgenden Werte aufweist, wird ein 64-Bit-Wert in den *Wert*übergeben:  
  
 SQL_ATTR_ASYNC_ENABLE  
  
 SQL_ATTR_ENLIST_IN_DTC  
  
 SQL_ATTR_ODBC_CURSORS  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLSetConnectOption**  
  
 Wenn der *Attribut* Parameter einen der folgenden Werte aufweist, wird ein 64-Bit-Wert in den *Wert*übergeben:  
  
 SQL_ATTR_QUIET_MODE  
  
 **SQLSetDescField**  
  
 Wenn der *fieldidentifier* -Parameter einen der folgenden Werte aufweist, wird ein 64-Bit-Wert in *ValuePtr*übergeben:  
  
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
  
 Wenn der *Attribut* Parameter einen der folgenden Werte aufweist, wird ein 64-Bit-Wert in *ValuePtr*übergeben:  
  
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
  
 Wenn der *Option* -Parameter einen der folgenden Werte aufweist, wird ein 64-Bit-Wert in den *Wert*übergeben:  
  
 SQL_KEYSET_SIZE  
  
 SQL_MAX_LENGTH  
  
 SQL_MAX_ROWS  
  
 SQL_ROWSET_SIZE  
  
## <a name="see-also"></a>Siehe auch  
 [Einführung in ODBC](../../odbc/reference/introduction-to-odbc.md)
