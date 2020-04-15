---
title: SQLGetFunctions-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetFunctions
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLGetFunctions
helpviewer_keywords:
- SQLGetFunctions function [ODBC]
ms.assetid: 0451d2f9-0f4f-46ba-b252-670956a52183
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 15537b28ff2bae8a4fcd3e7be82426eb53aa83a8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285330"
---
# <a name="sqlgetfunctions-function"></a>SQLGetFunctions-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetFunctions** gibt Informationen darüber zurück, ob ein Treiber eine bestimmte ODBC-Funktion unterstützt. Diese Funktion wird im Treiber-Manager implementiert. es kann auch in Treibern implementiert werden. Wenn ein Treiber **SQLGetFunctions**implementiert, ruft der Treiber-Manager die Funktion im Treiber auf. Andernfalls wird die Funktion selbst ausgeführt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLGetFunctions(  
     SQLHDBC           ConnectionHandle,  
     SQLUSMALLINT      FunctionId,  
     SQLUSMALLINT *    SupportedPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *ConnectionHandle*  
 [Eingabe] Verbindungshandle.  
  
 *Functionid*  
 [Eingabe] Ein **#define** Wert, der die ODBC-Funktion von Interesse identifiziert; **SQL_API_ODBC3_ALL_FUNCTIONS orSQL_API_ALL_FUNCTIONS**. **SQL_API_ODBC3_ALL_FUNCTIONS** wird von einer ODBC 3 *.x-Anwendung* verwendet, um die Unterstützung von ODBC 3 *.x* und früheren Funktionen zu bestimmen. **SQL_API_ALL_FUNCTIONS** wird von einer ODBC 2 *.x-Anwendung* verwendet, um die Unterstützung von ODBC 2 *.x* und früheren Funktionen zu bestimmen.  
  
 Eine Liste der **#define** Werte, die ODBC-Funktionen identifizieren, finden Sie in den Tabellen unter "Kommentare".  
  
 *SupportedPtr*  
 [Ausgabe]  Wenn *FunctionId* eine einzelne ODBC-Funktion identifiziert, verweist *SupportedPtr* auf einen einzelnen SQLUSMALLINT-Wert, der SQL_TRUE wird, wenn die angegebene Funktion vom Treiber unterstützt wird, und SQL_FALSE, wenn sie nicht unterstützt wird.  
  
 Wenn *FunctionId* SQL_API_ODBC3_ALL_FUNCTIONS ist, verweist *SupportedPtr* auf ein SQLSMALLINT-Array mit einer Anzahl von Elementen, die SQL_API_ODBC3_ALL_FUNCTIONS_SIZE entsprechen. Dieses Array wird vom Treiber-Manager als 4.000-Bit-Bitmap behandelt, mit der bestimmt werden kann, ob eine ODBC 3 *.x-* oder frühere Funktion unterstützt wird. Das SQL_FUNC_EXISTS Makro wird aufgerufen, um die Funktionsunterstützung zu bestimmen. (Siehe "Kommentare.") Eine ODBC 3 *.x-Anwendung* kann **SQLGetFunctions** mit SQL_API_ODBC3_ALL_FUNCTIONS entweder für einen ODBC 3 *.x-* oder ODBC 2 *.x-Treiber* aufrufen.  
  
 Wenn *FunctionId* SQL_API_ALL_FUNCTIONS ist, verweist *SupportedPtr* auf ein SQLUSMALLINT-Array mit 100 Elementen. Das Array wird durch **#define** Werte indiziert, die von *FunctionId* verwendet werden, um jede ODBC-Funktion zu identifizieren. Einige Elemente des Arrays sind nicht verwendet und für die zukünftige Verwendung reserviert. Ein Element ist SQL_TRUE, wenn es eine ODBC 2 *.x* oder frühere Funktion identifiziert, die vom Treiber unterstützt wird. Es ist SQL_FALSE, wenn es eine ODBC-Funktion identifiziert, die vom Treiber nicht unterstützt wird, oder eine ODBC-Funktion nicht.  
  
 Die in **SupportedPtr* zurückgegebenen Arrays verwenden eine nullbasierte Indizierung.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetFunctions** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DBC und einem *Handle* von *ConnectionHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLGetFunctions** zurückgegeben werden, und es werden die SQLSTATE-Werte im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------|-----|-----------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY010|Funktionssequenzfehler|(DM) **SQLGetFunctions** wurde vor **SQLConnect**, **SQLBrowseConnect**oder **SQLDriverConnect**aufgerufen.<br /><br /> (DM) **SQLBrowseConnect** wurde für den *ConnectionHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor **SQLBrowseConnect** SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgegeben wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für den *ConnectionHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY095|Funktionstyp aunter Bereich|(DM) Ein ungültiger *FunctionId-Wert* wurde angegeben.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
  
## <a name="comments"></a>Kommentare  
 **SQLGetFunctions** gibt immer zurück, dass **SQLGetFunctions**, **SQLDataSources**und **SQLDrivers** unterstützt werden. Dies geschieht, da diese Funktionen im Treiber-Manager implementiert sind. Der Treiber-Manager wird eine ANSI-Funktion der entsprechenden Unicode-Funktion zuordnen, wenn die Unicode-Funktion vorhanden ist, und eine Unicode-Funktion der entsprechenden ANSI-Funktion zuordnen, wenn die ANSI-Funktion vorhanden ist. Informationen dazu, wie Anwendungen **SQLGetFunctions**verwenden, finden Sie unter [Schnittstellenkonformitätsstufen](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 Im Folgenden finden Sie eine Liste gültiger Werte für *FunctionId* für Funktionen, die der ISO 92-Standards-Compliance-Stufe entsprechen:  
  
|FunctionId-Wert|FunctionId-Wert|  
|----------|----------|  
|SQL_API_SQLALLOCHANDLE|SQL_API_SQLGETDESCFIELD|  
|SQL_API_SQLBINDCOL|SQL_API_SQLGETDESCREC|  
|SQL_API_SQLCANCEL|SQL_API_SQLGETDIAGFIELD|  
|SQL_API_SQLCLOSECURSOR|SQL_API_SQLGETDIAGREC|  
|SQL_API_SQLCOLATTRIBUTE|SQL_API_SQLGETENVATTR|  
|SQL_API_SQLCONNECT|SQL_API_SQLGETFUNCTIONS|  
|SQL_API_SQLCOPYDESC|SQL_API_SQLGETINFO|  
|SQL_API_SQLDATASOURCES|SQL_API_SQLGETSTMTATTR|  
|SQL_API_SQLDESCRIBECOL|SQL_API_SQLGETTYPEINFO|  
|SQL_API_SQLDISCONNECT|SQL_API_SQLNUMRESULTCOLS|  
|SQL_API_SQLDRIVERS|SQL_API_SQLPARAMDATA|  
|SQL_API_SQLENDTRAN|SQL_API_SQLPREPARE|  
|SQL_API_SQLEXECDIRECT|SQL_API_SQLPUTDATA|  
|SQL_API_SQLEXECUTE|SQL_API_SQLROWCOUNT|  
|SQL_API_SQLFETCH|SQL_API_SQLSETCONNECTATTR|  
|SQL_API_SQLFETCHSCROLL|SQL_API_SQLSETCURSORNAME|  
|SQL_API_SQLFREEHANDLE|SQL_API_SQLSETDESCFIELD|  
|SQL_API_SQLFREESTMT|SQL_API_SQLSETDESCREC|  
|SQL_API_SQLGETCONNECTATTR|SQL_API_SQLSETENVATTR|  
|SQL_API_SQLGETCURSORNAME|SQL_API_SQLSETSTMTATTR|  
|SQL_API_SQLGETDATA| |  
  
 Im Folgenden finden Sie eine Liste gültiger Werte für *FunctionId* für Funktionen, die der Open Group-Standards-Compliance-Ebene entsprechen:  
  
|FunctionId-Wert|FunctionId-Wert|  
|-|-|  
|SQL_API_SQLCOLUMNS|SQL_API_SQLSTATISTICS|  
|SQL_API_SQLSPECIALCOLUMNS|SQL_API_SQLTABLES|  
  
 Im Folgenden finden Sie eine Liste gültiger Werte für *FunctionId* für Funktionen, die der ODBC-Standards-Compliance-Ebene entsprechen.  
  
|FunctionId-Wert|FunctionId-Wert|  
|-|-|  
|SQL_API_SQLBINDPARAMETER|SQL_API_SQLNATIVESQL|  
|SQL_API_SQLBROWSECONNECT|SQL_API_SQLNUMPARAMS|  
|SQL_API_SQLBULKOPERATIONS[1]|SQL_API_SQLPRIMARYKEYS|  
|SQL_API_SQLCOLUMNPRIVILEGES|SQL_API_SQLPROCEDURECOLUMNS|  
|SQL_API_SQLDESCRIBEPARAM|SQL_API_SQLPROCEDURES|  
|SQL_API_SQLDRIVERCONNECT|SQL_API_SQLSETPOS|  
|SQL_API_SQLFOREIGNKEYS|SQL_API_SQLTABLEPRIVILEGES|  
|SQL_API_SQLMORERESULTS| |  
  
 [1] Wenn Sie mit einem ODBC 2 *.x-Treiber* arbeiten, wird **SQLBulkOperations** nur dann als unterstützt zurückgegeben, wenn beide der folgenden Punkte wahr sind: Der ODBC 2 *.x-Treiber* unterstützt **SQLSetPos**, und der Informationstyp SQL_POS_OPERATIONS gibt das SQL_POS_ADD Bit als festgelegt zurück.  
  
 Im Folgenden finden Sie eine Liste gültiger Werte für *FunctionId* für Funktionen, die in ODBC 3.8 oder höher eingeführt wurden:  
  
|FunctionId-Wert|  
|-|  
|SQL_API_SQLCANCELHANDLE [2]|  
  
 [2] **SQLCancelHandle** wird nur dann als unterstützt zurückgegeben, wenn der Treiber sowohl **SQLCancel** als auch **SQLCancelHandle**unterstützt. Wenn **SQLCancel** unterstützt wird, **SQLCancelHandle** jedoch nicht, kann die Anwendung **SQLCancelHandle** weiterhin für ein Anweisungshandle aufrufen, da es **SQLCancel**zugeordnet wird.  
  
## <a name="sql_func_exists-macro"></a>SQL_FUNC_EXISTS Makro  
 Das SQL_FUNC_EXISTS(*SupportedPtr*, *FunctionID*) Makro wird verwendet, um die Unterstützung von ODBC 3 *.x* oder früheren Funktionen zu bestimmen, nachdem **SQLGetFunctions** mit dem *FunctionId-Argument* von SQL_API_ODBC3_ALL_FUNCTIONS aufgerufen wurde. Die Anwendung ruft SQL_FUNC_EXISTS mit dem *Argument SupportedPtr* auf den in *SQLGetFunctions*übergebenen *SupportedPtr* und das *FunctionID-Argument* auf die **#define** für die Funktion festgelegt. SQL_FUNC_EXISTS gibt SQL_TRUE zurück, wenn die Funktion unterstützt wird, und SQL_FALSE andernfalls.  
  
> [!NOTE]
>  Wenn Sie mit einem ODBC 2 *.x-Treiber* arbeiten, gibt der ODBC 3 *.x* Driver Manager SQL_TRUE für **SQLAllocHandle** und **SQLFreeHandle** zurück, da **SQLAllocHandle** **SQLAllocEnv**, **SQLAllocConnect**oder **SQLAllocStmt**zugeordnet ist und **SQLFreeHandle** **SQLFreeEnv**, **SQLFreeConnect**oder **SQLFreeStmt**zugeordnet ist. **SQLAllocHandle** oder **SQLFreeHandle** mit einem *HandleType-Argument* von SQL_HANDLE_DESC wird jedoch nicht unterstützt, obwohl SQL_TRUE für die Funktionen zurückgegeben wird, da es in diesem Fall keine ODBC 2 *.x-Funktion* gibt, der zugeordnet werden kann.  
  
## <a name="code-example"></a>Codebeispiel  
 Die folgenden drei Beispiele zeigen, wie eine Anwendung **SQLGetFunctions** verwendet, um zu bestimmen, ob ein Treiber **SQLTables**, **SQLColumns**und **SQLStatistics**unterstützt. Wenn der Treiber diese Funktionen nicht unterstützt, trennt die Anwendung die Verbindung zum Treiber. Im ersten Beispiel werden **SQLGetFunctions** einmal für jede Funktion aufgesucht.  
  
```cpp  
SQLUSMALLINT TablesExists, ColumnsExists, StatisticsExists;  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
  
retcodeTables = SQLGetFunctions(hdbc, SQL_API_SQLTABLES, &TablesExists);  
retcodeColumns = SQLGetFunctions(hdbc, SQL_API_SQLCOLUMNS, &ColumnsExists);  
retcodeStatistics = SQLGetFunctions(hdbc, SQL_API_SQLSTATISTICS, &StatisticsExists);  
  
// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.  
if (retcodeTables == SQL_SUCCESS && TablesExists == SQL_TRUE &&   
retcodeColumns == SQL_SUCCESS && ColumnsExists == SQL_TRUE &&   
retcodeStatistics == SQL_SUCCESS && StatisticsExists == SQL_TRUE)   
{  
  
   // Continue with application  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
 Im zweiten Beispiel ruft eine ODBC 3.x-Anwendung **SQLGetFunctions** auf und übergibt ihr ein Array, in dem **SQLGetFunctions** Informationen zu allen ODBC 3.x- und früheren Funktionen zurückgibt.  
  
```cpp  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
SQLUSMALLINT fExists[SQL_API_ODBC3_ALL_FUNCTIONS_SIZE];  
  
retcode = SQLGetFunctions(hdbc, SQL_API_ODBC3_ALL_FUNCTIONS, fExists);  
  
// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.  
if (reccode == SQL_SUCCESS &&   
SQL_FUNC_EXISTS(fExists, SQL_API_SQLTABLES) == SQL_TRUE &&  
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLCOLUMNS) == SQL_TRUE &&  
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLSTATISTICS) == SQL_TRUE)   
{  
  
   // Continue with application  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
 Das dritte Beispiel ist eine ODBC 2.x-Anwendung, die **SQLGetFunctions** aufruft und ihr ein Array von 100 Elementen übergibt, in dem **SQLGetFunctions** Informationen zu allen ODBC 2.x- und früheren Funktionen zurückgibt.  
  
```cpp  
#define FUNCTIONS 100  
  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
SQLUSMALLINT fExists[FUNCTIONS];  
  
retcode = SQLGetFunctions(hdbc, SQL_API_ALL_FUNCTIONS, fExists);  
  
/* SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver. */  
if (retcode == SQL_SUCCESS &&   
fExists[SQL_API_SQLTABLES] == SQL_TRUE &&  
   fExists[SQL_API_SQLCOLUMNS] == SQL_TRUE &&  
   fExists[SQL_API_SQLSTATISTICS] == SQL_TRUE)   
{  
  
   /* Continue with application */  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben der Einstellung eines Verbindungsattributs|[SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Zurückgeben von Informationen zu einem Treiber oder einer Datenquelle|[SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Zurückgeben der Einstellung eines Anweisungsattributs|[SQLGetStmtAttr-Funktion](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
