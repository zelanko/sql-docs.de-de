---
description: SQLPutData-Funktion
title: SQLPutData-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: 8adda30141a99c1a575d8cc66511f1606e77dcf5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487133"
---
# <a name="sqlputdata-function"></a>SQLPutData-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLPutData** ermöglicht es einer Anwendung, Daten für einen Parameter oder eine Spalte zur Anweisungs Ausführungszeit an den Treiber zu senden. Diese Funktion kann verwendet werden, um Zeichen-oder Binärdaten Werte in Teilen an eine Spalte mit einem Zeichen-, Binär-oder Datenquellen spezifischen Datentyp zu senden (z. b. Parameter der SQL_LONGVARBINARY oder SQL_LONGVARCHAR Typen). **SQLPutData** unterstützt die Bindung an einen Unicode-C-Datentyp, auch wenn der zugrunde liegende Treiber keine Unicode-Daten unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLPutData(  
      SQLHSTMT     StatementHandle,  
      SQLPOINTER   DataPtr,  
      SQLLEN       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 Der Anweisungs Handle.  
  
 *DataPtr*  
 Der Zeiger auf einen Puffer, der die tatsächlichen Daten für den Parameter oder die Spalte enthält. Die Daten müssen den C-Datentyp aufweisen, der im *ValueType* -Argument von **SQLBindParameter** (für Parameterdaten) oder das *TargetType* -Argument von **SQLBindCol** (für Spaltendaten) angegeben ist.  
  
 *StrLen_or_Ind*  
 Der Länge von \* *DataPtr*. Gibt die Menge der Daten an, die in einem **SQLPutData**-Befehl gesendet werden. Die Datenmenge kann je nach einem bestimmten Parameter oder einer Spalte variieren. *StrLen_Or_Ind* wird ignoriert, es sei denn, er erfüllt eine der folgenden Bedingungen:  
  
-   *StrLen_Or_Ind* ist SQL_NTS, SQL_NULL_DATA oder SQL_DEFAULT_PARAM.  
  
-   Der in **SQLBindParameter** oder **SQLBindCol** angegebene C-Datentyp ist SQL_C_CHAR oder SQL_C_BINARY.  
  
-   Der c-Datentyp ist SQL_C_DEFAULT, und der c-Standard Datentyp für den angegebenen SQL-Datentyp ist SQL_C_CHAR oder SQL_C_BINARY.  
  
 Wenn *StrLen_Or_Ind* für alle anderen Typen von C-Daten nicht SQL_NULL_DATA oder SQL_DEFAULT_PARAM ist, geht der Treiber davon aus, dass die Größe des \* *DataPtr* -Puffers die Größe des mit *ValueType* oder *TargetType* angegebenen C-Datentyps ist, und sendet den gesamten Datenwert. Weitere Informationen finden Sie unter "Datentypen" in Anhang D: Datentypen [von C in SQL-Daten](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) Typen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLPutData** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem *handle* von *StatementHandle*abgerufen werden. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die häufig von **SQLPutData** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichen folgen Daten, rechts abgeschnitten|Zeichen folgen-oder Binärdaten, die für einen Output-Parameter zurückgegeben wurden, führten zu einer Verkürzung von nicht leeren Zeichen oder Binärdaten, die nicht NULL sind. Wenn es sich um einen Zeichen folgen Wert handelt, wurde er rechts abgeschnitten. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Verletzung des Attributs für eingeschränkte Datentypen|Der Datenwert, der vom *ValueType* -Argument in **SQLBindParameter** für den gebundenen Parameter identifiziert wurde, konnte nicht in den Datentyp konvertiert werden, der durch das *Parameter Type* -Argument in **SQLBindParameter**identifiziert wird.|  
|07S01|Ungültige Verwendung des Standard Parameters.|Ein Parameterwert, der mit **SQLBindParameter**festgelegt wurde, wurde SQL_DEFAULT_PARAM, und der entsprechende Parameter hat keinen Standardwert.|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|22001|Zeichen folgen Daten, rechter Abschneiden|Die Zuweisung eines Zeichens oder Binärwerts zu einer Spalte führte zum Abschneiden von nicht leeren (Zeichen) oder nicht-NULL-Zeichen (binär) oder Bytes.<br /><br /> Der SQL_NEED_LONG_DATA_LEN Informationstyp in **SQLGetInfo** lautete "Y", und es wurden weitere Daten für einen Long-Parameter gesendet (der Datentyp war SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer Datenquellen spezifischer Datentyp), als mit dem *StrLen_or_IndPtr* -Argument in **SQLBindParameter**angegeben wurde.<br /><br /> Der SQL_NEED_LONG_DATA_LEN Informationstyp in **SQLGetInfo** lautete "Y", und es wurden weitere Daten für eine lange Spalte (der Datentyp SQL_LONGVARCHAR, SQL_LONGVARBINARY oder ein langer Datenquellen spezifischer Datentyp) als in dem Längenpuffer angegeben, der einer Spalte in einer Daten Zeile entspricht, die mit **SQLBulkOperations** hinzugefügt oder aktualisiert wurde oder mit **SQLSetPos**aktualisiert wurde.|  
|22003|Numerischer Wert außerhalb des zulässigen Bereichs|Die Daten, die für einen gebundenen numerischen Parameter oder eine Spalte gesendet werden, haben bewirkt, dass der gesamte (im Gegensatz zum Bruchteil) Teil der Zahl abgeschnitten wird, wenn er der zugeordneten Tabellenspalte zugewiesen wird.<br /><br /> Das Zurückgeben eines numerischen Werts (als numerisch oder Zeichenfolge) für einen oder mehrere Eingabe-/Ausgabe-oder Ausgabeparameter hätte dazu geführt, dass der gesamte (im Gegensatz zum Bruchteil) Teil der Zahl abgeschnitten wird.|  
|22007|Ungültiges datetime-Format.|Die Daten, die für einen Parameter oder eine Spalte gesendet wurden, die an eine Datums-, Uhrzeit-oder Zeitstempel Struktur gebunden waren, waren jeweils ein ungültiges Datum, eine Uhrzeit oder ein ungültiges Zeitstempel.<br /><br /> Ein Eingabe-/Ausgabe-oder Ausgabeparameter wurde an eine Datums-, Uhrzeit-oder Zeitstempel-C-Struktur gebunden, und ein Wert im zurückgegebenen Parameter war, bzw. ein ungültiges Datum, eine Uhrzeit oder ein ungültiger Zeitstempel. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22008|Überlauf bei DateTime-Feld|Ein für einen Eingabe-/Ausgabe-oder Ausgabeparameter berechneter DateTime-Ausdruck führte zu einer ungültigen Datums-, Uhrzeit-oder Zeitstempel-C-Struktur.|  
|22012|Division durch Null|Ein arithmetischer Ausdruck, der für einen Eingabe-/Ausgabe-oder Ausgabeparameter berechnet wurde, führte zu einer Division|  
|22015|Überlauf des Intervall Felds|Die Daten, die für eine genaue numerische oder Intervall Spalte oder einen bestimmten Intervall Parameter an einen SQL-Datentyp für das Intervall gesendet werden, haben einen Verlust signifikanter Ziffern<br /><br /> Es wurden Daten für eine Intervall Spalte oder einen Parameter mit mehr als einem Feld gesendet, in einen numerischen Datentyp konvertiert, und es gab keine Darstellung im numerischen Datentyp.<br /><br /> Die Daten, die für Spalten-oder Parameterdaten gesendet werden, wurden einem SQL-Intervalltyp zugewiesen, und es gab keine Darstellung des Werts des C-Typs im Interval-SQL-Typ.<br /><br /> Die Daten, die für eine genaue numerische Spalte oder Interval c-Spalte oder einen-Parameter an einen Interval-c-Typ gesendet werden, haben einen Verlust signifikanter Ziffern<br /><br /> Die Daten, die für Spalten-oder Parameterdaten gesendet werden, wurden einer Intervall-C-Struktur zugewiesen, und es gab keine Darstellung der Daten in der Intervall Datenstruktur.|  
|22018|Ungültiger Zeichen Wert für Umwandlungs Spezifikation.|Der C-Typ war ein genauer oder Ungefährer numerischer, DateTime-oder Interval-Datentyp. der SQL-Typ der Spalte war ein Zeichen Datentyp. und der Wert in der Spalte oder im Parameter war kein gültiges Literale des gebundenen C-Typs.<br /><br /> Der SQL-Typ war ein genauer oder Ungefährer numerischer, DateTime-oder Interval-Datentyp. der C-Typ war SQL_C_CHAR. und der Wert in der Spalte oder dem Parameter war kein gültiges Literale des gebundenen SQL-Typs.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für " *StatementHandle*" aktiviert. Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für " *StatementHandle*" aufgerufen. Anschließend wurde die Funktion erneut für " *StatementHandle*" aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **SQLCancel** oder **sqlcancelhandle** für das *StatementHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|(DM) das Argument *DataPtr* war ein NULL-Zeiger, und das Argument *StrLen_Or_Ind* war nicht 0, SQL_DEFAULT_PARAM oder SQL_NULL_DATA.|  
|HY010|Funktions Sequenz Fehler|(DM) der vorherige Funktions Aufrufwert war kein Aufrufder **SQLPutData** -oder **SQLParamData**-Funktion.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das mit dem *StatementHandle*verknüpft ist. Diese asynchrone Funktion wurde noch ausgeführt, als die SQLPutData-Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für das *StatementHandle* aufgerufen und wird noch ausgeführt, als diese Funktion aufgerufen wurde.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY019|In Teile gesendete nicht-Zeichen-und nicht-Binärdaten|**SQLPutData** wurde für einen Parameter oder eine Spalte mehrmals aufgerufen und wurde nicht zum Senden von Zeichen-c-Daten an eine Spalte mit einem Zeichen-, Binär-oder Datenquellen spezifischen Datentyp oder zum Senden binärer c-Daten an eine Spalte mit einem Zeichen-, Binär-oder Datenquellen spezifischen Datentyp verwendet.|  
|HY020|Es wurde versucht, einen NULL-Wert zu verketten.|**SQLPutData** wurde mehrmals aufgerufen, da der Aufruf, der SQL_NEED_DATA zurückgegeben hat, und in einem dieser Aufrufe das *StrLen_Or_Ind* -Argument SQL_NULL_DATA oder SQL_DEFAULT_PARAM enthielt.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|Das Argument *DataPtr* war kein NULL-Zeiger, und das Argument *StrLen_Or_Ind* war kleiner als 0, aber nicht gleich SQL_NTS oder SQL_NULL_DATA.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *StatementHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
  
 Wenn **SQLPutData** beim Senden von Daten für einen Parameter in einer SQL-Anweisung aufgerufen wird, kann es jeden SQLSTATE-Wert zurückgeben, der von der aufgerufenen Funktion zurückgegeben werden kann, um die Anweisung auszuführen (**SQLExecute** oder **SQLExecDirect**). Wenn Sie beim Senden von Daten für eine Spalte aufgerufen wird, die mit **SQLBulkOperations** aktualisiert oder hinzugefügt oder mit **SQLSetPos**aktualisiert wird, können alle SQLSTATE-Objekte zurückgegeben werden, die von **SQLBulkOperations** oder **SQLSetPos**zurückgegeben werden können.  
  
## <a name="comments"></a>Kommentare  
 **SQLPutData** kann aufgerufen werden, um Data-at-Execution-Daten für zwei Verwendungen bereitzustellen: Parameterdaten, die in einem Aufruf von **SQLExecute** oder **SQLExecDirect**verwendet werden sollen, oder Spaltendaten, die verwendet werden, wenn eine Zeile aktualisiert oder durch einen Aufruf **von** **SQLSetPos**aktualisiert wird.  
  
 Wenn eine Anwendung **SQLParamData** aufruft, um zu bestimmen, welche Daten gesendet werden sollen, gibt der Treiber einen Indikator zurück, der von der Anwendung verwendet werden kann, um zu bestimmen, welche Parameterdaten zu senden sind oder welche Spaltendaten gefunden werden. Außerdem wird SQL_NEED_DATA zurückgegeben, bei dem es sich um einen Indikator für die Anwendung handelt, der zum Senden der Daten **SQLPutData** aufruft. Im *DataPtr* -Argument von **SQLPutData**übergibt die Anwendung einen Zeiger auf den Puffer, der die tatsächlichen Daten für den Parameter oder die Spalte enthält.  
  
 Wenn der Treiber SQL_SUCCESS für **SQLPutData**zurückgibt, ruft die Anwendung **SQLParamData** erneut auf. **SQLParamData** gibt SQL_NEED_DATA zurück, wenn weitere Daten gesendet werden müssen. in diesem Fall ruft die Anwendung **SQLPutData** erneut auf. Wenn alle Data-at-Execution-Daten gesendet wurden, wird SQL_SUCCESS zurückgegeben. Die Anwendung ruft dann **SQLParamData** erneut auf. Wenn der Treiber SQL_NEED_DATA und einen weiteren Indikator in * \* ValuePtrPtr*zurückgibt, sind Daten für einen anderen Parameter oder eine Spalte erforderlich, und **SQLPutData** wird erneut aufgerufen. Wenn der Treiber SQL_SUCCESS zurückgibt, werden alle Data-at-Execution-Daten gesendet, und die SQL-Anweisung kann ausgeführt werden, oder der **SQLBulkOperations** -oder **SQLSetPos** -Rückruf kann verarbeitet werden.  
  
 Weitere Informationen zur Übergabe von Data-at-Execution-Parameterdaten zur Anweisungs Ausführungszeit finden Sie unter "übergeben von Parameterwerten" in [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) und [Senden von Long-Daten](../../../odbc/reference/develop-app/sending-long-data.md). Weitere Informationen zur Aktualisierung oder zum Hinzufügen von Data-at-Execution-Spaltendaten finden Sie im Abschnitt "Verwenden von SQLSetPos" in [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), "Ausführen von Massen Aktualisierungen mithilfe von Lesezeichen" in [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)und [Long Data und SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
> [!NOTE]  
>  Eine Anwendung kann **SQLPutData** nur zum Senden von Daten in Teilen verwenden, wenn Zeichen-c-Daten an eine Spalte mit einem Zeichen-, Binär-oder Datenquellen spezifischen Datentyp gesendet werden oder wenn binäre C-Daten an eine Spalte mit einem Zeichen-, Binär-oder Datenquellen spezifischen Datentyp gesendet werden. Wenn **SQLPutData** unter allen anderen Bedingungen mehrmals aufgerufen wird, gibt es SQL_ERROR und SQLSTATE HY019 (nicht-Zeichen-und nicht-Binärdaten, die in Teile gesendet werden) zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Datenquellen Name mit dem Namen Test angenommen. Die zugehörige Datenbank sollte über eine Tabelle verfügen, die Sie wie folgt erstellen können:  
  
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
|Abbrechen der Anweisungs Verarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen einer SQL-Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL-Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Zurückgeben des nächsten Parameters zum Senden von Daten|[SQLParamData-Funktion](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
