---
title: SQLColAttribute-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLColAttribute
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColAttribute
helpviewer_keywords:
- SQLColAttribute function [ODBC]
ms.assetid: 8c45c598-cb01-4789-a571-e93619a18ed9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c4577b97c827d527422fe2448656496d7c196c40
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118701"
---
# <a name="sqlcolattribute-function"></a>SQLColAttribute-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standardkompatibilität: ISO 92  
  
 **Zusammenfassung**  
 **SQLColAttribute** Deskriptorinformationen für eine Spalte in einem Resultset zurückgegeben. Informationen der Sicherheitsbeschreibung wird als eine Zeichenfolge, einen Deskriptor abhängige Wert oder ein ganzzahliger Wert zurückgegeben.  
  
> [!NOTE]  
>  Weitere Informationen über welche des Treiber-Managers ordnet diese Funktion zu, wenn eine ODBC-3. *x* Anwendung arbeitet mit einer ODBC 2. *X* -Treiber verwenden, finden Sie unter [Zuordnen von Ersatzfunktionen für Abwärtskompatibilität-Kompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLColAttribute (  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ColumnNumber,  
      SQLUSMALLINT    FieldIdentifier,  
      SQLPOINTER      CharacterAttributePtr,  
      SQLSMALLINT     BufferLength,  
      SQLSMALLINT *   StringLengthPtr,  
      SQLLEN *        NumericAttributePtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *StatementHandle*  
 [Eingabe] Anweisungshandle.  
  
 *ColumnNumber*  
 [Eingabe] Die Anzahl der den Datensatz in den IRD aus dem der Wert des Felds, wird abgerufen werden sollen. Dieses Argument entspricht die Spaltennummer der Ergebnisdaten, die nacheinander in zunehmenden Spaltenreihenfolge, beginnend mit 1 angeordnet. Spalten können in beliebiger Reihenfolge beschrieben werden.  
  
 Spalte 0 dieses Argument angegeben werden kann, aber alle Werte außer SQL_DESC_TYPE und SQL_DESC_OCTET_LENGTH nicht definierte Werte zurück.  
  
 *FieldIdentifier*  
 [Eingabe] Das Deskriptorhandle. Dieses Handle wird definiert, welches Feld in IRD (z. B. SQL_COLUMN_TABLE_NAME) abgefragt werden sollen.  
  
 *CharacterAttributePtr*  
 [Ausgabe] Zeiger auf einen Puffer für die Rückgabe des Werts in der *FieldIdentifier* Feld der *ColumnNumber* Zeile vom IRD, wenn das Feld eine Zeichenfolge ist. Andernfalls wird das Feld nicht verwendet.  
  
 Wenn *CharacterAttributePtr* NULL ist, *StringLengthPtr* gibt die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer zurückgegeben verweist *CharacterAttributePtr*.  
  
 *BufferLength*  
 [Eingabe] Wenn *FieldIdentifier* ist ein ODBC-definierten-Feld und *CharacterAttributePtr* zeigt auf eine Zeichenfolge oder ein binärer Puffer, in dieses Argument muss die Länge des \*  *CharacterAttributePtr*. Wenn *FieldIdentifier* ist ein ODBC-definierten-Feld und \* *CharacterAttribute*Ptr ist eine ganze Zahl, wird dieses Feld ignoriert. Wenn die  *\*CharacterAttributePtr* ist eine Unicodezeichenfolge (beim Aufrufen von **SQLColAttributeW**), wird die *Pufferlänge* Argument muss eine gerade Zahl sein. Wenn *FieldIdentifier* ist ein Feld treiberdefinierten, die Anwendung zeigt die Art des Felds um den Treiber-Manager an, indem die *Pufferlänge* Argument. *BufferLength* können die folgenden Werte aufweisen:  
  
-   Wenn *CharacterAttributePtr* ist ein Zeiger auf ein Zeiger ist, *Pufferlänge* Wert SQL_IS_POINTER haben sollte.  
  
-   Wenn *CharacterAttributePtr* ist ein Zeiger auf eine Zeichenfolge, die *Pufferlänge* ist die Länge des Puffers.  
  
-   Wenn *CharacterAttributePtr* ist ein Zeiger auf ein binärer Puffer, der Anwendung stellen das Ergebnis der SQL_LEN_BINARY_ATTR (*Länge*)-Makro in *Pufferlänge*. Dadurch wird einen negativen Wert im platziert *Pufferlänge*.  
  
-   Wenn *CharacterAttributePtr* ist ein Zeiger auf einen Datentyp mit fester Länge *Pufferlänge* muss eine der folgenden sein: SQL_IS_INTEGER SQL_IS_UNINTEGER, SQL_SMALLINT oder SQLUSMALLINT.  
  
 *StringLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierung Byte für Zeichendaten) zurück in zurück zur Verfügung **CharacterAttributePtr*.  
  
 Für Daten im Zeichenformat, wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *Pufferlänge*, das die Deskriptorinformationen in \* *CharacterAttributePtr* auf abgeschnitten *BufferLength* abzüglich der Länge des ein Null-Terminierungszeichen und Null-terminiert ist vom Treiber.  
  
 Für alle anderen Typen von Daten, die den Wert der *Pufferlänge* wird ignoriert, und der Treiber geht davon aus, die Größe des **CharacterAttributePtr* 32 Bit.  
  
 *NumericAttributePtr*  
 [Ausgabe] Ein Zeiger auf eine ganze Zahl Puffer für die Rückgabe des Werts in der *FieldIdentifier* Feld der *ColumnNumber* Zeile vom IRD, wenn das Feld einen numerischen Deskriptortyp, z. B. SQL_DESC_COLUMN_LENGTH ist. Andernfalls wird das Feld nicht verwendet. Bitte beachten Sie, dass einige Treiber nur die untere 32-Bit-schreiben können oder 16-Bit, der einen Puffer und eine verlassen Bits höherer Ordnung unverändert. Aus diesem Grund sollten Anwendungen den Wert auf 0 initialisiert, vor dem Aufrufen dieser Funktion.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLColAttribute** gibt SQL_ERROR oder SQL_SUCCESS_WITH_INFO, entweder ein zugeordneten SQLSTATE-Wert abgerufen werden kann, durch den Aufruf **SQLGetDiagRec** mit eine *HandleType*von SQL_HANDLE_STMT auf, und ein *behandeln* von *StatementHandle*. Die folgende Tabelle enthält die SQLSTATE-Werten, die häufig vom **SQLColAttribute** und erläutert, jeweils im Kontext dieser Funktion; die Notation "(DM)" vorangestellt ist, die Beschreibungen der SQLSTATEs, die vom Treiber-Manager zurückgegeben. Der Rückgabecode jeder SQLSTATE-Wert zugeordnet ist SQL_ERROR zurück, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber-spezifische Meldung dient zu Informationszwecken. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|Zeichenfolgendaten, rechts abgeschnitten|Der Puffer \* *CharacterAttributePtr* war nicht groß genug, um den Wert der gesamten Zeichenfolge zurückzugeben, damit der Zeichenfolgenwert abgeschnitten wurde. Die Länge des Werts den ungekürzten Zeichenfolge wird zurückgegeben, **StringLengthPtr*. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07005|Keine vorbereitete Anweisung eine *Cursor-Spezifikation*|Die zugeordnete Anweisung die *StatementHandle* hat ein Resultset nicht zurückgegeben und *FieldIdentifier* war nicht SQL_DESC_COUNT. Es wurden keine Spalten aus, um zu beschreiben.|  
|07009|Ungültiger Deskriptorindex|(DM) der angegebene Wert für *ColumnNumber* war gleich 0 und das Anweisungsattribut SQL_ATTR_USE_BOOKMARKS SQL_UB_OFF.<br /><br /> Der angegebene Wert für das Argument *ColumnNumber* war größer als die Anzahl der Spalten im Resultset.|  
|HY000|Allgemeiner Fehler.|Für die keine spezifischen SQLSTATE ist und für die keine implementierungsabhängige SQLSTATE definiert wurde, ist ein Fehler aufgetreten. Die zurückgegebene Fehlermeldung **SQLGetDiagField** von Diagnosedaten Struktur beschreibt den Fehler und seine Ursache.|  
|HY001|Fehler bei der speicherbelegung|Der Treiber konnte nicht zur speicherbelegung, die zur Unterstützung der Ausführung oder den Abschluss der Funktion erforderlich sind.|  
|HY008|Der Vorgang wurde abgebrochen|Die asynchrone Verarbeitung wurde aktiviert, für die *StatementHandle*. Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle*. Und dann die Funktion erneut aufgerufen wurde, auf die *StatementHandle*.<br /><br /> Die Funktion aufgerufen wurde, und bevor sie ausgeführt wurden, **SQLCancel** oder **SQLCancelHandle** aufgerufen wurde, auf die *StatementHandle* von einem anderen Thread in einem Multithread-Anwendung.|  
|HY010|Fehler in der Funktionsreihenfolge|(DM) eine asynchron ausgeführte Funktion wurde aufgerufen, der Verbindungshandles, die zugeordnet wird die *StatementHandle*. Diese Funktion Aynchronous wurde noch ausgeführt werden, wenn SQLColAttribute aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** wurde aufgerufen, die *StatementHandle* und SQL_PARAM_DATA_ zurückgegeben VERFÜGBAR. Diese Funktion war aufgerufen, bevor Daten für alle Stream-Parameter abgerufen wurde.<br /><br /> (DM) die Funktion wurde vor dem Aufruf aufgerufen **SQLPrepare**, **SQLExecDirect**, oder einer Katalogfunktion für die *StatementHandle*.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht auf dieses hier) wurde aufgerufen, die *StatementHandle* und wurde noch ausgeführt werden, wenn diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos** wurde aufgerufen, die *StatementHandle* und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor die Daten für alle Data-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Fehler bei arbeitsspeicherverwaltung|Der Funktionsaufruf kann nicht verarbeitet werden, da die zugrunde liegenden Speicherobjekte, möglicherweise aufgrund von unzureichendem Speicher konnte nicht zugegriffen werden.|  
|HY090|Ungültige Zeichenfolgen- oder Pufferlänge.|(DM)  *\*CharacterAttributePtr* ist eine Zeichenfolge und *Pufferlänge* war kleiner als 0, aber nicht SQL_NTS gleich.|  
|HY091|Ungültiger Deskriptorfeldbezeichner|Der angegebene Wert für das Argument *FieldIdentifier* war keiner der definierten Werte und war kein implementierungsdefinierte Wert.|  
|HY117|Verbindung wird aufgrund eines unbekannten Transaktionsstatus angehalten. Trennen Sie nur aus, und nur-Lese Funktionen sind zulässig.|(DM) finden Sie weitere Informationen zum angehaltenen Zustand, [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Vom Treiber nicht unterstützt|Der angegebene Wert für das Argument *FieldIdentifier* wurde vom Treiber nicht unterstützt.|  
|HYT01|Das Verbindungstimeout ist abgelaufen|Das Verbindungstimeout ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Das Verbindungstimeout festgelegt ist, über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Diese Funktion wird vom Treiber nicht unterstützt werden.|(DM) der Treiber zugeordnet der *StatementHandle* die Funktion nicht unterstützt.|  
|IM017|Abruf ist im Modus für asynchrone Benachrichtigung deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist Abruf deaktiviert.|  
|IM018|**SQLCompleteAsync** nicht zum Abschließen des vorherigen asynchronen Vorgangs auf diesem Handle aufgerufen wurde.|Wenn der vorherige Funktionsaufruf auf den Ziehpunkt SQL_STILL_EXECUTING zurückgibt und Notification-Modus aktiviert ist, **SQLCompleteAsync** muss aufgerufen werden, auf den Ziehpunkt, um nach der Verarbeitung und der Vorgang abgeschlossen werden.|  
  
 Beim Aufruf nach **SQLPrepare** und vor dem **SQLExecute**, **SQLColAttribute** können alle SQLSTATE, der zurückgegeben werden kann zurückgeben **SQLPrepare**oder **SQLExecute**, abhängig davon ab, wenn die Datenquelle die zugeordnete SQL-Anweisung ergibt die *StatementHandle*.  
  
 Zur Verbesserung der Leistung, eine Anwendung nicht aufrufen sollten **SQLColAttribute** vor der Ausführung einer Anweisung.  
  
## <a name="comments"></a>Kommentare  
 Informationen zur Verwendung von Anwendungen auf die zurückgegebenen Informationen **SQLColAttribute**, finden Sie unter [Ergebnismetadaten festgelegt](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 **SQLColAttribute** gibt Informationen zurück, entweder in \* *NumericAttributePtr* oder im \* *CharacterAttributePtr*. Integer-Informationen werden im zurückgegeben \* *NumericAttributePtr* als SQLLEN Wert; alle anderen Formate, die Informationen in zurückgegeben werden \* *CharacterAttributePtr*. Wenn die Informationen zurückgegeben wird \* *NumericAttributePtr*, ignoriert der Treiber die *CharacterAttributePtr*, *Pufferlänge*, und  *StringLengthPtr*. Wenn die Informationen zurückgegeben wird \* *CharacterAttributePtr*, ignoriert der Treiber die *NumericAttributePtr*.  
  
 **SQLColAttribute** Werte aus der deskriptorfelder vom IRD zurückgegeben. Die Funktion wird mit einer Deskriptorhandles, anstatt ein Anweisungshandle aufgerufen. Die Rückgabewerte **SQLColAttribute** für die *FieldIdentifier* weiter unten in diesem Abschnitt aufgeführten Werte können auch durch Aufrufen von abrufen **SQLGetDescField** mit der entsprechende IRD-Handle.  
  
 Der Deskriptor aktuell definierte Felder, die Version von ODBC in der sie eingeführt wurden, und die Argumente, die in denen Informationen, diese zurückgegeben werden werden weiter unten in diesem Abschnitt; Weitere deskriptortypen können von Treibern Nutzen aus verschiedenen Datenquellen definiert werden.  
  
 Eine ODBC-3. *x* Treiber muss einen Wert zurück, für jedes der deskriptorfelder. Wenn einem Beschreibungsfeld nicht für einen Treiber oder eine Datenquelle gelten und, sofern nichts anderes angegeben ist, der Treiber 0 gibt \* *StringLengthPtr* oder eine leere Zeichenfolge in **CharacterAttributePtr*.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Der ODBC-3. *x* Funktion **SQLColAttribute** ersetzt die veraltete ODBC 2. *X* Funktion **SQLColAttributes**. Beim Zuordnen von **SQLColAttributes** zu **SQLColAttribute** (bei einer ODBC 2. *X* Anwendung arbeitet mit einer ODBC 3. *X* Treiber), oder die Zuordnung **SQLColAttribute** zu **SQLColAttributes** (Wenn eine ODBC 3. *X* Anwendung arbeitet mit einer ODBC 2. *X* Treiber), der Treiber-Manager entweder übergibt den Wert des *FieldIdentifier* , ordnet es einen neuen Wert oder ein Fehler zurückgegeben, wie folgt:  
  
> [!NOTE]  
>  Das Präfix in verwendet *FieldIdentifier* Werte in ODBC 3. *X* wurde von diesem verwendet ODBC 2 geändert. *X*. Das neue Präfix ist "SQL_DESC"; das alte Präfix ist "SQL_COLUMN".  
  
-   Wenn die **#define** Wert, der die ODBC 2. *X* *FieldIdentifier* ist identisch mit der **#define** Wert die ODBC 3. *X* *FieldIdentifier*, der Wert im Aufruf Funktion wird nur übergeben.  
  
-   Die **#define** Werte die ODBC 2. *X* *FieldIdentifiers* SQL_COLUMN_LENGTH SQL_COLUMN_PRECISION und SQL_COLUMN_SCALE unterscheiden sich von der **#define** Werte die ODBC 3. *X* *FieldIdentifiers* SQL_DESC_SCALE, SQL_DESC_PRECISION und SQL_DESC_LENGTH. Eine ODBC-2. *x* Treiber muss nur die ODBC 2. unterstützen. *X* Werte. Eine ODBC-3. *x* Treiber muss sowohl "SQL_COLUMN" und "SQL_DESC" Werte für diese drei unterstützen *FieldIdentifiers*. Diese Werte unterscheiden sich, da die Genauigkeit, Dezimalstellen und Länge in ODBC 3. unterschiedlich definiert sind. *x* als Kacheln in ODBC 2. *X*. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
-   Wenn die **#define** Wert, der die ODBC 2. *X* *FieldIdentifier* unterscheidet sich von der **#define** Wert die ODBC 3. *X* *FieldIdentifier*, wie mit der Anzahl, Namen, tritt ein, und der entsprechende Wert NULL-Werten, den Wert im Aufruf Funktion zugeordnet ist. Z. B. SQL_COLUMN_COUNT SQL_DESC_COUNT, zugeordnet ist und SQL_DESC_COUNT SQL_COLUMN_COUNT, abhängig von der Richtung der Zuordnung zugeordnet ist.  
  
-   Wenn *FieldIdentifier* ist ein neuer Wert in ODBC 3. *X*, für die gab es keinen entsprechenden Wert in ODBC 2. *X*, es wird nicht zugeordnet werden, wenn eine ODBC 3. *X* Anwendung in einem Aufruf verwendet **SQLColAttribute** in einer ODBC 2. *X* Treiber, und der Aufruf SQLSTATE HY091 zurück (Ungültiger Deskriptorfeldbezeichner).  
  
 Die folgende Tabelle enthält die Sicherheitsbeschreibung-Typen, die vom **SQLColAttribute**. Der Typ für *NumericAttributePtr* Werte **SQLLEN \*** .  
  
|*FieldIdentifier*|Information<br /><br /> in zurückgegeben|Beschreibung|  
|-----------------------|---------------------------------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE, wenn die Spalte eine Spalte automatisch inkrementiert wird.<br /><br /> SQL_FALSE, wenn die Spalte keiner Spalte automatisch inkrementiert oder nicht numerisch ist.<br /><br /> Dieses Feld gilt für numerische Spalten vom Typ nur zur Verfügung. Eine Anwendung können Sie die Werte in eine Zeile mit sloupec Autoincrement eingefügt, aber die Werte in der Spalte in der Regel kann nicht aktualisiert werden.<br /><br /> Wenn eine Einfügung in sloupec Autoincrement erfolgt, wird ein eindeutiger Wert zum Zeitpunkt des Einfügens in die Spalte eingefügt. Die Schrittweite ist nicht definiert, aber Daten datenquellenspezifische ist. Eine Anwendung sollte nicht davon ausgehen, dass sloupec Autoincrement bestimmten Zeitpunkt oder Schritten durch keinen bestimmten Wert beginnt.|  
|SQL_DESC_BASE_COLUMN_NAME (ODBC 3.0)|*CharacterAttributePtr*|Der Name der Basisspalte für das Ergebnis legen Spalte. Wenn ein Name der Basisspalte nicht (wie im Fall von Spalten, bei denen Ausdrücke) vorhanden ist, enthält diese Variable eine leere Zeichenfolge.<br /><br /> Diese Informationen werden vom SQL_DESC_BASE_COLUMN_NAME-Datensatzfeld vom IRD zurückgegeben, die ein Feld schreibgeschützt ist.|  
|SQL_DESC_BASE_TABLE_NAME (ODBC 3.0)|*CharacterAttributePtr*|Der Name der Basistabelle, die die Spalte enthält. Wenn der Name der Basistabelle kann nicht definiert werden, oder es nicht, gilt und klicken Sie dann diese Variable eine leere Zeichenfolge enthält.<br /><br /> Diese Informationen werden vom SQL_DESC_BASE_TABLE_NAME-Datensatzfeld vom IRD zurückgegeben, die ein Feld schreibgeschützt ist.|  
|SQL_DESC_CASE_SENSITIVE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE, wenn die Spalte als Groß-/Kleinschreibung für Sortierungen und Vergleiche behandelt wird.<br /><br /> SQL_FALSE, wenn die Spalte nicht, wie Groß-/Kleinschreibung für Sortierungen und Vergleiche behandelt wird, oder nicht auf Zeichen basierende ist.|  
|SQL_DESC_CATALOG_NAME (ODBC 2.0)|*CharacterAttributePtr*|Der Katalog der Tabelle, die die Spalte enthält. Der zurückgegebene Wert ist Implementierung definiert, wenn die Spalte ein Ausdruck ist, oder wenn die Spalte Teil einer Ansicht ist. Wenn die Datenquelle keine Kataloge unterstützt oder der Name des Katalogs kann nicht bestimmt werden, wird eine leere Zeichenfolge zurückgegeben. Diese VARCHAR-Datensatzfeld ist nicht auf 128 Zeichen beschränkt.|  
|SQL_DESC_CONCISE_TYPE (ODBC 1.0)|*NumericAttributePtr*|Der präzisen Datentyp.<br /><br /> Für die Datentypen "DateTime" und das Intervall gibt dieses Feld den präzisen Datentyp zurück. z. B. SQL_TYPE_TIME oder SQL_INTERVAL_YEAR. (Weitere Informationen finden Sie unter [-datentypbezeichnungen und Deskriptoren](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) in Anhang D: Die Datentypen.)<br /><br /> Diese Informationen werden vom SQL_DESC_CONCISE_TYPE-Datensatzfeld vom IRD zurückgegeben.|  
|SQL_DESC_COUNT (ODBC 1.0)|*NumericAttributePtr*|Die Anzahl der Spalten im Resultset verfügbar sind. Dies gibt 0 zurück, wenn keine Spalten im Resultset vorhanden sind. Der Wert in der *ColumnNumber* Argument wird ignoriert.<br /><br /> Diese Informationen werden aus dem SQL_DESC_COUNT-Header-Feld vom IRD zurückgegeben.|  
|SQL_DESC_DISPLAY_SIZE (ODBC 1.0)|*NumericAttributePtr*|Maximale Anzahl von Zeichen, die zum Anzeigen von Daten aus der Spalte erforderlich. Weitere Informationen zu Größe, finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge übertragen und Anzeigen der Größe](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|SQL_DESC_FIXED_PREC_SCALE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE, wenn die Spalte hat eine feste Genauigkeit und die ungleich null Dezimalstellen, die Daten datenquellenspezifische sind.<br /><br /> SQL_FALSE, wenn die Spalte eine feste Genauigkeit und die ungleich null Dezimalstellen, die Daten datenquellenspezifische sind nicht besitzt.|  
|SQL_DESC_LABEL (ODBC 2.0)|*CharacterAttributePtr*|Die spaltenbezeichnung oder Titel. Z. B. eine Spalte namens EmpName kann mit der Bezeichnung Employee Name oder mit einem Alias gekennzeichnet werden kann.<br /><br /> Wenn eine Spalte nicht über eine Bezeichnung verfügt, wird der Name der Spalte zurückgegeben. Wenn die Spalte ohne Beschriftung und nicht benannt ist, wird eine leere Zeichenfolge zurückgegeben.|  
|SQL_DESC_LENGTH (ODBC 3.0)|*NumericAttributePtr*|Geben Sie einen numerischen Wert, der entweder die maximale oder die aktuelle Zeichenlänge von Zeichendaten Zeichenfolgen- oder Binärdatentyps. Es ist die maximale Zeichenlänge für einen Datentyp mit fester Länge oder die tatsächlichen Zeichenlänge für einen Datentyp mit variabler Länge. Der Wert umfasst nicht immer das Null-Terminierung Byte, das die Zeichenfolge endet.<br /><br /> Diese Informationen werden vom SQL_DESC_LENGTH-Datensatzfeld vom IRD zurückgegeben.<br /><br /> Weitere Informationen zu Länge, finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|SQL_DESC_LITERAL_PREFIX (ODBC 3.0)|*CharacterAttributePtr*|Dieses VARCHAR(128)-Datensatz-Feld enthält das Zeichen oder die Zeichen, die der Treiber als Präfix für ein Literal dieses Datentyps erkennt. Dieses Feld enthält eine leere Zeichenfolge für einen Datentyp, der für den ein Zeichenfolgenliteral-Präfix nicht anwendbar ist. Weitere Informationen finden Sie unter [Literal-Präfixe und Suffixe](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md).|  
|SQL_DESC_LITERAL_SUFFIX (ODBC 3.0)|*CharacterAttributePtr*|Dieses VARCHAR(128)-Datensatz-Feld enthält das Zeichen oder die Zeichen, die der Treiber als Suffix für ein Literal dieses Datentyps erkennt. Dieses Feld enthält eine leere Zeichenfolge für einen Datentyp für den ein literales Suffix nicht anwendbar ist. Weitere Informationen finden Sie unter [Literal-Präfixe und Suffixe](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md).|  
|SQL_DESC_LOCAL_TYPE_NAME (ODBC 3.0)|*CharacterAttributePtr*|Diese VARCHAR(128) Datensatzfeld enthält einen beliebigen Namen lokalisierte (native Language) für den Datentyp, der von der regulären Name des Datentyps unterscheiden kann. Wenn kein lokalisierter Name vorhanden ist, wird eine leere Zeichenfolge zurückgegeben. Dieses Feld ist nur zu Anzeigezwecken. Der Zeichensatz der Zeichenfolge ist vom Gebietsschema abhängige und in der Regel der Standardzeichensatz des Servers.|  
|SQL_DESC_NAME (ODBC 3.0)|*CharacterAttributePtr*|Der Spaltenalias, wenn sie angewendet wird. Wenn der Spaltenalias nicht anwendbar ist, wird der Name der Spalte zurückgegeben. In beiden Fällen wird die SQL_DESC_UNNAMED auf SQL_NAMED festgelegt. Wenn Sie keinen Spaltennamen oder Spaltenalias vorhanden ist, wird eine leere Zeichenfolge zurückgegeben, und SQL_DESC_UNNAMED SQL_UNNAMED projektbuildziel.<br /><br /> Diese Informationen werden vom SQL_DESC_NAME-Datensatzfeld vom IRD zurückgegeben.|  
|SQL_DESC_NULLABLE (ODBC 3.0)|*NumericAttributePtr*|SQL_ NULL-Werte zulässt, wenn die Spalte NULL-Werte enthalten kann; SQL_NO_NULLS, wenn die Spalte keinen NULL-Werte; oder SQL_NULLABLE_UNKNOWN, wenn nicht bekannt ist, ob die Spalte NULL-Werte annimmt.<br /><br /> Diese Informationen werden vom SQL_DESC_NULLABLE-Datensatzfeld vom IRD zurückgegeben.|  
|SQL_DESC_NUM_PREC_RADIX (ODBC 3.0)|*NumericAttributePtr*|Wenn der Datentyp, in das SQL_DESC_TYPE-Feld einen ungefähren numerischen Datentyp ist, enthält dieses SQLINTEGER-Feld den Wert 2, da die SQL_DESC_PRECISION-Feld die Anzahl der Bits enthält. Wenn der Datentyp, in das SQL_DESC_TYPE-Feld einen genauen numerischen Datentyp ist, enthält dieses Feld einen Wert von 10, da die SQL_DESC_PRECISION-Feld die Anzahl der Dezimalstellen enthält. Dieses Feld ist für alle Typen von nicht-numerische Daten auf 0 festgelegt.|  
|SQL_DESC_OCTET_LENGTH (ODBC 3.0)|*NumericAttributePtr*|Die Länge von einem Zeichendatentyp Zeichenfolgen- oder Binärdaten in Bytes. Zeichen mit fester Länge oder Binärtypen ist dies die tatsächliche Länge in Bytes. Zeichen von variabler Länge oder Binärtypen ist dies die maximale Länge in Bytes. Dieser Wert umfasst keine null-Abschlusszeichen.<br /><br /> Diese Informationen werden vom SQL_DESC_OCTET_LENGTH-Datensatzfeld vom IRD zurückgegeben.<br /><br /> Weitere Informationen zu Länge, finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|SQL_DESC_PRECISION (ODBC 3.0)|*NumericAttributePtr*|Ein numerischer Wert, der für einen numerischen Datentyp die entsprechende Genauigkeit bezeichnet. Bei allen Datentypen SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP, und alle die Interval-Datentypen, die ein Zeitintervall, dessen Wert darstellen, ist die anwendbaren Genauigkeit der Sekundenbruchteil-Komponente.<br /><br /> Diese Informationen werden vom SQL_DESC_PRECISION-Datensatzfeld vom IRD zurückgegeben.|  
|SQL_DESC_SCALE (ODBC 3.0)|*NumericAttributePtr*|Ein numerischer Wert, der die entsprechenden Skalierung für einen numerischen Datentyp aufweisen. Für die Datentypen DECIMAL und NUMERIC ist dies die definierten Anzahl von Dezimalstellen an. Es ist nicht für alle anderen Datentypen definiert.<br /><br /> Diese Informationen werden vom Skalierung-Datensatzfeld vom IRD zurückgegeben.|  
|SQL_DESC_SCHEMA_NAME (ODBC 2.0)|*CharacterAttributePtr*|Das Schema der Tabelle, die die Spalte enthält. Der zurückgegebene Wert ist Implementierung definiert, wenn die Spalte ein Ausdruck ist, oder wenn die Spalte Teil einer Ansicht ist. Wenn die Datenquelle keine Schemas unterstützt oder der Schemaname kann nicht bestimmt werden, wird eine leere Zeichenfolge zurückgegeben. Diese VARCHAR-Datensatzfeld ist nicht auf 128 Zeichen beschränkt.|  
|SQL_DESC_SEARCHABLE (ODBC 1.0)|*NumericAttributePtr*|SQL_PRED_NONE, wenn die Spalte in einer WHERE-Klausel verwendet werden kann. (Dies ist der SQL_UNSEARCHABLE-Wert in ODBC 2. identisch. *x*.)<br /><br /> SQL_PRED_CHAR, wenn die Spalte in einer WHERE-Klausel jedoch nur mit dem LIKE-Prädikat verwendet werden kann. (Dies ist der SQL_LIKE_ONLY-Wert in ODBC 2. identisch. *x*.)<br /><br /> SQL_PRED_BASIC, wenn die Spalte in einer WHERE-Klausel mit allen Vergleichsoperatoren mit Ausnahme von ähnlichen verwendet werden kann. (Dies ist der SQL_EXCEPT_LIKE-Wert in ODBC 2. identisch. *x*.)<br /><br /> SQL_PRED_SEARCHABLE, wenn die Spalte in einer WHERE-Klausel mit jedem Vergleichsoperator verwendet werden kann.<br /><br /> Spalten vom Datentyp SQL_LONGVARCHAR und in der Regel return SQL_PRED_CHAR SQL_LONGVARBINARY.|  
|SQL_DESC_TABLE_NAME (ODBC 2.0)|*CharacterAttributePtr*|Der Name der Tabelle, die die Spalte enthält. Der zurückgegebene Wert ist Implementierung definiert, wenn die Spalte ein Ausdruck ist, oder wenn die Spalte Teil einer Ansicht ist.<br /><br /> Wenn Sie den Namen der Tabelle nicht bestimmt werden kann, wird eine leere Zeichenfolge zurückgegeben.|  
|SQL_DESC_TYPE (ODBC 3.0)|*NumericAttributePtr*|Ein numerischer Wert, der angibt, den SQL-Datentyp.<br /><br /> Wenn *ColumnNumber* ist gleich 0 ist, wird SQL_BINARY für Lesezeichen mit variabler Länge zurückgegeben und SQL_INTEGER für Lesezeichen mit fester Länge ist.<br /><br /> Für die Datentypen "DateTime" und das Intervall gibt dieses Feld den Datentyp für die ausführliche zurück: SQL_DATETIME oder SQL_INTERVAL. (Weitere Informationen finden Sie unter [-datentypbezeichnungen und Deskriptoren](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) in Anhang D: Datentypen.<br /><br /> Diese Informationen werden vom SQL_DESC_TYPE-Datensatzfeld vom IRD zurückgegeben. **Hinweis**:  Die Arbeit mit ODBC 2. *x* Treiber, verwenden Sie stattdessen SQL_DESC_CONCISE_TYPE.|  
|SQL_DESC_TYPE_NAME VERWENDET WIRD (ODBC 1.0)|*CharacterAttributePtr*|Daten Datenquelle abhängiger Datentypname; z. B. "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY" oder "CHAR () für BIT-Daten".<br /><br /> Wenn der Typ unbekannt ist, wird eine leere Zeichenfolge zurückgegeben.|  
|SQL_DESC_UNNAMED (ODBC 3.0)|*NumericAttributePtr*|SQL_NAMED oder SQL_UNNAMED. Wenn vom IRD SQL_DESC_NAME-Felds einen Spaltenalias oder einen Spaltennamen enthält, wird die SQL_NAMED zurückgegeben. Wenn Sie keine Spaltennamen oder Spaltenalias vorhanden ist, wird die SQL_UNNAMED zurückgegeben.<br /><br /> Diese Informationen werden vom SQL_DESC_UNNAMED-Datensatzfeld vom IRD zurückgegeben.|  
|SQL_DESC_UNSIGNED (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE, wenn die Spalte (oder nicht numerisch) ohne Vorzeichen ist.<br /><br /> SQL_FALSE, wenn die Spalte signiert ist.|  
|SQL_DESC_UPDATABLE (ODBC 1.0)|*NumericAttributePtr*|Spalte wird von den Werten der definierten Konstanten beschrieben:<br /><br /> SQL_ATTR_READONLY SQL_ATTR_WRITE SQL_ATTR_READWRITE_UNKNOWN<br /><br /> SQL_DESC_UPDATABLE beschreibt die aktualisierbarkeit der Spalte im Resultset, nicht die Spalte in der Basistabelle. Die aktualisierbarkeit des auf dem die Resultsetspalte basiert Basisspalte kann von den Wert in dieses Feld unterscheiden. Kann auf den Datentyp, Benutzerberechtigungen und die Definition des Resultsets selbst, ob eine Spalte aktualisiert werden basieren. Wenn unklar ist, ob eine Spalte aktualisiert werden kann, sollte die SQL_ATTR_READWRITE_UNKNOWN zurückgegeben werden.|  
  
 **SQLColAttribute** ist eine erweiterbare Alternative zur **SQLDescribeCol**. **SQLDescribeCol** gibt einen festen Satz von Informationen der Sicherheitsbeschreibung, die basierend auf ANSI-89 SQL. **SQLColAttribute** ermöglicht den Zugriff auf die umfassendere Informationen der Sicherheitsbeschreibung im ANSI SQL-92 und DBMS-herstellererweiterungen verfügbar.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Binden einen Puffer an eine Spalte in einem Resultset|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Anweisungsverarbeitung Abbrechen|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einem Resultset|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Abrufen eines Zeilenblocks von Daten oder ein Ergebnis durchblättern festlegen|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen mehrerer Zeilen von Daten|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
  
## <a name="example"></a>Beispiel  
 Der folgende Code gibt keine Handles und Verbindungen frei. Finden Sie unter [SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md), [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md), und [SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md) Codebeispiele, Handles und Anweisungen freizugeben.  
  
```cpp  
// SQLColAttibute.cpp  
// compile with: user32.lib odbc32.lib  
  
#define UNICODE  
  
#include <windows.h>  
#include <sqlext.h>  
#include <strsafe.h>  
  
struct DataBinding {  
   SQLSMALLINT TargetType;  
   SQLPOINTER TargetValuePtr;  
   SQLINTEGER BufferLength;  
   SQLLEN StrLen_or_Ind;  
};  
  
void printStatementResult(SQLHSTMT hstmt) {  
   int bufferSize = 1024, i;  
   SQLRETURN retCode;  
   SQLSMALLINT numColumn = 0, bufferLenUsed;
   
   retCode = SQLNumResultCols(hstmt, &numColumn);  
   
   SQLPOINTER* columnLabels = (SQLPOINTER *)malloc( numColumn * sizeof(SQLPOINTER*) );  
   struct DataBinding* columnData = (struct DataBinding*)malloc( numColumn * sizeof(struct DataBinding) );  
  
   printf( "Columns from that table:\n" );  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnLabels[i] = (SQLPOINTER)malloc( bufferSize*sizeof(char) );  
  
      retCode = SQLColAttribute(hstmt, (SQLUSMALLINT)i + 1, SQL_DESC_LABEL, columnLabels[i], (SQLSMALLINT)bufferSize, &bufferLenUsed, NULL);  
      wprintf( L"Column %d: %s\n", i, (wchar_t*)columnLabels[i] );  
   }  
  
   // allocate memory for the binding  
   for ( i = 0 ; i < numColumn ; i++ ) {  
      columnData[i].TargetType = SQL_C_CHAR;  
      columnData[i].BufferLength = (bufferSize+1);  
      columnData[i].TargetValuePtr = malloc( sizeof(unsigned char)*columnData[i].BufferLength );  
   }  
  
   // setup the binding   
   for ( i = 0 ; i < numColumn ; i++ ) {  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, columnData[i].TargetType,   
         columnData[i].TargetValuePtr, columnData[i].BufferLength, &(columnData[i].StrLen_or_Ind));  
   }  
  
   printf( "Data from that table:\n" );  
   // fetch the data and print out the data  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt) ) {  
      int j;  
      for ( j = 0 ; j < numColumn ; j++ )  
         wprintf( L"%s: %hs\n", columnLabels[j], columnData[j].TargetValuePtr );  
      printf( "\n" );  
   }  
   printf( "\n" );   
}  
  
int main() {  
   int bufferSize = 1024, i, count = 1, numCols = 5;  
   wchar_t firstTableName[1024], * dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize ), * userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLWCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen, bufferLen;  
   SQLRETURN retCode;  
  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );  
   SQLWCHAR* selectAllQuery = (SQLWCHAR *)malloc( sizeof(SQLWCHAR) * bufferSize );  
  
   // connect to database  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLCHAR *)(void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, L"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // display the database information  
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferLen);  
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, &bufferLen);  
  
   for ( i = 0 ; i < numCols ; i++ ) {  
      catalogResult[i].TargetType = SQL_C_CHAR;  
      catalogResult[i].BufferLength = (bufferSize + 1);  
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );  
   }  
  
   // Set up the binding. This can be used even if the statement is closed by closeStatementHandle  
   for ( i = 0 ; i < numCols ; i++ )  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &(catalogResult[i].StrLen_or_Ind));  
  
   retCode = SQLTables( hstmt, (SQLWCHAR*)SQL_ALL_CATALOGS, SQL_NTS, L"", SQL_NTS, L"", SQL_NTS, L"", SQL_NTS );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   retCode = SQLTables( hstmt, dbName, SQL_NTS, userName, SQL_NTS, L"%", SQL_NTS, L"TABLE", SQL_NTS );  
  
   for ( retCode = SQLFetch(hstmt) ; retCode == SQL_SUCCESS || retCode == SQL_SUCCESS_WITH_INFO ; retCode = SQLFetch(hstmt), ++count )  
      if ( count == 1 )  
         StringCchPrintfW( firstTableName, 1024, L"%hs", catalogResult[2].TargetValuePtr );  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
  
   wprintf( L"Select all data from the first table (%s)\n", firstTableName );  
   StringCchPrintfW( selectAllQuery, bufferSize, L"SELECT * FROM %s", firstTableName );  
  
   retCode = SQLExecDirect(hstmt, selectAllQuery, SQL_NTS);  
   printStatementResult(hstmt);  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md)
