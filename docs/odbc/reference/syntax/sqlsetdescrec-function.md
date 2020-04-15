---
title: SQLSetDescRec-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetDescRec
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescRec
helpviewer_keywords:
- SQLSetDescRec function [ODBC]
ms.assetid: bf55256c-7eb7-4e3f-97ef-b0fee09ba829
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b29879ff7635d6eb7d5a0f7489ff3994758d4a35
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299530"
---
# <a name="sqlsetdescrec-function"></a>SQLSetDescRec-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 Die **SQLSetDescRec-Funktion** legt mehrere Deskriptorfelder fest, die sich auf den Datentyp und Puffer auswirken, die an eine Spalte oder Parameterdaten gebunden sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLSetDescRec(  
      SQLHDESC      DescriptorHandle,  
      SQLSMALLINT   RecNumber,  
      SQLSMALLINT   Type,  
      SQLSMALLINT   SubType,  
      SQLLEN        Length,  
      SQLSMALLINT   Precision,  
      SQLSMALLINT   Scale,  
      SQLPOINTER    DataPtr,  
      SQLLEN *      StringLengthPtr,  
      SQLLEN *      IndicatorPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *DescriptorHandle*  
 [Eingabe] Deskriptor-Handle. Dies darf kein IRD-Handle sein.  
  
 *RecNumber*  
 [Eingabe] Gibt den Deskriptordatensatz an, der die festzulegenden Felder enthält. Deskriptordatensätze werden von 0 nummeriert, wobei Datensatznummer 0 der Lesezeichendatensatz ist. Dieses Argument muss gleich oder größer als 0 sein. Wenn *RecNumber* größer als der Wert von SQL_DESC_COUNT ist, SQL_DESC_COUNTis in den Wert von *RecNumber*geändert.  
  
 *Typ*  
 [Eingabe] Der Wert, für den das feld SQL_DESC_TYPE für den Deskriptordatensatz festgelegt werden soll.  
  
 *Untertyp*  
 [Eingabe] Bei Datensätzen, deren Typ SQL_DATETIME oder SQL_INTERVAL ist, ist dies der Wert, auf den das Feld SQL_DESC_DATETIME_INTERVAL_CODE festgelegt werden soll.  
  
 *Länge*  
 [Eingabe] Der Wert, für den das Feld SQL_DESC_OCTET_LENGTH für den Deskriptordatensatz festgelegt werden soll.  
  
 *Genauigkeit*  
 [Eingabe] Der Wert, für den das Feld SQL_DESC_PRECISION für den Deskriptordatensatz festgelegt werden soll.  
  
 *Skalieren*  
 [Eingabe] Der Wert, für den das Feld SQL_DESC_SCALE für den Deskriptordatensatz festgelegt werden soll.  
  
 *DataPtr*  
 [Verzögerte Eingabe oder Ausgabe] Der Wert, für den das Feld SQL_DESC_DATA_PTR für den Deskriptordatensatz festgelegt werden soll. *DataPtr* kann auf einen Nullzeiger gesetzt werden.  
  
 Das *DataPtr-Argument* kann auf einen Nullzeiger festgelegt werden, um das SQL_DESC_DATA_PTR Feld auf einen Nullzeiger festzulegen. Wenn das Handle im *DescriptorHandle-Argument* einer ARD zugeordnet ist, wird die Bindung der Spalte aufgehoben.  
  
 *StringLengthPtr*  
 [Verzögerte Eingabe oder Ausgabe] Der Wert, für den das SQL_DESC_OCTET_LENGTH_PTR Feld für den Deskriptordatensatz festgelegt werden soll. *StringLengthPtr* kann auf einen Nullzeiger gesetzt werden, um das SQL_DESC_OCTET_LENGTH_PTR Feld auf einen Nullzeiger festzulegen.  
  
 *IndikatorPtr*  
 [Verzögerte Eingabe oder Ausgabe] Der Wert, für den das Feld SQL_DESC_INDICATOR_PTR für den Deskriptordatensatz festgelegt werden soll. *IndicatorPtr* kann auf einen Nullzeiger gesetzt werden, um das SQL_DESC_INDICATOR_PTR Feld auf einen Nullzeiger festzulegen.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetDescRec** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DESC und einem *Handle* von *DescriptorHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLSetDescRec** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger Deskriptorindex|Das *RecNumber-Argument* wurde auf 0 gesetzt, und *descriptorHandle* bezieht sich auf ein IPD-Handle.<br /><br /> Das *RecNumber-Argument* war kleiner als 0.<br /><br /> Das *RecNumber-Argument* war größer als die maximale Anzahl von Spalten oder Parametern, die die Datenquelle unterstützen kann, und das *DescriptorHandle-Argument* war eine APD, IPD oder ARD.<br /><br /> Das *RecNumber-Argument* war gleich 0, und das *DescriptorHandle-Argument* bezog sich auf eine implizit zugewiesene APD. (Dieser Fehler tritt bei einem explizit zugewiesenen Anwendungsdeskriptor nicht auf, da nicht bekannt ist, ob ein explizit zugewiesener Anwendungsdeskriptor bis zur Ausführung smuss eine APD oder ARD ist.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY010|Funktionssequenzfehler|(DM) Das *DescriptorHandle* wurde einem *StatementHandle* zugeordnet, für den eine asynchron ausführende Funktion (nicht diese) aufgerufen wurde und immer noch ausgeführt wurde, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen, dem das *DescriptorHandle* zugeordnet wurde und SQL_NEED_DATA zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) Für das Verbindungshandle, das dem *DescriptorHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLSetDescRec-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für eines der Anweisungshandles aufgerufen, die dem *DescriptorHandle* zugeordnet sind, und zurückgegebenSQL_PARAM_DATA_AVAILABLE. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY016|Eine Implementierungszeilenbeschreibung kann nicht geändert werden.|Das *DescriptorHandle-Argument* wurde einem IRD zugeordnet.|  
|HY021|Inkonsistente Deskriptorinformationen|Das *Feld Typ* oder ein anderes Feld, das dem feld SQL_DESC_TYPE im Deskriptor zugeordnet ist, war ungültig oder konsistent.<br /><br /> Die bei einer Konsistenzprüfung überprüften Deskriptorinformationen waren nicht konsistent. (Siehe "Konsistenzprüfungen", weiter unten in diesem Abschnitt.)|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) Der Treiber war ein ODBC *2.x-Treiber,* der Deskriptor war eine ARD, das *ColumnNumber-Argument* wurde auf 0 gesetzt, und der für das Argument *BufferLength* angegebene Wert war nicht gleich 4.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der treiber, der dem *DescriptorHandle* zugeordnet ist, unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung kann **SQLSetDescRec** aufrufen, um die folgenden Felder für eine einzelne Spalte oder einen Parameter festzulegen:  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (für Datensätze, deren Typ SQL_DATETIME oder SQL_INTERVAL ist)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_DATA_PTR  
  
-   SQL_DESC_OCTET_LENGTH_PTR  
  
-   SQL_DESC_INDICATOR_PTR  
  
> [!NOTE]  
>  Wenn ein Aufruf von **SQLSetDescRec** fehlschlägt, ist der Inhalt des Deskriptordatensatzes, der durch das *RecNumber-Argument* identifiziert wird, nicht definiert.  
  
 Beim Binden einer Spalte oder eines Parameters können Sie mit **SQLSetDescRec** mehrere Felder ändern, die die Bindung beeinflussen, ohne **SQLBindCol** oder **SQLBindParameter** aufzurufen oder mehrere Aufrufe von **SQLSetDescField**zu tätigen. **SQLSetDescRec** kann Felder für einen Deskriptor festlegen, der derzeit keiner Anweisung zugeordnet ist. Beachten Sie, dass **SQLBindParameter** mehr Felder als **SQLSetDescRec**festlegt, Felder für eine APD und eine IPD in einem Aufruf festlegen kann und kein Deskriptorhandle erfordert.  
  
> [!NOTE]  
>  Das Anweisungsattribut SQL_ATTR_USE_BOOKMARKS sollte immer festgelegt werden, bevor **SQLSetDescRec** mit dem *RecNumber-Argument* 0 aufgerufen wird, um Lesezeichenfelder festzulegen. Dies ist zwar nicht obligatorisch, wird jedoch dringend empfohlen.  
  
## <a name="consistency-checks"></a>Konsistenzprüfungen  
 Eine Konsistenzprüfung wird vom Treiber automatisch durchgeführt, wenn eine Anwendung das SQL_DESC_DATA_PTR Feld einer APD, ARD oder IPD festlegt. Wenn eines der Felder nicht mit anderen Feldern übereinstimmt, gibt **SQLSetDescRec** SQLSTATE HY021 (Inkonsistente Deskriptorinformationen) zurück.  
  
 Wenn eine Anwendung das SQL_DESC_DATA_PTR Feld einer APD, ARD oder IPD festlegt, überprüft der Treiber, ob der Wert des SQL_DESC_TYPE Feldes und die auf dieses SQL_DESC_TYPE Feld anwendbaren Werte gültig und konsistent sind. Diese Prüfung wird immer dann durchgeführt, wenn **SQLBindParameter** oder **SQLBindCol** aufgerufen wird oder wenn **SQLSetDescRec** für eine APD, ARD oder IPD aufgerufen wird. Diese Konsistenzprüfung umfasst die folgenden Prüfungen für Deskriptorfelder:  
  
-   Das Feld SQL_DESC_TYPE muss einer der gültigen ODBC C- oder SQL-Typen oder ein treiberspezifischer SQL-Typ sein. Das Feld SQL_DESC_CONCISE_TYPE muss einer der gültigen ODBC-C- oder SQL-Typen oder ein treiberspezifischer C- oder SQL-Typ sein, einschließlich der präzisen Datums- und Intervalltypen.  
  
-   Wenn das SQL_DESC_TYPE Datensatzfeld SQL_DATETIME oder SQL_INTERVAL ist, muss das SQL_DESC_DATETIME_INTERVAL_CODE Feld einer der gültigen Datumszeit- oder Intervallcodes sein. (Siehe beschreibung des SQL_DESC_DATETIME_INTERVAL_CODE Feldes in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
-   Wenn das Feld SQL_DESC_TYPE einen numerischen Typ angibt, werden die Felder SQL_DESC_PRECISION und SQL_DESC_SCALE als gültig überprüft.  
  
-   Wenn es sich bei dem SQL_DESC_CONCISE_TYPE Feld um einen Zeit- oder Zeitstempeldatentyp, einen Intervalltyp mit einer Sekundenkomponente oder einen der Intervalldatentypen mit einer Zeitkomponente handelt, wird das Feld SQL_DESC_PRECISION als gültige Sekundengenauigkeit überprüft.  
  
-   Wenn es sich bei der SQL_DESC_CONCISE_TYPE um einen Intervalldatentyp handelt, wird das Feld SQL_DESC_DATETIME_INTERVAL_PRECISION als gültiger Intervallführender Genauigkeitswert überprüft.  
  
 Das SQL_DESC_DATA_PTR Feld einer IPD wird normalerweise nicht festgelegt. Eine Anwendung kann dies jedoch tun, um eine Konsistenzprüfung von IPD-Feldern zu erzwingen. Eine Konsistenzprüfung kann für eine IRD nicht durchgeführt werden. Der Wert, auf den das SQL_DESC_DATA_PTR Feld der IPD festgelegt ist, wird nicht gespeichert und kann nicht durch einen Aufruf von **SQLGetDescField** oder **SQLGetDescRec**abgerufen werden. die Einstellung wird nur vorgenommen, um die Konsistenzprüfung zu erzwingen.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden einer Spalte|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Binden eines Parameters|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Abrufen eines einzelnen Deskriptorfelds|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Abrufen mehrerer Deskriptorfelder|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen einzelner Deskriptorfelder|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
