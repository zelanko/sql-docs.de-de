---
title: SQLPutData-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPutData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPutData
helpviewer_keywords:
- SQLPutData function [ODBC]
ms.assetid: 9a60f004-1477-4c54-a20c-7378e1116713
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c4e704d96924942812904ea63d0e3d4fce8748e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300040"
---
# <a name="sqlputdata-function"></a>SQLPutData-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLPutData** ermöglicht es einer Anwendung, Daten für einen Parameter oder eine Spalte zur Ausführungszeit der Anweisung an den Treiber zu senden. Diese Funktion kann verwendet werden, um Zeichen- oder Binärdatenwerte in Teilen an eine Spalte mit einem Zeichen-, Binär- oder datenquellenspezifischen Datentyp zu senden (z. B. Parameter der SQL_LONGVARBINARY oder SQL_LONGVARCHAR Typen). **SQLPutData** unterstützt die Bindung an einen Unicode C-Datentyp, auch wenn der zugrunde liegende Treiber Keine Unicode-Daten unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLPutData(  
      SQLHSTMT     StatementHandle,  
      SQLPOINTER   DataPtr,  
      SQLLEN       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *DataPtr*  
 [Eingabe] Zeiger auf einen Puffer, der die tatsächlichen Daten für den Parameter oder die Spalte enthält. Die Daten müssen sich im C-Datentyp befinden, der im *ValueType-Argument* von **SQLBindParameter** (für Parameterdaten) oder im *TargetType-Argument* von **SQLBindCol** (für Spaltendaten) angegeben ist.  
  
 *StrLen_or_Ind*  
 [Eingabe] Länge \*von *DataPtr*. Gibt die Datenmenge an, die bei einem Aufruf von **SQLPutData**gesendet wird. Die Datenmenge kann bei jedem Aufruf für einen bestimmten Parameter oder eine bestimmte Spalte variieren. *StrLen_or_Ind* wird ignoriert, es sei denn, sie erfüllt eine der folgenden Bedingungen:  
  
-   *StrLen_or_Ind* ist SQL_NTS, SQL_NULL_DATA oder SQL_DEFAULT_PARAM.  
  
-   Der in **SQLBindParameter** oder **SQLBindCol** angegebene C-Datentyp ist SQL_C_CHAR oder SQL_C_BINARY.  
  
-   Der C-Datentyp ist SQL_C_DEFAULT, und der Standard-C-Datentyp für den angegebenen SQL-Datentyp ist SQL_C_CHAR oder SQL_C_BINARY.  
  
 Bei allen anderen Arten von *StrLen_or_Ind* C-Daten geht der Treiber davon aus, \*dass die Größe des *DataPtr-Puffers* die Größe des mit *ValueType* oder *TargetType* angegebenen C-Datentyps ist, wenn StrLen_or_Ind nicht SQL_NULL_DATA oder SQL_DEFAULT_PARAM ist, und sendet den gesamten Datenwert. Weitere Informationen finden Sie unter [Konvertieren von Daten von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) in Anhang D: Datentypen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLPutData** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLPutData** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Zeichenfolgen- oder Binärdaten, die für einen Ausgabeparameter zurückgegeben wurden, führten zum Abschneiden von nicht leeren Zeichen oder Binärdaten, die nicht NULL sind. Wenn es sich um einen Zeichenfolgenwert handelte, wurde er rechts abgeschnitten. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des eingeschränkten Datentypattributs|Der datenwert, der durch das *ValueType-Argument* in **SQLBindParameter** für den bound-Parameter identifiziert wurde, konnte nicht in den Datentyp konvertiert werden, der durch das *ParameterType-Argument* in **SQLBindParameter**identifiziert wurde.|  
|07S01|Ungültige Verwendung des Standardparameters|Ein Parameterwert, der mit **SQLBindParameter**festgelegt wurde, wurde SQL_DEFAULT_PARAM, und der entsprechende Parameter hatte keinen Standardwert.|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|22001|Zeichenfolgendaten, rechtes Abschneiden|Die Zuweisung eines Zeichens oder Binärwerts zu einer Spalte führte zum Abschneiden von nicht leeren (Zeichen) oder Nicht-NULL-Zeichen oder Bytes (binär).<br /><br /> Der SQL_NEED_LONG_DATA_LEN-Informationstyp in **SQLGetInfo** war "Y", und es wurden mehr Daten für einen langen Parameter gesendet (der Datentyp wurde SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer datenquellenspezifischer Datentyp) als mit dem *Argument StrLen_or_IndPtr* in **SQLBindParameter**angegeben wurde.<br /><br /> Der SQL_NEED_LONG_DATA_LEN-Informationstyp in **SQLGetInfo** war "Y", und es wurden mehr Daten für eine lange Spalte gesendet (der Datentyp war SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer datenquellenspezifischer Datentyp), als im Längenpuffer angegeben wurde, der einer Spalte in einer Datenzeile entspricht, die mit **SQLBulkOperations** hinzugefügt oder aktualisiert oder mit **SQLSetPos**aktualisiert wurde.|  
|22003|Numerischer Wert aofc|Die für einen gebundenen numerischen Parameter oder eine gebundene Spalte gesendeten Daten haben dazu geführt, dass der gesamte (im Gegensatz zu fraktioniertem) Teil der Zahl abgeschnitten wurde, wenn er der zugeordneten Tabellenspalte zugewiesen wurde.<br /><br /> Das Zurückgeben eines numerischen Werts (als numerische oder Zeichenfolge) für einen oder mehrere Eingabe-/Ausgabe- oder Ausgabeparameter hätte dazu geführt, dass der gesamte (im Gegensatz zu fraktioniertem) Teil der Zahl abgeschnitten wurde.|  
|22007|Ungültiges Datumszeitformat|Die für einen Parameter oder eine Spalte gesendeten Daten, die an eine Datums-, Uhrzeit- oder Zeitstempelstruktur gebunden waren, waren jeweils ein ungültiges Datum, eine ungültige Uhrzeit oder ein Zeitstempel.<br /><br /> Ein Eingabe-/Ausgabe- oder Ausgabeparameter war an eine Datums-, Uhrzeit- oder Zeitstempel-C-Struktur gebunden, und ein Wert im zurückgegebenen Parameter war jeweils ein ungültiges Datum, eine ungültige Uhrzeit oder ein Zeitstempel. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22008|Datetime-Feldüberlauf|Ein Datumszeitausdruck, der für einen Eingabe-/Ausgabe- oder Ausgabeparameter berechnet wurde, führte zu einer ungültigen Datums-, Uhrzeit- oder Zeitstempel-C-Struktur.|  
|22012|Division durch Null|Ein arithmetischer Ausdruck, der für einen Eingabe-/Ausgabe- oder Ausgabeparameter berechnet wurde, führte zur Division durch Null.|  
|22015|Intervallfeldüberlauf|Die Daten, die für eine exakte numerische oder Intervallspalte oder einen Parameter an einen INTERVALL-SQL-Datentyp gesendet wurden, verursachten einen Verlust signifikanter Ziffern.<br /><br /> Daten wurden für eine Intervallspalte oder einen Parameter mit mehr als einem Feld gesendet, in einen numerischen Datentyp konvertiert und hatten keine Darstellung im numerischen Datentyp.<br /><br /> Die für Spalten- oder Parameterdaten gesendeten Daten wurden einem INTERVALL-SQL-Typ zugewiesen, und es gab keine Darstellung des Werts des Typs C im Intervall-SQL-Typ.<br /><br /> Die Daten, die für eine exakte numerische oder Intervall-C-Spalte oder einen Parameter an einen Intervall-C-Typ gesendet wurden, verursachten einen Verlust signifikanter Ziffern.<br /><br /> Die für Spalten- oder Parameterdaten gesendeten Daten wurden einer Intervall-C-Struktur zugewiesen, und es gab keine Darstellung der Daten in der Intervalldatenstruktur.|  
|22018|Ungültiger Zeichenwert für Umwandlungsspezifikation|Der C-Typ war ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp. Der SQL-Typ der Spalte war ein Zeichendatentyp; und der Wert in der Spalte oder dem Parameter war kein gültiges Literal des gebundenen C-Typs.<br /><br /> Der SQL-Typ war ein exakter oder ungefährer numerischer Typ, eine Datumszeit oder ein Intervalldatentyp. der Typ C wurde SQL_C_CHAR; und der Wert in der Spalte oder dem Parameter war kein gültiges Literal des gebundenen SQL-Typs.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) Das Argument *DataPtr* war ein Nullzeiger, und das Argument *StrLen_or_Ind* war nicht 0, SQL_DEFAULT_PARAM oder SQL_NULL_DATA.|  
|HY010|Funktionssequenzfehler|(DM) Der vorherige Funktionsaufruf war kein Aufruf von **SQLPutData** oder **SQLParamData**.<br /><br /> (DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die SQLPutData-Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY019|Nicht-Zeichen- und nicht-binäre Daten werden in Stücken gesendet|**SQLPutData** wurde mehr als einmal für einen Parameter oder eine Spalte aufgerufen, und es wurde nicht verwendet, um Zeichen-C-Daten an eine Spalte mit einem zeichen-, binären oder datenquellenspezifischen Datentyp zu senden oder binäre C-Daten an eine Spalte mit einem Zeichen-, Binär- oder Datenquellen-spezifischen Datentyp zu senden.|  
|HY020|Versuch, einen NULL-Wert zu verketten|**SQLPutData** wurde seit dem Aufruf, der SQL_NEED_DATA zurückgegeben hat, mehr als einmal aufgerufen, und in einem dieser Aufrufe enthielt das *StrLen_or_Ind-Argument* SQL_NULL_DATA oder SQL_DEFAULT_PARAM.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|Das Argument *DataPtr* war kein Nullzeiger, und das Argument *StrLen_or_Ind* war kleiner als 0, aber nicht gleich SQL_NTS oder SQL_NULL_DATA.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
 Wenn **SQLPutData** beim Senden von Daten für einen Parameter in einer SQL-Anweisung aufgerufen wird, kann es jede SQLSTATE zurückgeben, die von der Funktion zurückgegeben werden kann, die aufgerufen wird, die Anweisung auszuführen (**SQLExecute** oder **SQLExecDirect**). Wenn sie aufgerufen wird, während Daten für eine Spalte gesendet werden, die mit **SQLBulkOperations** aktualisiert oder hinzugefügt wird oder mit **SQLSetPos**aktualisiert wird, kann sie jede SQLSTATE zurückgeben, die von **SQLBulkOperations** oder **SQLSetPos**zurückgegeben werden kann.  
  
## <a name="comments"></a>Kommentare  
 **SQLPutData** kann aufgerufen werden, um Daten bei der Ausführung für zwei Verwendungen zu liefern: Parameterdaten, die in einem Aufruf von **SQLExecute** oder **SQLExecDirect**verwendet werden sollen, oder Spaltendaten, die verwendet werden sollen, wenn eine Zeile durch einen Aufruf von **SQLBulkOperations** oder durch einen Aufruf von **SQLSetPos**aktualisiert wird.  
  
 Wenn eine Anwendung **SQLParamData** aufruft, um zu bestimmen, welche Daten sie senden soll, gibt der Treiber einen Indikator zurück, mit dem die Anwendung bestimmen kann, welche Parameterdaten gesendet werden sollen oder wo Spaltendaten gefunden werden können. Es gibt auch SQL_NEED_DATA zurück, was ein Indikator für die Anwendung ist, dass sie **SQLPutData** aufrufen sollte, um die Daten zu senden. Im *DataPtr-Argument* für **SQLPutData**übergibt die Anwendung einen Zeiger an den Puffer, der die tatsächlichen Daten für den Parameter oder die Spalte enthält.  
  
 Wenn der Treiber SQL_SUCCESS für **SQLPutData**zurückgibt, ruft die Anwendung **SQLParamData** erneut auf. **SQLParamData** gibt SQL_NEED_DATA zurück, wenn mehr Daten gesendet werden müssen, in diesem Fall ruft die Anwendung **SQLPutData** erneut auf. Es gibt SQL_SUCCESS zurück, wenn alle Daten bei der Ausführung gesendet wurden. Die Anwendung ruft dann **SQLParamData** erneut auf. Wenn der Treiber SQL_NEED_DATA und einen anderen Indikator in * \*ValuePtrPtr*zurückgibt, sind Daten für einen anderen Parameter oder eine andere Spalte erforderlich, und **SQLPutData** wird erneut aufgerufen. Wenn der Treiber SQL_SUCCESS zurückgibt, wurden alle Daten bei der Ausführung gesendet, und die SQL-Anweisung kann ausgeführt werden, oder der **SQLBulkOperations-** oder **SQLSetPos-Aufruf** kann verarbeitet werden.  
  
 Weitere Informationen dazu, wie Data-at-Execution-Parameterdaten zur Ausführungszeit der Anweisung übergeben werden, finden Sie unter "Übergeben von Parameterwerten" in [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) und [Senden von Long Data](../../../odbc/reference/develop-app/sending-long-data.md). Weitere Informationen dazu, wie Daten-at-Execution-Spaltendaten aktualisiert oder hinzugefügt werden, finden Sie im Abschnitt "Verwenden von SQLSetPos" in [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), "Durchführen von Massenaktualisierungen mithilfe von Lesezeichen" in [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)und [Long Data und SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
> [!NOTE]  
>  Eine Anwendung kann **SQLPutData** verwenden, um Daten in Teilen nur zu senden, wenn Zeichen-C-Daten an eine Spalte mit einem zeichen-, binären oder datenquellenspezifischen Datentyp gesendet werden oder wenn binäre C-Daten an eine Spalte mit einem Zeichen-, Binär- oder Datenquellenspezifischen Datentyp gesendet werden. Wenn **SQLPutData** unter anderen Bedingungen mehr als einmal aufgerufen wird, gibt es SQL_ERROR und SQLSTATE HY019 zurück (nicht-zeichenförmige und nicht-binäre Daten, die in Teilen gesendet werden).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird von einem Datenquellennamen namens Test ausgegangen. Die zugeordnete Datenbank sollte über eine Tabelle verfügen, die Sie wie folgt erstellen können:  
  
```sql  
CREATE TABLE emp4 (NAME char(30), AGE int, BIRTHDAY datetime, Memo1 text)  
```  
  
```cpp  
// SQLPutData.cpp  
// compile with: odbc32.lib user32.lib  
#include <stdio.h>  
#include <windows.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define TEXTSIZE  12000  
#define MAXBUFLEN 256  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // SQLBindParameter variables.  
   SQLLEN cbTextSize, lbytes;  
  
   // SQLParamData variable.  
   PTR pParmID;  
  
   // SQLPutData variables.  
   UCHAR  Data[] =   
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyz";  
  
   SDWORD cbBatch = (SDWORD)sizeof(Data) - 1;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set parameters based on total data to send.  
   lbytes = (SDWORD)TEXTSIZE;  
   cbTextSize = SQL_LEN_DATA_AT_EXEC(lbytes);  
  
   // Bind the parameter marker.  
   retcode = SQLBindParameter (hstmt1,           // hstmt  
                               1,                // ipar  
                               SQL_PARAM_INPUT,  // fParamType  
                               SQL_C_CHAR,       // fCType  
                               SQL_LONGVARCHAR,  // FSqlType  
                               lbytes,           // cbColDef  
                               0,                // ibScale  
                               (VOID *)1,        // rgbValue  
                               0,                // cbValueMax  
                               &cbTextSize);     // pcbValue  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLBindParameter Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the command.  
   retcode =   
      SQLExecDirect(hstmt1, (UCHAR*)"INSERT INTO emp4 VALUES('Paul Borm', 46,'1950-11-12 00:00:00', ?)", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_NEED_DATA) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Check to see if NEED_DATA; if yes, use SQLPutData.  
   retcode = SQLParamData(hstmt1, &pParmID);  
   if (retcode == SQL_NEED_DATA) {  
      while (lbytes > cbBatch) {  
         SQLPutData(hstmt1, Data, cbBatch);  
         lbytes -= cbBatch;  
      }  
      // Put final batch.  
      retcode = SQLPutData(hstmt1, Data, lbytes);   
   }  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLParamData Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Make final SQLParamData call.  
   retcode = SQLParamData(hstmt1, &pParmID);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("Final SQLParamData Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clean up.  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an einen Parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Zurückgeben des nächsten Parameters zum Senden von Daten für|[SQLParamData-Funktion](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
