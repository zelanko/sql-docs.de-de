---
title: SQLSetDescRec-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetDescRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescRec
helpviewer_keywords:
- SQLSetDescRec function [ODBC]
ms.assetid: bf55256c-7eb7-4e3f-97ef-b0fee09ba829
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f76974a17fc12c4a72623c133586690c81269d06
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536275"
---
# <a name="sqlsetdescrec-function"></a>SQLSetDescRec-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 Die **SQLSetDescRec** -Funktion legt fest, mehrere deskriptorfelder, die den Datentyp auswirken und Puffer, der an eine Spalte oder Parameter Daten gebunden.  
  
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
 [Eingabe] Deskriptorhandles. Dies muss ein Handle IRD nicht sein.  
  
 *RecNumber*  
 [Eingabe] Gibt an, den anwendungsparameterdeskriptor-Datensatz, der die Felder, festgelegt werden, enthält. Deskriptordatensätze sind von 0 (null) mit der Datensatznummer lesezeichendatensatzes wird 0 nummeriert. Dieses Argument muss gleich oder größer als 0 sein. Wenn *RecNumber* ist größer als der Wert des SQL_DESC_COUNT, geändert wird, auf den Wert der SQL_DESC_COUNTis *RecNumber*.  
  
 *Typ*  
 [Eingabe] Der Wert, der das SQL_DESC_TYPE-Feld für den anwendungsparameterdeskriptor-Datensatz festgelegt.  
  
 *SubType*  
 [Eingabe] Für Datensätze vom Typ SQL_DATETIME oder SQL_INTERVAL hat, ist dies der Wert, auf das Feld SQL_DESC_DATETIME_INTERVAL_CODE festgelegt.  
  
 *Länge*  
 [Eingabe] Der Wert, auf das SQL_DESC_OCTET_LENGTH-Feld für den anwendungsparameterdeskriptor-Datensatz festgelegt.  
  
 *Genauigkeit*  
 [Eingabe] Der Wert, auf das SQL_DESC_PRECISION-Feld für den anwendungsparameterdeskriptor-Datensatz festgelegt.  
  
 *Dezimalstellen*  
 [Eingabe] Der Wert, auf das SQL_DESC_SCALE-Feld für den anwendungsparameterdeskriptor-Datensatz festgelegt.  
  
 *DataPtr*  
 [Verzögerte Eingabe oder Ausgabe] Der Wert, der das SQL_DESC_DATA_PTR-Feld für den anwendungsparameterdeskriptor-Datensatz festgelegt. *DataPtr* kann auf einen null-Zeiger festgelegt werden.  
  
 Die *DataPtr* Argument kann auf einen null-Zeiger festgelegt werden, um das SQL_DESC_DATA_PTR-Feld auf einen null-Zeiger festgelegt. Wenn das Handle in die *DescriptorHandle* Argument ein ARD zugeordnet ist, wird dies hebt die Bindung der Spalte.  
  
 *StringLengthPtr*  
 [Verzögerte Eingabe oder Ausgabe] Der Wert, auf das Feld SQL_DESC_OCTET_LENGTH_PTR für den anwendungsparameterdeskriptor-Datensatz festgelegt. *StringLengthPtr* kann auf ein null-Zeiger festgelegt werden, um das SQL_DESC_OCTET_LENGTH_PTR-Feld auf einen null-Zeiger festgelegt.  
  
 *IndicatorPtr*  
 [Verzögerte Eingabe oder Ausgabe] Der Wert, auf das SQL_DESC_INDICATOR_PTR-Feld für den anwendungsparameterdeskriptor-Datensatz festgelegt. *IndicatorPtr* kann auf einen null-Zeiger festgelegt werden, um das SQL_DESC_INDICATOR_PTR-Feld auf einen null-Zeiger festgelegt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetDescRec** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_ HANDLE_DESC und *behandeln* von *DescriptorHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLSetDescRec** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger Deskriptorindex|Die *RecNumber* -Argument wurde auf 0 (null) festgelegt und die *DescriptorHandle* bezeichnet ein IPD-Handle.<br /><br /> Die *RecNumber* Argument war kleiner als 0.<br /><br /> Die *RecNumber* Argument war größer als die maximale Anzahl von Spalten oder Parametern, die die Datenquelle unterstützt werden, und die *DescriptorHandle* Argument war ein APD IPD oder ARD.<br /><br /> Die *RecNumber* Argument war gleich 0 (null) und die *DescriptorHandle* Argument ein implizit zugewiesene APD bezeichnet. (Dieser Fehler tritt nicht mit einem explizit zugewiesene Anwendungsdienst-Deskriptor da nicht bekannt ist, ob ein explizit zugewiesene Anwendungsdienst-Deskriptor einer APD oder ARD erst einmal ausführen.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) die *DescriptorHandle* zugeordnet wurde eine *StatementHandle* für den eine asynchron ausgeführte Funktion (diese keiner) aufgerufen wurde, und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* mit dem die *DescriptorHandle* verknüpft und SQL_NEED_DATA zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *DescriptorHandle*. Diese Funktion Aynchronous war immer noch ausgeführt, wenn die **SQLSetDescRec** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** für eines der zugeordneten Anweisungshandles aufgerufen wurde die *DescriptorHandle* und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY016|Ein Implementierungszeilendeskriptor kann nicht geändert werden.|Die *DescriptorHandle* Argument wurde ein IRD zugeordnet.|  
|HY021|Inkonsistente deskriptorinformation|Die *Typ* Feld oder jedes andere Feld, das SQL_DESC_TYPE-Feld in der Deskriptor zugeordnet war nicht gültig oder konsistent.<br /><br /> Informationen der Sicherheitsbeschreibung, die während einer konsistenzprüfung eingecheckt war nicht konsistent. (Siehe "Konsistenzprüfungen," weiter unten in diesem Abschnitt.)|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM) der Treiber wurde von einer ODBC 2. *.x* -Treiber der Deskriptor wurde ein ARD, die *ColumnNumber* -Argument wurde auf 0 und dem Wert des Arguments festgelegt *Pufferlänge* wurde nicht gleich 4.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *DescriptorHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Kann eine Anwendung aufrufen **SQLSetDescRec** die folgenden Felder für eine einzelne Spalte oder Parameter festlegen:  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (für Datensätze vom Typ SQL_DATETIME oder SQL_INTERVAL hat)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_DATA_PTR  
  
-   SQL_DESC_OCTET_LENGTH_PTR  
  
-   SQL_DESC_INDICATOR_PTR  
  
> [!NOTE]  
>  Wenn ein Aufruf von **SQLSetDescRec** ein Fehler auftritt, wird der Inhalt der Deskriptordatensatz identifizierte die *RecNumber* Argument sind nicht definiert.  
  
 Beim Binden einer Spalte oder eines Parameters **SQLSetDescRec** können Sie mehrere Felder, die Auswirkungen auf die Bindung ohne ändern **SQLBindCol** oder **SQLBindParameter** oder mehrere Aufrufe an **SQLSetDescField**. **SQLSetDescRec** können Felder auf einen Deskriptor, der derzeit nicht mit einer Anweisung verknüpften festlegen. Beachten Sie, dass **SQLBindParameter** legt mehr Felder als **SQLSetDescRec**Felder kann festgelegt werden, auf eine APD und einem IPD in einem einzigen Aufruf und eine Deskriptorhandles ist nicht erforderlich.  
  
> [!NOTE]  
>  Das Anweisungsattribut SQL_ATTR_USE_BOOKMARKS sollte immer festgelegt werden, bevor **SQLSetDescRec** mit einem *RecNumber* Argument von 0 Lesezeichen Felder festlegen. Obwohl dies nicht erforderlich ist, wird dringend empfohlen.  
  
## <a name="consistency-checks"></a>Konsistenzprüfungen  
 Eine konsistenzprüfung wird automatisch vom Treiber ausgeführt, wenn eine Anwendung das SQL_DESC_DATA_PTR-Feld eines APD, ARD oder IPD festlegt. Wenn eines der Felder stimmt nicht mit anderen Feldern, **SQLSetDescRec** SQLSTATE HY021 zurück (inkonsistente Deskriptorinformationen).  
  
 Wenn eine Anwendung das SQL_DESC_DATA_PTR-Feld eines APD, ARD oder IPD festlegt, der Treiber überprüft, ob der Wert das SQL_DESC_TYPE-Feld und die Werte für das SQL_DESC_TYPE-Feld sind gültig und konsistent. Diese Überprüfung wird immer ausgeführt, wenn **SQLBindParameter** oder **SQLBindCol** aufgerufen wird oder wenn **SQLSetDescRec** ein APD ARD oder IPD aufgerufen wird. Diese konsistenzprüfung umfasst die folgenden Prüfungen auf deskriptorfelder:  
  
-   Das SQL_DESC_TYPE-Feld muss eine gültige ODBC-C oder SQL-Typen oder ein Treiber-spezifische SQL-Typ sein. Das Feld "SQL_DESC_CONCISE_TYPE" muss die gültigen Typen von ODBC-C "oder" SQL "oder" treiberspezifische C oder SQL ein, einschließlich der präzisen Datetime "und" Interval-Typen sein.  
  
-   Wenn das SQL_DESC_TYPE-Datensatzfeld SQL_DATETIME oder SQL_INTERVAL hat, muss das Feld "SQL_DESC_DATETIME_INTERVAL_CODE" ein gültiger DateTime-Wert oder Intervall Codes sein. (Siehe die Beschreibung des Felds SQL_DESC_DATETIME_INTERVAL_CODE in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
-   Wenn das SQL_DESC_TYPE-Feld einen numerischen Typ angibt, werden die Felder SQL_DESC_PRECISION und SQL_DESC_SCALE überprüft, gültig ist.  
  
-   Wenn das Feld "SQL_DESC_CONCISE_TYPE" eine Uhrzeit oder Zeitstempel-Datentyp ist, ein Intervall Geben Sie mit einer Komponente für Sekunden oder eines der Interval-Datentypen, mit der Zeitangabe, Feld SQL_DESC_PRECISION wird überprüft, eine gültige Genauigkeit sein.  
  
-   Ist die SQL_DESC_CONCISE_TYPE ein Intervall-Datentyp, wird das Feld "SQL_DESC_DATETIME_INTERVAL_PRECISION" überprüft, um einen gültigen Intervalls führende Genauigkeitswert handeln.  
  
 Das SQL_DESC_DATA_PTR-Feld von einem IPD ist normalerweise nicht festgelegt. Allerdings kann eine Anwendung durchführen, um eine konsistenzprüfung des IPD-Feldern zu erzwingen können. Eine konsistenzprüfung kann nicht auf eine IRD ausgeführt werden. Der Wert, der das SQL_DESC_DATA_PTR-Feld des IPD festgelegt ist, werden nicht tatsächlich gespeichert und kann nicht abgerufen werden, durch einen Aufruf von **SQLGetDescField** oder **SQLGetDescRec**; die Einstellung erfolgt nur für das Erzwingen der die konsistenzprüfung.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden eine Spalte|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ein Parameter gebunden|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Abrufen einer einzelnen Deskriptorfeld|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Abrufen von deskriptorfelder für mehrere|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen von einzelnen deskriptorfeldern|[SQLSetDescField-Funktion](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
