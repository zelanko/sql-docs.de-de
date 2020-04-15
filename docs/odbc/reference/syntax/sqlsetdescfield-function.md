---
title: SQLSetDescField-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetDescField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescField
helpviewer_keywords:
- SQLSetDescField function [ODBC]
ms.assetid: 8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 122d4b26d1d75811d4a8e252378ce8f81ca2c66b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299550"
---
# <a name="sqlsetdescfield-function"></a>SQLSetDescField-Funktion

**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLSetDescField** legt den Wert eines einzelnen Feldes eines Deskriptordatensatzes fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SQLRETURN SQLSetDescField(  
     SQLHDESC      DescriptorHandle,  
     SQLSMALLINT   RecNumber,  
     SQLSMALLINT   FieldIdentifier,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    BufferLength);  
```  
  
## <a name="arguments"></a>Argumente  
 *DescriptorHandle*  
 [Eingabe] Deskriptor-Handle.  
  
 *RecNumber*  
 [Eingabe] Gibt den Deskriptordatensatz an, der das Feld enthält, das die Anwendung festlegen möchte. Deskriptordatensätze werden von 0 nummeriert, wobei Datensatznummer 0 der Lesezeichendatensatz ist. Das *RecNumber-Argument* wird für Headerfelder ignoriert.  
  
 *FieldIdentifier*  
 [Eingabe] Gibt das Feld des Deskriptors an, dessen Wert festgelegt werden soll. Weitere Informationen finden Sie unter *"FieldIdentifier* Argument" im Abschnitt "Kommentare".  
  
 *ValuePtr*  
 [Eingabe] Zeiger auf einen Puffer, der die Deskriptorinformationen oder einen Ganzzahlwert enthält. Der Datentyp hängt vom Wert von *FieldIdentifier ab.* Wenn *ValuePtr* ein Ganzzahlwert ist, kann er je nach Wert des *FieldIdentifier-Arguments* als 8 Bytes (SQLLEN), 4 Bytes (SQLINTEGER) oder 2 Bytes (SQLSMALLINT) betrachtet werden.  
  
 *BufferLength*  
 [Eingabe] Wenn *FieldIdentifier* ein ODBC-definiertes Feld ist und *ValuePtr* auf eine Zeichenfolge oder einen Binärpuffer verweist, sollte dieses Argument die Länge von **ValuePtr*sein. Bei Zeichenfolgendaten sollte dieses Argument die Anzahl der Bytes in der Zeichenfolge enthalten.  
  
 Wenn *FieldIdentifier* ein ODBC-definiertes Feld und *ValuePtr* eine ganze Zahl ist, wird *BufferLength* ignoriert.  
  
 Wenn *FieldIdentifier* ein vom Treiber definiertes Feld ist, gibt die Anwendung die Art des Felds für den Treiber-Manager an, indem das *Argument BufferLength* festgelegt wird. *BufferLength* kann die folgenden Werte haben:  
  
-   Wenn *ValuePtr* ein Zeiger auf eine Zeichenfolge ist, ist *BufferLength* die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn *ValuePtr* ein Zeiger auf einen Binärpuffer ist, platziert die Anwendung das Ergebnis des*SQL_LEN_BINARY_ATTR(Länge*) Makros in *BufferLength*. Dadurch wird ein negativer Wert in *BufferLength*platziert.  
  
-   Wenn *ValuePtr* ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine Binärzeichenfolge ist, sollte *BufferLength* den Wert SQL_IS_POINTER haben.  
  
-   Wenn *ValuePtr* einen Wert mit fester Länge enthält, wird *BufferLength* entweder SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT oder SQL_IS_USMALLINT.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetDescField** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DESC und einem *Handle* von *DescriptorHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLSetDescField** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Der Treiber unterstützte nicht den in * \*ValuePtr* angegebenen Wert (wenn *ValuePtr* ein Zeiger war) oder den Wert in *ValuePtr* (wenn *ValuePtr* ein ganzzahliger Wert war), oder * \*ValuePtr* war aufgrund von Implementierungsarbeitsbedingungen ungültig, sodass der Treiber einen ähnlichen Wert ersetzte. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger Deskriptorindex|Das *FieldIdentifier-Argument* war ein Datensatzfeld, das *RecNumber-Argument* war 0, und das *DescriptorHandle-Argument* verweist auf ein IPD-Handle.<br /><br /> Das *RecNumber-Argument* war kleiner als 0, und das *DescriptorHandle-Argument* bezog sich auf eine ARD oder eine APD.<br /><br /> Das *RecNumber-Argument* war größer als die maximale Anzahl von Spalten oder Parametern, die von der Datenquelle unterstützt werden können, und das *DescriptorHandle-Argument* bezieht sich auf eine APD oder ARD.<br /><br /> (DM) Das *FieldIdentifier-Argument* wurde SQL_DESC_COUNT, und * \*das ValuePtr-Argument* war kleiner als 0.<br /><br /> Das *RecNumber-Argument* war gleich 0, und das *DescriptorHandle-Argument* bezog sich auf eine implizit zugewiesene APD. (Dieser Fehler tritt bei einem explizit zugewiesenen Anwendungsdeskriptor nicht auf, da nicht bekannt ist, ob ein explizit zugewiesener Anwendungsdeskriptor bis zur Ausführung s. B. eine APD oder ARD ist.)|  
|08S01|Kommunikationsverbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Verarbeitung abgeschlossen wurde.|  
|22001|String-Daten, rechts abgeschnitten|Das *FieldIdentifier-Argument* wurde SQL_DESC_NAME, und das *BufferLength-Argument* war ein Wert größer als SQL_MAX_IDENTIFIER_LEN.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText-Puffer* zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY010|Funktionssequenzfehler|(DM) Das *DescriptorHandle* wurde einem *StatementHandle* zugeordnet, für den eine asynchron ausführende Funktion (nicht diese) aufgerufen wurde und immer noch ausgeführt wurde, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen, dem das *DescriptorHandle* zugeordnet wurde und SQL_NEED_DATA zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) Für das Verbindungshandle, das dem *DescriptorHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLSetDescField-Funktion** aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für eines der Anweisungshandles aufgerufen, die dem *DescriptorHandle* zugeordnet sind, und zurückgegebenSQL_PARAM_DATA_AVAILABLE. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY016|Eine Implementierungszeilenbeschreibung kann nicht geändert werden.|Das *DescriptorHandle-Argument* wurde einem IRD zugeordnet, und das *FieldIdentifier-Argument* wurde nicht SQL_DESC_ARRAY_STATUS_PTR oder SQL_DESC_ROWS_PROCESSED_PTR.|  
|HY021|Inkonsistente Deskriptorinformationen|Die Felder SQL_DESC_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE bilden keinen gültigen ODBC SQL-Typ oder einen gültigen treiberspezifischen SQL-Typ (für IPDs) oder einen gültigen ODBC C-Typ (für APDs oder ARDs).<br /><br /> Die bei einer Konsistenzprüfung überprüften Deskriptorinformationen waren nicht konsistent. (Siehe "Konsistenzprüfung" in **SQLSetDescRec**.)|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) * \*ValuePtr* ist eine Zeichenfolge, und *BufferLength* war kleiner als Null, aber nicht gleich SQL_NTS.<br /><br /> (DM) Der Treiber war ein ODBC 2 *.x-Treiber,* der Deskriptor war eine ARD, das *ColumnNumber-Argument* wurde auf 0 gesetzt, und der für das Argument *BufferLength* angegebene Wert war nicht gleich 4.|  
|HY091|Ungültiger Deskriptorfeldbezeichner|Der für das *FieldIdentifier-Argument* angegebene Wert war kein ODBC-definiertes Feld und kein implementierungsdefinierter Wert.<br /><br /> Das *FieldIdentifier-Argument* war für das *DescriptorHandle-Argument* ungültig.<br /><br /> Das *FieldIdentifier-Argument* war ein schreibgeschütztes, ODBC-definiertes Feld.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|Der Wert in * \*ValuePtr* war für das *FieldIdentifier-Argument* ungültig.<br /><br /> Das *FieldIdentifier-Argument* wurde SQL_DESC_UNNAMED, und *ValuePtr* wurde SQL_NAMED.|  
|HY105|Ungültiger Parametertyp|(DM) Der für das Feld SQL_DESC_PARAMETER_TYPE angegebene Wert war ungültig. (Weitere Informationen finden Sie im Abschnitt "*InputOutputType* Argument" in **SQLBindParameter**.)|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie [unter Was ist neu in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der treiber, der dem *DescriptorHandle* zugeordnet ist, unterstützt die Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung kann **SQLSetDescField** aufrufen, um ein beliebiges Deskriptorfeld nach einander festzulegen. Ein Aufruf von **SQLSetDescField** legt ein einzelnes Feld in einem einzelnen Deskriptor fest. Diese Funktion kann aufgerufen werden, um ein beliebiges Feld in einem beliebigen Deskriptortyp festzulegen, vorausgesetzt, das Feld kann festgelegt werden. (Siehe die Tabelle weiter unten in diesem Abschnitt.)  
  
> [!NOTE]  
>  Wenn ein Aufruf von **SQLSetDescField** fehlschlägt, ist der Inhalt des Deskriptordatensatzes, der durch das *RecNumber-Argument* identifiziert wird, nicht definiert.  
  
 Andere Funktionen können aufgerufen werden, um mehrere Deskriptorfelder mit einem einzelnen Aufruf der Funktion festzulegen. Die **SQLSetDescRec-Funktion** legt eine Vielzahl von Feldern fest, die sich auf den Datentyp und Puffer auswirken, die an eine Spalte oder einen Parameter gebunden sind (die Felder SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_DATA_PTR, SQL_DESC_OCTET_LENGTH_PTR und SQL_DESC_INDICATOR_PTR). **SQLBindCol** oder **SQLBindParameter** können verwendet werden, um eine vollständige Spezifikation für die Bindung einer Spalte oder eines Parameters zu erstellen. Diese Funktionen legen eine bestimmte Gruppe von Deskriptorfeldern mit einem Funktionsaufruf fest.  
  
 **SQLSetDescField** kann aufgerufen werden, um die Bindungspuffer zu ändern, indem den Bindungszeigern (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR oder SQL_DESC_OCTET_LENGTH_PTR) ein Offset hinzugefügt wird. Dadurch werden die Bindungspuffer geändert, ohne **SQLBindCol** oder **SQLBindParameter**aufzurufen, wodurch eine Anwendung SQL_DESC_DATA_PTR ändern kann, ohne andere Felder zu ändern, z. B. SQL_DESC_DATA_TYPE.  
  
 Wenn eine Anwendung **SQLSetDescField** aufruft, um ein anderes Feld als SQL_DESC_COUNT oder die verzögerten Felder SQL_DESC_DATA_PTR, SQL_DESC_OCTET_LENGTH_PTR oder SQL_DESC_INDICATOR_PTR festzulegen, wird der Datensatz ungebunden.  
  
 Descriptor-Headerfelder werden festgelegt, indem **SQLSetDescField** mit dem entsprechenden *FieldIdentifier*aufgerufen wird. Viele Headerfelder sind auch Anweisungsattribute, sodass sie auch durch einen Aufruf von **SQLSetStmtAttr**festgelegt werden können. Auf diese Weise können Anwendungen ein Deskriptorfeld festlegen, ohne zuvor ein Deskriptor-Handle zu erhalten. Wenn **SQLSetDescField** aufgerufen wird, um ein Headerfeld festzulegen, wird das *RecNumber-Argument* ignoriert.  
  
 Eine *RecNumber* von 0 wird verwendet, um Lesezeichenfelder festzulegen.  
  
> [!NOTE]  
>  Das Anweisungsattribut SQL_ATTR_USE_BOOKMARKS sollte immer festgelegt werden, bevor **SQLSetDescField** aufgerufen wird, um Lesezeichenfelder festzulegen. Dies ist zwar nicht obligatorisch, wird jedoch dringend empfohlen.  
  
## <a name="sequence-of-setting-descriptor-fields"></a>Sequenz der Einstellungsdeskriptorfelder  
 Beim Festlegen von Deskriptorfeldern durch Aufrufen von **SQLSetDescField**muss die Anwendung einer bestimmten Sequenz folgen:  
  
1.  Die Anwendung muss zuerst das Feld SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE oder SQL_DESC_DATETIME_INTERVAL_CODE festlegen.  
  
2.  Nachdem eines dieser Felder festgelegt wurde, kann die Anwendung ein Attribut eines Datentyps festlegen, und der Treiber legt Datentypattributfelder auf die entsprechenden Standardwerte für den Datentyp fest. Die automatische Standardeinstellung von Typattributfeldern stellt sicher, dass der Deskriptor immer einsatzbereit ist, sobald die Anwendung einen Datentyp angegeben hat. Wenn die Anwendung explizit ein Datentypattribut festlegt, überschreibt sie das Standardattribut.  
  
3.  Nachdem eines der in Schritt 1 aufgeführten Felder festgelegt und Datentypattribute festgelegt wurden, kann die Anwendung SQL_DESC_DATA_PTR festlegen. Dadurch wird eine Konsistenzprüfung der Deskriptorfelder veranlasst. Wenn die Anwendung den Datentyp oder die Attribute ändert, nachdem sie das Feld SQL_DESC_DATA_PTR festgelegt hat, legt der Treiber SQL_DESC_DATA_PTR auf einen Nullzeiger fest, wodurch die Bindung des Datensatzes aufgehoben wird. Dadurch wird die Anwendung dazu zwingt, die richtigen Schritte nacheinander auszuführen, bevor der Deskriptordatensatz verwendet werden kann.  
  
## <a name="initialization-of-descriptor-fields"></a>Initialisierung der Deskriptorfelder  
 Wenn ein Deskriptor zugewiesen wird, können die Felder im Deskriptor auf einen Standardwert initialisiert, ohne Standardwert initialisiert oder für den Deskriptortyp nicht definiert werden. Die folgenden Tabellen geben die Initialisierung jedes Feldes für jeden Deskriptortyp an, wobei "D" angibt, dass das Feld mit einem Standard initialisiert wird, und "ND", das angibt, dass das Feld ohne Standard initialisiert wird. Wenn eine Zahl angezeigt wird, ist der Standardwert des Felds diese Zahl. Die Tabellen geben auch an, ob ein Feld lese/geschrieben (R/W) oder schreibgeschützt (R) ist.  
  
 Die Felder eines IRD haben erst einen Standardwert, nachdem die Anweisung vorbereitet oder ausgeführt wurde und die IRD aufgefüllt wurde, nicht, wenn das Anweisungshandle oder der Deskriptor zugewiesen wurde. Bis die IRD aufgefüllt ist, wird bei jedem Versuch, Zugriff auf ein Feld einer IRD zu erhalten, ein Fehler zurückgegeben.  
  
 Einige Deskriptorfelder sind für einen oder mehrere, aber nicht alle Deskriptortypen (ARDs und IRDs sowie APDs und IPDs) definiert. Wenn ein Feld für einen Deskriptortyp nicht definiert ist, wird es von keiner der Funktionen benötigt, die diesen Deskriptor verwenden.  
  
 Die Felder, auf die **SQLGetDescField** zugreifen kann, können nicht unbedingt von **SQLSetDescField**festgelegt werden. Felder, die von **SQLSetDescField** festgelegt werden können, sind in den folgenden Tabellen aufgeführt.  
  
 Die Initialisierung von Kopfzeilenfeldern wird in der folgenden Tabelle beschrieben.  
  
|Headerfeldname|type|R/W|Standard|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_ALLOC_TYPE|SQLSMALLINT|ARD: R APD: R IRD: R IPD: R|ARD: SQL_DESC_ALLOC_AUTO für implizite oder SQL_DESC_ALLOC_USER für explizite<br /><br /> APD: SQL_DESC_ALLOC_AUTO für implizite oder SQL_DESC_ALLOC_USER für explizite<br /><br /> IRD: SQL_DESC_ALLOC_AUTO<br /><br /> IPD: SQL_DESC_ALLOC_AUTO|  
|SQL_DESC_ARRAY_SIZE|SQLULEN|ARD: R/W APD: R/W IRD: Unused IPD: Unused|ARD:[1] APD:[1] IRD: Unused IPD: Unused|  
|SQL_DESC_ARRAY_STATUS_PTR|SQLUSMALLINT*|ARD: R/W APD: R/W IRD: R/W IPD: R/W|ARD: Null ptr APD: Null ptr IRD: Null ptr IPD: Null ptr|  
|SQL_DESC_BIND_OFFSET_PTR|SQLLEN*|ARD: R/W APD: R/W IRD: Unused IPD: Unused|ARD: Null ptr APD: Null ptr IRD: Unused IPD: Unused|  
|SQL_DESC_BIND_TYPE|SQLINTEGER|ARD: R/W APD: R/W IRD: Unused IPD: Unused|ARD: SQL_BIND_BY_COLUMN<br /><br /> APD: SQL_BIND_BY_COLUMN<br /><br /> IRD: Nicht verwendet<br /><br /> IPD: Nicht verwendet|  
|SQL_DESC_COUNT|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: 0 APD: 0 IRD: D IPD: 0|  
|SQL_DESC_ROWS_PROCESSED_PTR|SQLULEN*|ARD: Unbenutzte APD: Unbenutzte IRD: R/W IPD: R/W|ARD: Unused APD: Unused IRD: Null ptr IPD: Null ptr|  
  
 [1] Diese Felder werden nur definiert, wenn die IPD automatisch vom Treiber aufgefüllt wird. Wenn nicht, sind sie nicht definiert. Wenn eine Anwendung versucht, diese Felder festzulegen, wird SQLSTATE HY091 (Invalid descriptor field identifier) zurückgegeben.  
  
 Die Initialisierung von Datensatzfeldern ist wie in der folgenden Tabelle dargestellt.  
  
|Datensatzfeldname|type|R/W|Standard|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|ARD: Unused APD: Unused IRD: R IPD: Unused|ARD: Unused APD: Unused IRD: D IPD: Unused|  
|SQL_DESC_BASE_COLUMN_NAME|SQLCHAR *|ARD: Unused APD: Unused IRD: R IPD: Unused|ARD: Unused APD: Unused IRD: D IPD: Unused|  
|SQL_DESC_BASE_TABLE_NAME|SQLCHAR *|ARD: Unused APD: Unused IRD: R IPD: Unused|ARD: Unused APD: Unused IRD: D IPD: Unused|  
|SQL_DESC_CASE_SENSITIVE|SQLINTEGER|ARD: Unbenutzte APD: Unbenutzte IRD: R IPD: R|ARD: Unbenutzte APD: Unbenutzte IRD: D IPD: D[1]|  
|SQL_DESC_CATALOG_NAME|SQLCHAR *|ARD: Unused APD: Unused IRD: R IPD: Unused|ARD: Unused APD: Unused IRD: D IPD: Unused|  
|SQL_DESC_CONCISE_TYPE|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: SQL_C_ DEFAULT APD: SQL_C_ DEFAULT IRD: D IPD: ND|  
|SQL_DESC_DATA_PTR|SQLPOINTER|ARD: R/W APD: R/W IRD: Unused IPD: Unused|ARD: Null ptr APD: Null ptr IRD: Unused IPD: Unused[2]|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQLINTEGER|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_DISPLAY_SIZE|SQLLEN|ARD: Unused APD: Unused IRD: R IPD: Unused|ARD: Unused APD: Unused IRD: D IPD: Unused|  
|SQL_DESC_FIXED_PREC_SCALE|SQLSMALLINT|ARD: Unbenutzte APD: Unbenutzte IRD: R IPD: R|ARD: Unbenutzte APD: Unbenutzte IRD: D IPD: D[1]|  
|SQL_DESC_INDICATOR_PTR|SQLLEN *|ARD: R/W APD: R/W IRD: Unused IPD: Unused|ARD: Null ptr APD: Null ptr IRD: Unused IPD: Unused|  
|SQL_DESC_LABEL|SQLCHAR *|ARD: Unused APD: Unused IRD: R IPD: Unused|ARD: Unused APD: Unused IRD: D IPD: Unused|  
|SQL_DESC_LENGTH|SQLULEN|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_LITERAL_PREFIX|SQLCHAR *|ARD: Unused APD: Unused IRD: R IPD: Unused|ARD: Unused APD: Unused IRD: D IPD: Unused|  
|SQL_DESC_LITERAL_SUFFIX|SQLCHAR *|ARD: Unused APD: Unused IRD: R IPD: Unused|ARD: Unused APD: Unused IRD: D IPD: Unused|  
|SQL_DESC_LOCAL_TYPE_NAME|SQLCHAR *|ARD: Unbenutzte APD: Unbenutzte IRD: R IPD: R|ARD: Unbenutzte APD: Unbenutzte IRD: D IPD: D[1]|  
|SQL_DESC_NAME|SQLCHAR *|ARD: Unbenutzte APD: Unbenutzte IRD: R IPD: R/W|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_NULLABLE|SQLSMALLINT|ARD: Unbenutzte APD: Unbenutzte IRD: R IPD: R|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_NUM_PREC_RADIX|SQLINTEGER|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_OCTET_LENGTH|SQLLEN|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_OCTET_LENGTH_PTR|SQLLEN *|ARD: R/W APD: R/W IRD: Unused IPD: Unused|ARD: Null ptr APD: Null ptr IRD: Unused IPD: Unused|  
|SQL_DESC_PARAMETER_TYPE|SQLSMALLINT|ARD: Unbenutzte APD: Unbenutzte IRD: Unbenutzte IPD: R/W|ARD: Unused APD: Unused IRD: Unused IPD: D=SQL_PARAM_INPUT|  
|SQL_DESC_PRECISION|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_ROWVER|SQLSMALLINT|ARD: Ungenutzt<br /><br /> APD: Nicht verwendet<br /><br /> IRD: R<br /><br /> IPD: R|ARD: Ungenutzt<br /><br /> APD: Nicht verwendet<br /><br /> IRD: ND<br /><br /> IPD: ND|  
|SQL_DESC_SCALE|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_SCHEMA_NAME|SQLCHAR *|ARD: Unused APD: Unused IRD: R IPD: Unused|ARD: Unused APD: Unused IRD: D IPD: Unused|  
|SQL_DESC_SEARCHABLE|SQLSMALLINT|ARD: Unused APD: Unused IRD: R IPD: Unused|ARD: Unused APD: Unused IRD: D IPD: Unused|  
|SQL_DESC_TABLE_NAME|SQLCHAR *|ARD: Unused APD: Unused IRD: R IPD: Unused|ARD: Unused APD: Unused IRD: D IPD: Unused|  
|SQL_DESC_TYPE|SQLSMALLINT|ARD: R/W APD: R/W IRD: R IPD: R/W|ARD: SQL_C_DEFAULT APD: SQL_C_DEFAULT IRD: D IPD: ND|  
|SQL_DESC_TYPE_NAME|SQLCHAR *|ARD: Unbenutzte APD: Unbenutzte IRD: R IPD: R|ARD: Unbenutzte APD: Unbenutzte IRD: D IPD: D[1]|  
|SQL_DESC_UNNAMED|SQLSMALLINT|ARD: Unbenutzte APD: Unbenutzte IRD: R IPD: R/W|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_UNSIGNED|SQLSMALLINT|ARD: Unbenutzte APD: Unbenutzte IRD: R IPD: R|ARD: Unbenutzte APD: Unbenutzte IRD: D IPD: D[1]|  
|SQL_DESC_UPDATABLE|SQLSMALLINT|ARD: Unused APD: Unused IRD: R IPD: Unused|ARD: Unused APD: Unused IRD: D IPD: Unused|  
  
 [1] Diese Felder werden nur definiert, wenn die IPD automatisch vom Treiber aufgefüllt wird. Wenn nicht, sind sie nicht definiert. Wenn eine Anwendung versucht, diese Felder festzulegen, wird SQLSTATE HY091 (Invalid descriptor field identifier) zurückgegeben.  
  
 [2] Das SQL_DESC_DATA_PTR Feld in der IPD kann so eingestellt werden, dass eine Konsistenzprüfung erzwingt wird. Bei einem nachfolgenden Aufruf von **SQLGetDescField** oder **SQLGetDescRec**ist der Treiber nicht erforderlich, um den Wert zurückzugeben, auf den SQL_DESC_DATA_PTR festgelegt wurde.  
  
## <a name="fieldidentifier-argument"></a>FieldIdentifier-Argument  
 Das *FieldIdentifier-Argument* gibt das festzulegende Deskriptorfeld an. Ein Deskriptor enthält den *Deskriptorheader,* der aus den im nächsten Abschnitt "Headerfeldern" beschriebenen Headerfeldern und null oder mehr *Deskriptordatensätzen besteht,* die aus den Datensatzfeldern bestehen, die im Abschnitt nach dem Abschnitt "Headerfelder" beschrieben werden.  
  
## <a name="header-fields"></a>Headerfelder  
 Jeder Deskriptor verfügt über einen Header, der aus den folgenden Feldern besteht:  
  
 **SQL_DESC_ALLOC_TYPE [Alle]**  
 Dieses schreibgeschützte SQLSMALLINT-Headerfeld gibt an, ob der Deskriptor automatisch vom Treiber oder explizit von der Anwendung zugewiesen wurde. Die Anwendung kann dieses Feld abrufen, aber nicht ändern. Das Feld wird vom Treiber auf SQL_DESC_ALLOC_AUTO festgelegt, wenn der Deskriptor automatisch vom Treiber zugewiesen wurde. Sie wird vom Treiber auf SQL_DESC_ALLOC_USER festgelegt, wenn der Deskriptor explizit von der Anwendung zugewiesen wurde.  
  
 **SQL_DESC_ARRAY_SIZE [Anwendungsdeskriptoren]**  
 In ARDs gibt dieses SQLULEN-Headerfeld die Anzahl der Zeilen im Rowset an. Dies ist die Anzahl der Zeilen, die von einem Aufruf von **SQLFetch** oder **SQLFetchScroll** zurückgegeben oder durch einen Aufruf von **SQLBulkOperations** oder **SQLSetPos**betrieben werden sollen.  
  
 In APDs gibt dieses SQLULEN-Headerfeld die Anzahl der Werte für jeden Parameter an.  
  
 Der Standardwert dieses Feldes ist 1. Wenn SQL_DESC_ARRAY_SIZE größer als 1 ist, zeigen SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR der APD oder ARD auf Arrays. Die Kardinalität jedes Arrays ist gleich dem Wert dieses Felds.  
  
 Dieses Feld in der ARD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem Attribut SQL_ATTR_ROW_ARRAY_SIZE eingestellt werden. Dieses Feld in der APD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem Attribut SQL_ATTR_PARAMSET_SIZE festgelegt werden.  
  
 **SQL_DESC_ARRAY_STATUS_PTR [Alle]**  
 Für jeden Deskriptortyp verweist dieses SQLUSMALLINT *-Headerfeld auf ein Array von SQLUSMALLINT-Werten. Diese Arrays werden wie folgt benannt: Zeilenstatusarray (IRD), Parameterstatusarray (IPD), Row Operation Array (ARD) und Parameteroperation Array (APD).  
  
 In der IRD verweist dieses Headerfeld auf ein Zeilenstatusarray, das Statuswerte nach einem Aufruf von **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos**enthält. Das Array hat so viele Elemente wie Zeilen im Rowset. Die Anwendung muss ein Array von SQLUSMALLINTs zuweisen und dieses Feld so festlegen, dass es auf das Array abgibt. Das Feld wird standardmäßig auf einen Nullzeiger festgelegt. Der Treiber füllt das Array aus, es sei denn, das Feld SQL_DESC_ARRAY_STATUS_PTR wird auf einen Nullzeiger festgelegt, in diesem Fall werden keine Statuswerte generiert und das Array wird nicht aufgefüllt.  
  
> [!CAUTION]  
>  Das Treiberverhalten ist nicht definiert, wenn die Anwendung die Elemente des Zeilenstatusarrays festlegt, auf das durch das feld SQL_DESC_ARRAY_STATUS_PTR der IRD verwiesen wird.  
  
 Das Array wird zunächst durch einen Aufruf von **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos**aufgefüllt. Wenn der Aufruf nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben wurde, ist der Inhalt des Arrays, auf das durch dieses Feld verwiesen wird, nicht definiert. Die Elemente im Array können die folgenden Werte enthalten:  
  
-   SQL_ROW_SUCCESS: Die Zeile wurde erfolgreich abgerufen und hat sich seit dem letzten Abruf nicht geändert.  
  
-   SQL_ROW_SUCCESS_WITH_INFO: Die Zeile wurde erfolgreich abgerufen und hat sich seit dem letzten Abruf nicht geändert. Es wurde jedoch eine Warnung über die Zeile zurückgegeben.  
  
-   SQL_ROW_ERROR: Beim Abrufen der Zeile ist ein Fehler aufgetreten.  
  
-   SQL_ROW_UPDATED: Die Zeile wurde erfolgreich abgerufen und seit dem letzten Abruf aktualisiert. Wenn die Zeile erneut abgerufen wird, wird ihr Status SQL_ROW_SUCCESS.  
  
-   SQL_ROW_DELETED: Die Zeile wurde gelöscht, seit sie zuletzt abgerufen wurde.  
  
-   SQL_ROW_ADDED: Die Zeile wurde von **SQLBulkOperations**eingefügt. Wenn die Zeile erneut abgerufen wird, wird ihr Status SQL_ROW_SUCCESS.  
  
-   SQL_ROW_NOROW: Das Rowset überlappte das Ende des Resultsets, und es wurde keine Zeile zurückgegeben, die diesem Element des Zeilenstatusarrays entsprach.  
  
 Dieses Feld im IRD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem Attribut SQL_ATTR_ROW_STATUS_PTR festgelegt werden.  
  
 Das SQL_DESC_ARRAY_STATUS_PTR Feld des IRD ist erst gültig, nachdem SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben wurde. Wenn der Rückgabecode nicht einer dieser Codes ist, ist die Position, auf die SQL_DESC_ROWS_PROCESSED_PTR zeigt, nicht definiert.  
  
 In der IPD verweist dieses Headerfeld auf ein Parameterstatusarray, das Statusinformationen für jeden Satz von Parameterwerten nach einem Aufruf von **SQLExecute** oder **SQLExecDirect**enthält. Wenn der Aufruf von **SQLExecute** oder **SQLExecDirect** keine SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben hat, ist der Inhalt des Arrays, auf das durch dieses Feld verwiesen wird, nicht definiert. Die Anwendung muss ein Array von SQLUSMALLINTs zuweisen und dieses Feld so festlegen, dass es auf das Array abgibt. Der Treiber füllt das Array aus, es sei denn, das Feld SQL_DESC_ARRAY_STATUS_PTR wird auf einen Nullzeiger festgelegt, in diesem Fall werden keine Statuswerte generiert und das Array wird nicht aufgefüllt. Die Elemente im Array können die folgenden Werte enthalten:  
  
-   SQL_PARAM_SUCCESS: Die SQL-Anweisung wurde für diesen Satz von Parametern erfolgreich ausgeführt.  
  
-   SQL_PARAM_SUCCESS_WITH_INFO: Die SQL-Anweisung wurde für diesen Satz von Parametern erfolgreich ausgeführt. In der Diagnosedatenstruktur sind jedoch Warninformationen verfügbar.  
  
-   SQL_PARAM_ERROR: Bei der Verarbeitung dieses Parameterssatzes ist ein Fehler aufgetreten. Zusätzliche Fehlerinformationen finden Sie in der Diagnosedatenstruktur.  
  
-   SQL_PARAM_UNUSED: Dieser Parametersatz wurde nicht verwendet, möglicherweise aufgrund der Tatsache, dass ein vorheriger Parametersatz einen Fehler verursachte, der die weitere Verarbeitung abbrach, oder weil SQL_PARAM_IGNORE für diesen Satz von Parametern im Array festgelegt wurde, der durch das SQL_DESC_ARRAY_STATUS_PTR Feld der APD angegeben wurde.  
  
-   SQL_PARAM_DIAG_UNAVAILABLE: Diagnoseinformationen sind nicht verfügbar. Ein Beispiel hierfür ist, wenn der Treiber Arrays von Parametern als monolithische Einheit behandelt und daher diese Fehlerstufe nicht generiert.  
  
 Dieses Feld in der IPD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem Attribut SQL_ATTR_PARAM_STATUS_PTR festgelegt werden.  
  
 In der ARD zeigt dieses Headerfeld auf ein Zeilenoperationarray von Werten, die von der Anwendung festgelegt werden können, um anzugeben, ob diese Zeile für **SQLSetPos-Vorgänge** ignoriert werden soll. Die Elemente im Array können die folgenden Werte enthalten:  
  
-   SQL_ROW_PROCEED: Die Zeile wird im Massenvorgang mit **SQLSetPos**enthalten sein. (Diese Einstellung garantiert nicht, dass der Vorgang in der Zeile ausgeführt wird. Wenn die Zeile den Status SQL_ROW_ERROR im IRD-Zeilenstatusarray hat, kann der Treiber den Vorgang in der Zeile möglicherweise nicht ausführen.)  
  
-   SQL_ROW_IGNORE: Die Zeile wird vom Massenvorgang mit **SQLSetPos**ausgeschlossen.  
  
 Wenn keine Elemente des Arrays festgelegt sind, werden alle Zeilen in den Massenvorgang einbezogen. Wenn der Wert im feld SQL_DESC_ARRAY_STATUS_PTR der ARD ein Nullzeiger ist, werden alle Zeilen in den Massenvorgang einbezogen. Die Interpretation ist die gleiche, als ob der Zeiger auf ein gültiges Array zeigte und alle Elemente des Arrays SQL_ROW_PROCEED wurden. Wenn ein Element im Array auf SQL_ROW_IGNORE festgelegt ist, wird der Wert im Zeilenstatusarray für die ignorierte Zeile nicht geändert.  
  
 Dieses Feld in der ARD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem Attribut SQL_ATTR_ROW_OPERATION_PTR eingestellt werden.  
  
 In der APD zeigt dieses Headerfeld auf ein Parameter-Operation-Array von Werten, die von der Anwendung festgelegt werden können, um anzugeben, ob dieser Satz von Parametern ignoriert werden soll, wenn **SQLExecute** oder **SQLExecDirect** aufgerufen wird. Die Elemente im Array können die folgenden Werte enthalten:  
  
-   SQL_PARAM_PROCEED: Der Satz von Parametern ist im **SQLExecute-** oder **SQLExecDirect-Aufruf** enthalten.  
  
-   SQL_PARAM_IGNORE: Der Satz von Parametern wird vom **SQLExecute-** oder **SQLExecDirect-Aufruf** ausgeschlossen.  
  
 Wenn keine Elemente des Arrays festgelegt sind, werden alle Parametersätze im Array in den **SQLExecute-** oder **SQLExecDirect-Aufrufen** verwendet. Wenn der Wert im SQL_DESC_ARRAY_STATUS_PTR Feld der APD ein Nullzeiger ist, werden alle Parametersätze verwendet. Die Interpretation ist die gleiche, als ob der Zeiger auf ein gültiges Array zeigte und alle Elemente des Arrays SQL_PARAM_PROCEED wurden.  
  
 Dieses Feld in der APD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem Attribut SQL_ATTR_PARAM_OPERATION_PTR festgelegt werden.  
  
 **SQL_DESC_BIND_OFFSET_PTR [Anwendungsdeskriptoren]**  
 Dieses SQLLEN *-Headerfeld zeigt auf den Bindungsoffset. Er wird standardmäßig auf einen Nullzeiger festgelegt. Wenn dieses Feld kein Nullzeiger ist, verweist der Treiber den Zeiger und fügt den dereferenzierten Wert zu jedem der zurückgestellten Felder hinzu, die einen Nicht-Null-Wert im Deskriptordatensatz (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR) beim Abrufen aufweisen, und verwendet die neuen Zeigerwerte bei der Bindung.  
  
 Der Bindungsoffset wird immer direkt zu den Werten in den Feldern SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR hinzugefügt. Wenn der Offset in einen anderen Wert geändert wird, wird der neue Wert weiterhin direkt zum Wert in jedem Deskriptorfeld hinzugefügt. Der neue Offset wird nicht zum Feldwert plus einem früheren Offset hinzugefügt.  
  
 Dieses Feld ist ein *verzögertes Feld:* Es wird nicht zum Zeitpunkt der Festlegung verwendet, sondern zu einem späteren Zeitpunkt vom Treiber verwendet, wenn er Adressen für Datenpuffer ermitteln muss.  
  
 Dieses Feld in der ARD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem Attribut SQL_ATTR_ROW_BIND_OFFSET_PTR eingestellt werden. Dieses Feld in der ARD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem Attribut SQL_ATTR_PARAM_BIND_OFFSET_PTR eingestellt werden.  
  
 Weitere Informationen finden Sie in der Beschreibung der zeilenweisen Bindung in [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) und [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 **SQL_DESC_BIND_TYPE [Anwendungsdeskriptoren]**  
 Dieses SQLUINTEGER-Headerfeld legt die Bindungsausrichtung fest, die zum Binden von Spalten oder Parametern verwendet werden soll.  
  
 In ARDs gibt dieses Feld die Bindungsausrichtung an, wenn **SQLFetchScroll** oder **SQLFetch** für das zugeordnete Anweisungshandle aufgerufen wird.  
  
 Um die spaltenweise Bindung für Spalten auszuwählen, wird dieses Feld auf SQL_BIND_BY_COLUMN (Standardeinstellung) festgelegt.  
  
 Dieses Feld in der ARD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_ROW_BIND_TYPE *Attribut*festgelegt werden.  
  
 In APDs gibt dieses Feld die Bindungsausrichtung an, die für dynamische Parameter verwendet werden soll.  
  
 Um die spaltenweise Bindung für Parameter auszuwählen, wird dieses Feld auf SQL_BIND_BY_COLUMN (Standardeinstellung) festgelegt.  
  
 Dieses Feld in der APD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_PARAM_BIND_TYPE *Attribut*festgelegt werden.  
  
 **SQL_DESC_COUNT [Alle]**  
 Dieses SQLSMALLINT-Headerfeld gibt den 1-basierten Index des Datensatzes mit der höchsten Nummer an, der Daten enthält. Wenn der Treiber die Datenstruktur für den Deskriptor festlegt, muss er auch das Feld SQL_DESC_COUNT festlegen, um anzuzeigen, wie viele Datensätze signifikant sind. Wenn eine Anwendung eine Instanz dieser Datenstruktur zuweist, muss sie nicht angeben, für wie viele Datensätze reserviert werden sollen. Da die Anwendung den Inhalt der Datensätze angibt, ergreift der Treiber alle erforderlichen Maßnahmen, um sicherzustellen, dass das Deskriptorhandle auf eine Datenstruktur in der entsprechenden Größe verweist.  
  
 SQL_DESC_COUNT ist nicht die Anzahl aller Datenspalten, die gebunden sind (wenn das Feld in einer ARD ist) oder aller Parameter, die gebunden sind (wenn sich das Feld in einer APD befindet), sondern die Nummer des Datensatzes mit der höchsten Nummer. Wenn die Spalte oder der Parameter mit der höchsten Nummer ungebunden ist, wird SQL_DESC_COUNT in die Nummer der nächsten Spalte oder des nächsten Parameters mit der höchsten Nummer geändert. Wenn eine Spalte oder ein Parameter mit einer Zahl, die kleiner als die Nummer der Spalte mit der höchsten Nummer ist, ungebunden ist (durch Aufrufen von **SQLBindCol** mit dem *TargetValuePtr-Argument,* das auf einen Nullzeiger festgelegt ist, oder **SQLBindParameter** mit dem *Argument ParameterValuePtr,* das auf einen Nullzeiger festgelegt ist), wird SQL_DESC_COUNT nicht geändert. Wenn zusätzliche Spalten oder Parameter mit Zahlen gebunden sind, die größer sind als der Datensatz mit der höchsten Nummer, der Daten enthält, erhöht der Treiber automatisch den Wert im Feld SQL_DESC_COUNT. Wenn alle Spalten durch Aufrufen von **SQLFreeStmt** mit der Option SQL_UNBIND ungebunden sind, werden die SQL_DESC_COUNT Felder in ARD und IRD auf 0 gesetzt. Wenn **SQLFreeStmt** mit der Option SQL_RESET_PARAMS aufgerufen wird, werden die SQL_DESC_COUNT Felder in APD und IPD auf 0 gesetzt.  
  
 Der Wert in SQL_DESC_COUNT kann von einer Anwendung explizit festgelegt werden, indem **SQLSetDescField**aufgerufen wird. Wenn der Wert in SQL_DESC_COUNT explizit verringert wird, werden alle Datensätze mit Zahlen entfernt, die größer als der neue Wert in SQL_DESC_COUNT sind. Wenn der Wert in SQL_DESC_COUNT explizit auf 0 festgelegt ist und sich das Feld in einer ARD befindet, werden alle Datenpuffer mit Ausnahme einer gebundenen Lesezeichenspalte freigegeben.  
  
 Die Datensatzanzahl in diesem Bereich einer ARD enthält keine gebundene Lesezeichenspalte. Die einzige Möglichkeit, die Bindung einer Lesezeichenspalte zu heben, besteht darin, das Feld SQL_DESC_DATA_PTR auf einen Nullzeiger festzulegen.  
  
 **SQL_DESC_ROWS_PROCESSED_PTR [Implementierungsdeskriptoren]**  
 In einer IRD verweist \* dieses SQLULEN-Headerfeld auf einen Puffer, der die Anzahl der Zeilen enthält, die nach einem Aufruf von **SQLFetch** oder **SQLFetchScroll**abgerufen wurden, oder auf die Anzahl der Zeilen, die bei einem Massenvorgang betroffen sind, der von einem Aufruf von **SQLBulkOperations** oder **SQLSetPos**ausgeführt wird, einschließlich Fehlerzeilen.  
  
 In einer IPD zeigt dieses SQLUINTEGER *-Headerfeld auf einen Puffer, der die Anzahl der verarbeiteten Parametersätze enthält, einschließlich Fehlersätzen. Keine Zahl wird zurückgegeben, wenn es sich um einen Nullzeiger handelt.  
  
 SQL_DESC_ROWS_PROCESSED_PTR ist erst gültig, nachdem SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO nach einem Aufruf von **SQLFetch** oder **SQLFetchScroll** (für ein IRD-Feld) oder **SQLExecute**, **SQLExecDirect**oder **SQLParamData** (für ein IPD-Feld) zurückgegeben wurde. Wenn der Aufruf, auf den der Puffer mit diesem Feld zeigt, nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgibt, ist der Inhalt des Puffers nicht definiert, es sei denn, er gibt SQL_NO_DATA zurück, in diesem Fall wird der Wert im Puffer auf 0 gesetzt.  
  
 Dieses Feld in der ARD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem Attribut SQL_ATTR_ROWS_FETCHED_PTR eingestellt werden. Dieses Feld in der APD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem Attribut SQL_ATTR_PARAMS_PROCESSED_PTR festgelegt werden.  
  
 Der Puffer, auf den dieses Feld zeigt, wird von der Anwendung zugewiesen. Es handelt sich um einen verzögerten Ausgabepuffer, der vom Treiber festgelegt wird. Er wird standardmäßig auf einen Nullzeiger festgelegt.  
  
## <a name="record-fields"></a>Record Fields  
 Jeder Deskriptor enthält einen oder mehrere Datensätze, die aus Feldern bestehen, die je nach Deskriptortyp entweder Spaltendaten oder dynamische Parameter definieren. Jeder Datensatz ist eine vollständige Definition einer einzelnen Spalte oder eines einzelnen Parameters.  
  
 **SQL_DESC_AUTO_UNIQUE_VALUE [IRDs]**  
 Dieses schreibgeschützte SQLINTEGER-Datensatzfeld enthält SQL_TRUE, wenn es sich bei der Spalte um eine Spalte mit automatischer Inkrementellierung handelt, oder SQL_FALSE, wenn es sich bei der Spalte nicht um eine Spalte mit automatischer Inkrementelle Spalte handelt. Dieses Feld ist schreibgeschützt, aber die zugrunde liegende Spalte für die automatische Inkrementelle Ist nicht notwendigerweise schreibgeschützt.  
  
 **SQL_DESC_BASE_COLUMN_NAME [IRDs]**  
 Dieses schreibgeschützte SQLCHAR * Datensatzfeld enthält den Basisspaltennamen für die Ergebnissatzspalte. Wenn kein Basisspaltenname vorhanden ist (wie bei Spalten, die Ausdrücke sind), enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_BASE_TABLE_NAME [IRDs]**  
 Dieses schreibgeschützte SQLCHAR * Datensatzfeld enthält den Basistabellennamen für die Ergebnissatzspalte. Wenn ein Basistabellenname nicht definiert werden kann oder nicht anwendbar ist, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_CASE_SENSITIVE [Implementierungsdeskriptoren]**  
 Dieses schreibgeschützte SQLINTEGER-Datensatzfeld enthält SQL_TRUE, wenn die Spalte oder der Parameter bei Sortierungen und Vergleichen als Groß-/Kleinschreibung behandelt wird oder SQL_FALSE wenn die Spalte bei Sortierungen und Vergleichen nicht als Groß-/Kleinschreibung behandelt wird oder wenn es sich um eine Nichtzeichenspalte handelt.  
  
 **SQL_DESC_CATALOG_NAME [IRDs]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatzfeld enthält den Katalog für die Basistabelle, die die Spalte enthält. Der Rückgabewert ist treiberabhängig, wenn es sich bei der Spalte um einen Ausdruck handelt oder wenn die Spalte Teil einer Ansicht ist. Wenn die Datenquelle keine Kataloge unterstützt oder der Katalog nicht bestimmt werden kann, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_CONCISE_TYPE [Alle]**  
 Dieses SQLSMALLINT-Headerfeld gibt den präzisen Datentyp für alle Datentypen an, einschließlich der Datums- und Intervalldatentypen.  
  
 Die Werte in den Feldern SQL_DESC_CONCISE_TYPE, SQL_DESC_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE sind voneinander abhängig. Jedes Mal, wenn eines der Felder festgelegt wird, muss auch das andere festgelegt werden. SQL_DESC_CONCISE_TYPE kann durch einen Aufruf von **SQLBindCol** oder **SQLBindParameter**oder **SQLSetDescField**festgelegt werden. SQL_DESC_TYPE kann durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**festgelegt werden.  
  
 Wenn SQL_DESC_CONCISE_TYPE auf einen anderen kurzen Datentyp als einen Intervall- oder Datumszeitdatentyp festgelegt ist, wird das Feld SQL_DESC_TYPE auf denselben Wert und das Feld SQL_DESC_DATETIME_INTERVAL_CODE auf 0 festgelegt.  
  
 Wenn SQL_DESC_CONCISE_TYPE auf den datengenauen Datums- oder Intervalldatentyp festgelegt ist, wird das Feld SQL_DESC_TYPE auf den entsprechenden ausführlichen Typ (SQL_DATETIME oder SQL_INTERVAL) und das Feld SQL_DESC_DATETIME_INTERVAL_CODE auf den entsprechenden Untercode festgelegt.  
  
 **SQL_DESC_DATA_PTR [Anwendungsdeskriptoren und IPDs]**  
 Dieses SQLPOINTER-Datensatzfeld verweist auf eine Variable, die den Parameterwert (für APDs) oder den Spaltenwert (für ARDs) enthält. Dieses Feld ist ein *verzögertes Feld*. Es wird zum Zeitpunkt der Einstellung nicht verwendet, aber zu einem späteren Zeitpunkt vom Treiber zum Abrufen von Daten verwendet.  
  
 Die vom SQL_DESC_DATA_PTR-Feld der ARD angegebene Spalte ist ungebunden, wenn das *TargetValuePtr-Argument* in einem Aufruf von **SQLBindCol** ein Nullzeiger ist oder wenn das SQL_DESC_DATA_PTR Feld in der ARD durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec** auf einen Nullzeiger festgelegt wird. Andere Felder sind nicht betroffen, wenn das Feld SQL_DESC_DATA_PTR auf einen Nullzeiger festgelegt ist.  
  
 Wenn der Aufruf von **SQLFetch** oder **SQLFetchScroll,** der den Puffer ausfüllt, auf den durch dieses Feld verwiesen wird, nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben wird, ist der Inhalt des Puffers nicht definiert.  
  
 Wenn das feld SQL_DESC_DATA_PTR einer APD, ARD oder IPD festgelegt ist, überprüft der Treiber, ob der Wert im Feld SQL_DESC_TYPE einen der gültigen ODBC C-Datentypen oder einen treiberspezifischen Datentyp enthält und ob alle anderen Felder, die die Datentypen betreffen, konsistent sind. Das Einfordern einer Konsistenzprüfung ist die einzige Verwendung des SQL_DESC_DATA_PTR Feldes einer IPD. Wenn eine Anwendung das SQL_DESC_DATA_PTR Feld einer IPD festlegt und später **SQLGetDescField** für dieses Feld aufruft, wird nicht unbedingt der festgelegte Wert zurückgegeben. Weitere Informationen finden Sie unter "Konsistenzprüfungen" in [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 **SQL_DESC_DATETIME_INTERVAL_CODE [Alle]**  
 Dieses SQLSMALLINT-Datensatzfeld enthält den Untercode für den spezifischen Datumszeit- oder Intervalldatentyp, wenn das SQL_DESC_TYPE Feld SQL_DATETIME oder SQL_INTERVAL ist. Dies gilt sowohl für SQL- als auch für C-Datentypen. Der Code besteht aus dem Datentypnamen mit "CODE", der entweder durch "TYPE" oder "C_TYPE" (für Datumszeittypen) oder "CODE" ersetzt wird, ersetzt durch "INTERVAL" oder "C_INTERVAL" (für Intervalltypen).  
  
 Wenn SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE in einer Anwendungsdeskriptor auf SQL_C_DEFAULT festgelegt sind und der Deskriptor keinem Anweisungshandle zugeordnet ist, ist der Inhalt von SQL_DESC_DATETIME_INTERVAL_CODE nicht definiert.  
  
 Dieses Feld kann für die datumsaktuellen Datentypen festgelegt werden, die in der folgenden Tabelle aufgeführt sind.  
  
|Datetime-Typen|DATETIME_INTERVAL_CODE|  
|--------------------|------------------------------|  
|SQL_TYPE_DATE/SQL_C_TYPE_DATE|SQL_CODE_DATE|  
|SQL_TYPE_TIME/SQL_C_TYPE_TIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP/SQL_C_TYPE_TIMESTAMP|SQL_CODE_TIMESTAMP|  
  
 Dieses Feld kann für die in der folgenden Tabelle aufgeführten Intervalldatentypen festgelegt werden.  
  
|Intervalltyp|DATETIME_INTERVAL_CODE|  
|-------------------|------------------------------|  
|SQL_INTERVAL_DAY/SQL_C_INTERVAL_DAY|SQL_CODE_DAY|  
|SQL_INTERVAL_DAY_TO_HOUR/SQL_C_INTERVAL_DAY_TO_HOUR|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE/SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_CODE_DAY_TO_MINUTE|  
|SQL_INTERVAL_DAY_TO_SECOND/SQL_C_INTERVAL_DAY_TO_SECOND|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR/SQL_C_INTERVAL_HOUR|SQL_CODE_HOUR|  
|SQL_INTERVAL_HOUR_TO_MINUTE/SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND/SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE/SQL_C_INTERVAL_MINUTE|SQL_CODE_MINUTE|  
|SQL_INTERVAL_MINUTE_TO_SECOND/SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_CODE_MINUTE_TO_SECOND|  
|SQL_INTERVAL_MONTH/SQL_C_INTERVAL_MONTH|SQL_CODE_MONTH|  
|SQL_INTERVAL_SECOND/SQL_C_INTERVAL_SECOND|SQL_CODE_SECOND|  
|SQL_INTERVAL_YEAR/SQL_C_INTERVAL_YEAR|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH/SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_CODE_YEAR_TO_MONTH|  
  
 Weitere Informationen zu den Datenintervallen und diesem Feld finden Sie unter [Datentypbezeichner und Deskriptoren](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md).  
  
 **SQL_DESC_DATETIME_INTERVAL_PRECISION [Alle]**  
 Dieses SQLINTEGER-Datensatzfeld enthält die Intervallführungsgenauigkeit, wenn das SQL_DESC_TYPE Feld SQL_INTERVAL ist. Wenn das Feld SQL_DESC_DATETIME_INTERVAL_CODE auf einen Intervalldatentyp festgelegt ist, wird dieses Feld auf die standardmäßige Intervallführungsgenauigkeit festgelegt.  
  
 **SQL_DESC_DISPLAY_SIZE [IRDs]**  
 Dieses schreibgeschützte SQLINTEGER-Datensatzfeld enthält die maximale Anzahl von Zeichen, die zum Anzeigen der Daten aus der Spalte erforderlich sind.  
  
 **SQL_DESC_FIXED_PREC_SCALE [Implementierungsdeskriptoren]**  
 Dieses schreibgeschützte SQLSMALLINT-Datensatzfeld wird auf SQL_TRUE festgelegt, wenn es sich bei der Spalte um eine exakte numerische Spalte handelt und eine feste Genauigkeit und ein Maßstab ungleich Null besteht, oder auf SQL_FALSE, ob es sich bei der Spalte nicht um eine exakte numerische Spalte mit einer festen Genauigkeit und Skalierung handelt.  
  
 **SQL_DESC_INDICATOR_PTR [Anwendungsdeskriptoren]**  
 In ARDs zeigt dieses SQLLEN * Datensatzfeld auf die Indikatorvariable. Diese Variable enthält SQL_NULL_DATA, wenn der Spaltenwert NULL ist. Bei APDs wird die Indikatorvariable auf SQL_NULL_DATA festgelegt, um dynamische NULL-Argumente anzugeben. Andernfalls ist die Variable Null (es sei denn, die Werte in SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR sind derselbe Zeiger).  
  
 Wenn das SQL_DESC_INDICATOR_PTR Feld in einer ARD ein Nullzeiger ist, wird der Treiber daran gehindert, Informationen darüber zurückzugeben, ob die Spalte NULL ist oder nicht. Wenn die Spalte NULL ist und SQL_DESC_INDICATOR_PTR ein NULL-Zeiger ist, wird SQLSTATE 22002 (Indikatorvariable erforderlich, aber nicht angegeben) zurückgegeben, wenn der Treiber versucht, den Puffer nach einem Aufruf von **SQLFetch** oder **SQLFetchScroll**aufzufüllen. Wenn der Aufruf von **SQLFetch** oder **SQLFetchScroll** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO nicht zurückgegeben hat, ist der Inhalt des Puffers nicht definiert.  
  
 Das Feld SQL_DESC_INDICATOR_PTR bestimmt, ob das Feld festgelegt wird, auf das von SQL_DESC_OCTET_LENGTH_PTR zeigt. Wenn der Datenwert für eine Spalte NULL ist, setzt der Treiber die Indikatorvariable auf SQL_NULL_DATA. Das Feld, auf das SQL_DESC_OCTET_LENGTH_PTR wird dann nicht gesetzt. Wenn während des Abrufs kein NULL-Wert gefunden wird, wird der Puffer, auf den von SQL_DESC_INDICATOR_PTR verwiesen wird, auf Null und der Puffer, auf den von SQL_DESC_OCTET_LENGTH_PTR verwiesen wird, auf die Länge der Daten festgelegt.  
  
 Wenn das SQL_DESC_INDICATOR_PTR Feld in einer APD ein NULL-Zeiger ist, kann die Anwendung diesen Deskriptordatensatz nicht verwenden, um NULL-Argumente anzugeben.  
  
 Dieses Feld ist ein *verzögertes Feld:* Es wird nicht zum Zeitpunkt seiner Festlegung verwendet, sondern zu einem späteren Zeitpunkt vom Treiber verwendet, um null-Zulässigkeit (für ARDs) anzuzeigen oder um null-Zulässigkeit (für APDs) zu bestimmen.  
  
 **SQL_DESC_LABEL [IRDs]**  
 Dieses schreibgeschützte SQLCHAR * -Datensatzfeld enthält die Spaltenbezeichnung oder den Spaltentitel. Wenn die Spalte keine Bezeichnung hat, enthält diese Variable den Spaltennamen. Wenn die Spalte unbenannt und unbeschriftet ist, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_LENGTH [Alle]**  
 Dieses SQLULEN-Datensatzfeld ist entweder die maximale oder tatsächliche Länge einer Zeichenfolge in Zeichen oder ein binärer Datentyp in Bytes. Dabei handelt es sich um die maximale Länge für einen Datentyp mit fester Länge oder um die tatsächliche Länge für einen Datentyp variabler Länge. Sein Wert schließt immer das Null-Beendigungszeichen aus, das die Zeichenkette beendet. Bei Werten, deren Typ SQL_TYPE_DATE, SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP oder einem der SQL-Intervalldatentypen ist, hat dieses Feld die Länge der Zeichenkettendarstellung der Datumszeit oder des Intervallwerts in Zeichen.  
  
 Der Wert in diesem Feld kann sich vom Wert für "Länge" unterscheiden, wie in ODBC 2 *.x*definiert. Weitere Informationen finden Sie in [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_LITERAL_PREFIX [IRDs]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatzfeld enthält die Zeichen oder Zeichen, die der Treiber als Präfix für ein Literal dieses Datentyps erkennt. Diese Variable enthält eine leere Zeichenfolge für einen Datentyp, für den kein Literalpräfix gilt.  
  
 **SQL_DESC_LITERAL_SUFFIX [IRDs]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatzfeld enthält die Zeichen oder Zeichen, die der Treiber als Suffix für ein Literal dieses Datentyps erkennt. Diese Variable enthält eine leere Zeichenfolge für einen Datentyp, für den kein Literalsuffix anwendbar ist.  
  
 **SQL_DESC_LOCAL_TYPE_NAME [Implementierungsdeskriptoren]**  
 Dieses schreibgeschützte SQLCHAR *-Eintragsfeld enthält alle lokalisierten (muttersprachlichen) Namen für den Datentyp, die sich vom regulären Namen des Datentyps unterscheiden können. Wenn kein lokalisierter Name vorhanden ist, wird eine leere Zeichenfolge zurückgegeben. Dieses Feld dient nur zu Anzeigezwecken.  
  
 **SQL_DESC_NAME [Implementierungsdeskriptoren]**  
 Dieses SQLCHAR *-Datensatzfeld in einem Zeilendeskriptor enthält den Spaltenalias, sofern er angewendet wird. Wenn der Spaltenalias nicht zutrifft, wird der Spaltenname zurückgegeben. In beiden Fällen legt der Treiber das Feld SQL_DESC_UNNAMED auf SQL_NAMED, wenn er das Feld SQL_DESC_NAME festlegt. Wenn kein Spaltenname oder ein Spaltenalias vorhanden ist, gibt der Treiber eine leere Zeichenfolge im Feld SQL_DESC_NAME zurück und legt das Feld SQL_DESC_UNNAMED auf SQL_UNNAMED.  
  
 Eine Anwendung kann das SQL_DESC_NAME Feld einer IPD auf einen Parameternamen oder Alias festlegen, um gespeicherte Prozedurparameter nach Namen anzugeben. (Weitere Informationen finden Sie unter [Bindungsparameter nach Name (Benannte Parameter)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md).) Das SQL_DESC_NAME Feld eines IRD ist ein schreibgeschütztes Feld. SQLSTATE HY091 (Ungültiger Deskriptorfeldbezeichner) wird zurückgegeben, wenn eine Anwendung versucht, sie festzulegen.  
  
 In IPDs ist dieses Feld nicht definiert, wenn der Treiber benannte Parameter nicht unterstützt. Wenn der Treiber benannte Parameter unterstützt und Parameter beschreiben kann, wird der Parametername in diesem Feld zurückgegeben.  
  
 **SQL_DESC_NULLABLE [Implementierungsdeskriptoren]**  
 In IRDs wird dieses schreibgeschützte SQLSMALLINT-Datensatzfeld SQL_NULLABLE, ob die Spalte NULL-Werte haben kann, SQL_NO_NULLS, wenn die Spalte keine NULL-Werte hat, oder SQL_NULLABLE_UNKNOWN, wenn nicht bekannt ist, ob die Spalte NULL-Werte akzeptiert. Dieses Feld bezieht sich auf die Ergebnissatzspalte und nicht auf die Basisspalte.  
  
 In IPDs ist dieses Feld immer auf SQL_NULLABLE festgelegt, da dynamische Parameter immer null und nicht von einer Anwendung festgelegt werden können.  
  
 **SQL_DESC_NUM_PREC_RADIX [Alle]**  
 Dieses SQLINTEGER-Feld enthält den Wert 2, wenn der Datentyp im Feld SQL_DESC_TYPE ein ungefährer numerischer Datentyp ist, da das Feld SQL_DESC_PRECISION die Anzahl der Bits enthält. Dieses Feld enthält einen Wert von 10, wenn der Datentyp im Feld SQL_DESC_TYPE ein exakter numerischer Datentyp ist, da das Feld SQL_DESC_PRECISION die Anzahl der Dezimalstellen enthält. Dieses Feld ist für alle nicht numerischen Datentypen auf 0 festgelegt.  
  
 **SQL_DESC_OCTET_LENGTH [Alle]**  
 Dieses SQLLEN-Datensatzfeld enthält die Länge eines Zeichenfolgen- oder Binärdatentyps in Bytes. Bei Zeichen oder Binärtypen fester Länge ist dies die tatsächliche Länge in Bytes. Bei Zeichen variabler Länge oder binären Typen ist dies die maximale Länge in Bytes. Dieser Wert schließt immer Speicherplatz für das Null-Beendigungszeichen für Implementierungsdeskriptoren aus und enthält immer Speicherplatz für das Null-Beendigungszeichen für Anwendungsdeskriptoren. Für Anwendungsdaten enthält dieses Feld die Größe des Puffers. Für APDs ist dieses Feld nur für Ausgabe- oder Eingabe-/Ausgabeparameter definiert.  
  
 **SQL_DESC_OCTET_LENGTH_PTR [Anwendungsdeskriptoren]**  
 Dieses SQLLEN *-Datensatzfeld zeigt auf eine Variable, die die Gesamtlänge in Bytes eines dynamischen Arguments (für Parameterdeskriptoren) oder eines gebundenen Spaltenwerts (für Zeilendeskriptoren) enthält.  
  
 Bei einer APD wird dieser Wert für alle Argumente außer Zeichenzeichenfolge und Binärdatei ignoriert. Wenn dieses Feld auf SQL_NTS zeigt, muss das dynamische Argument null beendet werden. Um anzugeben, dass ein gebundener Parameter ein Data-at-Execution-Parameter ist, legt eine Anwendung dieses Feld im entsprechenden Datensatz der APD auf eine Variable fest, die zum Zeitpunkt der Ausführung den Wert SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC-Makros enthält. Wenn es mehr als ein solches Feld gibt, kann SQL_DESC_DATA_PTR auf einen Wert festgelegt werden, der den Parameter eindeutig identifiziert, damit die Anwendung bestimmen kann, welcher Parameter angefordert wird.  
  
 Wenn das OCTET_LENGTH_PTR Feld einer ARD ein Nullzeiger ist, gibt der Treiber keine Längeninformationen für die Spalte zurück. Wenn das SQL_DESC_OCTET_LENGTH_PTR Feld einer APD ein Nullzeiger ist, geht der Treiber davon aus, dass Zeichenfolgen und Binärwerte null-beendet sind. (Binäre Werte sollten nicht null-beendet werden, sondern eine Länge erhalten, um Abschneiden zu vermeiden.)  
  
 Wenn der Aufruf von **SQLFetch** oder **SQLFetchScroll,** der den Puffer ausfüllt, auf den durch dieses Feld verwiesen wird, nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben wird, ist der Inhalt des Puffers nicht definiert. Dieses Feld ist ein *verzögertes Feld*. Es wird nicht zum Zeitpunkt der Einstellung verwendet, sondern zu einem späteren Zeitpunkt vom Treiber verwendet, um die Oktettlänge der Daten zu bestimmen oder anzugeben.  
  
 **SQL_DESC_PARAMETER_TYPE [IPDs]**  
 Dieses SQLSMALLINT-Datensatzfeld ist auf SQL_PARAM_INPUT für einen Eingabeparameter festgelegt, SQL_PARAM_INPUT_OUTPUT für einen Eingabe-/Ausgabeparameter, SQL_PARAM_OUTPUT für einen Ausgabeparameter, SQL_PARAM_INPUT_OUTPUT_STREAM für einen von der Eingabe/Ausgabe gestreamten Parameter oder SQL_PARAM_OUTPUT_STREAM für einen ausgabegestreamten Parameter. Standardmäßig ist SQL_PARAM_INPUT festgelegt.  
  
 Bei einer IPD wird das Feld standardmäßig auf SQL_PARAM_INPUT festgelegt, wenn die IPD nicht automatisch vom Treiber aufgefüllt wird (das Attribut SQL_ATTR_ENABLE_AUTO_IPD-Anweisung ist SQL_FALSE). Eine Anwendung sollte dieses Feld in der IPD für Parameter festlegen, die keine Eingabeparameter sind.  
  
 **SQL_DESC_PRECISION [Alle]**  
 Dieses SQLSMALLINT-Datensatzfeld enthält die Anzahl der Ziffern für einen genauen numerischen Typ, die Anzahl der Bits in der Mantisse (binäre Genauigkeit) für einen ungefähren numerischen Typ oder die Anzahl der Ziffern in der Komponente Bruchsekunden für den Datentyp SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP oder SQL_INTERVAL_SECOND. Dieses Feld ist für alle anderen Datentypen nicht definiert.  
  
 Der Wert in diesem Feld kann sich vom Wert für "Präzision" gemäß ODBC 2 *.x*unterscheiden. Weitere Informationen finden Sie in [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_ROWVER [Implementierungsdeskriptoren]**  
 Dieses SQLSMALLINTrecord-Feld gibt an, ob eine Spalte automatisch vom DBMS geändert wird, wenn eine Zeile aktualisiert wird (z. B. eine Spalte vom Typ "Timestamp" in SQL Server). Der Wert dieses Datensatzfelds wird auf SQL_TRUE festgelegt, wenn es sich bei der Spalte um eine Zeilenversionsspalte handelt, und andernfalls auf SQL_FALSE. Dieses Spaltenattribut ähnelt dem Aufrufen von **SQLSpecialColumns** mit IdentifierType SQL_ROWVER, um zu bestimmen, ob eine Spalte automatisch aktualisiert wird.  
  
 **SQL_DESC_SCALE [Alle]**  
 Dieses SQLSMALLINT-Datensatzfeld enthält den definierten Maßstab für dezimale und numerische Datentypen. Das Feld ist für alle anderen Datentypen nicht definiert.  
  
 Der Wert in diesem Feld kann sich vom Wert für "scale" gemäß ODBC 2 *.x*unterscheiden. Weitere Informationen finden Sie in [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_SCHEMA_NAME [IRDs]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatzfeld enthält den Schemanamen der Basistabelle, die die Spalte enthält. Der Rückgabewert ist treiberabhängig, wenn es sich bei der Spalte um einen Ausdruck handelt oder wenn die Spalte Teil einer Ansicht ist. Wenn die Datenquelle keine Schemas unterstützt oder der Schemaname nicht bestimmt werden kann, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_SEARCHABLE [IRDs]**  
 Dieses schreibgeschützte SQLSMALLINT-Datensatzfeld wird auf einen der folgenden Werte festgelegt:  
  
-   SQL_PRED_NONE, wenn die Spalte nicht in einer **WHERE-Klausel** verwendet werden kann. (Dies entspricht dem SQL_UNSEARCHABLE Wert in ODBC 2 *.x*.)  
  
-   SQL_PRED_CHAR, ob die Spalte in einer **WHERE-Klausel** verwendet werden kann, jedoch nur mit dem **PRÄdikat LIKE.** (Dies entspricht dem SQL_LIKE_ONLY Wert in ODBC 2 *.x*.)  
  
-   SQL_PRED_BASIC, ob die Spalte in einer **WHERE-Klausel** mit allen Vergleichsoperatoren außer **LIKE**verwendet werden kann. (Dies entspricht dem SQL_EXCEPT_LIKE Wert in ODBC 2 *.x*.)  
  
-   SQL_PRED_SEARCHABLE, ob die Spalte in einer **WHERE-Klausel** mit einem beliebigen Vergleichsoperator verwendet werden kann.  
  
 **SQL_DESC_TABLE_NAME [IRDs]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatzfeld enthält den Namen der Basistabelle, die diese Spalte enthält. Der Rückgabewert ist treiberabhängig, wenn es sich bei der Spalte um einen Ausdruck handelt oder wenn die Spalte Teil einer Ansicht ist.  
  
 **SQL_DESC_TYPE [Alle]**  
 Dieses SQLSMALLINT-Datensatzfeld gibt den präzisen SQL- oder C-Datentyp für alle Datentypen außer Datums- und Intervalldatentypen an. Für die Datumszeit- und Intervalldatentypen gibt dieses Feld den ausführlichen Datentyp an, der SQL_DATETIME oder SQL_INTERVAL ist.  
  
 Wenn dieses Feld SQL_DATETIME oder SQL_INTERVAL enthält, muss das Feld SQL_DESC_DATETIME_INTERVAL_CODE den entsprechenden Untercode für den prägnanten Typ enthalten. Für datetime-Datentypen enthält SQL_DESC_TYPE SQL_DATETIME, und das Feld SQL_DESC_DATETIME_INTERVAL_CODE enthält einen Untercode für den spezifischen Datetime-Datentyp. Für Intervalldatentypen enthält SQL_DESC_TYPE SQL_INTERVAL und das Feld SQL_DESC_DATETIME_INTERVAL_CODE einen Untercode für den spezifischen Intervalldatentyp.  
  
 Die Werte in den Feldern SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE sind voneinander abhängig. Jedes Mal, wenn eines der Felder festgelegt wird, muss auch das andere festgelegt werden. SQL_DESC_TYPE kann durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**festgelegt werden. SQL_DESC_CONCISE_TYPE kann durch einen Aufruf von **SQLBindCol** oder **SQLBindParameter**oder **SQLSetDescField**festgelegt werden.  
  
 Wenn SQL_DESC_TYPE auf einen anderen kurzen Datentyp als einen Intervall- oder Datumszeitdatentyp festgelegt ist, wird das Feld SQL_DESC_CONCISE_TYPE auf denselben Wert und das Feld SQL_DESC_DATETIME_INTERVAL_CODE auf 0 festgelegt.  
  
 Wenn SQL_DESC_TYPE auf den ausführlichen Datums- oder Intervalldatentyp (SQL_DATETIME oder SQL_INTERVAL) und das Feld SQL_DESC_DATETIME_INTERVAL_CODE auf den entsprechenden Untercode festgelegt ist, wird das Feld SQL_DESC_CONCISE TYPE auf den entsprechenden prägnanten Typ festgelegt. Wenn Sie versuchen, SQL_DESC_TYPE auf einen der prägnanten Datumszeit- oder Intervalltypen festzulegen, wird SQLSTATE HY021 (Inkonsistente Deskriptorinformationen) zurückgegeben.  
  
 Wenn das feld SQL_DESC_TYPE durch einen Aufruf von **SQLBindCol**, **SQLBindParameter**oder **SQLSetDescField**festgelegt wird, werden die folgenden Felder auf die folgenden Standardwerte festgelegt, wie in der folgenden Tabelle dargestellt. Die Werte der verbleibenden Felder desselben Datensatzes sind nicht definiert.  
  
|Wert der SQL_DESC_TYPE|Andere Felder implizit festgelegt|  
|------------------------------|---------------------------------|  
|SQL_CHAR, SQL_VARCHAR, SQL_C_CHAR, SQL_C_VARCHAR|SQL_DESC_LENGTH ist auf 1 gesetzt. SQL_DESC_PRECISION ist auf 0 gesetzt.|  
|SQL_DATETIME|Wenn SQL_DESC_DATETIME_INTERVAL_CODE auf SQL_CODE_DATE oder SQL_CODE_TIME festgelegt ist, wird SQL_DESC_PRECISION auf 0 gesetzt. Wenn es auf SQL_DESC_TIMESTAMP gesetzt ist, wird SQL_DESC_PRECISION auf 6 gesetzt.|  
|SQL_DECIMAL, SQL_NUMERIC, SQL_C_NUMERIC|SQL_DESC_SCALE ist auf 0 gesetzt. SQL_DESC_PRECISION wird auf die implementierungsdefinierte Genauigkeit für den jeweiligen Datentyp festgelegt.<br /><br /> Unter [SQL zu C: Numerisch](../../../odbc/reference/appendixes/sql-to-c-numeric.md) finden Sie Informationen zum manuellen Binden eines SQL_C_NUMERIC Werts.|  
|SQL_FLOAT, SQL_C_FLOAT|SQL_DESC_PRECISION wird auf die implementierungsdefinierte Standardgenauigkeit für SQL_FLOAT festgelegt.|  
|SQL_INTERVAL|Wenn SQL_DESC_DATETIME_INTERVAL_CODE auf einen Intervalldatentyp festgelegt ist, wird SQL_DESC_DATETIME_INTERVAL_PRECISION auf 2 (Standardintervallführungsgenauigkeit) festgelegt. Wenn das Intervall eine Komponente für Sekunden aufweist, wird SQL_DESC_PRECISION auf 6 (Standardintervallsekundengenauigkeit) festgelegt.|  
  
 Wenn eine Anwendung **SQLSetDescField** aufruft, um Felder eines Deskriptors festzulegen, anstatt **SQLSetDescRec**aufzurufen, muss die Anwendung zuerst den Datentyp deklarieren. In diesem Bereich werden die anderen Felder, die in der vorherigen Tabelle angegeben sind, implizit festgelegt. Wenn einer der implizit festgelegten Werte nicht akzeptabel ist, kann die Anwendung **sqlSetDescField** oder **SQLSetDescRec** aufrufen, um den inakzeptablen Wert explizit festzulegen.  
  
 **SQL_DESC_TYPE_NAME [Implementierungsdeskriptoren]**  
 Dieses schreibgeschützte SQLCHAR * Datensatzfeld enthält den datenquellenabhängigen Typnamen (z. B. "CHAR", "VARCHAR" usw.). Wenn der Name des Datentyps unbekannt ist, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_UNNAMED [Implementierungsdeskriptoren]**  
 Dieses SQLSMALLINT-Datensatzfeld in einer Zeilendeskriptor wird vom Treiber auf SQL_NAMED oder SQL_UNNAMED festgelegt, wenn das Feld SQL_DESC_NAME festgelegt wird. Wenn das Feld SQL_DESC_NAME einen Spaltenalias enthält oder der Spaltenalias nicht angewendet wird, legt der Treiber das Feld SQL_DESC_UNNAMED auf SQL_NAMED fest. Wenn eine Anwendung das SQL_DESC_NAME Feld einer IPD auf einen Parameternamen oder Alias festlegt, legt der Treiber das SQL_DESC_UNNAMED Feld der IPD auf SQL_NAMED. Wenn kein Spaltenname oder ein Spaltenalias vorhanden ist, legt der Treiber das Feld SQL_DESC_UNNAMED auf SQL_UNNAMED.  
  
 Eine Anwendung kann das SQL_DESC_UNNAMED Feld einer IPD auf SQL_UNNAMED festlegen. Ein Treiber gibt SQLSTATE HY091 (Invalid descriptor field identifier) zurück, wenn eine Anwendung versucht, das SQL_DESC_UNNAMED Feld einer IPD auf SQL_NAMED festzulegen. Das SQL_DESC_UNNAMED Feld eines IRD ist schreibgeschützt; SQLSTATE HY091 (Ungültiger Deskriptorfeldbezeichner) wird zurückgegeben, wenn eine Anwendung versucht, sie festzulegen.  
  
 **SQL_DESC_UNSIGNED [Implementierungsdeskriptoren]**  
 Dieses schreibgeschützte SQLSMALLINT-Datensatzfeld wird auf SQL_TRUE festgelegt, wenn der Spaltentyp nicht signiert oder nicht numerisch ist oder SQL_FALSE, wenn der Spaltentyp signiert ist.  
  
 **SQL_DESC_UPDATABLE [IRDs]**  
 Dieses schreibgeschützte SQLSMALLINT-Datensatzfeld wird auf einen der folgenden Werte festgelegt:  
  
-   SQL_ATTR_READ_ONLY, wenn die Ergebnissatzspalte schreibgeschützt ist.  
  
-   SQL_ATTR_WRITE, wenn die Ergebnissatzspalte Lese-/Schreibvorgang ist.  
  
-   SQL_ATTR_READWRITE_UNKNOWN, ob nicht bekannt ist, ob die Ergebnissatzspalte aktualisierbar ist oder nicht.  
  
 SQL_DESC_UPDATABLE beschreibt die Updatability der Spalte im Resultset, nicht die Spalte in der Basistabelle. Die Updatability der Spalte in der Basistabelle, auf der diese Ergebnissatzspalte basiert, kann sich vom Wert in diesem Feld unterscheiden. Ob eine Spalte aufrüstbar ist, kann auf dem Datentyp, den Benutzerberechtigungen und der Definition des Resultsets selbst basieren. Wenn unklar ist, ob eine Spalte aufrüstbar ist, sollten SQL_ATTR_READWRITE_UNKNOWN zurückgegeben werden.  
  
## <a name="consistency-checks"></a>Konsistenzprüfungen  
 Eine Konsistenzprüfung wird vom Fahrer automatisch durchgeführt, wenn eine Anwendung einen Wert für das SQL_DESC_DATA_PTR Feld der ARD, APD oder IPD übergibt. Wenn eines der Felder nicht mit anderen Feldern übereinstimmt, gibt **SQLSetDescField** SQLSTATE HY021 (Inkonsistente Deskriptorinformationen) zurück. Weitere Informationen finden Sie unter "Konsistenzprüfung" in [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden einer Spalte|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Binden eines Parameters|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Abrufen eines Deskriptorfelds|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Abrufen mehrerer Deskriptorfelder|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen mehrerer Deskriptorfelder|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)
