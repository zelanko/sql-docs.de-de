---
title: SQLColAttribute-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c94de3dfc7036277f8be56c401326cdab07a9606
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301290"
---
# <a name="sqlcolattribute-function"></a>SQLColAttribute-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLColAttribute** gibt Deskriptorinformationen für eine Spalte in einem Resultset zurück. Deskriptorinformationen werden als Zeichenfolge, deskriptorabhängiger Wert oder ganzzahliger Wert zurückgegeben.  
  
> [!NOTE]  
>  Weitere Informationen darüber, was der Treiber-Manager dieser Funktion zuordnet, wenn ein ODBC 3. *x-Anwendung* arbeitet mit einem ODBC 2. *x-Treiber,* siehe [Mapping-Ersatzfunktionen für die Abwärtskompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
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
 [Eingabe] Die Nummer des Datensatzes im IRD, aus dem der Feldwert abgerufen werden soll. Dieses Argument entspricht der Spaltenanzahl der Ergebnisdaten, die sequenziell in steigender Spaltenreihenfolge sortiert werden, beginnend bei 1. Spalten können in beliebiger Reihenfolge beschrieben werden.  
  
 Spalte 0 kann in diesem Argument angegeben werden, aber alle Werte außer SQL_DESC_TYPE und SQL_DESC_OCTET_LENGTH geben nicht definierte Werte zurück.  
  
 *FieldIdentifier*  
 [Eingabe] Das Deskriptorhandle. Dieses Handle definiert, welches Feld im IRD abgefragt werden soll (z. B. SQL_COLUMN_TABLE_NAME).  
  
 *CharacterAttributePtr*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem der Wert im *FieldIdentifier-Feld* der *ColumnNumber-Zeile* der IRD zurückgegeben wird, wenn es sich bei dem Feld um eine Zeichenfolge handelt. Andernfalls wird das Feld nicht verwendet.  
  
 Wenn *CharacterAttributePtr* NULL ist, gibt *StringLengthPtr* weiterhin die Gesamtzahl der Bytes zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), auf die im Puffer von *CharacterAttributePtr*verwiesen wird.  
  
 *BufferLength*  
 [Eingabe] Wenn *FieldIdentifier* ein ODBC-definiertes Feld ist und *CharacterAttributePtr* auf eine Zeichenfolge oder \*einen Binärpuffer verweist, sollte dieses Argument die Länge von *CharacterAttributePtr*sein. Wenn *FieldIdentifier* ein ODBC-definiertes Feld und \* *CharacterAttribute*Ptr eine ganze Zahl ist, wird dieses Feld ignoriert. Wenn * \*der CharacterAttributePtr* eine Unicode-Zeichenfolge ist (beim Aufrufen von **SQLColAttributeW**), muss das *BufferLength-Argument* eine gerade Zahl sein. Wenn *FieldIdentifier* ein vom Treiber definiertes Feld ist, gibt die Anwendung die Art des Felds für den Treiber-Manager an, indem das *Argument BufferLength* festgelegt wird. *BufferLength* kann die folgenden Werte haben:  
  
-   Wenn *CharacterAttributePtr* ein Zeiger auf einen Zeiger ist, sollte *BufferLength* den Wert SQL_IS_POINTER haben.  
  
-   Wenn *CharacterAttributePtr* ein Zeiger auf eine Zeichenfolge ist, ist *BufferLength* die Länge des Puffers.  
  
-   Wenn *CharacterAttributePtr* ein Zeiger auf einen Binärpuffer ist, platziert die Anwendung das Ergebnis des*SQL_LEN_BINARY_ATTR(Länge*) -Makros in *BufferLength*. Dadurch wird ein negativer Wert in *BufferLength*platziert.  
  
-   Wenn *CharacterAttributePtr* ein Zeiger auf einen Datentyp fester Länge ist, muss *BufferLength* einer der folgenden sein: SQL_IS_INTEGER, SQL_IS_UNINTEGER, SQL_SMALLINT oder SQLUSMALLINT.  
  
 *StringLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes (mit Ausnahme des NULL-Beendigungsbytes für Zeichendaten) zurückgegeben werden soll, die in **CharacterAttributePtr*zurückgegeben werden können.  
  
 Wenn bei Zeichendaten die Anzahl der zurückzugebenden Bytes größer oder gleich *BufferLength* \*ist, werden die Deskriptorinformationen in *CharacterAttributePtr* auf *BufferLength* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten und vom Treiber null beendet.  
  
 Bei allen anderen Datentypen wird der Wert von *BufferLength* ignoriert, und der Treiber geht von einer Größe von **CharacterAttributePtr* von 32 Bit aus.  
  
 *NumericAttributePtr*  
 [Ausgabe] Zeiger auf einen Ganzzahlpuffer, in dem der Wert im *FieldIdentifier-Feld* der *ColumnNumber-Zeile* der IRD zurückgegeben wird, wenn es sich bei dem Feld um einen numerischen Deskriptortyp handelt, z. B. SQL_DESC_COLUMN_LENGTH. Andernfalls wird das Feld nicht verwendet. Bitte beachten Sie, dass einige Treiber möglicherweise nur das niedrigere 32-Bit oder 16-Bit eines Puffers schreiben und das Bit höherer Ordnung unverändert lassen. Daher sollten Anwendungen den Wert auf 0 initialisieren, bevor diese Funktion aufgerufen wird.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLColAttribute** entweder SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem *Handle* von *StatementHandle*aufgerufen wird. In der folgenden Tabelle sind die SQLSTATE-Werte aufgeführt, die häufig von **SQLColAttribute** zurückgegeben werden, und werden im Kontext dieser Funktion erläutert. Die Notation "(DM)" geht den Beschreibungen von SQLSTATEs voraus, die vom Treiber-Manager zurückgegeben werden. Der jedem SQLSTATE-Wert zugeordnete Rückgabecode ist SQL_ERROR, sofern nicht anders angegeben.  
  
|SQLSTATE|Fehler|Beschreibung|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiberspezifische Informationsmeldung. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01004|String-Daten, rechts abgeschnitten|Der \*Puffer *CharacterAttributePtr* war nicht groß genug, um den gesamten Zeichenfolgenwert zurückzugeben, sodass der Zeichenfolgenwert abgeschnitten wurde. Die Länge des nicht abgeschnittenen Zeichenfolgenwerts wird in **StringLengthPtr*zurückgegeben. (Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|07005|Vorbereitete Anweisung keine *Cursorspezifikation*|Die dem *StatementHandle* zugeordnete Anweisung hat kein Resultset zurückgegeben, und *FieldIdentifier* wurde nicht SQL_DESC_COUNT. Es gab keine Spalten zu beschreiben.|  
|07009|Ungültiger Deskriptorindex|(DM) Der für *ColumnNumber* angegebene Wert war gleich 0, und das SQL_ATTR_USE_BOOKMARKS Anweisungsattribut wurde SQL_UB_OFF.<br /><br /> Der für das Argument *ColumnNumber* angegebene Wert war größer als die Anzahl der Spalten im Resultset.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, für den es keine bestimmte SQLSTATE gab und für den keine implementierungsspezifische SQLSTATE definiert wurde. Die von **SQLGetDiagField** aus der Diagnosedatenstruktur zurückgegebene Fehlermeldung beschreibt den Fehler und seine Ursache.|  
|HY001|Speicherzuweisungsfehler|Der Treiber konnte den erforderlichen Speicher nicht zuweisen, um die Ausführung oder den Abschluss der Funktion zu unterstützen.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für das *StatementHandle*aktiviert. Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle*aufgerufen. Dann wurde die Funktion erneut auf dem *StatementHandle*aufgerufen.<br /><br /> Die Funktion wurde aufgerufen, und bevor die Ausführung abgeschlossen wurde, wurde **SQLCancel** oder **SQLCancelHandle** für das *StatementHandle* von einem anderen Thread in einer Multithreadanwendung aufgerufen.|  
|HY010|Funktionssequenzfehler|(DM) Für das Verbindungshandle, das dem *StatementHandle*zugeordnet ist, wurde eine asynchron ausgeführte Funktion aufgerufen. Diese asynchrone Funktion wurde noch ausgeführt, als SQLColAttribute aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** wurde für das *StatementHandle* aufgerufen und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreamten Parameter abgerufen wurden.<br /><br /> (DM) Die Funktion wurde aufgerufen, bevor **SIE SQLPrepare**, **SQLExecDirect**oder eine Katalogfunktion für das *StatementHandle aufruft.*<br /><br /> (DM) Eine asynchron ausgeführte Funktion (nicht diese) wurde für den *StatementHandle* aufgerufen und wurde noch ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** wurde für das *StatementHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Daten-at-Execution-Parameter oder Spalten gesendet wurden.|  
|HY013|Speicherverwaltungsfehler|Der Funktionsaufruf konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicherobjekte nicht zugegriffen werden konnte, möglicherweise aufgrund niedriger Speicherbedingungen.|  
|HY090|Ungültige Zeichenfolge oder Pufferlänge|(DM) * \*CharacterAttributePtr* ist eine Zeichenfolge, und *BufferLength* war kleiner als 0, aber nicht gleich SQL_NTS.|  
|HY091|Ungültiger Deskriptorfeldbezeichner|Der für das Argument *FieldIdentifier* angegebene Wert war nicht einer der definierten Werte und kein implementierungsdefinierter Wert.|  
|HY117|Die Verbindung wird aufgrund eines unbekannten Transaktionsstatus unterbrochen. Nur Trennen und Schreibgeschützte sind zulässig.|(DM) Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fahrer nicht fähig|Der für das Argument *FieldIdentifier* angegebene Wert wurde vom Treiber nicht unterstützt.|  
|HYT01|Verbindungstimeout abgelaufen|Der Verbindungstimeoutzeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Verbindungstimeoutzeitraum wird über **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Treiber unterstützt diese Funktion nicht|(DM) Der dem *StatementHandle* zugeordnete Treiber unterstützt die Funktion nicht.|  
|IM017|Polling ist im asynchronen Benachrichtigungsmodus deaktiviert|Wenn das Benachrichtigungsmodell verwendet wird, ist die Abfrage deaktiviert.|  
|IM018|**SQLCompleteAsync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungsmodus aktiviert ist, muss **SQLCompleteAsync** für das Handle aufgerufen werden, um die Nachbearbeitung durchzuführen und den Vorgang abzuschließen.|  
  
 Wenn **SQLColAttribute** nach **SQLPrepare** und vor **SQLExecute**aufgerufen wird, kann ES alle SQLSTATE zurückgeben, die von **SQLPrepare** oder **SQLExecute**zurückgegeben werden können, je nachdem, wann die Datenquelle die SQL-Anweisung auswertet, die dem *AnweisungShandle*zugeordnet ist.  
  
 Aus Leistungsgründen sollte eine Anwendung **SQLColAttribute** nicht aufrufen, bevor eine Anweisung ausgeführt wird.  
  
## <a name="comments"></a>Kommentare  
 Informationen dazu, wie Anwendungen die von **SQLColAttribute**zurückgegebenen Informationen verwenden, finden Sie unter [Ergebnissatzmetadaten](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 **SQLColAttribute** gibt Informationen \*entweder in *NumericAttributePtr* oder in \* *CharacterAttributePtr*zurück. Ganzzahlinformationen werden in \* *NumericAttributePtr* als SQLLEN-Wert zurückgegeben. Alle anderen Formate von \*Informationen werden in *CharacterAttributePtr*zurückgegeben. Wenn Informationen in \* *NumericAttributePtr*zurückgegeben werden, ignoriert der Treiber *CharacterAttributePtr*, *BufferLength*und *StringLengthPtr*. Wenn Informationen in \* *CharacterAttributePtr*zurückgegeben werden, ignoriert der Treiber *NumericAttributePtr*.  
  
 **SQLColAttribute** gibt Werte aus den Deskriptorfeldern der IRD zurück. Die Funktion wird mit einem Anweisungshandle und nicht mit einem Deskriptorhandle aufgerufen. Die von **SQLColAttribute** für die *FieldIdentifier-Werte,* die weiter unten in diesem Abschnitt aufgeführt sind, werden auch abgerufen, indem **SQLGetDescField** mit dem entsprechenden IRD-Handle aufgerufen wird.  
  
 Die derzeit definierten Deskriptorfelder, die Version von ODBC, in der sie eingeführt wurden, und die Argumente, in denen Informationen für sie zurückgegeben werden, werden weiter unten in diesem Abschnitt angezeigt. mehr Deskriptortypen können von Treibern definiert werden, um verschiedene Datenquellen zu nutzen.  
  
 Ein ODBC 3. *der x-Treiber* muss für jedes der Deskriptorfelder einen Wert zurückgeben. Wenn ein Deskriptorfeld nicht auf einen Treiber oder eine Datenquelle zutrifft \*und sofern nicht anders angegeben, gibt der Treiber 0 in *StringLengthPtr* oder eine leere Zeichenfolge in **CharacterAttributePtr*zurück.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Die ODBC 3. *x-Funktion* **SQLColAttribute** ersetzt den veralteten ODBC 2. *x-Funktion* **SQLColAttributes**. Beim Zuordnen von **SQLColAttributes** zu **SQLColAttribute** (wenn ein ODBC 2.* x-Anwendung* arbeitet mit einem ODBC 3. *x-Treiber)* oder **SQLColAttribute** **zu SQLColAttributes** zuzuordnen (wenn ein ODBC 3.* x-Anwendung* arbeitet mit einem ODBC 2. *x-Treiber),* übergibt der Treiber-Manager entweder den Wert von *FieldIdentifier,* ordnet ihn einem neuen Wert zu oder gibt einen Fehler wie folgt zurück:  
  
> [!NOTE]  
>  Das Präfix, das in *FieldIdentifier-Werten* in ODBC 3 verwendet wird. *x* wurde von dem in ODBC 2 verwendeten geändert. *x*. Das neue Präfix lautet "SQL_DESC"; das alte Präfix war "SQL_COLUMN".  
  
-   Wenn der **#define** Wert des ODBC 2. *x* *FieldIdentifier* entspricht dem **#define** Wert des ODBC 3. *x* *FieldIdentifier*wird der Wert im Funktionsaufruf gerade übergeben.  
  
-   Die **#define** Werte des ODBC 2. *x* *FieldIdentifiers* SQL_COLUMN_LENGTH, SQL_COLUMN_PRECISION und SQL_COLUMN_SCALE unterscheiden sich von den **#define** Werten des ODBC 3. *x* *FieldIdentifiers* SQL_DESC_PRECISION, SQL_DESC_SCALE und SQL_DESC_LENGTH. Ein ODBC 2. *x-Treiber* müssen nur den ODBC 2 unterstützen. *x-Werte.* Ein ODBC 3. *der x-Treiber* muss für diese drei *FieldIdentifiers*sowohl die Werte "SQL_COLUMN" als auch "SQL_DESC" unterstützen. Diese Werte unterscheiden sich, da Genauigkeit, Skalierung und Länge in ODBC 3 unterschiedlich definiert sind. *x* als in ODBC 2. *x*. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
-   Wenn der **#define** Wert des ODBC 2. *x* *FieldIdentifier* unterscheidet sich vom **#define** Wert des ODBC 3. *x* *FieldIdentifier*, wie bei den Werten COUNT, NAME und NULLABLE der Wert im Funktionsaufruf dem entsprechenden Wert zugeordnet. Beispielsweise wird SQL_COLUMN_COUNT SQL_DESC_COUNT zugeordnet, und SQL_DESC_COUNT wird SQL_COLUMN_COUNT zugeordnet, abhängig von der Richtung der Zuordnung.  
  
-   Wenn *FieldIdentifier* ein neuer Wert in ODBC 3 ist. *x*, für die es in ODBC 2 keinen entsprechenden Wert gab. *x*, wird es nicht zugeordnet, wenn ein ODBC 3. *x-Anwendung* verwendet es in einem Aufruf von **SQLColAttribute** in einem ODBC 2. *x-Treiber,* und der Aufruf gibt SQLSTATE HY091 (Invalid descriptor field identifier) zurück.  
  
 In der folgenden Tabelle sind die von **SQLColAttribute**zurückgegebenen Deskriptortypen aufgeführt. Der Typ für *NumericAttributePtr-Werte* ist **SQLLEN \* **.  
  
|*FieldIdentifier*|Information<br /><br /> zurück|Beschreibung|  
|-----------------------|---------------------------------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE, ob es sich bei der Spalte um eine Autoinkrementierungsspalte handelt.<br /><br /> SQL_FALSE, wenn es sich bei der Spalte nicht um eine Spalte mit automatischer Inkrementierung handelt oder nicht um numerische Spalten.<br /><br /> Dieses Feld ist nur für numerische Datentypspalten gültig. Eine Anwendung kann Werte in eine Zeile einfügen, die eine Autoincrement-Spalte enthält, aber normalerweise keine Werte in der Spalte aktualisieren.<br /><br /> Wenn eine Einfügung in eine Autoincrement-Spalte vorgenommen wird, wird ein eindeutiger Wert zum Zeitpunkt des Einfügens in die Spalte eingefügt. Das Inkrement ist nicht definiert, sondern datenquellenspezifisch. Eine Anwendung sollte nicht davon ausgehen, dass eine Autoincrement-Spalte an einem bestimmten Punkt oder in Schritten um einen bestimmten Wert beginnt.|  
|SQL_DESC_BASE_COLUMN_NAME (ODBC 3.0)|*CharacterAttributePtr*|Der Basisspaltenname für die Ergebnissatzspalte. Wenn kein Basisspaltenname vorhanden ist (wie bei Spalten, die Ausdrücke sind), enthält diese Variable eine leere Zeichenfolge.<br /><br /> Diese Informationen werden aus dem SQL_DESC_BASE_COLUMN_NAME Datensatzfeld des IRD zurückgegeben, bei dem es sich um ein schreibgeschütztes Feld handelt.|  
|SQL_DESC_BASE_TABLE_NAME (ODBC 3.0)|*CharacterAttributePtr*|Der Name der Basistabelle, die die Spalte enthält. Wenn der Basistabellenname nicht definiert werden kann oder nicht anwendbar ist, enthält diese Variable eine leere Zeichenfolge.<br /><br /> Diese Informationen werden aus dem SQL_DESC_BASE_TABLE_NAME Datensatzfeld des IRD zurückgegeben, bei dem es sich um ein schreibgeschütztes Feld handelt.|  
|SQL_DESC_CASE_SENSITIVE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE, wenn die Spalte bei Sortierungen und Vergleichen als Groß-/Kleinschreibung behandelt wird.<br /><br /> SQL_FALSE, wenn die Spalte bei Sortierungen und Vergleichen nicht als Groß-/Kleinschreibung behandelt wird oder nicht zeichenlos ist.|  
|SQL_DESC_CATALOG_NAME (ODBC 2.0)|*CharacterAttributePtr*|Der Katalog der Tabelle, die die Spalte enthält. Der zurückgegebene Wert ist implementierungsdefiniert, wenn es sich bei der Spalte um einen Ausdruck handelt oder wenn die Spalte Teil einer Ansicht ist. Wenn die Datenquelle keine Kataloge unterstützt oder der Katalogname nicht bestimmt werden kann, wird eine leere Zeichenfolge zurückgegeben. Dieses VARCHAR-Datensatzfeld ist nicht auf 128 Zeichen beschränkt.|  
|SQL_DESC_CONCISE_TYPE (ODBC 1.0)|*NumericAttributePtr*|Der prägnante Datentyp.<br /><br /> Für die Datumszeit- und Intervalldatentypen gibt dieses Feld den knappen Datentyp zurück. z. B. SQL_TYPE_TIME oder SQL_INTERVAL_YEAR. (Weitere Informationen finden Sie unter [Datentypbezeichner und Deskriptoren](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) in Anhang D: Datentypen.)<br /><br /> Diese Informationen werden aus dem SQL_DESC_CONCISE_TYPE Datensatzfeld der IRD zurückgegeben.|  
|SQL_DESC_COUNT (ODBC 1.0)|*NumericAttributePtr*|Die Anzahl der spaltenverfügbaren Spalten im Resultset. Dies gibt 0 zurück, wenn keine Spalten im Resultset vorhanden sind. Der Wert im *ColumnNumber-Argument* wird ignoriert.<br /><br /> Diese Informationen werden aus dem SQL_DESC_COUNT Kopffeld der IRD zurückgegeben.|  
|SQL_DESC_DISPLAY_SIZE (ODBC 1.0)|*NumericAttributePtr*|Maximale Anzahl von Zeichen, die zum Anzeigen von Daten aus der Spalte erforderlich sind. Weitere Informationen zur Anzeigegröße finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|SQL_DESC_FIXED_PREC_SCALE (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE, wenn die Spalte über eine feste Genauigkeit und einen Maßstab ungleich Null verfügt, die datenquellenspezifisch sind.<br /><br /> SQL_FALSE, wenn die Spalte keine feste Genauigkeit und einen Maßstab ungleich Null hat, die datenquellenspezifisch sind.|  
|SQL_DESC_LABEL (ODBC 2.0)|*CharacterAttributePtr*|Die Spaltenbezeichnung oder der Spaltentitel. Beispielsweise kann eine Spalte mit dem Namen "Employee Name" oder die Bezeichnung "Employee Name" oder "Employee Name" mit einem Alias versehen sein.<br /><br /> Wenn eine Spalte keine Bezeichnung hat, wird der Spaltenname zurückgegeben. Wenn die Spalte nicht beschriftet und unbenannt ist, wird eine leere Zeichenfolge zurückgegeben.|  
|SQL_DESC_LENGTH (ODBC 3.0)|*NumericAttributePtr*|Ein numerischer Wert, der entweder die maximale oder tatsächliche Zeichenlänge einer Zeichenfolge oder eines binären Datentyps ist. Dabei handelt es sich um die maximale Zeichenlänge für einen Datentyp fester Länge oder um die tatsächliche Zeichenlänge für einen Datentyp variabler Länge. Sein Wert schließt immer das Null-Beendigungs-Byte aus, das die Zeichenfolge beendet.<br /><br /> Diese Informationen werden aus dem SQL_DESC_LENGTH Datensatzfeld der IRD zurückgegeben.<br /><br /> Weitere Informationen zur Länge finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|SQL_DESC_LITERAL_PREFIX (ODBC 3.0)|*CharacterAttributePtr*|Dieses VARCHAR(128)-Datensatzfeld enthält das Zeichen oder die Zeichen, die der Treiber als Präfix für ein Literal dieses Datentyps erkennt. Dieses Feld enthält eine leere Zeichenfolge für einen Datentyp, für den kein Literalpräfix gilt. Weitere Informationen finden Sie unter [Literalpräfixe und Suffixe](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md).|  
|SQL_DESC_LITERAL_SUFFIX (ODBC 3.0)|*CharacterAttributePtr*|Dieses VARCHAR(128)-Datensatzfeld enthält das Zeichen oder die Zeichen, die der Treiber als Suffix für ein Literal dieses Datentyps erkennt. Dieses Feld enthält eine leere Zeichenfolge für einen Datentyp, für den kein Literalsuffix gilt. Weitere Informationen finden Sie unter [Literalpräfixe und Suffixe](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md).|  
|SQL_DESC_LOCAL_TYPE_NAME (ODBC 3.0)|*CharacterAttributePtr*|Dieses VARCHAR(128)-Datensatzfeld enthält alle lokalisierten (muttersprachlichen) Namen für den Datentyp, die sich vom regulären Namen des Datentyps unterscheiden können. Wenn kein lokalisierter Name vorhanden ist, wird eine leere Zeichenfolge zurückgegeben. Dieses Feld dient nur zu Anzeigezwecken. Der Zeichensatz der Zeichenfolge ist gebietsschemaabhängig und ist in der Regel der Standardzeichensatz des Servers.|  
|SQL_DESC_NAME (ODBC 3.0)|*CharacterAttributePtr*|Der Spaltenalias, sofern er angewendet wird. Wenn der Spaltenalias nicht zutrifft, wird der Spaltenname zurückgegeben. In beiden Fällen wird SQL_DESC_UNNAMED auf SQL_NAMED festgelegt. Wenn kein Spaltenname oder ein Spaltenalias vorhanden ist, wird eine leere Zeichenfolge zurückgegeben, und SQL_DESC_UNNAMED wird auf SQL_UNNAMED festgelegt.<br /><br /> Diese Informationen werden aus dem SQL_DESC_NAME Datensatzfeld der IRD zurückgegeben.|  
|SQL_DESC_NULLABLE (ODBC 3.0)|*NumericAttributePtr*|SQL_ NULLABLE, wenn die Spalte NULL-Werte haben kann; SQL_NO_NULLS, wenn die Spalte keine NULL-Werte hat. oder SQL_NULLABLE_UNKNOWN, ob nicht bekannt ist, ob die Spalte NULL-Werte akzeptiert.<br /><br /> Diese Informationen werden aus dem SQL_DESC_NULLABLE Datensatzfeld der IRD zurückgegeben.|  
|SQL_DESC_NUM_PREC_RADIX (ODBC 3.0)|*NumericAttributePtr*|Wenn der Datentyp im Feld SQL_DESC_TYPE ein ungefährer numerischer Datentyp ist, enthält dieses SQLINTEGER-Feld den Wert 2, da das Feld SQL_DESC_PRECISION die Anzahl der Bits enthält. Wenn der Datentyp im Feld SQL_DESC_TYPE ein exakter numerischer Datentyp ist, enthält dieses Feld den Wert 10, da das Feld SQL_DESC_PRECISION die Anzahl der Dezimalstellen enthält. Dieses Feld ist für alle nicht numerischen Datentypen auf 0 festgelegt.|  
|SQL_DESC_OCTET_LENGTH (ODBC 3.0)|*NumericAttributePtr*|Die Länge (in Bytes) einer Zeichenfolge oder eines binären Datentyps. Bei Zeichen oder Binärtypen fester Länge ist dies die tatsächliche Länge in Bytes. Bei Zeichen variabler Länge oder binären Typen ist dies die maximale Länge in Bytes. Dieser Wert enthält nicht den Null-Terminator.<br /><br /> Diese Informationen werden aus dem SQL_DESC_OCTET_LENGTH Datensatzfeld der IRD zurückgegeben.<br /><br /> Weitere Informationen zur Länge finden Sie unter [Spaltengröße, Dezimalziffern, Oktettlänge übertragen und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.|  
|SQL_DESC_PRECISION (ODBC 3.0)|*NumericAttributePtr*|Ein numerischer Wert, der für einen numerischen Datentyp die anwendbare Genauigkeit angibt. Bei Datentypen SQL_TYPE_TIME, SQL_TYPE_TIMESTAMP und allen Intervalldatentypen, die ein Zeitintervall darstellen, ist sein Wert die anwendbare Genauigkeit der Komponente Bruchsekunden.<br /><br /> Diese Informationen werden aus dem SQL_DESC_PRECISION Datensatzfeld der IRD zurückgegeben.|  
|SQL_DESC_SCALE (ODBC 3.0)|*NumericAttributePtr*|Ein numerischer Wert, der für einen numerischen Datentyp geeignet ist. Bei DECIMAL- und NUMERIC-Datentypen ist dies der definierte Maßstab. Sie ist für alle anderen Datentypen nicht definiert.<br /><br /> Diese Informationen werden aus dem SCALE-Datensatzfeld der IRD zurückgegeben.|  
|SQL_DESC_SCHEMA_NAME (ODBC 2.0)|*CharacterAttributePtr*|Das Schema der Tabelle, die die Spalte enthält. Der zurückgegebene Wert ist implementierungsdefiniert, wenn es sich bei der Spalte um einen Ausdruck handelt oder wenn die Spalte Teil einer Ansicht ist. Wenn die Datenquelle keine Schemas unterstützt oder der Schemaname nicht bestimmt werden kann, wird eine leere Zeichenfolge zurückgegeben. Dieses VARCHAR-Datensatzfeld ist nicht auf 128 Zeichen beschränkt.|  
|SQL_DESC_SEARCHABLE (ODBC 1.0)|*NumericAttributePtr*|SQL_PRED_NONE, wenn die Spalte nicht in einer WHERE-Klausel verwendet werden kann. (Dies entspricht dem SQL_UNSEARCHABLE Wert in ODBC 2. *x*.)<br /><br /> SQL_PRED_CHAR, ob die Spalte in einer WHERE-Klausel verwendet werden kann, jedoch nur mit dem PRÄdikat LIKE. (Dies entspricht dem SQL_LIKE_ONLY Wert in ODBC 2. *x*.)<br /><br /> SQL_PRED_BASIC, ob die Spalte in einer WHERE-Klausel mit allen Vergleichsoperatoren außer LIKE verwendet werden kann. (Dies entspricht dem SQL_EXCEPT_LIKE Wert in ODBC 2. *x*.)<br /><br /> SQL_PRED_SEARCHABLE, ob die Spalte in einer WHERE-Klausel mit einem beliebigen Vergleichsoperator verwendet werden kann.<br /><br /> Spalten vom Typ SQL_LONGVARCHAR und SQL_LONGVARBINARY geben in der Regel SQL_PRED_CHAR zurück.|  
|SQL_DESC_TABLE_NAME (ODBC 2.0)|*CharacterAttributePtr*|Der Name der Tabelle, die die Spalte enthält. Der zurückgegebene Wert ist implementierungsdefiniert, wenn es sich bei der Spalte um einen Ausdruck handelt oder wenn die Spalte Teil einer Ansicht ist.<br /><br /> Wenn der Tabellenname nicht bestimmt werden kann, wird eine leere Zeichenfolge zurückgegeben.|  
|SQL_DESC_TYPE (ODBC 3.0)|*NumericAttributePtr*|Ein numerischer Wert, der den SQL-Datentyp angibt.<br /><br /> Wenn *ColumnNumber* gleich 0 ist, wird SQL_BINARY für Lesezeichen variabler Länge zurückgegeben, und SQL_INTEGER wird für Lesezeichen mit fester Länge zurückgegeben.<br /><br /> Für die Datumszeit- und Intervalldatentypen gibt dieses Feld den ausführlichen Datentyp zurück: SQL_DATETIME oder SQL_INTERVAL. (Weitere Informationen finden Sie unter [Datentypbezeichner und Deskriptoren](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) in Anhang D: Datentypen.<br /><br /> Diese Informationen werden aus dem SQL_DESC_TYPE Datensatzfeld der IRD zurückgegeben. **Hinweis:**  So arbeiten Sie gegen ODBC 2. *x-Treiber,* verwenden Sie stattdessen SQL_DESC_CONCISE_TYPE.|  
|SQL_DESC_TYPE_NAME (ODBC 1.0)|*CharacterAttributePtr*|Datenquellenabhängiger Datentypname; z. B. "CHAR", "VARCHAR", "MONEY", "LONG VARBINARY" oder "CHAR ( ) FOR BIT DATA".<br /><br /> Wenn der Typ unbekannt ist, wird eine leere Zeichenfolge zurückgegeben.|  
|SQL_DESC_UNNAMED (ODBC 3.0)|*NumericAttributePtr*|SQL_NAMED oder SQL_UNNAMED. Wenn das SQL_DESC_NAME Feld des IRD einen Spaltenalias oder einen Spaltennamen enthält, wird SQL_NAMED zurückgegeben. Wenn kein Spaltenname oder Spaltenalias vorhanden ist, wird SQL_UNNAMED zurückgegeben.<br /><br /> Diese Informationen werden aus dem SQL_DESC_UNNAMED Datensatzfeld der IRD zurückgegeben.|  
|SQL_DESC_UNSIGNED (ODBC 1.0)|*NumericAttributePtr*|SQL_TRUE, wenn die Spalte nicht signiert (oder nicht numerisch) ist.<br /><br /> SQL_FALSE, wenn die Spalte signiert ist.|  
|SQL_DESC_UPDATABLE (ODBC 1.0)|*NumericAttributePtr*|Die Spalte wird durch die Werte für die definierten Konstanten beschrieben:<br /><br /> SQL_ATTR_READONLY SQL_ATTR_WRITE SQL_ATTR_READWRITE_UNKNOWN<br /><br /> SQL_DESC_UPDATABLE beschreibt die Updatability der Spalte im Resultset, nicht die Spalte in der Basistabelle. Die Updatability der Basisspalte, auf der die Ergebnissatzspalte basiert, kann sich vom Wert in diesem Feld unterscheiden. Ob eine Spalte aufrüstbar ist, kann auf dem Datentyp, den Benutzerberechtigungen und der Definition des Resultsets selbst basieren. Wenn unklar ist, ob eine Spalte aufrüstbar ist, sollten SQL_ATTR_READWRITE_UNKNOWN zurückgegeben werden.|  
  
 **SQLColAttribute** ist eine erweiterbare Alternative zu **SQLDescribeCol**. **SQLDescribeCol** gibt einen festen Satz von Deskriptorinformationen basierend auf ANSI-89 SQL zurück. **SQLColAttribute** ermöglicht den Zugriff auf den umfangreicheren Satz von Deskriptorinformationen, die in ANSI SQL-92- und DBMS-Anbietererweiterungen verfügbar sind.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Binden eines Puffers an eine Spalte in einer Ergebnismenge|[SQLBindCol-Funktion](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Abbrechen der Anweisungsverarbeitung|[SQLCancel-Funktion](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Zurückgeben von Informationen zu einer Spalte in einer Ergebnismenge|[SQLDescribeCol-Funktion](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Abrufen eines Datenblocks oder Scrollen eines Resultsets|[SQLFetchScroll-Funktion](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Abrufen mehrerer Datenzeilen|[SQLFetch-Funktion](../../../odbc/reference/syntax/sqlfetch-function.md)|  
  
## <a name="example"></a>Beispiel  
 Der folgende Beispielcode gibt keine Handles und Verbindungen frei. Siehe [SQLFreeHandle-Funktion](../../../odbc/reference/syntax/sqlfreehandle-function.md), [Beispiel-ODBC-Programm](../../../odbc/reference/sample-odbc-program.md)und [SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md) für Codebeispiele zum Freilassen von Handles und Anweisungen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC-Beispielprogramm](../../../odbc/reference/sample-odbc-program.md)
