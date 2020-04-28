---
title: SQLSetDescField-Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299550"
---
# <a name="sqlsetdescfield-function"></a>SQLSetDescField-Funktion

**Konformitäts**  
 Eingeführte Version: ODBC 3,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLSetDescField** legt den Wert eines einzelnen Felds eines deskriptordaten Satzes fest.  
  
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
 Der Deskriptorhandle.  
  
 *RecNumber*  
 Der Gibt den Deskriptordatensatz mit dem Feld an, das von der Anwendung festgelegt werden soll. Deskriptordatensätze werden von 0 nummeriert, wobei die Datensatznummer 0 der Lesezeichen-Datensatz ist. Das *RecNumber* -Argument wird für Header Felder ignoriert.  
  
 *FieldIdentifier*  
 Der Gibt das Feld des Deskriptors an, dessen Wert festgelegt werden soll. Weitere Informationen finden Sie unter "*fieldidentifier* -Argument" im Abschnitt "comments".  
  
 *ValuePtr*  
 Der Zeiger auf einen Puffer, der die Deskriptorinformationen enthält, oder ein ganzzahliger Wert. Der Datentyp hängt vom Wert von *fieldidentifier*ab. Wenn *ValuePtr* ein ganzzahliger Wert ist, kann er je nach Wert des *fieldidentifier* -Arguments als 8 Bytes (sqllen), 4 Bytes (SQLINTEGER) oder 2 Bytes (SQLSMALLINT) betrachtet werden.  
  
 *Pufferlänge*  
 Der Wenn *fieldidentifier* ein ODBC-definiertes Feld ist und *ValuePtr* auf eine Zeichenfolge oder einen binären Puffer zeigt, sollte dieses Argument die Länge von **ValuePtr*aufweisen. Für Zeichen folgen Daten sollte dieses Argument die Anzahl der Bytes in der Zeichenfolge enthalten.  
  
 Wenn *fieldidentifier* ein ODBC-definiertes Feld und *ValuePtr* eine ganze Zahl ist, wird *BufferLength* ignoriert.  
  
 Wenn *fieldidentifier* ein Treiber definiertes Feld ist, gibt die Anwendung die Art des Felds für den Treiber-Manager an, indem das *BufferLength* -Argument festgelegt wird. *BufferLength* kann die folgenden Werte aufweisen:  
  
-   Wenn *ValuePtr* ein Zeiger auf eine Zeichenfolge ist, entspricht *BufferLength* der Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn *ValuePtr* ein Zeiger auf einen binären Puffer ist, platziert die Anwendung das Ergebnis des Makros SQL_LEN_BINARY_ATTR (*length*) in *BufferLength*. Dadurch wird ein negativer Wert in *BufferLength*platziert.  
  
-   Wenn *ValuePtr* ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine binäre Zeichenfolge ist, sollte *BufferLength* den Wert SQL_IS_POINTER.  
  
-   Wenn *ValuePtr* einen Wert mit fester Länge enthält, ist *BufferLength* entweder SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT oder SQL_IS_USMALLINT.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetDescField** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_DESC und einem *handle* von *descriptorhandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgelistet, die von **SQLSetDescField** häufig zurückgegeben und im Kontext dieser Funktion erläutert werden. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01s02 entsprechen|Optionswert geändert|Der Treiber hat den in * \*ValuePtr* angegebenen Wert (wenn *ValuePtr* ein Zeiger war) oder den Wert in *ValuePtr* (wenn *ValuePtr* ein ganzzahliger Wert war) nicht unterstützt, oder * \*ValuePtr* war aufgrund von Implementierungs Arbeitsbedingungen ungültig, sodass der Treiber einen ähnlichen Wert ersetzt hat. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger deskriptorindex.|Das *fieldidentifier* -Argument war ein Daten Satz Feld, das " *RecNumber* "-Argument war "0", und das *Deskriptorhandle* -Argument wies auf ein IPD-handle hin.<br /><br /> Das *RecNumber* -Argument war kleiner als 0, und das *Deskriptorhandle* -Argument hat auf einen ARD oder eine APD verwiesen.<br /><br /> Das Argument " *RecNumber* " war größer als die maximale Anzahl von Spalten oder Parametern, die von der Datenquelle unterstützt werden können, und das *Deskriptorhandle* -Argument wies auf eine APD oder einen ARD hin.<br /><br /> (DM) das *fieldidentifier* -Argument wurde SQL_DESC_COUNT, und das * \*ValuePtr* -Argument war kleiner als 0 (null).<br /><br /> Das *RecNumber* -Argument war gleich 0, und das *Deskriptorhandle* -Argument hat auf eine implizit zugeordnete APD verwiesen. (Dieser Fehler tritt nicht bei einem explizit zugeordneten Anwendungs Deskriptor auf, da nicht bekannt ist, ob es sich bei einem explizit zugeordneten Anwendungs Deskriptor um eine APD oder einen ARD handelt, bis die Ausführungszeit erfolgt.)|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|22001|Zeichen folgen Daten, rechts abgeschnitten|Das *fieldidentifier* -Argument wurde SQL_DESC_NAME, und das *BufferLength* -Argument war ein Wert, der größer als SQL_MAX_IDENTIFIER_LEN ist.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im * \*MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY010|Funktions Sequenz Fehler|(DM) das *Deskriptorhandle* wurde mit einem *StatementHandle* verknüpft, für das eine asynchron ausgeführte Funktion (nicht diese) aufgerufen wurde und noch ausgeführt wurde, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen, dem das *Deskriptorhandle* zugeordnet und SQL_NEED_DATA zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde für das Verbindungs Handle aufgerufen, das dem *Deskriptorhandle*zugeordnet ist. Diese asynchrone Funktion wurde noch ausgeführt, als die **SQLSetDescField** -Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für eines der Anweisungs Handles aufgerufen, die dem *Deskriptorhandle* zugeordnet sind, und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY016|Ein Implementierungs Zeilen Deskriptor kann nicht geändert werden.|Das *Deskriptorhandle* -Argument wurde mit IRD verknüpft, und das *fieldidentifier* -Argument war nicht SQL_DESC_ARRAY_STATUS_PTR oder SQL_DESC_ROWS_PROCESSED_PTR.|  
|HY021|Inkonsistente Deskriptorinformationen|Die Felder "SQL_DESC_TYPE" und "SQL_DESC_DATETIME_INTERVAL_CODE" bilden keinen gültigen ODBC-SQL-Typ oder einen gültigen treiberspezifischen SQL-Typ (für IPDS) oder einen gültigen ODBC-C-Typ (für APDS oder ARDs).<br /><br /> Während einer Konsistenzprüfung überprüfte Deskriptorinformationen waren nicht konsistent. (Weitere Informationen finden Sie unter "Konsistenzprüfung" in **sqlsetdebug**.)|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|(DM) * \*ValuePtr* ist eine Zeichenfolge, und *BufferLength* war kleiner als 0 (null), war aber nicht gleich SQL_NTS.<br /><br /> (DM) der Treiber war ein ODBC 2 *. x* -Treiber, der Deskriptor war eine ARD, das *ColumnNumber* -Argument wurde auf 0 festgelegt, und der für das Argument *BufferLength* angegebene Wert war nicht gleich 4.|  
|HY091|Ungültiger Deskriptorfeldbezeichner.|Der für das *fieldidentifier* -Argument angegebene Wert war kein ODBC-definiertes Feld und war kein durch die Implementierung definierter Wert.<br /><br /> Das *fieldidentifier* -Argument war für das *Deskriptorhandle* -Argument ungültig.<br /><br /> Das *fieldidentifier* -Argument war ein Schreib geschütztes, ODBC-definiertes Feld.|  
|HY092|Ungültiger Attribut/Options Bezeichner|Der Wert in * \*ValuePtr* war für das *fieldidentifier* -Argument ungültig.<br /><br /> Das *fieldidentifier* -Argument wurde SQL_DESC_UNNAMED, und *ValuePtr* war SQL_NAMED.|  
|HY105|Ungültiger Parametertyp|(DM) der für das SQL_DESC_PARAMETER_TYPE Feld angegebene Wert war ungültig. (Weitere Informationen finden Sie im Abschnitt "*inputoutputtype* -Argument" in **SQLBindParameter**.)|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [What es New in ODBC 3,8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *Deskriptorhandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung kann **SQLSetDescField** aufrufen, um ein beliebiges Deskriptorfeld nacheinander festzulegen. Durch einen **SQLSetDescField** -Befehl wird ein einzelnes Feld in einem einzelnen Deskriptor festgelegt. Diese Funktion kann aufgerufen werden, um ein beliebiges Feld in einem beliebigen Deskriptortyp festzulegen, sofern das Feld festgelegt werden kann. (Weitere Informationen finden Sie in der Tabelle weiter unten in diesem Abschnitt.)  
  
> [!NOTE]  
>  Wenn beim Aufrufen von **SQLSetDescField** ein Fehler auftritt, ist der Inhalt des deskriptordaten Satzes, der durch das *RecNumber* -Argument identifiziert wird, nicht definiert.  
  
 Andere Funktionen können aufgerufen werden, um mehrere Deskriptorfelder mit einem einzigen Aufruf der-Funktion festzulegen. Die **SQLSetDescRec** -Funktion legt eine Vielzahl von Feldern fest, die den Datentyp und den Puffer beeinflussen, die an eine Spalte oder einen Parameter gebunden sind (die Felder SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_DATA_PTR, SQL_DESC_OCTET_LENGTH_PTR und SQL_DESC_INDICATOR_PTR). **SQLBindCol** oder **SQLBindParameter** kann verwendet werden, um eine umfassende Spezifikation für die Bindung einer Spalte oder eines Parameters zu erstellen. Diese Funktionen legen eine bestimmte Gruppe von Deskriptorfeldern mit einem Funktions aufzurufen fest.  
  
 **SQLSetDescField** kann aufgerufen werden, um die Bindungs Puffer durch Hinzufügen eines Offsets zu den Bindungs Zeigern (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR oder SQL_DESC_OCTET_LENGTH_PTR) zu ändern. Dadurch werden die Bindungs Puffer geändert, ohne dass **SQLBindCol** oder **SQLBindParameter**aufgerufen wird. Dadurch kann eine Anwendung SQL_DESC_DATA_PTR ändern, ohne andere Felder, z. b. SQL_DESC_DATA_TYPE, ändern zu müssen.  
  
 Wenn eine Anwendung **SQLSetDescField** aufruft, um ein anderes Feld als SQL_DESC_COUNT oder die verzögerten Felder SQL_DESC_DATA_PTR, SQL_DESC_OCTET_LENGTH_PTR oder SQL_DESC_INDICATOR_PTR festzulegen, wird der Datensatz nicht mehr gebunden.  
  
 Deskriptorheader-Felder werden durch Aufrufen von **SQLSetDescField** mit dem entsprechenden *fieldidentifier*festgelegt. Viele Header Felder sind ebenfalls Anweisungs Attribute, sodass Sie auch durch einen-Befehl von **SQLSetStmtAttr**festgelegt werden können. Dies ermöglicht es Anwendungen, ein Deskriptorfeld festzulegen, ohne zuerst ein Deskriptorhandle zu erhalten. Wenn **SQLSetDescField** aufgerufen wird, um ein Header Feld festzulegen, wird das *RecNumber* -Argument ignoriert.  
  
 Zum Festlegen von Lesezeichen Feldern wird eine *Zahl* von 0 verwendet.  
  
> [!NOTE]  
>  Das Anweisungs Attribut SQL_ATTR_USE_BOOKMARKS sollte vor dem Aufrufen von **SQLSetDescField** immer festgelegt werden, um Lesezeichen Felder festzulegen. Dies ist zwar nicht zwingend erforderlich, wird jedoch dringend empfohlen.  
  
## <a name="sequence-of-setting-descriptor-fields"></a>Sequenz der Einstellungs Deskriptorfelder  
 Wenn Sie Deskriptorfelder durch Aufrufen von **SQLSetDescField**festlegen, muss die Anwendung einer bestimmten Sequenz folgen:  
  
1.  Die Anwendung muss zuerst das Feld "SQL_DESC_TYPE", "SQL_DESC_CONCISE_TYPE" oder "SQL_DESC_DATETIME_INTERVAL_CODE" festlegen.  
  
2.  Nachdem eines dieser Felder festgelegt wurde, kann die Anwendung ein Attribut eines Datentyps festlegen, und der Treiber legt die Datentyp Attribut Felder auf die entsprechenden Standardwerte für den Datentyp fest. Die automatische standardmäßige standardmäßige Verwendung von Attribut Feldern stellt sicher, dass der Deskriptor immer zur Verwendung bereit ist, sobald die Anwendung einen Datentyp angegeben hat. Wenn die Anwendung explizit ein Datentyp Attribut festlegt, wird das default-Attribut überschrieben.  
  
3.  Nachdem eines der Felder, die in Schritt 1 aufgelistet wurden, festgelegt wurde und Datentyp Attribute festgelegt wurden, kann die Anwendung SQL_DESC_DATA_PTR festlegen. Dadurch wird eine Konsistenzprüfung der Deskriptorfelder angefordert. Wenn die Anwendung den Datentyp oder die Attribute nach dem Festlegen des SQL_DESC_DATA_PTR Felds ändert, legt der Treiber SQL_DESC_DATA_PTR auf einen NULL-Zeiger fest und hebt die Bindung des Datensatzes auf. Dadurch wird die Anwendung gezwungen, die richtigen Schritte nacheinander auszuführen, bevor der Deskriptordatensatz verwendet werden kann.  
  
## <a name="initialization-of-descriptor-fields"></a>Initialisierung der Deskriptorfelder  
 Wenn ein Deskriptor zugewiesen wird, können die Felder im Deskriptor mit einem Standardwert initialisiert, ohne einen Standardwert initialisiert werden oder für den Typ des Deskriptors nicht definiert sein. Die folgenden Tabellen geben die Initialisierung jedes Felds für jeden Deskriptortyp an, wobei "D" angibt, dass das Feld mit einem Standard initialisiert wurde, und "ND", das angibt, dass das Feld ohne Standard initialisiert wird. Wenn eine Zahl angezeigt wird, ist der Standardwert des Felds diese Zahl. Die Tabellen geben auch an, ob ein Feld Lese-/Schreibzugriff (r/W) oder schreibgeschützt (r) ist.  
  
 Die Felder eines IRD verfügen nur über einen Standardwert, nachdem die Anweisung vorbereitet oder ausgeführt wurde und der IRD aufgefüllt wurde. Dies gilt nicht, wenn das Anweisungs Handle oder der Deskriptor zugeordnet wurde. Solange der IRD nicht aufgefüllt wurde, wird bei jedem Versuch, Zugriff auf ein Feld eines IRD zu erhalten, ein Fehler zurückgegeben.  
  
 Einige Deskriptorfelder sind für mindestens einen der deskriptortypen ("ARDs", "unds", "APDS" und "IPDS") definiert. Wenn ein Feld für einen Deskriptortyp nicht definiert ist, wird es von keiner der Funktionen benötigt, die diesen Deskriptor verwenden.  
  
 Die Felder, auf die von **SQLGetDescField** zugegriffen werden kann, können nicht notwendigerweise von **SQLSetDescField**festgelegt werden. Felder, die von **SQLSetDescField** festgelegt werden können, sind in den folgenden Tabellen aufgeführt.  
  
 Die Initialisierung der Header Felder wird in der folgenden Tabelle beschrieben.  
  
|Name des Header Felds|Typ|R/W|Standard|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_ALLOC_TYPE|SQLSMALLINT|ARD: r APD: r IRD: r IPD: r|ARD: SQL_DESC_ALLOC_AUTO für implizites oder SQL_DESC_ALLOC_USER explizit<br /><br /> APD: SQL_DESC_ALLOC_AUTO für implizites oder SQL_DESC_ALLOC_USER für explizites Element<br /><br /> IRD: SQL_DESC_ALLOC_AUTO<br /><br /> IPD: SQL_DESC_ALLOC_AUTO|  
|SQL_DESC_ARRAY_SIZE|SQLULEN erstellt wurde|ARD: r/w APD: r/w ird: nicht verwendete IPD: nicht verwendet|ARD: [1] APD: [1] IRD: nicht verwendete IPD: nicht verwendet|  
|SQL_DESC_ARRAY_STATUS_PTR|Sqlusmallint *|ARD: r/w APD: r/w ird: r/w IPD: r/w|ARD: NULL PTR APD: NULL PTR IRD: NULL PTR IPD: NULL PTR|  
|SQL_DESC_BIND_OFFSET_PTR|SQLLEN|ARD: r/w APD: r/w ird: nicht verwendete IPD: nicht verwendet|ARD: NULL PTR APD: NULL PTR IRD: nicht verwendete IPD: nicht verwendet|  
|SQL_DESC_BIND_TYPE|SQLINTEGER|ARD: r/w APD: r/w ird: nicht verwendete IPD: nicht verwendet|ARD: SQL_BIND_BY_COLUMN<br /><br /> APD: SQL_BIND_BY_COLUMN<br /><br /> IRD: nicht verwendet<br /><br /> IPD: nicht verwendet|  
|SQL_DESC_COUNT|SQLSMALLINT|ARD: r/w APD: r/w ird: r IPD: r/w|ARD: 0 APD: 0 IRD: D IPD: 0|  
|SQL_DESC_ROWS_PROCESSED_PTR|SQLULEN erstellt wurde|ARD: nicht verwendeter APD: nicht verwendeter IRD: r/w IPD: r/w|ARD: nicht verwendetes APD: nicht verwendeter IRD: NULL PTR IPD: NULL PTR|  
  
 [1] diese Felder werden nur definiert, wenn die IPD automatisch vom Treiber ausgefüllt wird. Wenn dies nicht der Fall ist, sind Sie nicht definiert. Wenn eine Anwendung versucht, diese Felder festzulegen, wird SQLSTATE HY091 (Ungültiger Deskriptorfeldbezeichner) zurückgegeben.  
  
 Die Initialisierung von Daten Satz Feldern ist wie in der folgenden Tabelle dargestellt.  
  
|Name des Daten Satz Felds|Typ|R/W|Standard|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|ARD: nicht verwendetes APD: nicht verwendeter IRD: R IPD: nicht verwendet|ARD: nicht verwendetes APD: nicht verwendeter IRD: D IPD: nicht verwendet|  
|SQL_DESC_BASE_COLUMN_NAME|SQLCHAR|ARD: nicht verwendetes APD: nicht verwendeter IRD: R IPD: nicht verwendet|ARD: nicht verwendetes APD: nicht verwendeter IRD: D IPD: nicht verwendet|  
|SQL_DESC_BASE_TABLE_NAME|SQLCHAR|ARD: nicht verwendetes APD: nicht verwendeter IRD: R IPD: nicht verwendet|ARD: nicht verwendetes APD: nicht verwendeter IRD: D IPD: nicht verwendet|  
|SQL_DESC_CASE_SENSITIVE|SQLINTEGER|ARD: nicht verwendete APD: nicht verwendeter IRD: r IPD: r|ARD: nicht verwendetes APD: nicht verwendeter IRD: d IPD: d [1]|  
|SQL_DESC_CATALOG_NAME|SQLCHAR|ARD: nicht verwendetes APD: nicht verwendeter IRD: R IPD: nicht verwendet|ARD: nicht verwendetes APD: nicht verwendeter IRD: D IPD: nicht verwendet|  
|SQL_DESC_CONCISE_TYPE|SQLSMALLINT|ARD: r/w APD: r/w ird: r IPD: r/w|ARD: SQL_C_ Standard-APD: SQL_C_ Standardwert IRD: D IPD: ND|  
|SQL_DESC_DATA_PTR|SQLPOINTER|ARD: r/w APD: r/w ird: nicht verwendete IPD: nicht verwendet|ARD: NULL PTR APD: NULL PTR IRD: nicht verwendete IPD: nicht verwendet [2]|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQLSMALLINT|ARD: r/w APD: r/w ird: r IPD: r/w|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQLINTEGER|ARD: r/w APD: r/w ird: r IPD: r/w|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_DISPLAY_SIZE|SQLLEN|ARD: nicht verwendetes APD: nicht verwendeter IRD: R IPD: nicht verwendet|ARD: nicht verwendetes APD: nicht verwendeter IRD: D IPD: nicht verwendet|  
|SQL_DESC_FIXED_PREC_SCALE|SQLSMALLINT|ARD: nicht verwendete APD: nicht verwendeter IRD: r IPD: r|ARD: nicht verwendetes APD: nicht verwendeter IRD: d IPD: d [1]|  
|SQL_DESC_INDICATOR_PTR|SQLLEN|ARD: r/w APD: r/w ird: nicht verwendete IPD: nicht verwendet|ARD: NULL PTR APD: NULL PTR IRD: nicht verwendete IPD: nicht verwendet|  
|SQL_DESC_LABEL|SQLCHAR|ARD: nicht verwendetes APD: nicht verwendeter IRD: R IPD: nicht verwendet|ARD: nicht verwendetes APD: nicht verwendeter IRD: D IPD: nicht verwendet|  
|SQL_DESC_LENGTH|SQLULEN erstellt wurde|ARD: r/w APD: r/w ird: r IPD: r/w|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_LITERAL_PREFIX|SQLCHAR|ARD: nicht verwendetes APD: nicht verwendeter IRD: R IPD: nicht verwendet|ARD: nicht verwendetes APD: nicht verwendeter IRD: D IPD: nicht verwendet|  
|SQL_DESC_LITERAL_SUFFIX|SQLCHAR|ARD: nicht verwendetes APD: nicht verwendeter IRD: R IPD: nicht verwendet|ARD: nicht verwendetes APD: nicht verwendeter IRD: D IPD: nicht verwendet|  
|SQL_DESC_LOCAL_TYPE_NAME|SQLCHAR|ARD: nicht verwendete APD: nicht verwendeter IRD: r IPD: r|ARD: nicht verwendetes APD: nicht verwendeter IRD: d IPD: d [1]|  
|SQL_DESC_NAME|SQLCHAR|ARD: nicht verwendete APD: nicht verwendeter IRD: r IPD: r/W|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_NULLABLE|SQLSMALLINT|ARD: nicht verwendete APD: nicht verwendeter IRD: r IPD: r|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_NUM_PREC_RADIX|SQLINTEGER|ARD: r/w APD: r/w ird: r IPD: r/w|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_OCTET_LENGTH|SQLLEN|ARD: r/w APD: r/w ird: r IPD: r/w|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_OCTET_LENGTH_PTR|SQLLEN|ARD: r/w APD: r/w ird: nicht verwendete IPD: nicht verwendet|ARD: NULL PTR APD: NULL PTR IRD: nicht verwendete IPD: nicht verwendet|  
|SQL_DESC_PARAMETER_TYPE|SQLSMALLINT|ARD: nicht verwendete APD: nicht verwendeter IRD: nicht verwendete IPD: R/W|ARD: nicht verwendetes APD: nicht verwendeter IRD: nicht verwendete IPD: D = SQL_PARAM_INPUT|  
|SQL_DESC_PRECISION|SQLSMALLINT|ARD: r/w APD: r/w ird: r IPD: r/w|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_ROWVER|SQLSMALLINT|ARD: nicht verwendet<br /><br /> APD: nicht verwendet<br /><br /> IRD: R<br /><br /> IPD: R|ARD: nicht verwendet<br /><br /> APD: nicht verwendet<br /><br /> IRD: ND<br /><br /> IPD: ND|  
|SQL_DESC_SCALE|SQLSMALLINT|ARD: r/w APD: r/w ird: r IPD: r/w|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_SCHEMA_NAME|SQLCHAR|ARD: nicht verwendetes APD: nicht verwendeter IRD: R IPD: nicht verwendet|ARD: nicht verwendetes APD: nicht verwendeter IRD: D IPD: nicht verwendet|  
|SQL_DESC_SEARCHABLE|SQLSMALLINT|ARD: nicht verwendetes APD: nicht verwendeter IRD: R IPD: nicht verwendet|ARD: nicht verwendetes APD: nicht verwendeter IRD: D IPD: nicht verwendet|  
|SQL_DESC_TABLE_NAME|SQLCHAR|ARD: nicht verwendetes APD: nicht verwendeter IRD: R IPD: nicht verwendet|ARD: nicht verwendetes APD: nicht verwendeter IRD: D IPD: nicht verwendet|  
|SQL_DESC_TYPE|SQLSMALLINT|ARD: r/w APD: r/w ird: r IPD: r/w|ARD: SQL_C_DEFAULT APD: SQL_C_DEFAULT IRD: D IPD: ND|  
|SQL_DESC_TYPE_NAME|SQLCHAR|ARD: nicht verwendete APD: nicht verwendeter IRD: r IPD: r|ARD: nicht verwendetes APD: nicht verwendeter IRD: d IPD: d [1]|  
|SQL_DESC_UNNAMED|SQLSMALLINT|ARD: nicht verwendete APD: nicht verwendeter IRD: r IPD: r/W|ARD: ND APD: ND IRD: D IPD: ND|  
|SQL_DESC_UNSIGNED|SQLSMALLINT|ARD: nicht verwendete APD: nicht verwendeter IRD: r IPD: r|ARD: nicht verwendetes APD: nicht verwendeter IRD: d IPD: d [1]|  
|SQL_DESC_UPDATABLE|SQLSMALLINT|ARD: nicht verwendetes APD: nicht verwendeter IRD: R IPD: nicht verwendet|ARD: nicht verwendetes APD: nicht verwendeter IRD: D IPD: nicht verwendet|  
  
 [1] diese Felder werden nur definiert, wenn die IPD automatisch vom Treiber ausgefüllt wird. Wenn dies nicht der Fall ist, sind Sie nicht definiert. Wenn eine Anwendung versucht, diese Felder festzulegen, wird SQLSTATE HY091 (Ungültiger Deskriptorfeldbezeichner) zurückgegeben.  
  
 [2] das SQL_DESC_DATA_PTR Feld in der IPD kann festgelegt werden, um eine Konsistenzprüfung zu erzwingen. Bei einem nachfolgenden Aufrufen von **SQLGetDescField** oder **SQLGetDescRec**muss der Treiber nicht den Wert zurückgeben, auf den SQL_DESC_DATA_PTR festgelegt wurde.  
  
## <a name="fieldidentifier-argument"></a>Fieldidentifier-Argument  
 Das *fieldidentifier* -Argument gibt das festzulegende Deskriptorfeld an. Ein Deskriptor enthält den *deskriptorheader,* der aus den Header Feldern besteht, die im nächsten Abschnitt "Header Felder" beschrieben werden, sowie aus null oder mehr *deskriptordaten Sätzen,* bestehend aus den im Abschnitt nach dem Abschnitt "Header Felder" beschriebenen Daten Satz Feldern.  
  
## <a name="header-fields"></a>Header Felder  
 Jeder Deskriptor verfügt über einen Header, der aus den folgenden Feldern besteht:  
  
 **SQL_DESC_ALLOC_TYPE [alle]**  
 Dieses schreibgeschützte SQLSMALLINT-Header Feld gibt an, ob der Deskriptor automatisch vom Treiber oder explizit von der Anwendung zugeordnet wurde. Die Anwendung kann dieses Feld abrufen, aber nicht ändern. Das Feld wird vom Treiber auf SQL_DESC_ALLOC_AUTO festgelegt, wenn der Deskriptor vom Treiber automatisch zugeordnet wurde. Sie wird vom Treiber auf SQL_DESC_ALLOC_USER festgelegt, wenn der Deskriptor von der Anwendung explizit zugewiesen wurde.  
  
 **SQL_DESC_ARRAY_SIZE [Anwendungs Deskriptoren]**  
 In ARDs gibt dieses SQLULEN-Header Feld die Anzahl der Zeilen im Rowset an. Dies ist die Anzahl der Zeilen, die durch einen **SQLFetch** -oder **SQLFetchScroll** -Befehl zurückgegeben werden oder durch einen **SQLBulkOperations** -oder **SQLSetPos**-Aufrufs verarbeitet werden sollen.  
  
 In APDS gibt dieses SQLULEN-Header Feld die Anzahl der Werte für die einzelnen Parameter an.  
  
 Der Standardwert dieses Felds ist 1. Wenn SQL_DESC_ARRAY_SIZE größer als 1 ist, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR des APD-oder des ARD-Punkts auf Arrays. Die Kardinalität jedes Arrays ist gleich dem Wert dieses Felds.  
  
 Dieses Feld in der ARD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_ROW_ARRAY_SIZE-Attribut festgelegt werden. Dieses Feld in der APD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_PARAMSET_SIZE-Attribut festgelegt werden.  
  
 **SQL_DESC_ARRAY_STATUS_PTR [alle]**  
 Für jeden Deskriptortyp verweist dieses sqlusmallint *-Header Feld auf ein Array von sqlusmallint-Werten. Diese Arrays werden folgendermaßen benannt: Row Status Array (IRD), Parameter Status Array (IPD), Row Operation Array (ARD) und Parameter Operation Array (APD).  
  
 Im IRD verweist dieses Header Feld auf ein Zeilen Status Array, das nach einem **SQLBulkOperations**-, **SQLFetch**-, **SQLFetchScroll**-oder **SQLSetPos**-Aufrufs Statuswerte enthält. Das Array verfügt über so viele Elemente, wie Zeilen im Rowset vorhanden sind. Die Anwendung muss ein Array von sqlusmallints zuordnen und dieses Feld so festlegen, dass es auf das Array verweist. Das Feld wird standardmäßig auf einen NULL-Zeiger festgelegt. Der Treiber füllt das Array auf, es sei denn, das SQL_DESC_ARRAY_STATUS_PTR Feld ist auf einen NULL-Zeiger festgelegt. in diesem Fall werden keine Status Werte generiert, und das Array wird nicht aufgefüllt.  
  
> [!CAUTION]  
>  Das Treiber Verhalten ist nicht definiert, wenn die Anwendung die Elemente des Zeilen Status Arrays festlegt, auf das das SQL_DESC_ARRAY_STATUS_PTR-Feld von IRD zeigt.  
  
 Das Array wird anfänglich durch einen-Aufrufs von **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**oder **SQLSetPos**aufgefüllt. Wenn der-Befehl SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO nicht zurückgegeben hat, ist der Inhalt des Arrays, auf das von diesem Feld verwiesen wird, nicht definiert. Die Elemente im Array können die folgenden Werte enthalten:  
  
-   SQL_ROW_SUCCESS: die Zeile wurde erfolgreich abgerufen und seit dem letzten Abruf nicht geändert.  
  
-   SQL_ROW_SUCCESS_WITH_INFO: die Zeile wurde erfolgreich abgerufen und seit dem letzten Abruf nicht geändert. Es wurde jedoch eine Warnung zur Zeile zurückgegeben.  
  
-   SQL_ROW_ERROR: Fehler beim Abrufen der Zeile.  
  
-   SQL_ROW_UPDATED: die Zeile wurde erfolgreich abgerufen und seit der letzten abgerufenen Aktualisierung aktualisiert. Wenn die Zeile erneut abgerufen wird, lautet der Status SQL_ROW_SUCCESS.  
  
-   SQL_ROW_DELETED: die Zeile wurde gelöscht, seit Sie zuletzt abgerufen wurde.  
  
-   SQL_ROW_ADDED: die Zeile wurde von **SQLBulkOperations**eingefügt. Wenn die Zeile erneut abgerufen wird, lautet der Status SQL_ROW_SUCCESS.  
  
-   SQL_ROW_NOROW: das Rowset hat das Ende des Resultsets überlappen, und es wurde keine Zeile zurückgegeben, die diesem Element des Zeilen Status Arrays entsprach.  
  
 Dieses Feld in IRD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_ROW_STATUS_PTR-Attribut festgelegt werden.  
  
 Das SQL_DESC_ARRAY_STATUS_PTR-Feld des IRD ist erst gültig, nachdem SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben wurde. Wenn es sich bei dem Rückgabecode nicht um einen der folgenden handelt, ist der Speicherort, auf den SQL_DESC_ROWS_PROCESSED_PTR verweist, nicht definiert.  
  
 In der IPD zeigt dieses Header Feld auf ein Parameter Status Array, das Statusinformationen für jeden Satz von Parameterwerten enthält, nachdem **SQLExecute** oder **SQLExecDirect**aufgerufen wurde. Wenn der-Befehl **SQLExecute** oder **SQLExecDirect** nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben hat, ist der Inhalt des Arrays, auf das dieses Feld verweist, nicht definiert. Die Anwendung muss ein Array von sqlusmallints zuordnen und dieses Feld so festlegen, dass es auf das Array verweist. Der Treiber füllt das Array auf, es sei denn, das SQL_DESC_ARRAY_STATUS_PTR Feld ist auf einen NULL-Zeiger festgelegt. in diesem Fall werden keine Status Werte generiert, und das Array wird nicht aufgefüllt. Die Elemente im Array können die folgenden Werte enthalten:  
  
-   SQL_PARAM_SUCCESS: die SQL-Anweisung wurde für diesen Parametersatz erfolgreich ausgeführt.  
  
-   SQL_PARAM_SUCCESS_WITH_INFO: die SQL-Anweisung wurde für diesen Parametersatz erfolgreich ausgeführt. Warn Informationen sind jedoch in der Diagnosedaten Struktur verfügbar.  
  
-   SQL_PARAM_ERROR: Fehler beim Verarbeiten dieser Gruppe von Parametern. Zusätzliche Fehlerinformationen sind in der Diagnosedaten Struktur verfügbar.  
  
-   SQL_PARAM_UNUSED: dieser Parametersatz wurde nicht verwendet, möglicherweise aufgrund der Tatsache, dass ein vorheriger Parametersatz einen Fehler verursacht hat, der die weitere Verarbeitung abgebrochen hat, oder weil SQL_PARAM_IGNORE für diesen Parametersatz in dem Array festgelegt wurde, das vom SQL_DESC_ARRAY_STATUS_PTR-Feld der APD angegeben wurde.  
  
-   SQL_PARAM_DIAG_UNAVAILABLE: Diagnoseinformationen sind nicht verfügbar. Dies ist beispielsweise der Fall, wenn der Treiber Arrays von Parametern als monolithische Einheit behandelt und daher nicht diese Ebene der Fehlerinformationen generiert.  
  
 Dieses Feld in der IPD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_PARAM_STATUS_PTR-Attribut festgelegt werden.  
  
 In der ARD zeigt dieses Header Feld auf ein Zeilen Vorgangs Array von Werten, die von der Anwendung festgelegt werden können, um anzugeben, ob diese Zeile für **SQLSetPos** -Vorgänge ignoriert werden soll. Die Elemente im Array können die folgenden Werte enthalten:  
  
-   SQL_ROW_PROCEED: die Zeile wird mithilfe von **SQLSetPos**in den Massen Vorgang eingeschlossen. (Diese Einstellung garantiert nicht, dass der Vorgang in der Zeile erfolgt. Wenn in der Zeile der Status SQL_ROW_ERROR im Status Array "IRD" angezeigt wird, ist der Treiber möglicherweise nicht in der Lage, den Vorgang in der Zeile auszuführen.)  
  
-   SQL_ROW_IGNORE: die Zeile wird mithilfe von **SQLSetPos**vom Massen Vorgang ausgeschlossen.  
  
 Wenn keine Elemente des Arrays festgelegt sind, werden alle Zeilen in den Massen Vorgang eingeschlossen. Wenn der Wert im SQL_DESC_ARRAY_STATUS_PTR-Feld der ARD ein NULL-Zeiger ist, werden alle Zeilen in den Massen Vorgang eingeschlossen. die Interpretation ist identisch mit dem Zeiger, der auf ein gültiges Array zeigt, und alle Elemente des Arrays wurden SQL_ROW_PROCEED. Wenn ein Element im Array auf SQL_ROW_IGNORE festgelegt ist, wird der Wert im Zeilen Status Array für die ignorierte Zeile nicht geändert.  
  
 Dieses Feld in der ARD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_ROW_OPERATION_PTR-Attribut festgelegt werden.  
  
 In der APD zeigt dieses Header Feld auf ein Parameter Vorgangs Array von Werten, die von der Anwendung festgelegt werden können, um anzugeben, ob dieser Satz von Parametern ignoriert werden soll, wenn **SQLExecute** oder **SQLExecDirect** aufgerufen wird. Die Elemente im Array können die folgenden Werte enthalten:  
  
-   SQL_PARAM_PROCEED: der Satz von Parametern ist im **SQLExecute** -oder **SQLExecDirect** -Befehl enthalten.  
  
-   SQL_PARAM_IGNORE: der Satz von Parametern wird vom **SQLExecute** -oder **SQLExecDirect** -Befehl ausgeschlossen.  
  
 Wenn keine Elemente des Arrays festgelegt sind, werden alle Sätze von Parametern im Array in den Aufrufen **SQLExecute** oder **SQLExecDirect** verwendet. Wenn der Wert im SQL_DESC_ARRAY_STATUS_PTR-Feld der APD ein NULL-Zeiger ist, werden alle Parametersätze verwendet; die Interpretation ist identisch mit dem Zeiger, der auf ein gültiges Array zeigt, und alle Elemente des Arrays wurden SQL_PARAM_PROCEED.  
  
 Dieses Feld in der APD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_PARAM_OPERATION_PTR-Attribut festgelegt werden.  
  
 **SQL_DESC_BIND_OFFSET_PTR [Anwendungs Deskriptoren]**  
 Dieses sqllen *-Header Feld verweist auf den Bindungs Offset. Standardmäßig ist es auf einen NULL-Zeiger festgelegt. Wenn dieses Feld kein NULL-Zeiger ist, dereferenziert der Treiber den Zeiger und fügt jedem der zurück gestellten Felder, die einen Wert ungleich NULL im Deskriptordatensatz (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR) zur Abruf Zeit aufweisen, den Wert des dereferenzierten Werts hinzu und verwendet die neuen Zeiger Werte bei der Bindung.  
  
 Der Bindungs Offset wird immer direkt den Werten in den Feldern SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR hinzugefügt. Wenn der Offset in einen anderen Wert geändert wird, wird der neue Wert dem Wert in jedem Deskriptorfeld weiterhin direkt hinzugefügt. Der neue Offset wird nicht dem Feldwert plus einem früheren Offset hinzugefügt.  
  
 Dieses Feld ist ein *Verzögertes Feld*, das zum Zeitpunkt der Festlegung nicht verwendet wird, sondern zu einem späteren Zeitpunkt vom Treiber verwendet wird, wenn die Adressen für Datenpuffer bestimmt werden müssen.  
  
 Dieses Feld in der ARD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_ROW_BIND_OFFSET_PTR-Attribut festgelegt werden. Dieses Feld in der ARD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_PARAM_BIND_OFFSET_PTR-Attribut festgelegt werden.  
  
 Weitere Informationen finden Sie in der Beschreibung der Zeilen bezogenen Bindung in [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) und [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 **SQL_DESC_BIND_TYPE [Anwendungs Deskriptoren]**  
 Mit diesem SQLUINTEGER-Header Feld wird die Bindungs Ausrichtung festgelegt, die zum Binden von Spalten oder Parametern verwendet wird.  
  
 In ARDs gibt dieses Feld die Bindungs Ausrichtung an, wenn **SQLFetchScroll** oder **SQLFetch** für das zugeordnete Anweisungs Handle aufgerufen wird.  
  
 Um die spaltenweise Bindung für Spalten auszuwählen, wird dieses Feld auf SQL_BIND_BY_COLUMN (Standard) festgelegt.  
  
 Dieses Feld in der ARD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_ROW_BIND_TYPE- *Attribut*festgelegt werden.  
  
 In APDS gibt dieses Feld die Bindungs Ausrichtung an, die für dynamische Parameter verwendet werden soll.  
  
 Um die spaltenweise Bindung für Parameter auszuwählen, wird dieses Feld auf SQL_BIND_BY_COLUMN (Standard) festgelegt.  
  
 Dieses Feld in der APD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_PARAM_BIND_TYPE- *Attribut*festgelegt werden.  
  
 **SQL_DESC_COUNT [alle]**  
 Dieses SQLSMALLINT-Header Feld gibt den 1-basierten Index des mit der höchsten Zahl nummerierten Datensatzes an, der Daten enthält. Wenn der Treiber die Datenstruktur für den Deskriptor festlegt, muss er auch das SQL_DESC_COUNT Feld festlegen, um anzuzeigen, wie viele Datensätze wichtig sind. Wenn eine Anwendung eine Instanz dieser Datenstruktur reserviert, muss nicht angegeben werden, für wie viele Datensätze Platz reserviert werden soll. Wenn die Anwendung den Inhalt der Datensätze angibt, führt der Treiber alle erforderlichen Maßnahmen aus, um sicherzustellen, dass das Deskriptorhandle auf eine Datenstruktur der angemessenen Größe verweist.  
  
 SQL_DESC_COUNT ist nicht für alle Datenspalten, die gebunden sind (wenn das Feld in einer ARD ist), oder für alle Parameter, die gebunden sind (wenn das Feld in einer APD ist), aber die Nummer des mit der höchsten nummerierten Datensatzes. Wenn die Bindung der höchsten nummerierten Spalte oder des Parameters aufgehoben wird, wird SQL_DESC_COUNT in die Nummer der nächsthöheren Spalte oder des nächsthöheren Parameters geändert. Wenn eine Spalte oder ein Parameter mit einer Zahl, die kleiner ist als die Nummer der höchsten nummerierten Spalte ist SQL_DESC_COUNT, nicht gebunden ist (durch Aufrufen von **SQLBindCol** mit dem *targetvalueptr* -Argument, das auf einen NULL-Zeiger festgelegt ist, oder **SQLBindParameter** , bei dem das *ParameterValuePtr* -Argument auf einen NULL-Zeiger festgelegt ist), Wenn zusätzliche Spalten oder Parameter mit Zahlen gebunden werden, die größer als der mit der höchsten Zahl nummerierte Datensatz sind, der Daten enthält, erhöht der Treiber automatisch den Wert im Feld SQL_DESC_COUNT. Wenn alle Spalten aufgehoben werden, indem **SQLFreeStmt** mit der Option SQL_UNBIND aufgerufen wird, werden die SQL_DESC_COUNT Felder in der Datei "ARD" und "IRD" auf "0" festgelegt. Wenn **SQLFreeStmt** mit der Option SQL_RESET_PARAMS aufgerufen wird, werden die SQL_DESC_COUNT Felder in APD und IPD auf 0 festgelegt.  
  
 Der Wert in SQL_DESC_COUNT kann explizit durch eine Anwendung durch Aufrufen von **SQLSetDescField**festgelegt werden. Wenn der Wert in SQL_DESC_COUNT explizit verringert wird, werden alle Datensätze mit Zahlen, die größer sind als der neue Wert in SQL_DESC_COUNT, tatsächlich entfernt. Wenn der Wert in SQL_DESC_COUNT explizit auf 0 festgelegt ist und sich das Feld in einer ARD befindet, werden alle Datenpuffer außer einer gebundenen Lesezeichen Spalte freigegeben.  
  
 Die Anzahl der Datensätze in diesem Feld einer ARD enthält keine gebundene Lesezeichen Spalte. Die Bindung einer Lesezeichen Spalte kann nur aufgehoben werden, indem das SQL_DESC_DATA_PTR-Feld auf einen NULL-Zeiger festgelegt wird.  
  
 **SQL_DESC_ROWS_PROCESSED_PTR [Implementierungs Deskriptoren]**  
 In einem IRD zeigt dieses SQLULEN \* -Header Feld auf einen Puffer, der die Anzahl der Zeilen enthält, die nach einem **SQLFetch** -oder **SQLFetchScroll**-Befehl abgerufen wurden, oder die Anzahl der Zeilen, die bei einem Massen Vorgang betroffen sind, der durch einen **SQLBulkOperations** -oder **SQLSetPos**-Aufrufs ausgeführt wird, einschließlich Fehler Zeilen.  
  
 In einer IPD zeigt dieses SQLUINTEGER *-Header Feld auf einen Puffer, der die Anzahl der verarbeiteten Parametersätze enthält, einschließlich der Fehler Sätze. Wenn dies ein NULL-Zeiger ist, wird keine Zahl zurückgegeben.  
  
 SQL_DESC_ROWS_PROCESSED_PTR ist nur gültig, nachdem SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO nach einem **SQLFetch** -oder **SQLFetchScroll** -Befehl (bei einem IRD-Feld) oder **SQLExecute**, **SQLExecDirect**oder **SQLParamData** (für ein IPD-Feld) zurückgegeben wurde. Wenn der aufzurufende-Puffer, auf den dieses Feld zeigt, nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgibt, ist der Inhalt des Puffers nicht definiert, es sei denn, er gibt SQL_NO_DATA zurück. in diesem Fall wird der Wert im Puffer auf 0 festgelegt.  
  
 Dieses Feld in der ARD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_ROWS_FETCHED_PTR-Attribut festgelegt werden. Dieses Feld in der APD kann auch durch Aufrufen von **SQLSetStmtAttr** mit dem SQL_ATTR_PARAMS_PROCESSED_PTR-Attribut festgelegt werden.  
  
 Der Puffer, auf den dieses Feld zeigt, wird von der Anwendung zugeordnet. Es handelt sich um einen verzögerten Ausgabepuffer, der vom Treiber festgelegt wird. Standardmäßig ist es auf einen NULL-Zeiger festgelegt.  
  
## <a name="record-fields"></a>Daten Satz Felder  
 Jeder Deskriptor enthält einen oder mehrere Datensätze, die aus Feldern bestehen, die je nach Typ des Deskriptors entweder Spaltendaten oder dynamische Parameter definieren. Jeder Datensatz ist eine komplette Definition einer einzelnen Spalte oder eines einzelnen Parameters.  
  
 **SQL_DESC_AUTO_UNIQUE_VALUE [unds]**  
 Dieses schreibgeschützte SQLINTEGER-Daten Satz Feld enthält SQL_TRUE, wenn die Spalte eine automatisch inkrementbare Spalte ist, oder SQL_FALSE, wenn die Spalte keine automatisch inkrementierende Spalte ist. Dieses Feld ist schreibgeschützt, aber die zugrunde liegende Spalte, die automatisch inkrementiert wird, ist nicht unbedingt schreibgeschützt.  
  
 **SQL_DESC_BASE_COLUMN_NAME [unds]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatz-Feld enthält den Basis Spaltennamen für die Resultsetspalte. Wenn kein Basis Spaltenname vorhanden ist (wie bei Spalten, bei denen es sich um Ausdrücke handelt), enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_BASE_TABLE_NAME [unds]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatz-Feld enthält den Basistabellen Namen für die Resultsetspalte. Wenn ein Basistabellen Name nicht definiert werden kann oder nicht anwendbar ist, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_CASE_SENSITIVE [Implementierungs Deskriptoren]**  
 Dieses schreibgeschützte SQLINTEGER-Daten Satz Feld enthält SQL_TRUE, wenn die Spalte oder der Parameter bei Sortierungen und vergleichen als Unterscheidung nach Groß-/Kleinschreibung behandelt wird, oder SQL_FALSE, wenn die Spalte bei Sortierungen und vergleichen nicht als Unterscheidung nach Groß-/Kleinschreibung behandelt wird oder wenn es sich um eine nicht-Zeichen  
  
 **SQL_DESC_CATALOG_NAME [unds]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatz-Feld enthält den Katalog für die Basistabelle, die die Spalte enthält. Der Rückgabewert ist Treiber abhängig, wenn die Spalte ein Ausdruck ist, oder wenn die Spalte Teil einer Sicht ist. Wenn die Datenquelle keine Kataloge unterstützt oder der Katalog nicht bestimmt werden kann, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_CONCISE_TYPE [alle]**  
 Dieses SQLSMALLINT-Header Feld gibt den präzisen Datentyp für alle Datentypen an, einschließlich der DateTime-und interval-Datentypen.  
  
 Die Werte in den Feldern SQL_DESC_CONCISE_TYPE, SQL_DESC_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE sind voneinander abhängig. Jedes Mal, wenn eines der Felder festgelegt ist, muss das andere ebenfalls festgelegt werden. SQL_DESC_CONCISE_TYPE können durch einen **SQLBindCol** -oder **SQLBindParameter**-oder SQLSetDescField-Befehl festgelegt werden. **SQLSetDescField** SQL_DESC_TYPE können durch einen **SQLSetDescField** -oder **SQLSetDescRec**-Befehl festgelegt werden.  
  
 Wenn SQL_DESC_CONCISE_TYPE auf einen präzisen Datentyp festgelegt ist, der kein Intervall-oder DateTime-Datentyp ist, wird das SQL_DESC_TYPE Feld auf denselben Wert festgelegt, und das SQL_DESC_DATETIME_INTERVAL_CODE Feld ist auf 0 festgelegt.  
  
 Wenn SQL_DESC_CONCISE_TYPE auf den präzisen Datentyp DateTime oder interval festgelegt ist, wird das SQL_DESC_TYPE Feld auf den entsprechenden ausführlichen Typ (SQL_DATETIME oder SQL_INTERVAL) festgelegt, und das SQL_DESC_DATETIME_INTERVAL_CODE Feld wird auf den entsprechenden Subcode festgelegt.  
  
 **SQL_DESC_DATA_PTR [Anwendungs Deskriptoren und IPDS]**  
 Dieses SQLPOINTER-Daten Satz Feld verweist auf eine Variable, die den Parameterwert (für APDs) oder den Spaltenwert (für ARDs) enthält. Dieses Feld ist ein *Verzögertes Feld*. Sie wird nicht zum Zeitpunkt der Festlegung verwendet, sondern wird zu einem späteren Zeitpunkt vom Treiber zum Abrufen von Daten verwendet.  
  
 Die Bindung der durch das SQL_DESC_DATA_PTR-Feld der ARD angegebenen Spalte wird aufgehoben, wenn das *targetvalueptr* -Argument in einem **SQLBindCol** -Befehl ein NULL-Zeiger ist oder wenn das SQL_DESC_DATA_PTR Feld in der ARD durch einen **SQLSetDescField** -oder **SQLSetDescRec** -Befehl auf einen NULL-Zeiger festgelegt wird. Andere Felder sind nicht betroffen, wenn das SQL_DESC_DATA_PTR Feld auf einen NULL-Zeiger festgelegt ist.  
  
 Wenn der **SQLFetch** -oder **SQLFetchScroll** -Befehl, der den Puffer füllt, auf den dieses Feld zeigt, nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben hat, ist der Inhalt des Puffers nicht definiert.  
  
 Wenn das SQL_DESC_DATA_PTR-Feld eines APD, einer ARD oder einer IPD festgelegt ist, überprüft der Treiber, ob der Wert im Feld SQL_DESC_TYPE einen der gültigen ODBC-C-Datentypen oder einen treiberspezifischen Datentyp enthält und ob alle anderen Felder, die sich auf die Datentypen auswirken, konsistent sind. Die Eingabeaufforderung für eine Konsistenzprüfung ist die einzige Verwendung des SQL_DESC_DATA_PTR-Felds einer IPD. Insbesondere, wenn eine Anwendung das SQL_DESC_DATA_PTR-Feld einer IPD festlegt und später **SQLGetDescField** für dieses Feld aufruft, wird nicht notwendigerweise der Wert zurückgegeben, den Sie festgelegt hat. Weitere Informationen finden Sie unter "Konsistenzprüfungen" in [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 **SQL_DESC_DATETIME_INTERVAL_CODE [alle]**  
 Dieses SQLSMALLINT-Daten Satz Feld enthält den Subcode für den spezifischen DateTime-oder Interval-Datentyp, wenn das SQL_DESC_TYPE Feld SQL_DATETIME oder SQL_INTERVAL ist. Dies gilt sowohl für SQL-als auch für C-Datentypen. Der Code besteht aus dem Datentyp Namen mit "Code", der entweder "Type" oder "C_TYPE" (für DateTime-Typen) ersetzt, oder "Code" ersetzt "Interval" oder "C_INTERVAL" (für Intervall Typen).  
  
 Wenn SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE in einem Anwendungs Deskriptor auf SQL_C_DEFAULT festgelegt sind und der Deskriptor keinem Anweisungs Handle zugeordnet ist, sind die Inhalte der SQL_DESC_DATETIME_INTERVAL_CODE nicht definiert.  
  
 Dieses Feld kann für die DateTime-Datentypen festgelegt werden, die in der folgenden Tabelle aufgeführt sind.  
  
|DateTime-Typen|DATETIME_INTERVAL_CODE|  
|--------------------|------------------------------|  
|SQL_TYPE_DATE/SQL_C_TYPE_DATE|SQL_CODE_DATE|  
|SQL_TYPE_TIME/SQL_C_TYPE_TIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP/SQL_C_TYPE_TIMESTAMP|SQL_CODE_TIMESTAMP|  
  
 Dieses Feld kann für die in der folgenden Tabelle aufgeführten Intervall Datentypen festgelegt werden.  
  
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
  
 Weitere Informationen zu den Daten Intervallen und diesem Feld finden Sie unter [Datentyp Bezeichner und Deskriptoren](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md).  
  
 **SQL_DESC_DATETIME_INTERVAL_PRECISION [alle]**  
 Dieses SQLINTEGER-Daten Satz Feld enthält die angegebene Intervall Genauigkeit, wenn das SQL_DESC_TYPE Feld SQL_INTERVAL ist. Wenn das SQL_DESC_DATETIME_INTERVAL_CODE-Feld auf einen Interval-Datentyp festgelegt ist, wird dieses Feld auf die standardmäßige Intervall führende Genauigkeit festgelegt.  
  
 **SQL_DESC_DISPLAY_SIZE [unds]**  
 Dieses schreibgeschützte SQLINTEGER-Daten Satz Feld enthält die maximale Anzahl von Zeichen, die erforderlich sind, um die Daten aus der Spalte anzuzeigen.  
  
 **SQL_DESC_FIXED_PREC_SCALE [Implementierungs Deskriptoren]**  
 Dieses schreibgeschützte SQLSMALLINT-Daten Satz Feld ist auf SQL_TRUE festgelegt, wenn es sich bei der Spalte um eine genaue numerische Spalte handelt, die eine dezimalskala mit fester Genauigkeit und einer Größe ungleich NULL aufweist, oder SQL_FALSE, wenn die Spalte keine genaue numerische Spalte mit fester Genauigkeit und Dezimalzahl ist.  
  
 **SQL_DESC_INDICATOR_PTR [Anwendungs Deskriptoren]**  
 In ARDs verweist dieses sqllen *-Daten Satz Feld auf die Indikator Variable. Diese Variable enthält SQL_NULL_DATA, wenn der Spaltenwert NULL ist. Für APDS ist die Indikator Variable auf SQL_NULL_DATA festgelegt, um dynamische NULL-Argumente anzugeben. Andernfalls ist die Variable 0 (null) (es sei denn, die Werte in SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR sind derselbe Zeiger).  
  
 Wenn das SQL_DESC_INDICATOR_PTR-Feld in einer ARD ein NULL-Zeiger ist, wird der Treiber daran gehindert, Informationen darüber zurückzugeben, ob die Spalte NULL ist oder nicht. Wenn die Spalte NULL ist und SQL_DESC_INDICATOR_PTR ein NULL-Zeiger ist, wird SQLSTATE 22002 (Indikator Variable erforderlich, aber nicht angegeben) zurückgegeben, wenn der Treiber versucht, den Puffer nach einem **SQLFetch** -oder **SQLFetchScroll**-Befehl aufzufüllen. Wenn der Befehl **SQLFetch** oder **SQLFetchScroll** nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben hat, ist der Inhalt des Puffers nicht definiert.  
  
 Das SQL_DESC_INDICATOR_PTR Feld bestimmt, ob das Feld, auf das von SQL_DESC_OCTET_LENGTH_PTR verwiesen wird, festgelegt ist. Wenn der Datenwert für eine Spalte NULL ist, legt der Treiber die Indikator Variable auf SQL_NULL_DATA fest. Das Feld, auf das SQL_DESC_OCTET_LENGTH_PTR verweist, wird nicht festgelegt. Wenn während des Abruf Vorgangs kein NULL-Wert gefunden wird, wird der Puffer, auf den SQL_DESC_INDICATOR_PTR verweist, auf NULL festgelegt, und der Puffer, auf den SQL_DESC_OCTET_LENGTH_PTR verweist, ist auf die Länge der Daten festgelegt.  
  
 Wenn das SQL_DESC_INDICATOR_PTR-Feld in einer APD ein NULL-Zeiger ist, kann die Anwendung diesen Deskriptordatensatz nicht zum Angeben von NULL-Argumenten verwenden.  
  
 Dieses Feld ist ein *Verzögertes Feld*, das zum Zeitpunkt der Festlegung nicht verwendet wird, aber zu einem späteren Zeitpunkt vom Treiber verwendet wird, um die NULL-Zulässigkeit (für ARDs) anzugeben oder die NULL-Zulässigkeit (für APDs) zu bestimmen.  
  
 **SQL_DESC_LABEL [unds]**  
 Dieses schreibgeschützte SQLCHAR *-Daten Satz Feld enthält die Spalten Bezeichnung oder den Titel. Wenn die Spalte nicht über eine Bezeichnung verfügt, enthält diese Variable den Spaltennamen. Wenn die Spalte unbenannt und nicht beschriftet ist, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_LENGTH [alle]**  
 Dieses SQLULEN-Daten Satz Feld ist entweder die maximale oder die tatsächliche Länge einer Zeichenfolge in Zeichen oder ein binärer Datentyp in Bytes. Dies ist die maximale Länge für einen Datentyp mit fester Länge oder die tatsächliche Länge für einen Datentyp mit variabler Länge. Der Wert schließt immer das NULL-Terminierungs Zeichen aus, das die Zeichenfolge beendet. Bei Werten, deren Typ "SQL_TYPE_DATE", "SQL_TYPE_TIME", "SQL_TYPE_TIMESTAMP" oder einem der SQL-Intervall Datentypen ist, enthält dieses Feld die Länge in Zeichen der Zeichen folgen Darstellung des DateTime-oder Interval-Werts.  
  
 Der Wert in diesem Feld kann sich von dem Wert für "length" unterscheiden, wie er in ODBC 2 *. x*definiert ist. Weitere Informationen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_LITERAL_PREFIX [unds]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatz-Feld enthält die Zeichen oder Zeichen, die der Treiber als Präfix für ein literaldieses Datentyps erkennt. Diese Variable enthält eine leere Zeichenfolge für einen Datentyp, für den kein literalpräfix anwendbar ist.  
  
 **SQL_DESC_LITERAL_SUFFIX [unds]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatz-Feld enthält die Zeichen oder Zeichen, die der Treiber als Suffix für ein literaldieses Datentyps erkennt. Diese Variable enthält eine leere Zeichenfolge für einen Datentyp, für den kein LiteralSuffix anwendbar ist.  
  
 **SQL_DESC_LOCAL_TYPE_NAME [Implementierungs Deskriptoren]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatz-Feld enthält alle lokalisierten (in der systemeigenen Sprache) Namen für den Datentyp, der sich vom regulären Namen des Datentyps unterscheiden kann. Wenn kein lokalisierter Name vorhanden ist, wird eine leere Zeichenfolge zurückgegeben. Dieses Feld dient nur zu Anzeige Zwecken.  
  
 **SQL_DESC_NAME [Implementierungs Deskriptoren]**  
 Dieses SQLCHAR *-Daten Satz Feld in einem Zeilen Deskriptor enthält den Spaltenalias, sofern zutreffend. Wenn der Spaltenalias nicht zutrifft, wird der Spaltenname zurückgegeben. In beiden Fällen legt der Treiber das SQL_DESC_UNNAMED-Feld auf SQL_NAMED fest, wenn das SQL_DESC_NAME Feld festgelegt wird. Wenn kein Spaltenname oder Spaltenalias vorhanden ist, gibt der Treiber im Feld SQL_DESC_NAME eine leere Zeichenfolge zurück und legt das SQL_DESC_UNNAMED Feld auf SQL_UNNAMED fest.  
  
 Eine Anwendung kann das SQL_DESC_NAME-Feld einer IPD auf einen Parameternamen oder Alias festlegen, um die Parameter gespeicherter Prozeduren anhand ihres Namens anzugeben. (Weitere Informationen finden Sie unter [Binden von Parametern anhand des Namens (benannte Parameter)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md).) Das SQL_DESC_NAME-Feld eines IRD ist ein Schreib geschütztes Feld. SQLSTATE HY091 (Ungültiger Deskriptorfeldbezeichner) wird zurückgegeben, wenn eine Anwendung versucht, Sie festzulegen.  
  
 In IPDS ist dieses Feld nicht definiert, wenn der Treiber keine benannten Parameter unterstützt. Wenn der Treiber benannte Parameter unterstützt und Parameter beschreiben kann, wird der Parameter Name in diesem Feld zurückgegeben.  
  
 **SQL_DESC_NULLABLE [Implementierungs Deskriptoren]**  
 In "unds" ist dieses schreibgeschützte SQLSMALLINT-Daten Satz Feld SQL_NULLABLE, wenn die Spalte NULL-Werte aufweisen kann, SQL_NO_NULLS, wenn die Spalte keine NULL-Werte enthält, oder SQL_NULLABLE_UNKNOWN, wenn nicht bekannt ist, ob die Spalte NULL-Werte akzeptiert. Dieses Feld bezieht sich auf die Resultsetspalte, nicht auf die Basis Spalte.  
  
 In IPDS ist dieses Feld immer auf SQL_NULLABLE festgelegt, da dynamische Parameter immer NULL-Werte zulassen und von einer Anwendung nicht festgelegt werden können.  
  
 **SQL_DESC_NUM_PREC_RADIX [alle]**  
 Dieses SQLINTEGER-Feld enthält den Wert 2, wenn der Datentyp im SQL_DESC_TYPE Feld ein ungefähren numerischer Datentyp ist, da das SQL_DESC_PRECISION Feld die Anzahl der Bits enthält. Dieses Feld enthält den Wert 10, wenn der Datentyp im Feld SQL_DESC_TYPE ein genauer numerischer Datentyp ist, da das SQL_DESC_PRECISION Feld die Anzahl der Dezimalstellen enthält. Dieses Feld wird für alle nicht numerischen Datentypen auf 0 festgelegt.  
  
 **SQL_DESC_OCTET_LENGTH [alle]**  
 Dieses sqllen-Daten Satz Feld enthält die Länge einer Zeichenfolge oder eines Binär Datentyps (in Byte). Für Zeichen-oder Binär Typen mit fester Länge ist dies die tatsächliche Länge in Bytes. Für Zeichen-oder Binär Typen mit variabler Länge ist dies die maximale Länge in Bytes. Dieser Wert schließt den Platz für das NULL-Beendigungs Zeichen für Implementierungs Deskriptoren immer aus und enthält immer Leerzeichen für das NULL-Terminierungs Zeichen für Anwendungs Deskriptoren. Für Anwendungsdaten enthält dieses Feld die Größe des Puffers. Für APDS ist dieses Feld nur für Ausgabe-oder Eingabe-/Ausgabeparameter definiert.  
  
 **SQL_DESC_OCTET_LENGTH_PTR [Anwendungs Deskriptoren]**  
 Dieses sqllen *-Daten Satz Feld verweist auf eine Variable, die die Gesamtlänge eines dynamischen Arguments (für Parameter Deskriptoren) oder eines gebundenen Spaltenwerts (für Zeilen Deskriptoren) in Bytes enthält.  
  
 Bei einem APD wird dieser Wert für alle Argumente außer Zeichenfolge und Binär ignoriert. Wenn dieses Feld auf SQL_NTS zeigt, muss das dynamische Argument auf Null enden. Um anzugeben, dass es sich bei einem gebundenen Parameter um einen Data-at-Execution-Parameter handelt, legt eine Anwendung dieses Feld im entsprechenden Datensatz der APD auf eine Variable fest, die zur Ausführungszeit den Wert SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC Makros enthält. Wenn mehr als ein solches Feld vorhanden ist, kann SQL_DESC_DATA_PTR auf einen Wert festgelegt werden, der den Parameter eindeutig identifiziert, damit die Anwendung ermitteln kann, welcher Parameter angefordert wird.  
  
 Wenn das OCTET_LENGTH_PTR-Feld einer ARD ein NULL-Zeiger ist, gibt der Treiber keine Längen Informationen für die Spalte zurück. Wenn das SQL_DESC_OCTET_LENGTH_PTR-Feld eines APD ein NULL-Zeiger ist, geht der Treiber davon aus, dass Zeichen folgen und Binär Werte auf Null enden. (Binäre Werte dürfen nicht mit Null enden, sondern sollten eine Länge aufweisen, um das Abschneiden zu vermeiden.)  
  
 Wenn der **SQLFetch** -oder **SQLFetchScroll** -Befehl, der den Puffer füllt, auf den dieses Feld zeigt, nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben hat, ist der Inhalt des Puffers nicht definiert. Dieses Feld ist ein *Verzögertes Feld*. Sie wird nicht verwendet, wenn Sie festgelegt wird, sondern wird zu einem späteren Zeitpunkt vom Treiber verwendet, um die Oktett-Länge der Daten zu ermitteln oder anzugeben.  
  
 **SQL_DESC_PARAMETER_TYPE [IPDS]**  
 Dieses SQLSMALLINT-Daten Satz Feld ist auf SQL_PARAM_INPUT für einen Eingabeparameter festgelegt, SQL_PARAM_INPUT_OUTPUT für einen Eingabe-/Ausgabeparameter, SQL_PARAM_OUTPUT für einen Output-Parameter, SQL_PARAM_INPUT_OUTPUT_STREAM für einen eingegebenen/Ausgabestream-Parameter oder SQL_PARAM_OUTPUT_STREAM für einen Output-Stream-Parameter. Er ist standardmäßig auf SQL_PARAM_INPUT festgelegt.  
  
 Bei einer IPD wird das Feld standardmäßig auf SQL_PARAM_INPUT festgelegt, wenn die IPD nicht automatisch vom Treiber aufgefüllt wird (das Attribut der SQL_ATTR_ENABLE_AUTO_IPD Anweisung ist SQL_FALSE). Eine Anwendung sollte dieses Feld in der IPD für Parameter festlegen, die keine Eingabeparameter sind.  
  
 **SQL_DESC_PRECISION [alle]**  
 Dieses SQLSMALLINT-Daten Satz Feld enthält die Anzahl der Ziffern für einen exakten numerischen Typ, die Anzahl der Bits in der Mantisse (binäre Genauigkeit) für einen ungefähren numerischen Typ oder die Anzahl der Ziffern in der Komponente für Sekundenbruchteile für den SQL_TYPE_TIME-, SQL_TYPE_TIMESTAMP-oder SQL_INTERVAL_SECOND-Datentyp. Dieses Feld ist für alle anderen Datentypen nicht definiert.  
  
 Der Wert in diesem Feld kann sich von dem Wert für "Genauigkeit" unterscheiden, wie er in ODBC 2 *. x*definiert ist. Weitere Informationen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_ROWVER [Implementierungs Deskriptoren]**  
 Dieses sqlsmallintrecord-Feld gibt an, ob eine Spalte automatisch durch das DBMS geändert wird, wenn eine Zeile aktualisiert wird (z. b. eine Spalte vom Typ "timestamp" in SQL Server). Der Wert dieses Daten Satz Felds ist auf SQL_TRUE festgelegt, wenn es sich bei der Spalte um eine Spalte für die Zeilen Versionsverwaltung handelt, und SQL_FALSE andernfalls. Dieses Spalten Attribut ähnelt dem Aufrufen von **SQLSpecialColumns** mit dem IdentifierType SQL_ROWVER, um zu bestimmen, ob eine Spalte automatisch aktualisiert wird.  
  
 **SQL_DESC_SCALE [alle]**  
 Dieses SQLSMALLINT-Daten Satz Feld enthält die definierte Skala für die Datentypen decimal und numeric. Das Feld ist für alle anderen Datentypen nicht definiert.  
  
 Der Wert in diesem Feld kann sich von dem Wert für "Scale" unterscheiden, wie er in ODBC 2 *. x*definiert ist. Weitere Informationen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_SCHEMA_NAME [unds]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatz-Feld enthält den Schema Namen der Basistabelle, die die Spalte enthält. Der Rückgabewert ist Treiber abhängig, wenn die Spalte ein Ausdruck ist, oder wenn die Spalte Teil einer Sicht ist. Wenn die Datenquelle keine Schemas unterstützt oder der Schema Name nicht bestimmt werden kann, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_SEARCHABLE [unds]**  
 Dieses schreibgeschützte SQLSMALLINT-Daten Satz Feld wird auf einen der folgenden Werte festgelegt:  
  
-   SQL_PRED_NONE, wenn die Spalte nicht in einer **Where** -Klausel verwendet werden kann. (Dies entspricht dem SQL_UNSEARCHABLE Wert in ODBC 2 *. x*.)  
  
-   SQL_PRED_CHAR, wenn die Spalte in einer **Where** -Klausel verwendet werden kann, jedoch nur mit dem **like** -Prädikat. (Dies entspricht dem SQL_LIKE_ONLY Wert in ODBC 2 *. x*.)  
  
-   SQL_PRED_BASIC, wenn die Spalte in einer **Where** -Klausel mit allen Vergleichs Operatoren mit Ausnahme von **like**verwendet werden kann. (Dies entspricht dem SQL_EXCEPT_LIKE Wert in ODBC 2 *. x*.)  
  
-   SQL_PRED_SEARCHABLE, wenn die Spalte in einer **Where** -Klausel mit einem beliebigen Vergleichs Operator verwendet werden kann.  
  
 **SQL_DESC_TABLE_NAME [unds]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatz-Feld enthält den Namen der Basistabelle, die diese Spalte enthält. Der Rückgabewert ist Treiber abhängig, wenn die Spalte ein Ausdruck ist, oder wenn die Spalte Teil einer Sicht ist.  
  
 **SQL_DESC_TYPE [alle]**  
 Dieses SQLSMALLINT-Daten Satz Feld gibt den präzisen SQL-oder C-Datentyp für alle Datentypen außer datetime-und interval-Datentypen an. Für die Datentypen datetime und Interval gibt dieses Feld den ausführlichen Datentyp an, der SQL_DATETIME oder SQL_INTERVAL ist.  
  
 Wenn dieses Feld SQL_DATETIME oder SQL_INTERVAL enthält, muss das SQL_DESC_DATETIME_INTERVAL_CODE Feld den entsprechenden Subcode für den präzisen Typ enthalten. Für datetime-Datentypen enthält SQL_DESC_TYPE SQL_DATETIME, und das Feld SQL_DESC_DATETIME_INTERVAL_CODE enthält einen Subcode für den spezifischen DateTime-Datentyp. Für Intervall Datentypen enthält SQL_DESC_TYPE SQL_INTERVAL, und das Feld SQL_DESC_DATETIME_INTERVAL_CODE enthält einen Subcode für den spezifischen Interval-Datentyp.  
  
 Die Werte in den Feldern SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE sind voneinander abhängig. Jedes Mal, wenn eines der Felder festgelegt ist, muss das andere ebenfalls festgelegt werden. SQL_DESC_TYPE können durch einen **SQLSetDescField** -oder **SQLSetDescRec**-Befehl festgelegt werden. SQL_DESC_CONCISE_TYPE können durch einen **SQLBindCol** -oder **SQLBindParameter**-oder SQLSetDescField-Befehl festgelegt werden. **SQLSetDescField**  
  
 Wenn SQL_DESC_TYPE auf einen präzisen Datentyp festgelegt ist, der kein Intervall-oder DateTime-Datentyp ist, wird das SQL_DESC_CONCISE_TYPE Feld auf denselben Wert festgelegt, und das SQL_DESC_DATETIME_INTERVAL_CODE Feld ist auf 0 festgelegt.  
  
 Wenn SQL_DESC_TYPE auf den Datentyp ausführliche DateTime oder Interval (SQL_DATETIME oder SQL_INTERVAL) festgelegt ist und das SQL_DESC_DATETIME_INTERVAL_CODE Feld auf den entsprechenden Subcode festgelegt ist, wird das Feld SQL_DESC_CONCISE Type auf den entsprechenden präzisen Typ festgelegt. Wenn Sie SQL_DESC_TYPE auf einen der präzisen DateTime-oder Interval-Typen festlegen, wird SQLSTATE HY021 (inkonsistente Deskriptorinformationen) zurückgegeben.  
  
 Wenn das SQL_DESC_TYPE-Feld durch einen **SQLBindCol**-, **SQLBindParameter**-oder **SQLSetDescField**-Befehl festgelegt wird, werden die folgenden Felder auf die folgenden Standardwerte festgelegt, wie in der folgenden Tabelle dargestellt. Die Werte der restlichen Felder desselben Datensatzes sind nicht definiert.  
  
|Wert SQL_DESC_TYPE|Andere Felder implizit festgelegt|  
|------------------------------|---------------------------------|  
|SQL_CHAR, SQL_VARCHAR SQL_C_CHAR, SQL_C_VARCHAR|SQL_DESC_LENGTH ist auf 1 festgelegt. SQL_DESC_PRECISION ist auf 0 festgelegt.|  
|SQL_DATETIME|Wenn SQL_DESC_DATETIME_INTERVAL_CODE auf SQL_CODE_DATE oder SQL_CODE_TIME festgelegt ist, wird SQL_DESC_PRECISION auf 0 festgelegt. Wenn Sie auf SQL_DESC_TIMESTAMP festgelegt ist, wird SQL_DESC_PRECISION auf 6 festgelegt.|  
|SQL_DECIMAL, SQL_NUMERIC SQL_C_NUMERIC|SQL_DESC_SCALE ist auf 0 festgelegt. SQL_DESC_PRECISION auf die durch die Implementierung definierte Genauigkeit für den jeweiligen Datentyp festgelegt ist.<br /><br /> Informationen dazu, wie ein SQL_C_NUMERIC Wert manuell gebunden wird, finden Sie unter [SQL to C: numeric](../../../odbc/reference/appendixes/sql-to-c-numeric.md) .|  
|SQL_FLOAT SQL_C_FLOAT|SQL_DESC_PRECISION auf die von der Implementierung definierte Standardgenauigkeit für SQL_FLOAT festgelegt ist.|  
|SQL_INTERVAL|Wenn SQL_DESC_DATETIME_INTERVAL_CODE auf einen Interval-Datentyp festgelegt ist, wird SQL_DESC_DATETIME_INTERVAL_PRECISION auf 2 festgelegt (die standardmäßige Intervall führende Genauigkeit). Wenn das Intervall eine Sekunden Komponente aufweist, wird SQL_DESC_PRECISION auf 6 festgelegt (die Standardgenauigkeit in Sekunden).|  
  
 Wenn eine Anwendung **SQLSetDescField** aufruft, um Felder eines Deskriptors festzulegen, anstatt **SQLSetDescRec**aufzurufen, muss die Anwendung zuerst den Datentyp deklarieren. Wenn dies der Fall ist, werden die anderen Felder, die in der vorherigen Tabelle angegeben sind, implizit festgelegt. Wenn einer der Werte implizit festgelegt ist, kann die Anwendung **SQLSetDescField** oder **SQLSetDescRec** aufrufen, um den unzulässigen Wert explizit festzulegen.  
  
 **SQL_DESC_TYPE_NAME [Implementierungs Deskriptoren]**  
 Dieses schreibgeschützte SQLCHAR *-Datensatz-Feld enthält den von der Datenquelle abhängigen Typnamen (z. b. "char", "varchar" usw.). Wenn der Datentyp Name unbekannt ist, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_UNNAMED [Implementierungs Deskriptoren]**  
 Dieses SQLSMALLINT-Daten Satz Feld in einem Zeilen Deskriptor wird vom Treiber entweder auf SQL_NAMED oder SQL_UNNAMED festgelegt, wenn das SQL_DESC_NAME Feld festgelegt wird. Wenn das SQL_DESC_NAME Feld einen Spaltenalias enthält oder der Spaltenalias nicht zutrifft, legt der Treiber das SQL_DESC_UNNAMED Feld auf SQL_NAMED fest. Wenn eine Anwendung das SQL_DESC_NAME-Feld einer IPD auf einen Parameternamen oder Alias festlegt, legt der Treiber das SQL_DESC_UNNAMED-Feld der IPD auf SQL_NAMED fest. Wenn kein Spaltenname oder Spaltenalias vorhanden ist, legt der Treiber das SQL_DESC_UNNAMED-Feld auf SQL_UNNAMED fest.  
  
 Eine Anwendung kann das SQL_DESC_UNNAMED-Feld einer IPD auf SQL_UNNAMED festlegen. Ein Treiber gibt SQLSTATE HY091 (Ungültiger Deskriptorfeldbezeichner) zurück, wenn eine Anwendung versucht, das SQL_DESC_UNNAMED-Feld einer IPD auf SQL_NAMED festzulegen. Das SQL_DESC_UNNAMED-Feld eines IRD ist schreibgeschützt. SQLSTATE HY091 (Ungültiger Deskriptorfeldbezeichner) wird zurückgegeben, wenn eine Anwendung versucht, Sie festzulegen.  
  
 **SQL_DESC_UNSIGNED [Implementierungs Deskriptoren]**  
 Dieses schreibgeschützte SQLSMALLINT-Daten Satz Feld wird auf SQL_TRUE festgelegt, wenn der Spaltentyp nicht signiert oder nicht numerisch ist, oder SQL_FALSE, wenn der Spaltentyp signiert ist.  
  
 **SQL_DESC_UPDATABLE [unds]**  
 Dieses schreibgeschützte SQLSMALLINT-Daten Satz Feld wird auf einen der folgenden Werte festgelegt:  
  
-   SQL_ATTR_READ_ONLY, wenn die Resultsetspalte schreibgeschützt ist.  
  
-   SQL_ATTR_WRITE, wenn die Resultsetspalte Lese-/Schreibzugriff hat.  
  
-   SQL_ATTR_READWRITE_UNKNOWN, wenn nicht bekannt ist, ob die Resultsetspalte aktualisierbar ist.  
  
 SQL_DESC_UPDATABLE beschreibt die Aktualisierbarkeit der Spalte im Resultset, nicht die Spalte in der Basistabelle. Die Aktualisierbarkeit der Spalte in der Basistabelle, auf der diese Resultsetspalte basiert, kann sich von dem Wert in diesem Feld unterscheiden. Ob eine Spalte aktualisierbar ist, kann auf dem Datentyp, den Benutzerrechten und der Definition des Resultsets basieren. Wenn unklar ist, ob eine Spalte aktualisierbar ist, sollten SQL_ATTR_READWRITE_UNKNOWN zurückgegeben werden.  
  
## <a name="consistency-checks"></a>Konsistenzprüfungen  
 Vom Treiber wird automatisch eine Konsistenzprüfung durchgeführt, wenn eine Anwendung einen Wert für das Feld "SQL_DESC_DATA_PTR" von "ARD", "APD" oder "IPD" übergibt. Wenn eines der Felder nicht mit anderen Feldern konsistent ist, gibt **SQLSetDescField** SQLSTATE HY021 (inkonsistente Deskriptorinformationen) zurück. Weitere Informationen finden Sie unter "Konsistenzprüfung" in [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Binden einer Spalte|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Binden eines Parameters|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Erhalten eines deskriptorfelds|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Mehrere Deskriptorfelder werden abgerufen.|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen mehrerer Deskriptorfelder|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-Header Dateien](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)
