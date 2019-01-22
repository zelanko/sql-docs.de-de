---
title: SQLGetDiagField-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetDiagField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDiagField
helpviewer_keywords:
- SQLGetDiagField function [ODBC]
ms.assetid: 1dbc4398-97a8-4585-bb77-1f7ea75e24c4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f975b15d07bf837c0f5fe5d2649cc78b341d23c6
ms.sourcegitcommit: 480961f14405dc0b096aa8009855dc5a2964f177
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2019
ms.locfileid: "54420165"
---
# <a name="sqlgetdiagfield-function"></a>SQLGetDiagField-Funktion

**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetDiagField** gibt den aktuellen Wert eines Felds eines Datensatzes von der Diagnosedaten-Struktur (mit einem angegebenen Handle zugeordnete), Fehler-, Warnungs-und Statusinformationen enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
SQLRETURN SQLGetDiagField(  
     SQLSMALLINT     HandleType,  
     SQLHANDLE       Handle,  
     SQLSMALLINT     RecNumber,  
     SQLSMALLINT     DiagIdentifier,  
     SQLPOINTER      DiagInfoPtr,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 [Eingabe] Ein Handle-Typbezeichner, der den Typ des Handles wird beschrieben, für die Diagnose erforderlich sind. Dies muss eine der folgenden Ressourcen sein:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN Handle wird nur von der Treiber-Manager und Treiber verwendet. Anwendungen sollten nicht mit dieser Handletyp verwenden. Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN, finden Sie unter [Entwickeln von Verbindungspool Unterstützung in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Handle*  
 [Eingabe] Ein Handle für die Diagnose Datenstruktur, die vom angegebenen Typ *HandleType*. Wenn *HandleType* SQL_HANDLE_ENV auf, wird *behandeln* kann entweder eine freigegebene oder ein nicht freigegebenes Umgebungshandle sein.  
  
 *RecNumber*  
 [Eingabe] Gibt an, den Status-Datensatz, der von dem die Anwendung Informationen sucht. Statusdatensätze werden von 1 nummeriert. Wenn die *DiagIdentifier* Argument gibt an, ein Feld des Diagnose-Headers *RecNumber* wird ignoriert. Wenn dies nicht der Fall ist, es sollte größer als 0 sein.  
  
 *DiagIdentifier*  
 [Eingabe] Gibt das Feld der Diagnose, deren Wert zurückgegeben werden. Weitere Informationen finden Sie unter der "*DiagIdentifier* Argument" im Abschnitt "Kommentare".  
  
 *DiagInfoPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in den Diagnoseinformationen zurückgegeben werden sollen. Der Datentyp hängt vom Wert der *DiagIdentifier*. Wenn *DiagInfoPtr* ein ganzzahliger Typ, einen Puffer mit SQLULEN sollte von Anwendungen verwendet, und initialisieren, die der Wert auf 0 vor dem Aufrufen dieser Funktion, als einige Treiber können Sie nur die unteren 32-Bit- oder 16-Bit eines Puffers zu schreiben, und lassen Sie die höherer Ordnung Bit unverändert.  
  
 Wenn *DiagInfoPtr* NULL ist, *StringLengthPtr* gibt die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen für Zeichendaten) noch verfügbar, die in den Puffer, der auf zurückgegeben *DiagInfoPtr*.  
  
 *BufferLength*  
 [Eingabe] Wenn *DiagIdentifier* ist ein ODBC-definierten Diagnose- und *DiagInfoPtr* zeigt auf eine Zeichenfolge oder ein binärer Puffer, in dieses Argument muss die Länge des \* *DiagInfoPtr* . Wenn *DiagIdentifier* ist ein ODBC-definierten-Feld und \* *DiagInfoPtr* ist eine ganze Zahl, *Pufferlänge* wird ignoriert. Wenn der Wert in  *\*DiagInfoPtr* ist eine Unicodezeichenfolge (beim Aufrufen von **SQLGetDiagFieldW**), wird die *Pufferlänge* Argument muss eine gerade Zahl sein.  
  
 Wenn *DiagIdentifier* ist ein Feld treiberdefinierten, die Anwendung zeigt die Art des Felds um den Treiber-Manager an, indem die *Pufferlänge* Argument. *BufferLength* können die folgenden Werte aufweisen:  
  
-   Wenn *DiagInfoPtr* ist ein Zeiger auf eine Zeichenfolge, *Pufferlänge* ist die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn *DiagInfoPtr* ist ein Zeiger auf ein binärer Puffer, der Anwendung stellen das Ergebnis der SQL_LEN_BINARY_ATTR (*Länge*)-Makro in *Pufferlänge*. Dadurch wird einen negativen Wert im platziert *Pufferlänge*.  
  
-   Wenn *DiagInfoPtr* ist ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder Binärzeichenfolge, *Pufferlänge* Wert SQL_IS_POINTER haben sollte.  
  
-   Wenn  *\*DiagInfoPtr* enthält einen Datentyp mit fester Länge *Pufferlänge* SQL_IS_INTEGER SQL_IS_UINTEGER, SQL_IS_SMALLINT oder SQL_IS_USMALLINT, als geeignet ist.  
  
 *StringLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer für die Rückgabe der Gesamtanzahl der Bytes, die (mit Ausnahme von der Anzahl der Bytes, die für die Null-Terminierungszeichen erforderlich) zur Verfügung, die in zurückgegeben \* *DiagInfoPtr*, für Zeichendaten. Wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *Pufferlänge*, den Text im \* *DiagInfoPtr* auf abgeschnitten *Pufferlänge* minus die Länge eines Zeichens Null-Terminierung vorliegt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE, or SQL_NO_DATA.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLGetDiagField** veröffentlichen DiagnoseDatensätze nicht für sich selbst. Sie können die folgenden Rückgabewerte verwendet, um das Ergebnis seiner eigenen Ausführung zu melden:  
  
-   SQL_SUCCESS: Diagnoseinformationen wird von die Funktion wurde erfolgreich zurückgegeben.  
  
-   SQL_SUCCESS_WITH_INFO: \**DiagInfoPtr* war zu klein für das angeforderte Feld für die Diagnose. Aus diesem Grund wurden die Daten in das diagnosefeld abgeschnitten. Um zu bestimmen, dass durch das Abschneiden aufgetreten ist, vergleichen Sie die Anwendung muss *Pufferlänge* auf die tatsächliche Anzahl von Bytes verfügbar ist, das wird **StringLengthPtr*.  
  
-   SQL_INVALID_HANDLE: Das Handle angegeben wird, indem *HandleType* und *behandeln* war es sich nicht um ein gültiges Handle.  
  
-   SQL_ERROR: Eine der folgenden aufgetreten ist:  
  
    -   *Die DiagIdentifier* Argument war keiner der gültigen Werte.  
  
    -   *Die DiagIdentifier* Argument war SQL_DIAG_CURSOR_ROW_COUNT SQL_DIAG_DYNAMIC_FUNCTION, SQL_DIAG_DYNAMIC_FUNCTION_CODE oder SQL_DIAG_ROW_COUNT, aber *behandeln* war es sich nicht um ein Anweisungshandle. (Der Treiber-Manager gibt dies diagnostische.)  
  
    -   *Die RecNumber* Argument war negativ oder 0 bei *DiagIdentifier* ein Feld aus der ein Diagnosedatensatz angegeben. *RecNumber* wird für die Felder ignoriert.  
  
    -   Der Wert, der angefordert wurde, eine Zeichenfolge und *Pufferlänge* ist kleiner als 0 (null).  
  
    -   Wenn Sie asynchrone Benachrichtigung verwenden zu können, war der asynchrone Vorgang auf den Ziehpunkt nicht abgeschlossen werden.  
  
-   SQL_NO_DATA: *RecNumber* war größer als die Zahl der DiagnoseDatensätze, die für das Handle, das im angegebenen vorhanden waren *behandeln.* Die Funktion gibt SQL_NO_DATA auch für eine beliebige Positive *RecNumber* treten keine DiagnoseDatensätze für *behandeln*.  
  
## <a name="comments"></a>Kommentare  
 Ruft eine Anwendung in der Regel **SQLGetDiagField** um eines der drei Ziele erreichen:  
  
1.  Zum Abrufen bestimmter Fehler oder eine Warnung, wenn es sich bei ein Funktionsaufruf SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgegeben hat (oder SQL_NEED_DATA zurück, für die **SQLBrowseConnect** Funktion).  
  
2.  Um die Anzahl der Zeilen in der Datenquelle zu ermitteln, die betroffen sind, wenn Einfüge-, Lösch- oder Updatevorgänge, mit einem Aufruf von ausgeführt wurden **SQLExecute**, **SQLExecDirect**,  **SQLBulkOperations**, oder **SQLSetPos** (aus dem SQL_DIAG_ROW_COUNT-Header-Feld), oder um zu bestimmen die Anzahl der Zeilen, die in der aktuellen geöffneten Cursor vorhanden sind, wenn der Treiber diese Informationen angeben kann (von der SQL_DIAG_CURSOR_ROW_COUNT Headerfeld).  
  
3.  Um zu bestimmen, welche Funktion ausgeführt wurde, durch einen Aufruf von **SQLExecDirect** oder **SQLExecute** (von Headerfelder SQL_DIAG_DYNAMIC_FUNCTION und SQL_DIAG_DYNAMIC_FUNCTION_CODE).  
  
 Eine ODBC-Funktion kann bereitstellen, 0 (null) oder mehrere DiagnoseDatensätze jedes Mal, dass die It aufgerufen wird, so dass eine Anwendung aufrufen kann **SQLGetDiagField** nach jedem Aufruf der ODBC-Funktion. Es gibt keine Beschränkung der Anzahl der DiagnoseDatensätze, die zu jedem Zeitpunkt gespeichert werden können. **SQLGetDiagField** ruft nur die zuletzt der Diagnosedaten-Struktur, die im angegebenen zugeordnete Diagnoseinformationen der *behandeln* Argument. Wenn die Anwendung eine ODBC-Funktion aufruft, die als **SQLGetDiagField** oder **SQLGetDiagRec**, sämtliche Diagnoseinformationen von einem vorherigen Aufruf mit dem gleichen Handle verloren gegangen ist.  
  
 Eine Anwendung kann alle DiagnoseDatensätze gescannt werden. durch erhöhen *RecNumber*, solange **SQLGetDiagField** gibt SQL_SUCCESS zurück. Die Anzahl der Statusdatensätze wird in das Headerfeld SQL_DIAG_NUMBER angegeben. Aufrufe von **SQLGetDiagField** an den Header und der Datensatz nicht destruktiv sind. Die Anwendung kann Aufrufen **SQLGetDiagField** es später noch Mal ein Feld aus einem Datensatz, abrufen, solange eine Funktion als die Diagnosefunktionen nicht in der Zwischenzeit aufgerufen wurde die Einträge für dasselbe Handle bereitstellen würden.  
  
 Kann eine Anwendung aufrufen **SQLGetDiagField** zurückzugebenden alle diagnosefeld jederzeit außer SQL_DIAG_CURSOR_ROW_COUNT oder SQL_DIAG_ROW_COUNT, der SQL_ERROR zurückgegeben wird, wenn *behandeln* kein Anweisungshandle. Wenn alle anderen diagnosefeld nicht definiert ist, ist der Aufruf von **SQLGetDiagField** gibt SQL_SUCCESS zurück, (vorausgesetzt, dass keine anderen Diagnose gefunden wird) und ein nicht definierter Wert wird zurückgegeben, für das Feld.  
  
 Weitere Informationen finden Sie unter [mithilfe von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md) und [Implementieren von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md).  
  
 Aufrufen einer API als dem, der asynchron ausgeführt wird, wird HY010 generiert "Sequenzfehler Function". Allerdings kann nicht Error-Datensatzes nicht abgerufen werden, bevor der asynchrone Vorgang abgeschlossen ist.  
  
## <a name="handletype-argument"></a>HandleType-Argument  
 Jede Handletyp kann Diagnoseinformationen zugeordnet haben. Die *HandleType* Argument gibt den Handletyp "der *behandeln*.  
  
 Einige Felder Header und eines Eintrags können nicht für die Umgebung, Verbindung, anweisungs- und Deskriptorstatuswerte Handles zurückgegeben werden. Diese Handles, die für die ein Feld nicht anwendbar ist, werden in den folgenden Abschnitten "Headerfelder" und "Datensatzfelder" angezeigt.  
  
 Wenn *HandleType* SQL_HANDLE_ENV auf, wird *behandeln* kann freigegeben werden oder nicht freigegebene Umgebungshandle sein.  
  
 Keine Treiber-spezifische Header Diagnosefelder sollte ein Umgebungshandle zugeordnet werden.  
  
 Nur diagnostische Headerfelder, die für ein Handle für die Sicherheitsbeschreibung definiert sind, sind SQL_DIAG_NUMBER "und" SQL_DIAG_RETURNCODE.  
  
## <a name="diagidentifier-argument"></a>DiagIdentifier-Argument  
 Dieses Argument gibt den Bezeichner des Felds aus der Struktur von Diagnosedaten erforderlich. Wenn *RecNumber* ist größer als oder gleich 1 ist, die Daten in das Feld beschreibt die Diagnoseinformationen, die von einer Funktion zurückgegeben. Wenn *RecNumber* gleich 0 ist, das Feld in der Kopfzeile der Diagnosedaten-Struktur und aus diesem Grund enthält Daten, die für den Aufruf der Funktion, die die Diagnoseinformationen zu erhalten, nicht an die spezifischen Informationen zurückgegeben.  
  
 Treiber können Treiber-spezifische Header und Datensatzfelder in der Struktur Diagnosedaten definieren.  
  
 Eine ODBC 3.*.x* Anwendung mit einer ODBC 2.*.x* Treiber werden in der Lage, rufen Sie **SQLGetDiagField** nur mit einem *DiagIdentifier* ein Argument vom SQL_DIAG_CLASS_ORIGIN SQL_DIAG_CLASS_SUBCLASS_ORIGIN, SQL_DIAG_CONNECTION_NAME, SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_NUMBER, SQL_DIAG_RETURNCODE, SQL_DIAG_SERVER_NAME oder SQL_DIAG_SQLSTATE. Alle anderen Feldern gibt SQL_ERROR zurück.  
  
## <a name="header-fields"></a>Headerfelder  
 Die Headerfelder, die in der folgenden Tabelle aufgeführten können enthalten sein, der *DiagIdentifier* Argument.  
  
|DiagIdentifier|Rückgabetyp|Rückgabewert|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CURSOR_ROW_COUNT|SQLLEN|Dieses Feld enthält die Anzahl der Zeilen im Cursor. Die Semantik richten sich nach der **SQLGetInfo** Informationstypen SQL_DYNAMIC_CURSOR_ATTRIBUTES2, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2 und SQL_STATIC_CURSOR_ATTRIBUTES2, die die angibt, ob Zeilenanzahl stehen für jeden Cursortyp (in der SQL_CA2_CRC_EXACT und SQL_CA2_CRC_APPROXIMATE, Bits).<br /><br /> Der Inhalt dieses Felds wird definiert, nur für Anweisungshandles und erst nach **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** aufgerufen wurde. Aufrufen von **SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_CURSOR_ROW_COUNT auf als eine Anweisung Handle SQL_ERROR zurück.|  
|SQL_DIAG_DYNAMIC_FUNCTION|SQLCHAR *|Dies ist eine Zeichenfolge, die die SQL-Anweisung wird beschrieben, die die zugrunde liegende Funktion ausgeführt wird. (Siehe "Values Felder dynamischen Funktion" weiter unten in diesem Abschnitt nach bestimmten Werten). Der Inhalt dieses Felds wird definiert, nur für Anweisungshandles und nur nach einem Aufruf von **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults**. Aufrufen von **SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_DYNAMIC_FUNCTION auf als eine Anweisung Handle SQL_ERROR zurück. Der Wert dieses Felds ist nicht definiert, vor einem Aufruf von **SQLExecute** oder **SQLExecDirect**.|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|SQLINTEGER|Dies ist ein numerischer Code, der die SQL-Anweisung wird beschrieben, die von der zugrunde liegende Funktion ausgeführt wurde. (Bestimmten Wert finden Sie unter "Werte von der dynamischen Funktion Felder," weiter unten in diesem Abschnitt.) Der Inhalt dieses Felds wird definiert, nur für Anweisungshandles und nur nach einem Aufruf von **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults**. Aufrufen von **SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_DYNAMIC_FUNCTION_CODE auf als eine Anweisung Handle SQL_ERROR zurück. Der Wert dieses Felds ist nicht definiert, vor einem Aufruf von **SQLExecute** oder **SQLExecDirect**.|  
|SQL_DIAG_NUMBER|SQLINTEGER|Die Anzahl der Statusdatensätze, die für das angegebene Handle verfügbar sind.|  
|SQL_DIAG_RETURNCODE|SQLRETURN|Rückgabecode von der Funktion zurückgegeben. Eine Liste von Rückgabecodes, finden Sie unter [Rückgabecodes](../../../odbc/reference/develop-app/return-codes-odbc.md). Der Treiber keine SQL_DIAG_RETURNCODE implementieren; Es wird immer vom Treiber-Manager implementiert. Wenn für die noch keine Funktion aufgerufen wurde die *behandeln*, wird SQL_SUCCESS für SQL_DIAG_RETURNCODE zurückgegeben.|  
|SQL_DIAG_ROW_COUNT|SQLLEN|Die Anzahl der Zeilen, die von einer INSERT-, DELETE- oder Update, die von ausgeführten betroffen **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, oder **SQLSetPos**. Es wird nach dem Treiber definiert eine *Cursorspezifikation* ausgeführt wurde. Die Inhalte dieser Felder werden nur für Anweisungshandles definiert. Aufrufen von **SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_ROW_COUNT auf als eine Anweisung Handle SQL_ERROR zurück. Die Daten in dieses Feld werden auch zurückgegeben, der *RowCountPtr* Argument **SQLRowCount**. Die Daten in dieses Feld werden nach jedem Funktionsaufruf nondiagnostic zurückgesetzt, während die Anzahl der Zeilen von zurückgegeben **SQLRowCount** bleibt unverändert, bis die Anweisung wieder in den vorbereiteten oder zugeordneten Zustand festgelegt wird.|  
  
## <a name="record-fields"></a>Notieren Sie die Felder  
 Die Datensatzfelder, die in der folgenden Tabelle aufgeführten enthalten sein können, der *DiagIdentifier* Argument.  
  
|DiagIdentifier|Rückgabetyp|Rückgabewert|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CLASS_ORIGIN|SQLCHAR *|Eine Zeichenfolge, die das Dokument gibt an, das den Klassenteil des der SQLSTATE-Wert in diesem Datensatz definiert. Der Wert ist "ISO 9075" für alle SQLSTATEs durch Open Group und ISO-Call-Level-Interface definiert. Für ODBC-spezifische SQLSTATEs (alle Mitarbeiter, deren SQLSTATE-Klasse ist "IM") der Wert ist "ODBC 3.0".|  
|SQL_DIAG_COLUMN_NUMBER|SQLINTEGER|Wenn das Feld "SQL_DIAG_ROW_NUMBER" eine gültige Zeilennummer, in ein Rowset oder einen Satz von Parametern ist, enthält dieses Feld den Wert, der die Nummer der Spalte im Resultset oder die Anzahl der Parameter in den Satz von Parametern darstellt. Resultset-Spalte, die die Versionsnummern immer bei 1 beginnen; Wenn dieser Status-Datensatz zu einer Lesezeichenspalte bezieht, kann das Feld NULL sein. Parameter-Versionsnummern beginnen bei 1. Es hat es sich um den Wert SQL_NO_COLUMN_NUMBER, wenn der Status-Datensatz nicht Nummer der Spalte oder Parameter Nr. zugeordnet ist. Wenn der Treiber nicht ermitteln kann, die Nummer der Spalte oder Parameter mit der Nummer, die diesem Datensatz zugeordnet ist, ist dieses Feld den Wert SQL_COLUMN_NUMBER_UNKNOWN an.<br /><br /> Die Inhalte dieser Felder werden nur für Anweisungshandles definiert.|  
|SQL_DIAG_CONNECTION_NAME|SQLCHAR *|Eine Zeichenfolge, die den Namen der Verbindung gibt an, die mit dem Diagnosedatensatz verknüpft. Dieses Feld ist treiberdefinierten. Für Diagnosedaten-Strukturen, die das Umgebungshandle zugeordnet und für die Diagnose, die nicht auf eine beliebige Verbindung beziehen, ist dieses Feld eine Zeichenfolge der Länge 0 (null).|  
|SQL_DIAG_MESSAGE_TEXT|SQLCHAR *|Eine informationsmeldung für den Fehler oder die Warnung. Dieses Feld wird formatiert, siehe [Diagnosemeldungen](../../../odbc/reference/develop-app/diagnostic-messages.md). Es gibt keine maximale Länge für den Text für die diagnosemeldung ein.|  
|SQL_DIAG_NATIVE|SQLINTEGER|Ein Treiber/Data Source-spezifische systemeigener Fehlercode. Es ist kein systemeigener Fehlercode, gibt der Treiber 0 zurück.|  
|SQL_DIAG_ROW_NUMBER|SQLLEN|Dieses Feld enthält die Nummer der Zeile im Rowset oder die Anzahl der Parameter in der Menge aus Parametern, mit denen der Status-Datensatz zugeordnet ist. Beginnen mit 1, Zeilennummern und Parameter-Zahlen. Dieses Feld hat den Wert SQL_NO_ROW_NUMBER auf, wenn dieser Status-Datensatz keine Zeilennummer oder Parameter zugeordnet ist. Wenn der Treiber nicht ermitteln kann, die Nummer der Zeile oder einen Parameter mit der Nummer, die diesem Datensatz zugeordnet ist, ist dieses Feld den Wert SQL_ROW_NUMBER_UNKNOWN an.<br /><br /> Die Inhalte dieser Felder werden nur für Anweisungshandles definiert.|  
|SQL_DIAG_SERVER_NAME|SQLCHAR *|Eine Zeichenfolge, die den Namen des Servers, dem angibt mit dem Diagnosedatensatz verknüpft. Es ist identisch mit den Rückgabewert für einen Aufruf von **SQLGetInfo** mit der Option SQL_DATA_SOURCE_NAME. Für Diagnosedaten-Strukturen, die das Umgebungshandle zugeordnet und für die Diagnose, die nicht auf einem beliebigen Server beziehen, ist dieses Feld eine Zeichenfolge der Länge 0 (null).|  
|SQL_DIAG_SQLSTATE|SQLCHAR *|Ein fünfstelligen SQLSTATE Diagnose Code. Weitere Informationen finden Sie unter [SQLSTATEs](../../../odbc/reference/develop-app/sqlstates.md).|  
|SQL_DIAG_SUBCLASS_ORIGIN|SQLCHAR *|Eine Zeichenfolge mit dem gleichen Format und die gültigen Werte als SQL_DIAG_CLASS_ORIGIN, die die definierenden Teil der unterklassenteil des SQLSTATE-Codes identifiziert. Der ODBC-spezifische SQLSTATES für das "ODBC 3.0" zurückgegeben wird, umfassen Folgendes:<br /><br /> 01 S 00, 01 S 01, 01 S 02, 01S06, 01 S 07, 07S01, 08 S 01 21S01, 21S02, 25S01, 25S02, 25S03, 42S01, 42S02, 42S11, 42S12, 42S21, 42S22, HY095, HY097, HY098, HY099, HY100, HY101, HY105, HY107, HY109, HY110, HY111, HYT00, HYT01, IM001, IM002, IM003, IM004, IM005, IM006, IM007 IM008, IM010, IM011, IM012.|  
  
## <a name="values-of-the-dynamic-function-fields"></a>Werte der Felder dynamischen-Funktion  
 Die folgende Tabelle beschreibt die Werte der SQL_DIAG_DYNAMIC_FUNCTION und SQL_DIAG_DYNAMIC_FUNCTION_CODE, die für jeden Typ von SQL-Anweisung ausgeführt, die durch einen Aufruf von gelten **SQLExecute** oder **SQLExecDirect**. Der Treiber kann die aufgeführten treiberdefinierten Werte hinzufügen.  
  
|SQL-Anweisung<br /><br /> ausgeführt|Wert des<br /><br /> SQL_DIAG_DYNAMIC_FUNCTION|Wert des<br /><br /> SQL_DIAG_DYNAMIC_FUNCTION_CODE|  
|--------------------------------|-----------------------------------------------|-----------------------------------------------------|  
|*alter-domain-statement*|"ALTER DER DOMÄNE"|SQL_DIAG_ALTER_DOMAIN|  
|*alter-table-statement*|"ALTER TABLE"|SQL_DIAG_ALTER_TABLE|  
|*assertion-definition*|"ERSTELLEN SIE ASSERTION"|SQL_DIAG_CREATE_ASSERTION|  
|*character-set-definition*|"CREATE-ZEICHENSATZ AUSGEWÄHLT WERDEN."|SQL_DIAG_CREATE_CHARACTER_SET|  
|*collation-definition*|"ERSTELLEN DER SORTIERUNG"|SQL_DIAG_CREATE_COLLATION|  
|*domainn-definition*|"ERSTELLEN SIE DOMÄNE"|SQL_DIAG_CREATE_DOMAIN|
|*create-index-statement*|"ERSTELLEN SIE INDEX"|SQL_DIAG_CREATE_INDEX|  
|*create-table-statement*|"ERSTELLEN SIE TABELLE"|SQL_DIAG_CREATE_TABLE|  
|*create-view-statement*|"ERSTELLEN SIE ANSICHT"|SQL_DIAG_CREATE_VIEW|  
|*cursor-specification*|"SELECT CURSOR"|SQL_DIAG_SELECT_CURSOR|  
|*delete-statement-positioned*|"DELETE MIT DYNAMIC-CURSOR"|SQL_DIAG_DYNAMIC_DELETE_CURSOR|  
|*delete-statement-searched*|"WHERE LÖSCHEN"|SQL_DIAG_DELETE_WHERE|  
|*drop-assertion-statement*|"ASSERTION" DROP "|SQL_DIAG_DROP_ASSERTION|  
|*drop-character-set-stmt*|"DROP-ZEICHENSATZ"|SQL_DIAG_DROP_CHARACTER_SET|  
|*drop-collation-statement*|"DROP COLLATION"|SQL_DIAG_DROP_COLLATION|  
|*drop-domain-statement*|"DROP-DOMÄNE"|SQL_DIAG_DROP_DOMAIN|  
|*drop-index-statement*|"DROP INDEX"|SQL_DIAG_DROP_INDEX|  
|*drop-schema-statement*|"DROP SCHEMA"|SQL_DIAG_DROP_SCHEMA|  
|*drop-table-statement*|"DROP TABLE"|SQL_DIAG_DROP_TABLE|  
|*drop-translation-statement*|"DROP TRANSLATION"|SQL_DIAG_DROP_TRANSLATION|  
|*drop-view-statement*|"DROP VIEW"|SQL_DIAG_DROP_VIEW|  
|*grantstatement*|"GEWÄHRUNG"|SQL_DIAG_GRANT|
|*insert-statement*|"INSERT"|SQL_DIAG_INSERT|  
|*ODBC-procedure-extension*|"CALL"|SQL_DIAG_-AUFRUF|  
|*revoke-statement*|"REVOKE"|SQL_DIAG_REVOKE|  
|*schema-definition*|"ERSTELLEN SIE SCHEMA"|SQL_DIAG_CREATE_SCHEMA|  
|*translation-definition*|"ÜBERSETZUNG ZU ERSTELLEN"|SQL_DIAG_CREATE_TRANSLATION|  
|*update-statement-positioned*|"DYNAMISCHES UPDATE CURSOR"|SQL_DIAG_DYNAMIC_UPDATE_CURSOR|  
|*update-statement-searched*|"AKTUALISIEREN, WO"|SQL_DIAG_UPDATE_WHERE|  
|Unknown|*leere Zeichenfolge*|SQL_DIAG_UNKNOWN_STATEMENT|  

<!--
These two malformed table rows were fixed by educated GUESS only.
Each pair starts with the original flawed row.
Flawed because treated as only two cells by HTML render,
and because missing info anyway.
Also, these flawed rows lacked '|' as their first nonWhitespace character (although markdown technically allows this omission, unfortunately).
Arguably the following SQL.H file shows the sequence of the flawed rows in the table was suboptimal also.

ftp://www.fpc.org/fpc32/VS6Disk1/VC98/INCLUDE/SQL.H

GeneMi , 2019/01/19
- - - - - - - - - - - - - -

n-definition*|"CREATE DOMAIN"|SQL_DIAG_CREATE_DOMAIN|  
|*domain-definition*|"CREATE DOMAIN"|SQL_DIAG_CREATE_DOMAIN|

-statement*|"GRANT"|SQL_DIAG_GRANT|  
|*grant-statement*|"GRANT"|SQL_DIAG_GRANT|
-->

## <a name="sequence-of-status-records"></a>Sequenz der Statusdatensätze

 Statusdatensätze werden in einer Sequenz, die anhand der Zeilennummer und den Typ der Diagnose positioniert. Der Treiber-Manager bestimmt die endgültige Reihenfolge in den statusdatensätzen zurückgegeben, die es generiert. Der Treiber ermittelt, die endgültige Reihenfolge in den statusdatensätzen zurückgegeben, die es generiert.  
  
 Wenn sowohl der Treiber-Manager als auch der Treiber DiagnoseDatensätze bereitgestellt werden, ist der Treiber-Manager für ihre Anordnung verantwortlich.  
  
 Wenn mindestens zwei Statusdatensätze vorhanden sind, wird die Reihenfolge der Datensätze zuerst durch Nummer der Zeile bestimmt. Die folgenden Regeln gelten für die zur Bestimmung der Reihenfolge von Diagnosedatensätzen von Zeile:  
  
-   Datensätze, die nicht auf eine beliebige Zeile entsprechen angezeigt vor Datensätze, die einer bestimmten Zeile, entsprechen, da es sich bei SQL_NO_ROW_NUMBER definiert ist, dass-1 sein.  
  
-   Datensätze, die für die Nummer der Zeile unbekannt ist werden vor allen anderen Datensätzen angezeigt, da es sich bei SQL_ROW_NUMBER_UNKNOWN definiert ist, dass-2 werden.  
  
-   Für alle Datensätze, die bestimmte Zeilen betreffen, werden die Datensätze durch den Wert in das Feld "SQL_DIAG_ROW_NUMBER" sortiert. Alle Fehler und Warnungen der ersten Zeile betroffen sind aufgeführt, und klicken Sie dann alle Fehler und Warnungen der nächsten Zeile betroffenen und so weiter.  
  
> [!NOTE]
>  Die ODBC 3.*.x* -Treiber-Manager sortiert nicht Statusdatensätze in der Warteschlange diagnostische Wenn SQLSTATE 01 s 01 (Fehler in Zeile) wird zurückgegeben, von einer ODBC 2.*.x* Treiber oder, wenn SQLSTATE 01 s 01 (Fehler in Zeile) wird durch ODBC zurückgegeben 3 *.x* Treiber beim **SQLExtendedFetch** aufgerufen wird oder **SQLSetPos** aufgerufen wird, auf einen Cursor, der mit positioniert ist **SQLExtendedFetch** .  
  
 Innerhalb jeder Zeile, oder für alle Datensätze, die für die Nummer der Zeile unbekannt ist oder eine Zeile nicht entsprechen, oder für alle Datensätze mit einer Zeilennummer SQL_NO_ROW_NUMBER gleich, wird der erste Datensatz aufgeführten bestimmt mithilfe eines Satzes von Regeln zu sortieren. Nach dem des ersten Datensatzes ist die Reihenfolge von den anderen Datensätzen, die Auswirkungen auf eine Zeile nicht definiert. Eine Anwendung kann nicht davon ausgehen, dass der Fehler, Warnungen nach dem ersten Datensatz vorangestellt sein. Anwendungen sollten die vollständige Diagnosedaten-Struktur, um vollständige Informationen zu einer nicht erfolgreichen Aufruf einer Funktion erhalten überprüfen.  
  
 Die folgenden Regeln werden verwendet, um den ersten Datensatz in einer Zeile zu bestimmen. Der Datensatz mit den höchsten Rang ist der erste Datensatz. Die Quelle eines Datensatzes (Treiber-Manager, Treiber, Gateway, usw.) wird nicht berücksichtigt, wenn Datensätze Rangfolge.  
  
-   **Fehler** Statusdatensätze, die Fehler beschreiben, weisen den höchsten Rang. Um Fehler zu sortieren, werden die folgenden Regeln angewendet:  
  
    -   Datensätze, die ein Fehlschlagen der Transaktion oder möglichen Transaktionsfehler angeben outrank alle anderen Datensätze.  
  
    -   Wenn zwei oder mehr Datensätze über die gleiche fehlerbedingung beschreiben, outrank SQLSTATEs, die durch die Open Group-CLI-Spezifikation (Klassen 03 über HZ) definiert ODBC und treiberdefinierten SQLSTATEs.  
  
-   **Keine Datenwerte Implementierung definierten** Statusdatensätze, die beschreiben, treiberdefinierten keine Datenwerte (Klasse 02) haben die zweite höchsten Rang.  
  
-   **Warnungen** Status-Datensätze, die beschreiben, Warnungen (01-Klasse) sind den niedrigsten Rang. Wenn zwei oder mehr Datensätze die gleichen warnungsbedingung, durch die Open Group-CLI-Spezifikation definiert SQLSTATEs Warnung beschreiben outrank ODBC-definierten und treiberdefinierten SQLSTATEs.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Abrufen von mehreren Feldern einer Datenstruktur für die Diagnose|[SQLGetDiagRec-Funktion](sqlgetdiagrec-function.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
