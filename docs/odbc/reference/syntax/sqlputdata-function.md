---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f91799e5d484a763c23fcc132232a8a35fc6152c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63186114"
---
# <a name="sqlputdata-function"></a>SQLPutData-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLPutData** ermöglicht es einer Anwendung zum Senden von Daten für einen Parameter oder eine Spalte für den Treiber während der Ausführung der Anweisung. Diese Funktion kann verwendet werden, zum Senden von Zeichen- oder Binärdaten-Werten in Teilen auf eine Spalte mit einem Zeichen oder den binären datenquellenspezifische-Datentyp (z. B. Parameter der Typen SQL_LONGVARBINARY oder SQL_LONGVARCHAR). **SQLPutData** unterstützt die Bindung an eine Unicode-C-Datentyp, selbst wenn die zugrunde liegenden Treiber Unicode-Daten nicht unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQLRETURN SQLPutData(  
      SQLHSTMT     StatementHandle,  
      SQLPOINTER   DataPtr,  
      SQLLEN       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *DataPtr*  
 [Eingabe] Zeiger auf einen Puffer, die die tatsächlichen Daten für den Parameter oder die Spalte enthält. Die Daten müssen in der C-Datentyp, der im angegebenen sein der *ValueType* Argument der **SQLBindParameter** (für Parameterdaten) oder die *TargetType* Argument  **SQLBindCol** (für Spaltendaten).  
  
 *StrLen_or_Ind*  
 [Eingabe] Länge der \* *DataPtr*. Gibt an, die Menge der Daten in einem Aufruf von gesendeten **SQLPutData**. Die Menge der Daten kann mit jedem Aufruf für einen bestimmten Parameter oder eine Spalte variieren. *StrLen_or_Ind* wird ignoriert, wenn sie eine der folgenden Bedingungen erfüllt:  
  
-   *StrLen_or_Ind* ist SQL_NTS, SQL_NULL_DATA oder SQL_DEFAULT_PARAM.  
  
-   Die C-Datentyp, der im angegebenen **SQLBindParameter** oder **SQLBindCol** ist SQL_C_CHAR oder sql_c_binary angegeben.  
  
-   Die C-Datentyp ist SQL_C_DEFAULT; der Standard-C-Datentyp für den angegebenen SQL-Datentyp ist SQL_C_CHAR oder sql_c_binary angegeben.  
  
 Für alle anderen Typen von C-Daten Wenn *StrLen_or_Ind* ist kein SQL_NULL_DATA oder SQL_DEFAULT_PARAM der Treiber setzt voraus, dass die Größe des der \* *DataPtr* Puffer ist die Größe des angegebenen C-Datentyp mit *ValueType* oder *TargetType* und sendet den gesamten Datenwert. Weitere Informationen finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) in Anhang D: Datentypen.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLPutData** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_STMT und *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLPutData** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Description|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Zeichenfolgen- oder Binärdaten, die für ein Output-Parameter zurückgegeben hat das Abschneiden von nicht leeren Zeichen oder binäre Daten ungleich NULL. Falls es sich um einen Zeichenfolgenwert handelt, war es, rechts abgeschnitten. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07006|Attributverletzung eingeschränkter Daten|Der Wert von identifiziert die *ValueType* -Argument in **SQLBindParameter** für der gebundene Parameter nicht in der identifizierte Datentyp konvertiert werden kann die *ParameterType*-Argument in **SQLBindParameter**.|  
|07S01|Ungültige Verwendung des Standardparameters|Legen Sie ein Parameterwert mit **SQLBindParameter**SQL_DEFAULT_PARAM wurde und der entsprechende Parameter keinen Standardwert.|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|22001|Zeichenfolgendaten, rechts abgeschnitten.|Die Zuweisung von einem Zeichen- oder binären Wert einer Spalte führte das Abschneiden von NichtLeer (Zeichen), (binär) nicht-Null-Zeichen oder Bytes.<br /><br /> Der Typ des SQL_NEED_LONG_DATA_LEN-Informationen in **SQLGetInfo** wurde von "Y", und weitere Daten für einen Parameter "long" (der Datentyp wurde SQL_LONGVARCHAR, SQL_LONGVARBINARY oder einen long-Daten datenquellenspezifische-Datentyp) gesendet wurde, als angegeben wurde mit der *StrLen_or_IndPtr* -Argument in **SQLBindParameter**.<br /><br /> Der Typ des SQL_NEED_LONG_DATA_LEN-Informationen in **SQLGetInfo** wurde von "Y", und weitere Daten für eine lange Spalte (der Datentyp wurde SQL_LONGVARCHAR, SQL_LONGVARBINARY oder einen long-Daten datenquellenspezifische-Datentyp) gesendet wurde, als im angegebenen die Puffer der Länge für eine Spalte in eine Zeile mit Daten, die hinzugefügt oder aktualisiert wurde **SQLBulkOperations** oder mit aktualisierten **SQLSetPos**.|  
|22003|Numerischer Wert außerhalb des gültigen Bereichs|Die Daten, die für einen gebundenen numerische Parameter gesendet oder Spalte verursacht des gesamten (im Gegensatz zu Bruch) Teils der Zahl abgeschnitten wird, wenn der zugeordnete Tabellenspalte zugewiesen.<br /><br /> Einen numerischen Wert (als numerisch oder Zeichenfolge) für einen oder mehrere Eingabe-/Ausgabe- oder Ausgabe-Parameter zurückgegeben würde den gesamten (im Gegensatz zu Bruch) Teil der Zahl abgeschnitten wird verursacht.|  
|22007|Ungültiges Datetime-format|Die Daten für einen Parameter oder eine Spalte, die auf ein Datum, Uhrzeit oder Zeitstempel-Struktur gebunden wurde gesendet wurde, ein ungültiges Datum, Uhrzeit oder Zeitstempel.<br /><br /> Ein Eingabe-/Ausgabe- oder Ausgabe-Parameter gebunden wurde ein Datum, Uhrzeit oder Zeitstempel C-Struktur, und ein Wert in der zurückgegebenen Parameter war, jeweils ein ungültiges Datum, Uhrzeit oder Zeitstempel. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|22008|Überlauf im DateTime-Feld|Ein Datetime-Ausdruck berechnet, für die Eingabe/Ausgabe oder Ausgabeparameter führte dazu, dass ein Datum, Uhrzeit oder Zeitstempel C-Struktur, die ungültig war.|  
|22012|Division durch 0 (null)|Ein arithmetischer Ausdruck berechnet, für die Eingabe/Ausgabe oder Ausgabeparameter führte Division durch 0 (null).|  
|22015|Überlauf bei Intervallfeld|Die Daten, die für eine genaue numerische oder Intervall gesendet werden oder Parameter, um ein Intervall SQL-Datentyp hat ein Verlust signifikanter Ziffern.<br /><br /> Daten für eine Interval-Spalte oder Parameter mit mehr als ein Feld gesendet wurde, wurde in einen numerischen Datentyp konvertiert, und wurden bisher keine Darstellung des numerischen Datentyps.<br /><br /> Die Daten, die gesendet werden, für die Spalte oder den Parameterdaten wurde ein Intervall von SQL-Typ zugewiesen, und gab es keine Darstellung des Werts von der C-Typ in der SQL-Typ-Intervall.<br /><br /> Die für ein genauer numerischer Wert oder Intervall C-Spalte oder Parameter für den Intervalltyp C gesendeten Daten verursacht einen Verlust signifikanter Ziffern.<br /><br /> Die Daten, die gesendet werden, für die Spalte oder Parameterdaten eine C-Intervall-Struktur zugewiesen wurde, und gab es keine Entsprechung für die Daten in der Datenstruktur Intervall.|  
|22018|Ungültiger Zeichenwert für Konvertierungsangabe|Der C-Typ war eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp. der SQL-Typ der Spalte konnte einen Zeichendatentyp; und kein Wert in der Spalte oder Parameter wurde ein gültiger Literal des gebundenen Typen aus C#.<br /><br /> Der SQL-Typ war eine genaue oder ungefähre numerische, einen datetime-Wert oder ein Intervall-Datentyp. der C-Typ wurde SQL_C_CHAR; und kein Wert in der Spalte oder Parameter wurde ein gültiger Literal des gebundenen Typen aus SQL.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY009|Ungültige Verwendung eines null-Zeiger|(DM) das Argument *DataPtr* wurde ein null-Zeiger ist, und das Argument *StrLen_or_Ind* war nicht 0 (null) SQL_DEFAULT_PARAM oder SQL_NULL_DATA.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) der vorherigen Funktionsaufruf war keinem Aufruf von **SQLPutData** oder **SQLParamData**.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Diese asynchronen Funktion wurde noch ausgeführt werden, wenn die SQLPutData-Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY019|Nicht-Zeichendaten und nicht binäre Daten wurden in Einzelteilen versandt|**SQLPutData** war aufgerufen mehr als einmal für einen Parameter oder eine Spalte, und es war nicht verwendet wird, zum Senden von Zeichendaten C an eine Spalte mit einem Zeichen oder den binären datenquellenspezifische Datentyp oder zum Senden von Binärdaten C an eine Spalte mit einem Zeichen , Binär- oder Data Source-spezifische-Datentyp.|  
|HY020|Versucht, einen null-Wert zu verketten.|**SQLPutData** mehr als einmal aufgerufen wurde, seit dem Aufruf, der SQL_NEED_DATA zurückgegeben, und klicken Sie in einem dieser Aufrufe, die *StrLen_or_Ind* Argument enthalten, SQL_NULL_DATA oder SQL_DEFAULT_PARAM.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|Das Argument *DataPtr* war nicht, ein null-Zeiger ist, und das Argument *StrLen_or_Ind* war kleiner als 0, aber nicht gleich SQL_NTS lauten oder SQL_NULL_DATA.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
 Wenn **SQLPutData** wird aufgerufen, beim Senden von Daten für einen Parameter in einer SQL­Anweisung, jeder SQLSTATE, die von der Funktion wird aufgerufen, um die Ausführung der Anweisung zurückgegeben werden kann zurückgegeben werden kann (**SQLExecute** oder **SQLExecDirect**). Wenn sie, beim Senden von Daten für eine Spalte aufgerufen wird, die aktualisiert oder hinzugefügt, die mit **SQLBulkOperations** oder aktualisiert wird **SQLSetPos**, alle SQLSTATE zurückgegeben werden kann, die zurückgegeben werden kann  **SQLBulkOperations** oder **SQLSetPos**.  
  
## <a name="comments"></a>Kommentare  
 **SQLPutData** aufgerufen werden, um das Bereitstellen von Data-at-Execution-Daten für zwei Zwecke: Parameterdaten in einem Aufruf verwendet werden **SQLExecute** oder **SQLExecDirect**, oder die Spaltendaten verwendet werden, wenn eine Zeile aktualisiert wird oder durch einen Aufruf von hinzugefügt **SQLBulkOperations** oder aktualisiert wird, durch einen Aufruf von **SQLSetPos**.  
  
 Wenn eine Anwendung ruft **SQLParamData** um zu bestimmen, welche Daten es sollte zu senden, gibt der Treiber einen Indikator, die die Anwendung verwenden kann, um zu bestimmen, welche die zu sendenden Parameterdaten oder, in dem Daten der Spalte gefunden werden. Sie gibt überdies SQL_NEED_DATA zurückgegeben, die ein Indikator dafür, dass die Anwendung ist, die sie aufrufen, sollten **SQLPutData** zum Senden der Daten. In der *DataPtr* Argument **SQLPutData**, die Anwendung übergibt einen Zeiger auf den Puffer, die die tatsächlichen Daten für den Parameter oder die Spalte enthält.  
  
 Wenn der Treiber gibt SQL_SUCCESS zurück, für die **SQLPutData**, die Anwendung ruft **SQLParamData** erneut aus. **SQLParamData** gibt SQL_NEED_DATA zurück, wenn weitere Daten gesendet werden, müssen in diesem Fall wird die Anwendung ruft **SQLPutData** erneut aus. Es gibt SQL_SUCCESS zurück, wenn alle Data-at-Execution-Daten gesendet wurde. Die Anwendung ruft dann **SQLParamData** erneut aus. Wenn der Treiber SQL_NEED_DATA zurückgegeben und ein anderer Indikator in zurückgibt  *\*ValuePtrPtr*, Daten für einen anderen Parameter oder eine Spalte erforderlich und **SQLPutData** erneut aufgerufen wird. Wenn der Treiber SQL_SUCCESS, klicken Sie dann alle Data-at-Execution gibt-Daten gesendet wurde, und die SQL-Anweisung kann ausgeführt werden oder die **SQLBulkOperations** oder **SQLSetPos** Aufruf verarbeitet werden kann.  
  
 Weitere Informationen zu wie Data-at-Execution-Parameterdaten zur Ausführungszeit für die Anweisung übergeben wird, finden Sie unter "Übergeben von Parameterwerten" in [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) und [Senden von Long-Daten](../../../odbc/reference/develop-app/sending-long-data.md). Weitere Informationen zu wie Data-at-Execution-Spalte aktualisiert oder hinzugefügt wird, finden Sie im Abschnitt "Verwenden von SQLSetPos" in [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), "Ausführen von Massenladen Updates mithilfe von Lesezeichen" in [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), und [Long-Daten, SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
> [!NOTE]  
>  Eine Anwendung kann mithilfe **SQLPutData** zum Senden von Daten in Teile nur beim Senden von Zeichendaten C an eine Spalte mit einem Zeichen oder den binären datenquellenspezifische Datentyp oder beim Senden von Binärdaten C an eine Spalte mit einem Zeichen, binär, oder Daten datenquellenspezifische-Datentyp. Wenn **SQLPutData** wird aufgerufen, mehr als einmal unter anderen Bedingungen gibt SQL_ERROR zurück, und SQLSTATE HY019 (nicht-Zeichendaten und nicht binäre Daten wurden in Einzelteilen gesendet).  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird vorausgesetzt, Name der Datenquelle namens Test. Die zugeordnete Datenbank sollte es sich um eine Tabelle verfügen, die Sie, wie folgt erstellen können:  
  
```  
CREATE TABLE emp4 (NAME char(30), AGE int, BIRTHDAY datetime, Memo1 text)  
```  
  
```  
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
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer, an einen parameter|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Ausführen einer SQL­Anweisung|[SQLExecDirect-Funktion](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Ausführen einer vorbereiteten SQL­Anweisung|[SQLExecute-Funktion](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Den nächsten Parameter zum Senden von Daten für die Rückgabe|[SQLParamData-Funktion](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
