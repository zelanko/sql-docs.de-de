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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4cca223510ebb6838048e3babbf8fdcada42f87a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039737"
---
# <a name="sqlsetdescfield-function"></a>SQLSetDescField-Funktion

**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standardkompatibilität: ISO 92  
  
 **Zusammenfassung**  
 **SQLSetDescField** legt den Wert für ein einzelnes Feld einem anwendungsparameterdeskriptor-Datensatz.  
  
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
 [Eingabe] Deskriptorhandles.  
  
 *RecNumber*  
 [Eingabe] Gibt an, der Deskriptordatensatz, enthält das Feld, das möchte, dass die Anwendung festlegen. Deskriptordatensätze sind von 0 (null) mit der Datensatznummer lesezeichendatensatzes wird 0 nummeriert. Die *RecNumber* Argument wird ignoriert, für die Felder.  
  
 *FieldIdentifier*  
 [Eingabe] Gibt das Feld des Deskriptors, dessen Wert festgelegt werden. Weitere Informationen finden Sie unter "*FieldIdentifier* Argument" im Abschnitt "Kommentare".  
  
 *ValuePtr*  
 [Eingabe] Zeiger auf einen Puffer, das die Deskriptorinformationen oder einen ganzzahligen Wert enthält. Der Datentyp hängt vom Wert der *FieldIdentifier*. Wenn *ValuePtr* ist ein ganzzahliger Wert, kann als 8 Bytes (SQLLEN), 4 Byte (SQLINTEGER) oder 2 Bytes (SQLSMALLINT), abhängig vom Wert betrachtet die *FieldIdentifier* Argument.  
  
 *BufferLength*  
 [Eingabe] Wenn *FieldIdentifier* ist ein ODBC-definierten-Feld und *ValuePtr* zeigt auf eine Zeichenfolge oder ein binärer Puffer, in dieses Argument muss die Länge des **ValuePtr*. Für Zeichenfolgendaten sollte dieses Argument die Anzahl der Bytes in der Zeichenfolge enthalten.  
  
 Wenn *FieldIdentifier* ist ein ODBC-definierten-Feld und *ValuePtr* ist eine ganze Zahl, *Pufferlänge* wird ignoriert.  
  
 Wenn *FieldIdentifier* ist ein Feld treiberdefinierten, die Anwendung zeigt die Art des Felds um den Treiber-Manager an, indem die *Pufferlänge* Argument. *BufferLength* können die folgenden Werte aufweisen:  
  
-   Wenn *ValuePtr* ist ein Zeiger auf eine Zeichenfolge, *Pufferlänge* ist die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn *ValuePtr* ist ein Zeiger auf ein binärer Puffer, aus, und klicken Sie dann die Anwendung das Ergebnis der SQL_LEN_BINARY_ATTR platziert (*Länge*)-Makro in *Pufferlänge*. Dadurch wird einen negativen Wert im platziert *Pufferlänge*.  
  
-   Wenn *ValuePtr* ist ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine binäre Zeichenfolge *Pufferlänge* Wert SQL_IS_POINTER haben sollte.  
  
-   Wenn *ValuePtr* enthält einen Wert fester Länge *Pufferlänge* ist entweder SQL_IS_INTEGER SQL_IS_UINTEGER, SQL_IS_SMALLINT oder SQL_IS_USMALLINT, nach Bedarf.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetDescField** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurück, die einen zugeordneten SQLSTATE-Wert abgerufen werden können, durch den Aufruf **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_DESC und *behandeln* von *DescriptorHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLSetDescField** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01S02|Optionswert geändert|Der Treiber nicht den Wert im angegebenen  *\*ValuePtr* (Wenn *ValuePtr* war ein Zeiger) oder den Wert in *ValuePtr* (Wenn *ValuePtr*  wurde ein ganzzahliger Wert), oder  *\*ValuePtr* sind ungültig aufgrund von Arbeitsbedingungen Implementierung, damit der Treiber einen ähnlichen Wert ersetzt. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07009|Ungültiger Deskriptorindex|Die *FieldIdentifier* Argument wurde ein Datensatzfeld, der *RecNumber* Argument wurde 0 (null) und die *DescriptorHandle* Argument bezeichnet ein IPD-Handle.<br /><br /> Die *RecNumber* Argument war kleiner als 0 (null) und die *DescriptorHandle* Argument ein ARD oder ein APD bezeichnet.<br /><br /> Die *RecNumber* Argument war größer als die maximale Anzahl von Spalten oder Parametern, die die Datenquelle unterstützt werden, und die *DescriptorHandle* Argument ein APD oder ARD bezeichnet.<br /><br /> (DM) die *FieldIdentifier* Argument war SQL_DESC_COUNT, und  *\*ValuePtr* Argument war kleiner als 0.<br /><br /> Die *RecNumber* Argument war gleich 0 (null) und die *DescriptorHandle* Argument ein implizit zugewiesene APD bezeichnet. (Führen Sie dieser Fehler tritt keinen explizit zugewiesenen Anwendungsdienst-Deskriptor aus, da nicht bekannt ist, ob ein explizit zugewiesene Anwendungsdienst-Deskriptor einer APD oder ARD erst einmal.)|  
|08S01|Kommunikations-Verbindungsfehler|Die kommunikationsverbindung zwischen dem Treiber und der Datenquelle, die mit der der Treiber verbunden wurde, Fehler vor der Verarbeitung für die Funktion abgeschlossen.|  
|22001|Zeichenfolgendaten, rechts abgeschnitten|Die *FieldIdentifier* Argument war SQL_DESC_NAME, und die *Pufferlänge* Argument wurde ein Wert größer als SQL_MAX_IDENTIFIER_LEN.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagRec** in die  *\*MessageText* Puffer beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) die *DescriptorHandle* zugeordnet wurde eine *StatementHandle* für den eine asynchron ausgeführte Funktion (diese keiner) aufgerufen wurde, und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die  *StatementHandle* mit dem die *DescriptorHandle* verknüpft und SQL_NEED_DATA zurückgegeben wurde. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.<br /><br /> (DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *DescriptorHandle*. Dieser asynchrone Funktion war weiterhin ausgeführt, wenn die **SQLSetDescField** Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** für eines der zugeordneten Anweisungshandles aufgerufen wurde die *DescriptorHandle* und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY016|Ein Implementierungszeilendeskriptor kann nicht geändert werden.|Die *DescriptorHandle* Argument wurde ein IRD zugeordnet und die *FieldIdentifier* Argument war kein SQL_DESC_ARRAY_STATUS_PTR oder SQL_DESC_ROWS_PROCESSED_PTR.|  
|HY021|Inkonsistente deskriptorinformation|Die Felder SQL_DESC_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE bilden keine gültiger ODBC-SQL-Typ oder eine gültige treiberspezifischen SQL-Typ (für Descriptor, IPD) oder einen gültigen Typ für den ODBC-C (für APDs oder ARDs).<br /><br /> Informationen der Sicherheitsbeschreibung, die während einer konsistenzprüfung eingecheckt war nicht konsistent. (Finden Sie unter "Konsistenzprüfung" in **SQLSetDescRec**.)|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM)  *\*ValuePtr* ist eine Zeichenfolge und *Pufferlänge* war kleiner als null aber nicht gleich SQL_NTS.<br /><br /> (DM) der Treiber wurde von einer ODBC 2. *.x* -Treiber der Deskriptor wurde ein ARD, die *ColumnNumber* -Argument wurde auf 0 und dem Wert des Arguments festgelegt *Pufferlänge* wurde nicht gleich 4.|  
|HY091|Ungültiger Deskriptorfeldbezeichner|Der angegebene Wert für die *FieldIdentifier* Argument war es sich nicht um ein Feld mit ODBC-definierten und war keine implementierungsdefinierte Wert.<br /><br /> Die *FieldIdentifier* Argument war ungültig, für die *DescriptorHandle* Argument.<br /><br /> Die *FieldIdentifier* Argument wurde ein Feld schreibgeschützt, ODBC-definierten.|  
|HY092|Ungültiger Attribut-/Optionsbezeichner|Der Wert in  *\*ValuePtr* war nicht gültig für die *FieldIdentifier* Argument.<br /><br /> Die *FieldIdentifier* Argument war sql_desc_unnamed darf, und *ValuePtr* SQL_NAMED wurde.|  
|HY105|Ungültiger Parametertyp|(DM) war für das Feld "SQL_DESC_PARAMETER_TYPE" angegebene Wert ungültig. (Weitere Informationen finden Sie unter der "*InputOutputType* Argument" im Abschnitt **SQLBindParameter**.)|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [Neuigkeiten in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *DescriptorHandle* die Funktion nicht unterstützt.|  
  
## <a name="comments"></a>Kommentare  
 Kann eine Anwendung aufrufen **SQLSetDescField** alle Deskriptorfeld eine zu einem Zeitpunkt festlegen. Ein Aufruf von **SQLSetDescField** legt ein einzelnes Feld in einem einzelnen Deskriptor. Diese Funktion wird aufgerufen, um jedes Feld in einen Deskriptortyp festlegen, vorausgesetzt, dass das Feld festgelegt werden kann. (Siehe die Tabelle weiter unten in diesem Abschnitt.)  
  
> [!NOTE]  
>  Wenn ein Aufruf von **SQLSetDescField** ein Fehler auftritt, wird der Inhalt der Deskriptordatensatz identifizierte die *RecNumber* Argument sind nicht definiert.  
  
 Andere Funktionen können aufgerufen werden, um mehrere deskriptorfelder, die mit einem einzigen Aufruf der Funktion festzulegen. Die **SQLSetDescRec** -Funktion legt einer Vielzahl von Feldern, die sich auf den Datentyp und der Puffer gebunden werden, auf eine Spalte oder Parameter (die SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL_ fest DESC_SCALE, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR Felder). **SQLBindCol** oder **SQLBindParameter** kann verwendet werden, um eine vollständige Spezifikation für die Bindung einer Spalte oder Parameter zu machen. Legen diese Funktionen eine bestimmte Gruppe von deskriptorfelder, die mit einem Funktionsaufruf.  
  
 **SQLSetDescField** aufgerufen werden, um die Puffer für die Bindung zu ändern, indem das Hinzufügen eines Offsets zum Zeiger Bindung (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR). Dadurch wird die Bindung Puffer ohne **SQLBindCol** oder **SQLBindParameter**, damit kann eine Anwendung SQL_DESC_DATA_PTR zu ändern, ohne die anderen Felder, z. B. SQL_DESC_DATA_ ändern GEBEN SIE EIN.  
  
 Wenn eine Anwendung ruft **SQLSetDescField** um jedes Feld als SQL_DESC_COUNT oder SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR oder SQL_DESC_OCTET_LENGTH_PTR zurückgestellten Felder festgelegt, der Datensatz wird als aufgehoben.  
  
 Deskriptorheaderfelder werden festgelegt, durch den Aufruf **SQLSetDescField** mit dem entsprechenden *FieldIdentifier*. Viele Headerfelder sind auch Anweisungsattribute, damit sie auch können, durch einen Aufruf von festgelegt werden **SQLSetStmtAttr**. Dadurch können Anwendungen, die einem Beschreibungsfeld festlegen, ohne zunächst eine Deskriptorhandles abzurufen. Wenn **SQLSetDescField** wird aufgerufen, um ein Headerfeld, Festlegen der *RecNumber* Argument wird ignoriert.  
  
 Ein *RecNumber* 0 dient zum Festlegen von Lesezeichen-Felder.  
  
> [!NOTE]  
>  Das Anweisungsattribut SQL_ATTR_USE_BOOKMARKS sollte immer festgelegt werden, bevor **SQLSetDescField** Lesezeichen Felder festlegen. Obwohl dies nicht erforderlich ist, wird dringend empfohlen.  
  
## <a name="sequence-of-setting-descriptor-fields"></a>Sequenz der Festlegen von Deskriptorfeldern  
 Beim Festlegen von deskriptorfelder durch Aufrufen von **SQLSetDescField**, die Anwendung muss eine bestimmte Reihenfolge ausführen:  
  
1.  Die Anwendung muss zunächst das SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE oder SQL_DESC_DATETIME_INTERVAL_CODE Feld festlegen.  
  
2.  Nachdem Sie eines dieser Felder festgelegt wurde, die Anwendung kann ein Attribut des einen Datentyp festlegen und der Treiber setzt Datentyp Attributfelder auf die entsprechenden Standardwerte für den Datentyp. Automatische Standardwert des Typs Attributfelder wird sichergestellt, dass der Deskriptor immer verwendet werden, nachdem die Anwendung einen Datentyp angegeben wurde. Wenn die Anwendung explizit ein Data-Type-Attribut festlegt, ist das Standardattribut überschreiben müssen.  
  
3.  Nachdem eines der Felder, die in Schritt 1 aufgeführten festgelegt wurde und Daten Typattribute festgelegt wurden, kann die Anwendung SQL_DESC_DATA_PTR festlegen. Dadurch wird eine Überprüfung der Konsistenz von deskriptorfelder. Wenn die Anwendung den Datentyp oder Attributen ändert, nachdem Sie das SQL_DESC_DATA_PTR-Feld festgelegt haben, wird der Treiber SQL_DESC_DATA_PTR auf ein null-Zeiger, Aufheben der Bindung des Datensatzes an. Dies erzwingt, dass die Anwendung die richtigen Schritte nacheinander ausführen, bevor es sich bei den anwendungsparameterdeskriptor-Datensatz verwendet werden kann.  
  
## <a name="initialization-of-descriptor-fields"></a>Initialisierung der Deskriptorfelder  
 Wenn ein Deskriptor zugeordnet ist, die Felder im Deskriptor können auf einen Standardwert initialisiert werden, ohne einen Standardwert initialisiert werden, oder für den Typ des Deskriptors nicht definiert. Die folgende Tabelle gibt an, die Initialisierung der einzelnen Felder für jeden Typ des Deskriptors, "D", der angibt, dass das Feld hat den Standardwert initialisiert wird, und "ND", der angibt, dass das Feld ohne Standardwert initialisiert wird. Wenn eine Zahl angezeigt wird, ist der Standardwert des Felds diese Anzahl an. In den Tabellen geben auch an, ob ein Feld (R/W) Lese-/Schreibzugriff oder schreibgeschützten (R) ist.  
  
 Die Felder einer IRD über einen Standardwert verfügen, erst, nachdem die Anweisung vorbereitet oder ausgeführt wurde und IRD aufgefüllt wurde, nicht verwendet werden, wenn die Anweisungshandle oder der Deskriptor zugeordnet wurde. Bis IRD aufgefüllt wurde, wird jeder Versuch, den Zugriff auf ein Feld einer IRD einen Fehler zurück.  
  
 Einige deskriptorfelder sind für eine oder mehrere, aber nicht alle der deskriptortypen (ARDs und IRDs, APDs und Descriptor, IPD) definiert. Wenn ein Feld für einen Deskriptor nicht definiert ist, ist es nicht durch eine der Funktionen benötigt, der dieser Deskriptor verwendet.  
  
 Die Felder, die von zugegriffen werden können **SQLGetDescField** kann nicht zwingend festgelegt werden, indem **SQLSetDescField**. Felder, die festgelegt werden kann, indem **SQLSetDescField** sind in den folgenden Tabellen aufgeführt.  
  
 Die Initialisierung von Headerfeldern ist in der Tabelle beschrieben, die folgt.  
  
|Header-Feldname|Typ|R/W|Default|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_ALLOC_TYPE|SQLSMALLINT|ARD: R-APD: R-IRD: R-IPD: R|ARD: SQL_DESC_ALLOC_AUTO für implizite oder SQL_DESC_ALLOC_USER für explizite<br /><br /> APD: SQL_DESC_ALLOC_AUTO für implizite oder SQL_DESC_ALLOC_USER für explizite<br /><br /> IRD: SQL_DESC_ALLOC_AUTO<br /><br /> IPD: SQL_DESC_ALLOC_AUTO|  
|SQL_DESC_ARRAY_SIZE|SQLULEN ERSTELLT WURDE|ARD: R/W-APD: R/W-IRD: Nicht verwendete IPD: Nicht verwendet|ARD: [1] APD: [1] IRD: Nicht verwendete IPD: Nicht verwendet|  
|SQL_DESC_ARRAY_STATUS_PTR|SQLUSMALLINT *|ARD: R/W-APD: R/W-IRD: R/W-IPD: R/W|ARD: NULL-Ptr-APD: NULL-Ptr-IRD: NULL-Ptr-IPD: NULL ptr|  
|SQL_DESC_BIND_OFFSET_PTR|SQLLEN *|ARD: R/W-APD: R/W-IRD: Nicht verwendete IPD: Nicht verwendet|ARD: NULL-Ptr-APD: NULL-Ptr-IRD: Nicht verwendete IPD: Nicht verwendet|  
|SQL_DESC_BIND_TYPE|SQLINTEGER|ARD: R/W-APD: R/W-IRD: Nicht verwendete IPD: Nicht verwendet|ARD: SQL_BIND_BY_COLUMN<br /><br /> APD: SQL_BIND_BY_COLUMN<br /><br /> IRD: Nicht verwendet<br /><br /> IPD: Nicht verwendet|  
|SQL_DESC_COUNT|SQLSMALLINT|ARD: R/W-APD: R/W-IRD: R-IPD: R/W|ARD: 0 APD: 0 IRD: D IPD: 0|  
|SQL_DESC_ROWS_PROCESSED_PTR|SQLULEN *|ARD: Nicht verwendete APD: Nicht verwendete IRD: R/W-IPD: R/W|ARD: Nicht verwendete APD: Nicht verwendete IRD: NULL-Ptr-IPD: NULL ptr|  
  
 [1] für diese Felder werden definiert, nur, wenn die IPD vom Treiber automatisch aufgefüllt wird. Falls nicht, sind sie nicht definiert. Wenn eine Anwendung versucht, diese Felder SQLSTATE HY091 festgelegt werden (Ungültiger Deskriptorfeldbezeichner) zurückgegeben.  
  
 Die Initialisierung Datensatzfeldern ist wie in der folgenden Tabelle gezeigt.  
  
|Datensatz-Feldnamen|Typ|R/W|Default|  
|-----------------------|----------|----------|-------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: Nicht verwendet|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: Nicht verwendet|  
|SQL_DESC_BASE_COLUMN_NAME|SQLCHAR *|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: Nicht verwendet|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: Nicht verwendet|  
|SQL_DESC_BASE_TABLE_NAME|SQLCHAR *|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: Nicht verwendet|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: Nicht verwendet|  
|SQL_DESC_CASE_SENSITIVE|SQLINTEGER|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: R|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: D[1]|  
|SQL_DESC_CATALOG_NAME|SQLCHAR *|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: Nicht verwendet|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: Nicht verwendet|  
|SQL_DESC_CONCISE_TYPE|SQLSMALLINT|ARD: R/W-APD: R/W-IRD: R-IPD: R/W|ARD: STANDARD-APD SQL_C_: STANDARD-IRD SQL_C_: D IPD: %ND|  
|SQL_DESC_DATA_PTR|SQLPOINTER|ARD: R/W-APD: R/W-IRD: Nicht verwendete IPD: Nicht verwendet|ARD: NULL-Ptr-APD: NULL-Ptr-IRD: Nicht verwendete IPD: ' Nicht verwendet ' [2]|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQLSMALLINT|ARD: R/W-APD: R/W-IRD: R-IPD: R/W|ARD: ND APD: ND IRD: D IPD: %ND|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQLINTEGER|ARD: R/W-APD: R/W-IRD: R-IPD: R/W|ARD: ND APD: ND IRD: D IPD: %ND|  
|SQL_DESC_DISPLAY_SIZE|SQLLEN|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: Nicht verwendet|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: Nicht verwendet|  
|SQL_DESC_FIXED_PREC_SCALE|SQLSMALLINT|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: R|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: D[1]|  
|SQL_DESC_INDICATOR_PTR|SQLLEN *|ARD: R/W-APD: R/W-IRD: Nicht verwendete IPD: Nicht verwendet|ARD: NULL-Ptr-APD: NULL-Ptr-IRD: Nicht verwendete IPD: Nicht verwendet|  
|SQL_DESC_LABEL|SQLCHAR *|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: Nicht verwendet|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: Nicht verwendet|  
|SQL_DESC_LENGTH|SQLULEN ERSTELLT WURDE|ARD: R/W-APD: R/W-IRD: R-IPD: R/W|ARD: ND APD: ND IRD: D IPD: %ND|  
|SQL_DESC_LITERAL_PREFIX|SQLCHAR *|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: Nicht verwendet|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: Nicht verwendet|  
|SQL_DESC_LITERAL_SUFFIX|SQLCHAR *|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: Nicht verwendet|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: Nicht verwendet|  
|SQL_DESC_LOCAL_TYPE_NAME|SQLCHAR *|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: R|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: D[1]|  
|SQL_DESC_NAME|SQLCHAR *|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: R/W|ARD: ND APD: ND IRD: D IPD: %ND|  
|SQL_DESC_NULLABLE|SQLSMALLINT|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: R|ARD: ND APD: ND IRD: D IPD: %ND|  
|SQL_DESC_NUM_PREC_RADIX|SQLINTEGER|ARD: R/W-APD: R/W-IRD: R-IPD: R/W|ARD: ND APD: ND IRD: D IPD: %ND|  
|SQL_DESC_OCTET_LENGTH|SQLLEN|ARD: R/W-APD: R/W-IRD: R-IPD: R/W|ARD: ND APD: ND IRD: D IPD: %ND|  
|SQL_DESC_OCTET_LENGTH_PTR|SQLLEN *|ARD: R/W-APD: R/W-IRD: Nicht verwendete IPD: Nicht verwendet|ARD: NULL-Ptr-APD: NULL-Ptr-IRD: Nicht verwendete IPD: Nicht verwendet|  
|SQL_DESC_PARAMETER_TYPE|SQLSMALLINT|ARD: Nicht verwendete APD: Nicht verwendete IRD: Nicht verwendete IPD: R/W|ARD: Nicht verwendete APD: Nicht verwendete IRD: Nicht verwendete IPD: D = SQL_PARAM_INPUT|  
|SQL_DESC_PRECISION|SQLSMALLINT|ARD: R/W-APD: R/W-IRD: R-IPD: R/W|ARD: ND APD: ND IRD: D IPD: %ND|  
|SQL_DESC_ROWVER|SQLSMALLINT|ARD: Nicht verwendet<br /><br /> APD: Nicht verwendet<br /><br /> IRD: R<br /><br /> IPD: R|ARD: Nicht verwendet<br /><br /> APD: Nicht verwendet<br /><br /> IRD: %ND<br /><br /> IPD: %ND|  
|SQL_DESC_SCALE|SQLSMALLINT|ARD: R/W-APD: R/W-IRD: R-IPD: R/W|ARD: ND APD: ND IRD: D IPD: %ND|  
|SQL_DESC_SCHEMA_NAME|SQLCHAR *|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: Nicht verwendet|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: Nicht verwendet|  
|SQL_DESC_SEARCHABLE|SQLSMALLINT|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: Nicht verwendet|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: Nicht verwendet|  
|SQL_DESC_TABLE_NAME|SQLCHAR *|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: Nicht verwendet|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: Nicht verwendet|  
|SQL_DESC_TYPE|SQLSMALLINT|ARD: R/W-APD: R/W-IRD: R-IPD: R/W|ARD: SQL_C_DEFAULT APD: SQL_C_DEFAULT IRD: D IPD: %ND|  
|SQL_DESC_TYPE_NAME|SQLCHAR *|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: R|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: D[1]|  
|SQL_DESC_UNNAMED|SQLSMALLINT|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: R/W|ARD: ND APD: ND IRD: D IPD: %ND|  
|SQL_DESC_UNSIGNED|SQLSMALLINT|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: R|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: D[1]|  
|SQL_DESC_UPDATABLE|SQLSMALLINT|ARD: Nicht verwendete APD: Nicht verwendete IRD: R-IPD: Nicht verwendet|ARD: Nicht verwendete APD: Nicht verwendete IRD: D IPD: Nicht verwendet|  
  
 [1] für diese Felder werden definiert, nur, wenn die IPD vom Treiber automatisch aufgefüllt wird. Falls nicht, sind sie nicht definiert. Wenn eine Anwendung versucht, diese Felder SQLSTATE HY091 festgelegt werden (Ungültiger Deskriptorfeldbezeichner) zurückgegeben.  
  
 [2] das SQL_DESC_DATA_PTR-Feld in IPD kann festgelegt werden, um eine Überprüfung der Konsistenz zu erzwingen. In einem nachfolgenden Aufruf **SQLGetDescField** oder **SQLGetDescRec**, der Treiber ist nicht erforderlich, um den Wert zurückzugeben, die für SQL_DESC_DATA_PTR festgelegt.  
  
## <a name="fieldidentifier-argument"></a>FieldIdentifier-Argument  
 Die *FieldIdentifier* Argument gibt an, das Deskriptorfeld festgelegt werden. Eine Sicherheitsbeschreibung enthält die *Deskriptor-Header,* bestehend aus den Headerfeldern, die im nächsten Abschnitt, "Headerfelder, die" und 0 (null) oder mehrere beschrieben *deskriptordatensätze,* bestehend aus den Feldern des Datensatzes im Abschnitt "Headerfelder" Abschnitt beschrieben.  
  
## <a name="header-fields"></a>Headerfelder  
 Jede Sicherheitsbeschreibung hat es sich um eine Kopfzeile, bestehend aus den folgenden Feldern:  
  
 **SQL_DESC_ALLOC_TYPE [All]**  
 Dieser schreibgeschütztes SQLSMALLINT-Header-Feld gibt an, ob der Deskriptor automatisch vom Treiber oder explizit durch die Anwendung zugewiesen wurde. Die Anwendung kann zu erhalten, aber nicht ändern, dieses Feld wird. Das Feld wird vom Treiber auf SQL_DESC_ALLOC_AUTO festgelegt, wenn der Deskriptor automatisch vom Treiber zugewiesen wurde. Es wird auf SQL_DESC_ALLOC_USER vom Treiber festgelegt, wenn der Deskriptor explizit von der Anwendung belegt wurde.  
  
 **SQL_DESC_ARRAY_SIZE [Anwendungsdiensts]**  
 Dieses SQLULEN-Headerfeld in ARDs gibt an, dass die Anzahl der Zeilen im Rowset. Dies ist die Anzahl der Zeilen durch einen Aufruf zurückzugebenden **SQLFetch** oder **SQLFetchScroll** oder durch einen Aufruf verarbeitet werden sollen **SQLBulkOperations** oder **SQLSetPos** .  
  
 Dieses SQLULEN-Headerfeld in APDs gibt an, dass die Anzahl der Werte für jeden Parameter.  
  
 Der Standardwert dieses Felds ist 1. Wenn SQL_DESC_ARRAY_SIZE größer als 1 ist, zeigen SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR APD oder ARD auf Arrays an. Die Kardinalität jedes Arrays ist gleich dem Wert dieses Felds.  
  
 Dieses Feld in der ARD kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit dem SQL_ATTR_ROW_ARRAY_SIZE-Attribut. Dieses Feld in APD kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit dem Attribut verweist SQL_ATTR_PARAMSET_SIZE.  
  
 **SQL_DESC_ARRAY_STATUS_PTR [All]**  
 Für jeden Deskriptortyp dieser SQLUSMALLINT * Header Feld zeigt auf ein Array von SQLUSMALLINT-Werten. Diese Arrays werden wie folgt benannt: Zeile Statusarray (IRD), Parameter Statusarray (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor), Zeile Operation-Array (ARD) und Vorgang Parameterarray (APD).  
  
 In IRD dieser Headerfeld verweist, um ein zeilenstatusarray, die Statuswerte nach einem Aufruf von **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, oder **SQLSetPos**. Das Array hat so viele Elemente als Zeilen im Rowset vorhanden sind. Die Anwendung muss ein Array von SQLUSMALLINTs zuordnen und legen Sie dieses Feld, um auf das Array zu verweisen. Die Standardeinstellung für des Felds ist eines null-Zeigers. Der Treiber wird das Array - zu füllen, wenn auf einen null-Zeiger ist das Feld "SQL_DESC_ARRAY_STATUS_PTR" festgelegt ist, in diesem Fall werden keine Statuswerte generiert und das Array wird nicht aufgefüllt.  
  
> [!CAUTION]  
>  Treiber-Verhalten ist nicht definiert, wenn die Anwendung die Elemente der zeilenstatusarray verweist das Feld SQL_DESC_ARRAY_STATUS_PTR IRD festlegt.  
  
 Das Array wird zunächst durch einen Aufruf von aufgefüllt **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, oder **SQLSetPos**. Wenn der Aufruf nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben wurde, sind den Inhalt des Arrays zeigt dieses Feld nicht definiert. Die Elemente im Array können die folgenden Werte enthalten:  
  
-   SQL_ROW_SUCCESS: Die Zeile wurde erfolgreich abgerufen und seit dem letzten Abruf nicht geändert werden.  
  
-   SQL_ROW_SUCCESS_WITH_INFO: Die Zeile wurde erfolgreich abgerufen und seit dem letzten Abruf nicht geändert werden. Allerdings wurde eine Warnung zur Zeile zurückgegeben.  
  
-   SQL_ROW_ERROR: Fehler beim Abrufen der Zeile.  
  
-   SQL_ROW_UPDATED: Die Zeile wurde erfolgreich abgerufen und wurde aktualisiert, seit sie zuletzt abgerufen wurde. Wenn die Zeile erneut abgerufen wird, ist dessen Status SQL_ROW_SUCCESS an.  
  
-   SQL_ROW_DELETED: Die Zeile wurde seit dem letzten Abruf wurde gelöscht.  
  
-   SQL_ROW_ADDED: Die Zeile eingefügt wurde, indem **SQLBulkOperations**. Wenn die Zeile erneut abgerufen wird, ist dessen Status SQL_ROW_SUCCESS an.  
  
-   SQL_ROW_NOROW: Das Rowset überlappende das Ende des Resultsets und keine Zeile zurückgegeben wurde, dass, die für dieses Element von der zeilenstatusarray entsprach.  
  
 Dieses Feld in IRD kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit dem SQL_ATTR_ROW_STATUS_PTR-Attribut.  
  
 Das Feld SQL_DESC_ARRAY_STATUS_PTR IRD ist gültig, erst nach SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben wurde. Ist der Rückgabecode nicht eines der folgenden, ist der Speicherort verweist SQL_DESC_ROWS_PROCESSED_PTR nicht definiert.  
  
 In den IPD Dieses Headerfeld verweist, in ein Parameterarray-Status mit Statusinformationen für jeden Satz von Parameterwerten nach einem Aufruf von **SQLExecute** oder **SQLExecDirect**. Wenn der Aufruf von **SQLExecute** oder **SQLExecDirect** hat keine zurückgegeben SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO, den Inhalt des Arrays zeigt dieses Feld sind nicht definiert. Die Anwendung muss ein Array von SQLUSMALLINTs zuordnen und legen Sie dieses Feld, um auf das Array zu verweisen. Der Treiber wird das Array - zu füllen, wenn auf einen null-Zeiger ist das Feld "SQL_DESC_ARRAY_STATUS_PTR" festgelegt ist, in diesem Fall werden keine Statuswerte generiert und das Array wird nicht aufgefüllt. Die Elemente im Array können die folgenden Werte enthalten:  
  
-   SQL_PARAM_SUCCESS: Die SQL-Anweisung wurde erfolgreich für diesen Satz von Parametern ausgeführt.  
  
-   SQL_PARAM_SUCCESS_WITH_INFO: Die SQL-Anweisung wurde erfolgreich für diesen Satz von Parametern ausgeführt. Allerdings ist Warninformationen in die Diagnose-Datenstruktur verfügbar.  
  
-   SQL_PARAM_ERROR: Fehler bei der Verarbeitung dieser Satz von Parametern. Zusätzliche Fehlerinformationen ist in der Datenstruktur für die Diagnose verfügbar.  
  
-   SQL_PARAM_UNUSED: Dieser Parameter festgelegt wurde möglicherweise nicht verwendet werden, darauf zurückzuführen, dass einige vorherigen Parametersatz einen Fehler verursacht hat, der weitere Verarbeitung abgebrochen, oder weil für diese Gruppe von Parametern im Array anhand des Felds SQL_DESC_ARRAY_STATUS_PTR der SQL_PARAM_IGNORE festgelegt wurde APD.  
  
-   SQL_PARAM_DIAG_UNAVAILABLE: Diagnoseinformationen ist nicht verfügbar. Ein Beispiel hierfür ist, wenn der Treiber von Parameterarrays als monolithische Einheit behandelt, und damit diese Art von Fehlerinformationen nicht generiert.  
  
 Dieses Feld in IPD kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit dem SQL_ATTR_PARAM_STATUS_PTR-Attribut.  
  
 In der ARD Dieses Headerfeld verweist, auf eine Zeile Operation-Array von Werten, die festgelegt werden können, von der Anwendung an, ob diese Zeile gilt für ignoriert werden **SQLSetPos** Vorgänge. Die Elemente im Array können die folgenden Werte enthalten:  
  
-   SQL_ROW_PROCEED: Die Zeile befindet sich in der Bulk-Vorgang mit **SQLSetPos**. (Diese Einstellung garantiert nicht, dass der Vorgang in der Zeile stattfindet. Wenn die Zeile der Status den SQL_ROW_ERROR in den IRD-zeilenstatusarray verfügt, der Treiber zum Ausführen des Vorgangs in der Zeile können möglicherweise nicht.)  
  
-   SQL_ROW_IGNORE: Die Zeile wird aus dem Bulk-Vorgang mit ausgeschlossen **SQLSetPos**.  
  
 Wenn keine Elemente des Arrays festgelegt werden, sind alle Zeilen in den Massenvorgang enthalten. Wenn der Wert im Feld SQL_DESC_ARRAY_STATUS_PTR der ARD ein null-Zeiger ist, werden alle Zeilen in den Massenvorgang enthalten; die Interpretation ist identisch, als ob der Zeiger auf ein gültiges Array verweist und alle Elemente des Arrays SQL_ROW_PROCEED wurden. Wenn ein Element im Array auf SQL_ROW_IGNORE festgelegt ist, wird der Wert in der zeilenstatusarray für die Zeile ignoriert nicht geändert werden.  
  
 Dieses Feld in der ARD kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit dem SQL_ATTR_ROW_OPERATION_PTR-Attribut.  
  
 Im APD, diese Headerfeld verweist, in ein Parameterarray-Vorgang von Werten, die festgelegt werden kann, von der Anwendung an, ob dieser Satz von Parametern ist, werden ignoriert, wenn **SQLExecute** oder **SQLExecDirect**aufgerufen wird. Die Elemente im Array können die folgenden Werte enthalten:  
  
-   SQL_PARAM_PROCEED: Der Satz von Parametern befindet sich in der **SQLExecute** oder **SQLExecDirect** aufrufen.  
  
-   SQL_PARAM_IGNORE: Der Satz von Parametern wird ausgeschlossen. die **SQLExecute** oder **SQLExecDirect** aufrufen.  
  
 Wenn keine Elemente des Arrays festgelegt werden, werden alle Sätze von Parametern im Array in verwendet die **SQLExecute** oder **SQLExecDirect** aufrufen. Wenn der Wert im Feld SQL_DESC_ARRAY_STATUS_PTR APD ein null-Zeiger ist, werden alle Sätze von Parametern verwendet. die Interpretation ist identisch, als ob der Zeiger auf ein gültiges Array verweist und alle Elemente des Arrays SQL_PARAM_PROCEED wurden.  
  
 Dieses Feld in APD kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit dem SQL_ATTR_PARAM_OPERATION_PTR-Attribut.  
  
 **SQL_DESC_BIND_OFFSET_PTR [Anwendungsdiensts]**  
 Diese SQLLEN * Header-Feld zeigt den Offset für die Bindung. Es ist standardmäßig auf einen null-Zeiger festgelegt. Wenn dieses Feld keinen null-Zeiger ist, wird der Treiber dereferenziert den Zeiger und fügt den verweislosen Wert jedem der zurückgestellten Felder, die einen Wert ungleich Null im Deskriptordatensatz (SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR) Beim rufen Sie Zeit und verwendet die neuen Zeigerwerte ab, bei der Bindung.  
  
 Der Offset für die Bindung wird immer direkt auf die Werte in den Feldern SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR hinzugefügt. Wenn der Offset in einen anderen Wert geändert wird, ist der neue Wert direkt auf den Wert in jedem Deskriptorfeld weiterhin hinzugefügt. Der neue Offset ist der Wert des Felds sowie alle früheren Offset nicht hinzugefügt.  
  
 Dieses Feld ist ein *verzögerte Feld*: Es wird nicht zum Zeitpunkt verwendet, wird festgelegt, aber es wird zu einem späteren Zeitpunkt vom Treiber verwendet, wenn die Adressen für Datenpuffer ermittelt werden muss.  
  
 Dieses Feld in der ARD kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit dem SQL_ATTR_ROW_BIND_OFFSET_PTR-Attribut. Dieses Feld in der ARD kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit dem SQL_ATTR_PARAM_BIND_OFFSET_PTR-Attribut.  
  
 Weitere Informationen finden Sie unter der Beschreibung der zeilenweisen Bindung in [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) und [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 **SQL_DESC_BIND_TYPE [Anwendungsdiensts]**  
 Dieses SQLUINTEGER-Header-Feld legt fest, der die Ausrichtung der Bindung zum Binden von Spalten oder Parameter verwendet werden soll.  
  
 In ARDs, dieses Feld gibt die Ausrichtung der Bindung beim **SQLFetchScroll** oder **SQLFetch** für das zugeordnete Anweisungshandle aufgerufen wird.  
  
 Um spaltenbezogene Bindungen für Spalten auswählen, wird dieses Feld auf SQL_BIND_BY_COLUMN ein (Standard) festgelegt.  
  
 Dieses Feld in der ARD kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit der SQL_ATTR_ROW_BIND_TYPE *Attribut*.  
  
 Dieses Feld in APDs gibt an, dass die Bindung Ausrichtung für dynamische Parameter verwendet werden soll.  
  
 Um spaltenbezogene Bindungen für Parameter auswählen, wird dieses Feld auf SQL_BIND_BY_COLUMN ein (Standard) festgelegt.  
  
 Dieses Feld in APD kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit der SQL_ATTR_PARAM_BIND_TYPE *Attribut*.  
  
 **SQL_DESC_COUNT [All]**  
 Dieses SQLSMALLINT-Header-Feld gibt den 1 basierenden Index des höchsten Datensatzes, der Daten enthält. Wenn der Treiber die Datenstruktur für den Deskriptor setzt, muss es auch die SQL_DESC_COUNT-Felds, um anzuzeigen, wie viele Datensätze von Bedeutung sind festlegen. Wenn eine Anwendung eine Instanz dieser Datenstruktur zuordnet, es keine an wie viele Datensätze, um Platz für zu reservieren. Wie die Anwendung den Inhalt der Datensätze angibt, verwendet der Treiber Maßnahmen erforderlich, stellen Sie sicher, dass das Deskriptorhandle auf eine Datenstruktur, die geeignete Größe bezieht.  
  
 SQL_DESC_COUNT ist nicht die Anzahl von alle Datenspalten, die gebunden sind (wenn das Feld in einer ARD ist) oder alle Parameter, die gebunden sind (wenn das Feld in einer APD ist), aber die Anzahl von der höchsten Datensatz. Wenn der höchste nummerierte Spalte oder des Parameters aufgehoben wird, wird SQL_DESC_COUNT klicken Sie dann auf die Anzahl der nächsten höchste nummerierte Spalte oder des Parameters geändert werden. Wenn eine Spalte oder einen Parameter mit einer Zahl ist, die kleiner als die Anzahl der höchste nummerierte Spalte aufgehoben wird (durch Aufrufen von **SQLBindCol** mit der *TargetValuePtr* Argument festgelegt wird, zu einem null-Zeiger ist oder **SQLBindParameter** mit der *ParameterValuePtr* -Argument auf einen null-Zeiger festgelegt), SQL_DESC_COUNT wird nicht geändert. Wenn zusätzliche Spalten oder Parametern mit Zahlen größer als der höchste nummerierte Datensatz, die Daten enthält gebunden sind, wird der Treiber automatisch den Wert in das Feld "SQL_DESC_COUNT" erhöht. Wenn alle Spalten durch Aufrufen von nicht gebundenen sind **SQLFreeStmt** SQL_DESC_COUNT Felder in der ARD und IRD werden mit der Option SQL_UNBIND auf 0 festgelegt. Wenn **SQLFreeStmt** wird aufgerufen, mit der Option SQL_RESET_PARAMS werden die Felder SQL_DESC_COUNT im APD und IPD auf 0 festgelegt.  
  
 Der Wert in SQL_DESC_COUNT kann explizit festgelegt werden von einer Anwendung durch Aufrufen von **SQLSetDescField**. Wenn der Wert in SQL_DESC_COUNT explizit verringert wird, werden alle Datensätze mit Zahlen größer als der neue Wert in SQL_DESC_COUNT effektiv entfernt. Wenn der Wert in SQL_DESC_COUNT explizit auf 0 festgelegt ist, und das Feld befindet sich in einem ARD, werden alle Datenpuffer mit der Ausnahme eine gebundene Lesezeichenspalte veröffentlicht.  
  
 Die Anzahl der Datensätze in diesem Feld von einem ARD umfasst eine gebundene Lesezeichenspalte nicht. Die einzige Möglichkeit zum Aufheben der Bindung einer Lesezeichen-Spalteninhalts ist das SQL_DESC_DATA_PTR-Feld auf einen null-Zeiger festgelegt.  
  
 **SQL_DESC_ROWS_PROCESSED_PTR [Implementierung Deskriptoren]**  
 In einer IRD dieser SQLULEN \* Header-Feld-verweist auf einen Puffer, enthält die Anzahl der Zeilen, die nach einem Aufruf abgerufen **SQLFetch** oder **SQLFetchScroll**, oder die Anzahl der betroffenen Zeilen in einem Massenvorgang durch einen Aufruf von ausgeführten **SQLBulkOperations** oder **SQLSetPos**, einschließlich der Fehlerzeilen.  
  
 In einem IPD, diese SQLUINTEGER * Header Feld verweist auf einen Puffer, der die Anzahl der Sätze von Parametern, die verarbeitet wurden einschließlich Fehler, enthält. Keine Anzahl wird zurückgegeben, wenn dies ein null-Zeiger ist.  
  
 SQL_DESC_ROWS_PROCESSED_PTR gilt erst nach einem Aufruf von SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben wurde **SQLFetch** oder **SQLFetchScroll** (für ein IRD-Feld) oder **SQLExecute** , **SQLExecDirect**, oder **SQLParamData** (für ein IPD-Feld). Wenn der Aufruf, der im Puffer füllt, zeigt dieses Feld gibt keine SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück, den Inhalt des Puffers nicht definiert ist, es sei denn, Sie gibt SQL_NO_DATA zurückgibt, in dem Fall wird der Wert im Puffer auf 0 festgelegt ist.  
  
 Dieses Feld in der ARD kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit das SQL_ATTR_ROWS_FETCHED_PTR-Attribut. Dieses Feld in APD kann auch festgelegt werden, durch den Aufruf **SQLSetStmtAttr** mit das SQL_ATTR_PARAMS_PROCESSED_PTR-Attribut.  
  
 Der Puffer, die auf dieses Feld wird von der Anwendung zugeordnet. Es ist eine verzögerte Ausgabepuffer, der vom Treiber festgelegt ist. Es ist standardmäßig auf einen null-Zeiger festgelegt.  
  
## <a name="record-fields"></a>Notieren Sie die Felder  
 Jede Sicherheitsbeschreibung enthält einen oder mehrere Datensätze mit Feldern, die Spaltendaten oder dynamische Parameter je nach Art des Deskriptors definieren. Jeder Datensatz ist eine vollständige Definition der eine einzelne Spalte oder Parameter.  
  
 **SQL_DESC_AUTO_UNIQUE_VALUE [IRDs]**  
 Dieses Feld schreibgeschützt SQLINTEGER-Eintrag enthält SQL_TRUE, wenn die Spalte eine Spalte automatisch erhöht oder SQL_FALSE ist, wenn die Spalte nicht auf einer automatisch inkrementierten Spalte ist. Dieses Feld ist schreibgeschützt, aber die zugrunde liegende automatisch inkrementierten Spalte ist nicht unbedingt schreibgeschützt.  
  
 **SQL_DESC_BASE_COLUMN_NAME [IRDs]**  
 Diese schreibgeschützte SQLCHAR * Feld "Record" der Name der Basisspalte enthält, für die Resultsetspalte. Wenn ein Name der Basisspalte nicht (wie im Fall von Spalten, bei denen Ausdrücke) vorhanden ist, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_BASE_TABLE_NAME [IRDs]**  
 Diese schreibgeschützte SQLCHAR * Feld "Record" enthält den Namen der Basistabelle, für die Resultsetspalte. Wenn Sie ein Namen für die Basistabelle kann nicht definiert werden oder ist nicht anwendbar, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_CASE_SENSITIVE [Implementierung Deskriptoren]**  
 Dieses Feld schreibgeschützt SQLINTEGER-Eintrag enthält SQL_TRUE, Spalte oder des Parameters so behandelt, als für Sortierungen und Vergleiche oder SQL_FALSE Groß-/Kleinschreibung, wenn die Spalte als Groß-/Kleinschreibung für Sortierungen und Vergleiche nicht behandelt wird oder wenn sie eine nicht auf Zeichen basierende ist die Spalte.  
  
 **SQL_DESC_CATALOG_NAME [IRDs]**  
 Diese schreibgeschützte SQLCHAR * Feld "Record" enthält den Katalog für die Basistabelle, die die Spalte enthält. Der Rückgabewert ist treiberabhängig auf, wenn die Spalte ein Ausdruck ist, oder wenn die Spalte Teil einer Ansicht ist. Wenn die Datenquelle keine Kataloge unterstützt oder der Katalog kann nicht bestimmt werden, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_CONCISE_TYPE [All]**  
 Dieses SQLSMALLINT-Headerfeld gibt den präzisen Datentyp für alle Datentypen, einschließlich der Datentypen "DateTime" und das Intervall an.  
  
 Die Werte in den Feldern SQL_DESC_TYPE, SQL_DESC_CONCISE_TYPE und SQL_DESC_DATETIME_INTERVAL_CODE sind voneinander abhängig. Jedes Mal eines der Felder festgelegt ist, muss der andere ebenfalls festgelegt werden. SQL_DESC_CONCISE_TYPE kann festgelegt werden, durch einen Aufruf von **SQLBindCol** oder **SQLBindParameter**, oder **SQLSetDescField**. SQL_DESC_TYPE kann festgelegt werden, durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**.  
  
 Wenn SQL_DESC_CONCISE_TYPE in einen präzisen Datentyp als ein Intervall oder Datetime-Datentyp festgelegt ist, wird das SQL_DESC_TYPE-Feld auf den gleichen Wert festgelegt ist, und das Feld "SQL_DESC_DATETIME_INTERVAL_CODE" auf 0 festgelegt ist.  
  
 Wenn SQL_DESC_CONCISE_TYPE in den präzisen Datentyp "DateTime" oder das Intervall festgelegt ist, das SQL_DESC_TYPE-Feld in den entsprechenden ausführlichen Typ (SQL_DATETIME oder SQL_INTERVAL) festgelegt ist, und das Feld "SQL_DESC_DATETIME_INTERVAL_CODE" auf dem entsprechenden Subcode festgelegt ist.  
  
 **SQL_DESC_DATA_PTR [Anwendungsdiensts und Identitätsanbieter]**  
 Diese SQLPOINTER Datensatzfeldaustausch verweist auf eine Variable, die den Parameterwert (für APDs) oder den Spaltenwert (für ARDs) enthält. Dieses Feld ist ein *verzögerte Feld*. Es wird nicht zum Zeitpunkt verwendet, wird festgelegt, aber es wird zu einem späteren Zeitpunkt vom Treiber verwendet, um Daten abzurufen.  
  
 Die durch das SQL_DESC_DATA_PTR-Feld, der die ARD angegebene Spalte wird aufgehoben, wenn die *TargetValuePtr* Argument in einem Aufruf von **SQLBindCol** ein null-Zeiger ist oder wenn das SQL_DESC_DATA_PTR im Feld der ARD festgelegt, eine aufrufen, um **SQLSetDescField** oder **SQLSetDescRec** auf einen null-Zeiger. Andere Felder sind nicht betroffen, wenn das SQL_DESC_DATA_PTR-Feld auf einen null-Zeiger festgelegt wird.  
  
 Wenn der Aufruf von **SQLFetch** oder **SQLFetchScroll** füllt die Puffer, die auf dieses Feld nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben wurde kann, der Inhalt des Puffers nicht definiert sind.  
  
 Wenn das SQL_DESC_DATA_PTR-Feld eines APD, ARD oder IPD festgelegt ist, überprüft der Treiber an, dass der Wert in das SQL_DESC_TYPE-Feld die gültige ODBC-C-Datentypen oder ein Treiber-spezifische Daten enthält und alle anderen Felder, die Auswirkungen auf die Datentypen konsistent sind. Aufforderung eine konsistenzprüfung ist die einzige Verwendung für das SQL_DESC_DATA_PTR-Feld, der einem IPD. Insbesondere, wenn eine Anwendung das SQL_DESC_DATA_PTR-Feld von einem IPD und spätere Aufrufe festlegt **SQLGetDescField** auf dieses Feld nicht unbedingt zurückgegeben wird den Wert, der Sie eingerichtet haben. Weitere Informationen finden Sie unter "Von Konsistenzprüfungen" in [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 **SQL_DESC_DATETIME_INTERVAL_CODE [All]**  
 Dieses SQLSMALLINT-Datensatzfeld enthält dem Subcode für den spezifischen Datentyp "DateTime" oder das Intervall an, wenn das SQL_DESC_TYPE-Feld SQL_DATETIME oder SQL_INTERVAL hat. Dies gilt auch für SQL und C#-Datentypen. Der Code besteht aus den Datentypnamen mit "CODE" für "TYPE" oder "C_TYPE" (für Datetime-Typen) ersetzt, oder "CODE" für "INTERVAL" oder "C_INTERVAL" (für die Interval-Datentypen) ersetzt.  
  
 Wenn SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE in einen Anwendungsdienst-Deskriptor SQL_C_DEFAULT festgelegt und des Deskriptors kein Anweisungshandle zugeordnet, sind die Inhalte der SQL_DESC_DATETIME_INTERVAL_CODE nicht definiert.  
  
 Dieses Feld kann für die Datetime-Datentypen, die in der folgenden Tabelle aufgeführten festgelegt werden.  
  
|DateTime-Typen|DATETIME_INTERVAL_CODE|  
|--------------------|------------------------------|  
|SQL_TYPE_DATE/SQL_C_TYPE_DATE|SQL_CODE_DATE|  
|SQL_TYPE_TIME/SQL_C_TYPE_TIME|SQL_CODE_TIME|  
|SQL_TYPE_TIMESTAMP/ SQL_C_TYPE_TIMESTAMP|SQL_CODE_TIMESTAMP|  
  
 Dieses Feld kann für die Interval-Datentypen, die in der folgenden Tabelle aufgeführten festgelegt werden.  
  
|Intervalltyp|DATETIME_INTERVAL_CODE|  
|-------------------|------------------------------|  
|SQL_INTERVAL_DAY / SQL_C_INTERVAL_DAY|SQL_CODE_DAY|  
|SQL_INTERVAL_DAY_TO_HOUR / SQL_C_INTERVAL_DAY_TO_HOUR|SQL_CODE_DAY_TO_HOUR|  
|SQL_INTERVAL_DAY_TO_MINUTE / SQL_C_INTERVAL_DAY_TO_MINUTE|SQL_CODE_DAY_TO_MINUTE|  
|SQL_INTERVAL_DAY_TO_SECOND / SQL_C_INTERVAL_DAY_TO_SECOND|SQL_CODE_DAY_TO_SECOND|  
|SQL_INTERVAL_HOUR/ SQL_C_INTERVAL_HOUR|SQL_CODE_HOUR|  
|SQL_INTERVAL_HOUR_TO_MINUTE/ SQL_C_INTERVAL_HOUR_TO_MINUTE|SQL_CODE_HOUR_TO_MINUTE|  
|SQL_INTERVAL_HOUR_TO_SECOND / SQL_C_INTERVAL_HOUR_TO_SECOND|SQL_CODE_HOUR_TO_SECOND|  
|SQL_INTERVAL_MINUTE/ SQL_C_INTERVAL_MINUTE|SQL_CODE_MINUTE|  
|SQL_INTERVAL_MINUTE_TO_SECOND / SQL_C_INTERVAL_MINUTE_TO_SECOND|SQL_CODE_MINUTE_TO_SECOND|  
|SQL_INTERVAL_MONTH/ SQL_C_INTERVAL_MONTH|SQL_CODE_MONTH|  
|SQL_INTERVAL_SECOND / SQL_C_INTERVAL_SECOND|SQL_CODE_SECOND|  
|SQL_INTERVAL_YEAR/ SQL_C_INTERVAL_YEAR|SQL_CODE_YEAR|  
|SQL_INTERVAL_YEAR_TO_MONTH / SQL_C_INTERVAL_YEAR_TO_MONTH|SQL_CODE_YEAR_TO_MONTH|  
  
 Weitere Informationen zu den datenintervallen und dieses Feld, finden Sie unter [-datentypbezeichnungen und Deskriptoren](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md).  
  
 **SQL_DESC_DATETIME_INTERVAL_PRECISION [All]**  
 Dieses SQLINTEGER-Datensatz-Feld enthält die Genauigkeit ist das SQL_DESC_TYPE-Feld SQL_INTERVAL für anführenden Intervallwert. Wenn das Feld "SQL_DESC_DATETIME_INTERVAL_CODE" in einen Datentyp für Intervall festgelegt ist, wird dieses Feld auf die Genauigkeit für anführenden Intervallwert für standardmäßig festgelegt.  
  
 **SQL_DESC_DISPLAY_SIZE [IRDs]**  
 Dieses Feld schreibgeschützt SQLINTEGER Datensatz enthält die maximale Anzahl von Zeichen, die zum Anzeigen der Daten aus der Spalte erforderlich.  
  
 **SQL_DESC_FIXED_PREC_SCALE [Implementierung Deskriptoren]**  
 Dieses Feld schreibgeschützt SQLSMALLINT Datensatz wird auf SQL_TRUE, wenn die Spalte eine exakte numerische Spalte ist, und verfügt über eine feste Genauigkeit und ungleich null Dezimalstellen oder SQL_FALSE festgelegt, ist die Spalte keine genaue numerische Spalte mit einer festen Genauigkeit und Dezimalstellenanzahl.  
  
 **SQL_DESC_INDICATOR_PTR [Anwendungsdiensts]**  
 In ARDs, diese SQLLEN * Feld verweist auf die Indikatorvariable aufzeichnen. Diese Variable enthält SQL_NULL_DATA, wenn der Spaltenwert NULL ist. Für APDs die Indikatorvariable auf SQL_NULL_DATA festgelegt, um dynamische Argumente NULL anzugeben. Die Variable ist, andernfalls 0 (null), (es sei denn, die Werte in SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR den gleichen Zeiger).  
  
 Wenn das SQL_DESC_INDICATOR_PTR-Feld in einer ARD ein null-Zeiger ist, wird verhindert, dass der Treiber Zurückgeben von Informationen, ob die Spalte NULL oder nicht ist. Wenn die Spalte NULL ist und SQL_DESC_INDICATOR_PTR ist ein null-Zeiger, SQLSTATE 22002 (Indikatorvariable erforderlich, jedoch nicht bereitgestellt) wird zurückgegeben, wenn der Treiber versucht wird, zum Auffüllen des Puffers nach einem Aufruf von **SQLFetch** oder  **SQLFetchScroll**. Wenn der Aufruf von **SQLFetch** oder **SQLFetchScroll** hat keine zurückgegeben SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO, den Inhalt des Puffers sind nicht definiert.  
  
 Das Feld "SQL_DESC_INDICATOR_PTR" bestimmt, ob das Feld verweist SQL_DESC_OCTET_LENGTH_PTR festgelegt ist. Wenn der Datenwert für eine Spalte NULL ist, legt der Treiber die Indikatorvariable auf SQL_NULL_DATA fest. Das Feld verweist SQL_DESC_OCTET_LENGTH_PTR wird nicht festgelegt. Wenn ein NULL-Wert während der Abrufvorgang nicht gefunden wird, wird der Puffer, indem SQL_DESC_INDICATOR_PTR auf 0 (null) festgelegt ist, und der Puffer, der auf SQL_DESC_OCTET_LENGTH_PTR auf die Länge der Daten festgelegt ist.  
  
 Wenn das SQL_DESC_INDICATOR_PTR-Feld in einer APD ein null-Zeiger ist, kann nicht die Anwendung diese anwendungsparameterdeskriptor-Datensatz verwenden, NULL-Argumente an.  
  
 Dieses Feld ist ein *verzögerte Feld*: Es wird nicht zum Zeitpunkt verwendet, wird festgelegt, aber es wird zu einem späteren Zeitpunkt vom Treiber verwendet, um NULL-Zulässigkeit (für ARDs) oder NULL-Zulässigkeit (für APDs) zu ermitteln.  
  
 **SQL_DESC_LABEL [IRDs]**  
 Diese schreibgeschützte SQLCHAR * Feld "Record" enthält die spaltenbezeichnung oder den Titel. Wenn die Spalte nicht über eine Bezeichnung verfügt, enthält diese Variable den Namen der Spalte an. Wenn die Spalte nicht benannt ist und ohne Beschriftung ist, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_LENGTH [All]**  
 Diese SQLULEN-Datensatzfeld ist entweder die maximale oder die tatsächliche Länge einer Zeichenfolge in Zeichen oder ein binärer Datentyp in Byte. Es ist die maximale Länge für einen Datentyp mit fester Länge oder die tatsächliche Länge für einen Datentyp mit variabler Länge. Der Wert umfasst nicht immer die Null-Terminierungszeichen, das die Zeichenfolge endet. Für Werte, deren Typ SQL_TYPE_DATE, SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP oder eines der SQL-Interval-Datentypen ist, ist dieses Feld die Länge in Zeichen des Zeichen eine Zeichenfolgendarstellung des Werts "DateTime" oder das Intervall an.  
  
 Der Wert in dieses Feld möglicherweise von den Wert für "Length" als definiert, in ODBC 2. *.x*. Weitere Informationen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_LITERAL_PREFIX [IRDs]**  
 Diese schreibgeschützte SQLCHAR * Feld "Record" enthält, oder der Zeichen, die der Treiber als Präfix für ein Literal dieses Datentyps erkennt. Diese Variable enthält eine leere Zeichenfolge für einen Datentyp, der für den ein Zeichenfolgenliteral-Präfix nicht anwendbar ist.  
  
 **SQL_DESC_LITERAL_SUFFIX [IRDs]**  
 Diese schreibgeschützte SQLCHAR * Feld "Record" enthält, oder der Zeichen, die der Treiber als Suffix für ein Literal dieses Datentyps erkennt. Diese Variable enthält eine leere Zeichenfolge für einen Datentyp für den ein literales Suffix nicht anwendbar ist.  
  
 **SQL_DESC_LOCAL_TYPE_NAME [Implementierung Deskriptoren]**  
 Diese schreibgeschützte SQLCHAR * Feld "Record" enthält lokalisierte (native Language)-Namen für den Datentyp, der von der regulären Name des Datentyps unterscheiden kann. Wenn kein lokalisierter Name vorhanden ist, wird eine leere Zeichenfolge zurückgegeben. Dieses Feld ist nur zu Anzeigezwecken.  
  
 **SQL_DESC_NAME [Implementierung Deskriptoren]**  
 Diese SQLCHAR * Datensatzfeld im einen Deskriptor für die Zeile enthält den Spaltenalias aus, wenn sie angewendet wird. Wenn der Spaltenalias nicht anwendbar ist, wird der Name der Spalte zurückgegeben. In beiden Fällen setzt der Treiber für das Feld SQL_DESC_UNNAMED auf SQL_NAMED fest, wenn SQL_DESC_NAME-Felds festgelegt. Wenn Sie keinen Spaltennamen oder Spaltenalias vorhanden ist, wird der Treiber eine leere Zeichenfolge in SQL_DESC_NAME-Felds zurück und legt für die Feld SQL_DESC_UNNAMED SQL_UNNAMED fest.  
  
 Eine Anwendung kann von einem IPD SQL_DESC_NAME-Felds, der Parametername oder Alias, Parameter gespeicherter Prozeduren mit Namen anzugeben festlegen. (Weitere Informationen finden Sie unter [Bindungsparameter von Namen (Parameter genannt)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md).) Von einem IRD SQL_DESC_NAME-Felds ist ein schreibgeschütztes Feld. SQLSTATE HY091 (Ungültiger Deskriptorfeldbezeichner) wird zurückgegeben, wenn eine Anwendung versucht, die sie festgelegt.  
  
 In den Identitätsanbieter ist dieses Feld nicht definiert, wenn der Treiber keine benannten Parameter unterstützt. Wenn der Treiber benannte Parameter unterstützt und ist in der Lage, Parameter zu beschreiben, wird der Name des Parameters in diesem Feld zurückgegeben.  
  
 **SQL_DESC_NULLABLE [Implementierung Deskriptoren]**  
 In IRDs ist dieses Feld schreibgeschützt SQLSMALLINT Datensatz SQL_NULLABLE aus, wenn die Spalte NULL-Werte, SQL_NO_NULLS, wenn die Spalte keinen NULL-Werte oder SQL_NULLABLE_UNKNOWN verfügen kann, wenn nicht bekannt ist, ob die Spalte NULL-Werte annimmt. Dieses Feld bezieht sich auf die Resultsetspalte, nicht der Basisspalte.  
  
 In den Identitätsanbieter ist dieses Feld immer auf SQL_NULLABLE festgelegt, da dynamische Parameter immer NULL-Werte zulässt sind und können nicht von einer Anwendung festgelegt werden.  
  
 **SQL_DESC_NUM_PREC_RADIX [All]**  
 Dieses SQLINTEGER-Feld enthält den Wert 2 ist der Datentyp, in das SQL_DESC_TYPE-Feld einen ungefähren numerischen Datentyp, da das Feld "SQL_DESC_PRECISION" die Anzahl der Bits enthält. Dieses Feld enthält den Wert 10, wenn der Datentyp, in das SQL_DESC_TYPE-Feld einen genauen numerischen Datentyp ist, da die SQL_DESC_PRECISION-Feld die Anzahl der Dezimalstellen enthält. Dieses Feld ist für alle Typen von nicht-numerische Daten auf 0 festgelegt.  
  
 **SQL_DESC_OCTET_LENGTH [All]**  
 Dieses SQLLEN-Datensatz-Feld enthält die Länge einer Zeichenfolge oder Binärdatentyp in Bytes. Zeichen mit fester Länge oder Binärtypen ist dies die tatsächliche Länge in Bytes. Zeichen von variabler Länge oder Binärtypen ist dies die maximale Länge in Bytes. Dieser Wert immer schließt das Leerzeichen für die Null-Terminierungszeichen für Deskriptoren für Implementierung und immer Speicherplatz für die Null-Terminierungszeichen des Anwendungsdiensts enthält. Für Anwendungsdaten enthält dieses Feld die Größe des Puffers. Für APDs wird dieses Feld nur für die Ausgabe- oder Eingabe-/Ausgabeparameter definiert.  
  
 **SQL_DESC_OCTET_LENGTH_PTR [Anwendungsdiensts]**  
 Diese SQLLEN * Aufzeichnen von Feld-verweist auf eine Variable, die die gesamte Länge in Byte einer dynamischen Argument (für Deskriptoren für Parameter) oder ein Wert der gebundenen Spalte (für Deskriptoren für Zeile) enthalten soll.  
  
 Bei einer APD ist dieser Wert für alle Argumente außer Zeichen Zeichenfolgen- und Binärtypen ignoriert; Wenn dieses Feld zu SQL_NTS verweist, muss das dynamische Argument Null-terminiert sein. Führen Sie auf die Zeit zum anzugeben, dass ein gebundener Parameter ein Data-at-Execution-Parameter, eine Anwendung setzt dieses Feld in den entsprechenden Datensatz der APD auf eine Variable, die enthält den Wert SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC Makros . Bei mehr als ein entsprechendes Feld wird können SQL_DESC_DATA_PTR werden auf einen Wert festgelegt, die den Parameter eindeutig identifiziert können Sie die Anwendung zu bestimmen, welcher Parameter angefordert wird.  
  
 Wenn das Feld OCTET_LENGTH_PTR ein ARD ein null-Zeiger ist, gibt der Treiber keine Informationen zur Länge der Spalte zurück. Wenn das Feld SQL_DESC_OCTET_LENGTH_PTR ein APD ein null-Zeiger ist, nimmt der Treiber an, dass es sich bei Zeichenfolgen sowie binäre Werte Null-terminierte sind. (Binäre Werte darf nicht Null-terminiert sein aber müssen eine Länge, um das Abschneiden vermeiden zugewiesen werden.)  
  
 Wenn der Aufruf von **SQLFetch** oder **SQLFetchScroll** füllt die Puffer, die auf dieses Feld nicht SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben wurde kann, der Inhalt des Puffers nicht definiert sind. Dieses Feld ist ein *verzögerte Feld*. Es wird nicht zum Zeitpunkt verwendet, wird festgelegt, aber es wird zu einem späteren Zeitpunkt vom Treiber verwendet, um zu bestimmen, oder geben Sie die Oktettlänge der Daten.  
  
 **SQL_DESC_PARAMETER_TYPE [Identitätsanbieter]**  
 Diese SQLSMALLINT-Datensatzfeld ist für einen Eingabeparameter, SQL_PARAM_INPUT_OUTPUT für ein Eingabe-/Ausgabeparameter, SQL_PARAM_OUTPUT für ein Output-Parameter SQL_PARAM_INPUT_OUTPUT_STREAM für einen e/a-Stream-Parameter oder SQL_ auf SQL_PARAM_INPUT festgelegt. PARAM_OUTPUT_STREAM für gestreamt Output-Parameter. Es ist standardmäßig auf SQL_PARAM_INPUT festgelegt.  
  
 Für eine IPD ist das Feld SQL_PARAM_INPUT standardmäßig auf festgelegt, wenn die IPD nicht automatisch vom Treiber eingefügt wird (das Anweisungsattribut SQL_ATTR_ENABLE_AUTO_IPD wird SQL_FALSE). Eine Anwendung sollte dieses Feld in den IPD für Parameter festlegen, die keine Eingabeparameter sind.  
  
 **SQL_DESC_PRECISION [All]**  
 Dieses SQLSMALLINT-Datensatzfeld enthält die Anzahl der Ziffern für einen exakten numerischen Typ, die Anzahl der Bits in der Mantisse (Binary-Genauigkeit) für einen ungefähren numerischen Typ oder die Anzahl der Ziffern in der Komponente für Sekundenbruchteile für die SQL_TYPE_TIME, SQL_TYPE _TIMESTAMP oder SQL_INTERVAL_SECOND-Datentyp. Dieses Feld ist für alle anderen Datentypen nicht definiert.  
  
 Der Wert in dieses Feld möglicherweise von den Wert für "Precision" als definiert, in ODBC 2. *.x*. Weitere Informationen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_ROWVER [Implementierung Deskriptoren]**  
 Dieses Feld SQLSMALLINTrecord gibt an, ob eine Spalte automatisch vom DBMS geändert wird, wenn eine Zeile (z. B. eine Spalte vom Typ "Timestamp" in SQL Server) aktualisiert wird. Der Wert dieses Felds Datensatz festgelegt ist, SQL_TRUE, wenn die Spalte eine Spalte mit zeilenversionsverwaltung und SQL_FALSE andernfalls. Dieses Spaltenattribut ist vergleichbar mit einem Aufruf **SQLSpecialColumns** mit der SQL_ROWVER IdentifierType, um festzustellen, ob eine Spalte automatisch aktualisiert wird.  
  
 **SQL_DESC_SCALE [All]**  
 Dieses SQLSMALLINT-Datensatzfeld enthält definierte Anzahl von Dezimalstellen für die Datentypen decimal und numeric. Das Feld ist für alle anderen Datentypen nicht definiert.  
  
 Der Wert in dieses Feld möglicherweise von den Wert für "Scale" gemäß ODBC 2. *.x*. Weitere Informationen finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 **SQL_DESC_SCHEMA_NAME [IRDs]**  
 Diese schreibgeschützte SQLCHAR * Feld "Record" enthält den Schemanamen der Basistabelle, die die Spalte enthält. Der Rückgabewert ist treiberabhängig auf, wenn die Spalte ein Ausdruck ist, oder wenn die Spalte Teil einer Ansicht ist. Wenn die Datenquelle keine Schemas unterstützt oder der Schemaname kann nicht bestimmt werden, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_SEARCHABLE [IRDs]**  
 Dieses Feld schreibgeschützt SQLSMALLINT Datensatz wird auf einen der folgenden Werte festgelegt:  
  
-   SQL_PRED_NONE, wenn die Spalte kann, in verwendet werden einem **, in denen** Klausel. (Dies ist identisch mit der SQL_UNSEARCHABLE-Wert in ODBC 2. *.x*.)  
  
-   SQL_PRED_CHAR, wenn die Spalte kann, in verwendet werden eine **, in denen** -Klausel jedoch nur mit der **wie** Prädikat. (Dies ist identisch mit der SQL_LIKE_ONLY-Wert in ODBC 2. *.x*.)  
  
-   SQL_PRED_BASIC, wenn die Spalte kann, in verwendet werden einem **, in denen** -Klausel mit allen Vergleichsoperatoren mit Ausnahme **wie**. (Dies ist identisch mit der SQL_EXCEPT_LIKE-Wert in ODBC 2. *.x*.)  
  
-   SQL_PRED_SEARCHABLE, wenn die Spalte kann, in verwendet werden einem **, in denen** -Klausel mit jedem Vergleichsoperator.  
  
 **SQL_DESC_TABLE_NAME [IRDs]**  
 Diese schreibgeschützte SQLCHAR * Feld "Record" enthält den Namen der Basistabelle, die diese Spalte enthält. Der Rückgabewert ist treiberabhängig auf, wenn die Spalte ein Ausdruck ist, oder wenn die Spalte Teil einer Ansicht ist.  
  
 **SQL_DESC_TYPE [All]**  
 Dieser SQLSMALLINT-Datensatzfeld gibt an, die präzise SQL oder C-Datentyp für alle Datentypen mit Ausnahme von "DateTime" "und" Interval-Datentypen. Für die Datentypen "DateTime" und das Intervall gibt dieses Feld die ausführliche Datentyp, der SQL_DATETIME oder SQL_INTERVAL hat.  
  
 Wenn dieses Feld SQL_DATETIME oder SQL_INTERVAL enthält, muss das SQL_DESC_DATETIME_INTERVAL_CODE-Feld dem entsprechenden Subcode für den präzise Typ enthalten. Für Datetime-Datentypen SQL_DESC_TYPE enthält SQL_DATETIME und das Feld "SQL_DESC_DATETIME_INTERVAL_CODE" enthält ein Subcode für den bestimmten Datetime-Datentyp. Für die Interval-Datentypen SQL_DESC_TYPE enthält SQL_INTERVAL und die SQL_DESC_DATETIME_INTERVAL_CODE Feld eine Subcode für den bestimmten Intervall-Datentyp.  
  
 Die Werte in den Feldern SQL_DESC_TYPE und SQL_DESC_CONCISE_TYPE sind voneinander abhängig. Jedes Mal eines der Felder festgelegt ist, muss der andere ebenfalls festgelegt werden. SQL_DESC_TYPE kann festgelegt werden, durch einen Aufruf von **SQLSetDescField** oder **SQLSetDescRec**. SQL_DESC_CONCISE_TYPE kann festgelegt werden, durch einen Aufruf von **SQLBindCol** oder **SQLBindParameter**, oder **SQLSetDescField**.  
  
 Wenn SQL_DESC_TYPE in einen präzisen Datentyp als ein Intervall oder Datetime-Datentyp festgelegt ist, das Feld "SQL_DESC_CONCISE_TYPE" auf den gleichen Wert festgelegt ist, und das Feld "SQL_DESC_DATETIME_INTERVAL_CODE" auf 0 festgelegt ist.  
  
 Wenn SQL_DESC_TYPE auf den ausführlichen "DateTime" oder die Interval-Datentypen (SQL_DATETIME oder SQL_INTERVAL) festgelegt ist, und das Feld "SQL_DESC_DATETIME_INTERVAL_CODE" auf dem entsprechenden Subcode festgelegt ist, wird die SQL_DESC_CONCISE TYPE-Feld mit dem entsprechenden präzisen Datentyp festgelegt. SQL_DESC_TYPE auf eine präzise Typen "DateTime" oder das Intervall Festlegen der SQLSTATE-HY021 zurück (inkonsistente Deskriptorinformationen).  
  
 Wenn das SQL_DESC_TYPE-Feld festgelegt ist, durch einen Aufruf von **SQLBindCol**, **SQLBindParameter**, oder **SQLSetDescField**, die folgenden Felder werden auf die folgenden Standardwerte festgelegt. wie in der folgenden Tabelle gezeigt. Die Werte für die verbleibenden Felder eines Datensatzes sind nicht definiert.  
  
|Wert des SQL_DESC_TYPE|Andere Felder festgelegt implizit.|  
|------------------------------|---------------------------------|  
|SQL_CHAR, SQL_VARCHAR, SQL_C_CHAR, SQL_C_VARCHAR|SQL_DESC_LENGTH wird auf 1 festgelegt. SQL_DESC_PRECISION wird auf 0 festgelegt.|  
|SQL_DATETIME|Wenn SQL_CODE_DATE oder SQL_CODE_TIME SQL_DESC_DATETIME_INTERVAL_CODE festgelegt ist, wird die SQL_DESC_PRECISION auf 0 festgelegt. Wenn es um SQL_DESC_TIMESTAMP festgelegt ist, wird die SQL_DESC_PRECISION auf 6 festgelegt.|  
|SQL_DECIMAL, SQL_NUMERIC, SQL_C_NUMERIC|SQL_DESC_SCALE wird auf 0 festgelegt. SQL_DESC_PRECISION wird auf die Implementierung definierten Genauigkeit für den entsprechenden Datentyp festgelegt.<br /><br /> Finden Sie unter [SQL zu C: Numerische](../../../odbc/reference/appendixes/sql-to-c-numeric.md) Informationen dazu, wie Sie manuell einen SQL_C_NUMERIC Wert binden.|  
|SQL_FLOAT, SQL_C_FLOAT|SQL_DESC_PRECISION wird auf die standardmäßige Implementierung definierten Genauigkeit für SQL_FLOAT festgelegt.|  
|SQL_INTERVAL|Wenn auf einen Datentyp Interval SQL_DESC_DATETIME_INTERVAL_CODE festgelegt ist, wird die SQL_DESC_DATETIME_INTERVAL_PRECISION auf 2 (die standardmäßige Intervall führende Genauigkeit) festgelegt. Wenn das Intervall eine Komponente für Sekunden aufweist, wird die SQL_DESC_PRECISION auf 6 (der Standard-Intervall Sekunden Genauigkeit) festgelegt.|  
  
 Wenn eine Anwendung ruft **SQLSetDescField** festzulegende Felder einen Deskriptor aufrufen, sondern **SQLSetDescRec**, die Anwendung muss zuerst deklarieren Sie den Datentyp. Wenn dies der Fall, werden die anderen Felder, die in der vorherigen Tabelle aufgeführten implizit festgelegt. Wenn einer der Werte implizit festgelegt sind unzulässig ist, wird die Anwendung kann dann aufrufen **SQLSetDescField** oder **SQLSetDescRec** den unzulässige Wert explizit festlegen.  
  
 **SQL_DESC_TYPE_NAME [Implementierung Deskriptoren]**  
 Diese schreibgeschützte SQLCHAR * Feld "Record" enthält, der Datenquelle abhängiger Datentypname (z. B. "CHAR", "VARCHAR", und So weiter). Wenn der Datentypname unbekannt ist, enthält diese Variable eine leere Zeichenfolge.  
  
 **SQL_DESC_UNNAMED [Implementierung Deskriptoren]**  
 Dieses SQLSMALLINT Datensatz-Feld in einer Zeile Deskriptor wird vom Treiber auf SQL_NAMED oder SQL_UNNAMED festgelegt, wenn es sich bei SQL_DESC_NAME-Felds festgelegt. Wenn SQL_DESC_NAME-Felds einen Spaltenalias enthält, oder wenn der Spaltenalias nicht anwendbar ist, setzt der Treiber das SQL_DESC_UNNAMED-Feld auf SQL_NAMED an. Wenn eine Anwendung von einem IPD SQL_DESC_NAME-Felds, der Parametername oder Alias festlegt, setzt der Treiber das SQL_DESC_UNNAMED-Feld des IPD auf SQL_NAMED an. Liegt keine Spaltennamen oder Spaltenalias, legt der Treiber die Feld SQL_DESC_UNNAMED SQL_UNNAMED fest.  
  
 Eine Anwendung kann das Feld sql_desc_unnamed darf eine IPD auf SQL_UNNAMED festgelegt. Gibt ein Treiber SQLSTATE HY091 (Ungültiger Deskriptorfeldbezeichner), wenn eine Anwendung versucht, das Feld sql_desc_unnamed darf eine IPD auf SQL_NAMED festgelegt. Das Feld sql_desc_unnamed darf eine IRD ist schreibgeschützt; SQLSTATE HY091 (Ungültiger Deskriptorfeldbezeichner) wird zurückgegeben, wenn eine Anwendung versucht, die sie festgelegt.  
  
 **SQL_DESC_UNSIGNED [Implementierung Deskriptoren]**  
 Dieses Feld schreibgeschützt SQLSMALLINT Datensatz wird SQL_TRUE, wenn der Spaltentyp nicht signierte oder nicht numerisch ist und SQL_FALSE festgelegt, wenn der Spaltentyp signiert ist.  
  
 **SQL_DESC_UPDATABLE [IRDs]**  
 Dieses Feld schreibgeschützt SQLSMALLINT Datensatz wird auf einen der folgenden Werte festgelegt:  
  
-   SQL_ATTR_READ_ONLY, wenn die Resultsetspalte ist schreibgeschützt.  
  
-   SQL_ATTR_WRITE, wenn die Resultsetspalte ist Lese-/ Schreibzugriff.  
  
-   SQL_ATTR_READWRITE_UNKNOWN, wenn nicht bekannt ist, ob das Resultset-Spalte kann aktualisiert werden oder nicht.  
  
 SQL_DESC_UPDATABLE beschreibt die aktualisierbarkeit der Spalte im Resultset, nicht die Spalte in der Basistabelle. Möglicherweise anders als der Wert in dieses Feld die aktualisierbarkeit der Spalte in der Basistabelle, die auf dem dieses Resultset-Spalte basiert. Kann auf den Datentyp, Benutzerberechtigungen und die Definition des Resultsets selbst, ob eine Spalte aktualisiert werden basieren. Wenn unklar ist, ob eine Spalte aktualisiert werden kann, sollte die SQL_ATTR_READWRITE_UNKNOWN zurückgegeben werden.  
  
## <a name="consistency-checks"></a>Konsistenzprüfungen  
 Eine konsistenzprüfung wird automatisch vom Treiber ausgeführt, wenn eine Anwendung in einen Wert für das SQL_DESC_DATA_PTR-Feld des ARD, APD oder IPD übergibt. Wenn eines der Felder stimmt nicht mit anderen Feldern, **SQLSetDescField** SQLSTATE HY021 zurück (inkonsistente Deskriptorinformationen). Weitere Informationen finden Sie unter "Konsistenzprüfung" in [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden eine Spalte|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Ein Parameter gebunden|[SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Abrufen von einem Beschreibungsfeld|[SQLGetDescField-Funktion](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Abrufen von deskriptorfelder für mehrere|[SQLGetDescRec-Funktion](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Festlegen von mehreren deskriptorfeldern|[SQLSetDescRec-Funktion](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)
