---
title: SQLGetDiagField-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a26319868a4b94b895da73d39b284f612fe35889
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285430"
---
# <a name="sqlgetdiagfield-function"></a>SQLGetDiagField-Funktion

**Konformität**  
 Eingeführte Version: ODBC 3.0-Normkonformität: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetDiagField** gibt den aktuellen Wert eines Felds eines Datensatzes der Diagnosedatenstruktur (die einem angegebenen Handle zugeordnet ist) zurück, das Fehler-, Warnungs- und Statusinformationen enthält.  
  
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
 [Eingabe] Ein Handletypbezeichner, der den Typ des Handles beschreibt, für den eine Diagnose erforderlich ist. Dies muss eine der folgenden Ressourcen sein:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN Handle wird nur vom Treiber-Manager und -Treiber verwendet. Anwendungen sollten diesen Handletyp nicht verwenden. Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN finden Sie unter [Entwickeln von Verbindungspool-Awareness in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Handle*  
 [Eingabe] Ein Handle für die Diagnosedatenstruktur des von *HandleType*angegebenen Typs . Wenn *HandleType* SQL_HANDLE_ENV ist, kann *Handle* entweder ein freigegebenes oder ein nicht freigegebenes Umgebungshandle sein.  
  
 *RecNumber*  
 [Eingabe] Gibt den Statusdatensatz an, aus dem die Anwendung Informationen sucht. Statusdatensätze werden von 1 nummeriert. Wenn das *Argument DiagIdentifier* ein Feld des Diagnoseheaders angibt, wird *RecNumber* ignoriert. Wenn nicht, sollte es mehr als 0 sein.  
  
 *DiagIdentifier*  
 [Eingabe] Gibt das Feld der Diagnose an, deren Wert zurückgegeben werden soll. Weitere Informationen finden Sie im Abschnitt *"DiagIdentifier* Argument" unter "Kommentare".  
  
 *DiagInfoPtr*  
 [Ausgabe] Zeigen Sie auf einen Puffer, in dem die Diagnoseinformationen zurückgegeben werden sollen. Der Datentyp hängt vom Wert von *DiagIdentifier*ab. Wenn *DiagInfoPtr* ein ganzzahliger Typ ist, sollten Anwendungen einen Puffer von SQLULEN verwenden und den Wert auf 0 initialisieren, bevor sie diese Funktion aufrufen, da einige Treiber möglicherweise nur den unteren 32-Bit- oder 16-Bit-Puffer schreiben und das Bit höherer Ordnung unverändert lassen.  
  
 Wenn *DiagInfoPtr* NULL ist, gibt *StringLengthPtr* weiterhin die Gesamtzahl der Bytes zurück (mit Ausnahme des Null-Beendigungszeichens für Zeichendaten), auf die im Puffer von *DiagInfoPtr*verwiesen wird.  
  
 *BufferLength*  
 [Eingabe] Wenn *DiagIdentifier* eine ODBC-definierte Diagnose ist und *DiagInfoPtr* auf eine Zeichenfolge oder einen \*Binärpuffer verweist, sollte dieses Argument die Länge von *DiagInfoPtr*sein. Wenn *DiagIdentifier* ein ODBC-definiertes Feld und \* *DiagInfoPtr* eine ganze Zahl ist, wird *BufferLength* ignoriert. Wenn der Wert in * \*DiagInfoPtr* eine Unicode-Zeichenfolge ist (beim Aufrufen von **SQLGetDiagFieldW**) muss das *BufferLength-Argument* eine gerade Zahl sein.  
  
 Wenn *DiagIdentifier* ein vom Treiber definiertes Feld ist, gibt die Anwendung die Art des Felds für den Treiber-Manager an, indem das *Argument BufferLength* festgelegt wird. *BufferLength* kann die folgenden Werte haben:  
  
-   Wenn *DiagInfoPtr* ein Zeiger auf eine Zeichenfolge ist, ist *BufferLength* die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn *DiagInfoPtr* ein Zeiger auf einen Binärpuffer ist, platziert die Anwendung das Ergebnis des*SQL_LEN_BINARY_ATTR(Länge*) -Makros in *BufferLength*. Dadurch wird ein negativer Wert in *BufferLength*platziert.  
  
-   Wenn *DiagInfoPtr* ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder binäre Zeichenfolge ist, sollte *BufferLength* den Wert SQL_IS_POINTER haben.  
  
-   Wenn * \*DiagInfoPtr* einen Datentyp fester Länge enthält, ist *BufferLength* SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT oder SQL_IS_USMALLINT.  
  
 *StringLengthPtr*  
 [Ausgabe] Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes (mit Ausnahme der Anzahl der \*Bytes, die für das Null-Beendigungszeichen erforderlich sind) zurückgegeben werden soll, die in *DiagInfoPtr*für Zeichendaten zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *BufferLength*ist, wird der Text in \* *DiagInfoPtr* auf *BufferLength* abzüglich der Länge eines Nullbeendigungszeichens abgeschnitten.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_NO_DATA.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLGetDiagField** stellt keine Diagnosedatensätze für sich selbst bereit. Es verwendet die folgenden Rückgabewerte, um das Ergebnis seiner eigenen Ausführung zu melden:  
  
-   SQL_SUCCESS: Die Funktion hat erfolgreich Diagnoseinformationen zurückgegeben.  
  
-   SQL_SUCCESS_WITH_INFO: \* *DiagInfoPtr* war zu klein, um das angeforderte Diagnosefeld zu halten. Daher wurden die Daten im Diagnosefeld abgeschnitten. Um zu ermitteln, dass eine Kürzung erfolgt ist, muss die Anwendung *BufferLength* mit der tatsächlichen Anzahl der verfügbaren Bytes vergleichen, die in **StringLengthPtr*geschrieben wird.  
  
-   SQL_INVALID_HANDLE: Das von *HandleType* und *Handle* angegebene Handle war kein gültiges Handle.  
  
-   SQL_ERROR: Einer der folgenden Fehler ist aufgetreten:  
  
    -   *Das Argument DiagIdentifier* war nicht einer der gültigen Werte.  
  
    -   *Das DiagIdentifier-Argument* wurde SQL_DIAG_CURSOR_ROW_COUNT, SQL_DIAG_DYNAMIC_FUNCTION, SQL_DIAG_DYNAMIC_FUNCTION_CODE oder SQL_DIAG_ROW_COUNT, aber *Handle* war kein Anweisungshandle. (Der Treiber-Manager gibt diese Diagnose zurück.)  
  
    -   *Das RecNumber-Argument* war negativ oder 0, wenn *DiagIdentifier* ein Feld aus einem Diagnosedatensatz angab. *RecNumber* wird für Headerfelder ignoriert.  
  
    -   Der angeforderte Wert war eine Zeichenfolge und *BufferLength* kleiner als Null.  
  
    -   Bei Verwendung einer asynchronen Benachrichtigung war der asynchrone Vorgang für das Handle nicht abgeschlossen.  
  
-   SQL_NO_DATA: *RecNumber* war größer als die Anzahl der Diagnosedatensätze, die für das in Handle angegebene Handle vorhanden *waren.* Die Funktion gibt auch SQL_NO_DATA für eine positive *RecNumber* zurück, wenn keine Diagnosedatensätze für *Handle*vorhanden sind.  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung ruft in der Regel **SQLGetDiagField** auf, um eines von drei Zielen zu erreichen:  
  
1.  So erhalten Sie bestimmte Fehler- oder Warnungsinformationen, wenn ein Funktionsaufruf SQL_ERROR oder SQL_SUCCESS_WITH_INFO (oder SQL_NEED_DATA für die **SQLBrowseConnect-Funktion)** zurückgegeben wurde.  
  
2.  Um die Anzahl der Zeilen in der Datenquelle zu bestimmen, die beim Einfügen, Löschen oder Aktualisieren von Vorgängen mit einem Aufruf von **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** (aus dem SQL_DIAG_ROW_COUNT-Headerfeld) betroffen waren, oder um die Anzahl der Zeilen zu bestimmen, die im aktuellen geöffneten Cursor vorhanden sind, wenn der Treiber diese Informationen bereitstellen kann (aus dem SQL_DIAG_CURSOR_ROW_COUNT Headerfeld).  
  
3.  So bestimmen Sie, welche Funktion durch einen Aufruf von **SQLExecDirect** oder **SQLExecute** ausgeführt wurde (aus den SQL_DIAG_DYNAMIC_FUNCTION- und SQL_DIAG_DYNAMIC_FUNCTION_CODE-Headerfeldern).  
  
 Jede ODBC-Funktion kann bei jedem Aufruf von Null oder mehr Diagnosedatensätzen buchen, sodass eine Anwendung **SQLGetDiagField** nach jedem ODBC-Funktionsaufruf aufrufen kann. Die Anzahl der Diagnosedatensätze, die gleichzeitig gespeichert werden können, ist unbegrenzt. **SQLGetDiagField** ruft nur die Diagnoseinformationen ab, die zuletzt der Diagnosedatenstruktur zugeordnet sind, die im *Handle-Argument* angegeben ist. Wenn die Anwendung eine andere ODBC-Funktion als **SQLGetDiagField** oder **SQLGetDiagRec**aufruft, gehen alle Diagnoseinformationen eines vorherigen Aufrufs mit demselben Handle verloren.  
  
 Eine Anwendung kann alle Diagnosedatensätze scannen, indem *recNumber*erhöht wird, solange **SQLGetDiagField** SQL_SUCCESS zurückgibt. Die Anzahl der Statusdatensätze wird im Kopffeld SQL_DIAG_NUMBER angegeben. Aufrufe von **SQLGetDiagField** sind für die Header- und Datensatzfelder zerstörungsfrei. Die Anwendung kann **SQLGetDiagField** später erneut aufrufen, um ein Feld aus einem Datensatz abzurufen, solange eine andere Funktion als die Diagnosefunktionen nicht zwischenzeitlich aufgerufen wurde, wodurch Datensätze für dasselbe Handle gesendet werden.  
  
 Eine Anwendung kann **SQLGetDiagField aufrufen,** um jedes Diagnosefeld jederzeit zurückzugeben, mit Ausnahme von SQL_DIAG_CURSOR_ROW_COUNT oder SQL_DIAG_ROW_COUNT, die SQL_ERROR zurückgibt, wenn *Handle* kein Anweisungshandle ist. Wenn ein anderes Diagnosefeld nicht definiert ist, gibt der Aufruf von **SQLGetDiagField** SQL_SUCCESS zurück (vorausgesetzt, es wird keine andere Diagnose gefunden), und es wird ein nicht definierter Wert für das Feld zurückgegeben.  
  
 Weitere Informationen finden Sie unter [Verwenden von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md) und [Implementieren von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md).  
  
 Wenn Sie eine andere API als die, die asynchron ausgeführt wird, aufrufen, wird HY010 "Funktionssequenzfehler" generiert. Der Fehlerdatensatz kann jedoch nicht abgerufen werden, bevor der asynchrone Vorgang abgeschlossen ist.  
  
## <a name="handletype-argument"></a>HandleType-Argument  
 Jedem Handlestyp können Diagnoseinformationen zugeordnet sein. Das *HandleType-Argument* gibt den Handletyp *von Handle*an.  
  
 Einige Header- und Datensatzfelder können nicht für Umgebungs-, Verbindungs-, Anweisungs- und Deskriptorhandles zurückgegeben werden. Die Handles, für die kein Feld gilt, sind in den folgenden Abschnitten "Headerfelder" und "Datensatzfelder" angegeben.  
  
 Wenn *HandleType* SQL_HANDLE_ENV ist, kann *Handle* entweder ein freigegebenes oder ein nicht freigegebenes Umgebungshandle sein.  
  
 Einem Umgebungshandle sollten keine treiberspezifischen Headerdiagnosefelder zugeordnet werden.  
  
 Die einzigen Diagnoseheaderfelder, die für ein Deskriptorhandle definiert sind, sind SQL_DIAG_NUMBER und SQL_DIAG_RETURNCODE.  
  
## <a name="diagidentifier-argument"></a>DiagIdentifier-Argument  
 Dieses Argument gibt den Bezeichner des Feldes an, das aus der Diagnosedatenstruktur benötigt wird. Wenn *RecNumber* größer oder gleich 1 ist, werden die Diagnoseinformationen, die von einer Funktion zurückgegeben werden, in den Daten im Feld beschrieben. Wenn *RecNumber* 0 ist, befindet sich das Feld im Header der Diagnosedatenstruktur und enthält daher Daten zum Funktionsaufruf, der die Diagnoseinformationen zurückgegeben hat, nicht zu den spezifischen Informationen.  
  
 Treiber können treiberspezifische Header- und Datensatzfelder in der Diagnosedatenstruktur definieren.  
  
 Eine ODBC 3 *.x-Anwendung,* die mit einem ODBC 2 *.x-Treiber* arbeitet, kann **SQLGetDiagField** nur mit einem *DiagIdentifier-Argument* von SQL_DIAG_CLASS_ORIGIN, SQL_DIAG_CLASS_SUBCLASS_ORIGIN, SQL_DIAG_CONNECTION_NAME, SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_NUMBER, SQL_DIAG_RETURNCODE, SQL_DIAG_SERVER_NAME oder SQL_DIAG_SQLSTATE aufrufen. Alle anderen Diagnosefelder geben SQL_ERROR zurück.  
  
## <a name="header-fields"></a>Headerfelder  
 Die in der folgenden Tabelle aufgeführten Headerfelder können in das *Argument DiagIdentifier* eingeschlossen werden.  
  
|DiagIdentifier|Rückgabetyp|Rückgabe|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CURSOR_ROW_COUNT|SQLLEN|Dieses Feld enthält die Anzahl der Zeilen im Cursor. Die Semantik hängt von den **SQLGetInfo-Informationstypen** SQL_DYNAMIC_CURSOR_ATTRIBUTES2, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2 und SQL_STATIC_CURSOR_ATTRIBUTES2 ab, die angeben, welche Zeilenanzahlen für jeden Cursortyp verfügbar sind (im SQL_CA2_CRC_EXACT und SQL_CA2_CRC_APPROXIMATE Bits).<br /><br /> Der Inhalt dieses Felds wird nur für Anweisungshandles definiert und nur nach dem Aufruf von **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults.** Wenn **SIE SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_CURSOR_ROW_COUNT auf einem anderen als einem Anweisungshandle aufrufen, wird SQL_ERROR zurückgegeben.|  
|SQL_DIAG_DYNAMIC_FUNCTION|SQLCHAR *|Dies ist eine Zeichenfolge, die die SQL-Anweisung beschreibt, die von der zugrunde liegenden Funktion ausgeführt wurde. (Siehe "Werte der Felder dynamische Funktion" weiter unten in diesem Abschnitt für bestimmte Werte.) Der Inhalt dieses Felds wird nur für Anweisungshandles und erst nach einem Aufruf von **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults**definiert. Wenn **SIE SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_DYNAMIC_FUNCTION auf einem anderen als einem Anweisungshandle aufrufen, wird SQL_ERROR zurückgegeben. Der Wert dieses Felds ist vor einem Aufruf von **SQLExecute** oder **SQLExecDirect**nicht definiert.|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|SQLINTEGER|Dies ist ein numerischer Code, der die SQL-Anweisung beschreibt, die von der zugrunde liegenden Funktion ausgeführt wurde. (Siehe "Werte der dynamischen Funktionsfelder", weiter unten in diesem Abschnitt, für einen bestimmten Wert.) Der Inhalt dieses Felds wird nur für Anweisungshandles und erst nach einem Aufruf von **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults**definiert. Wenn **SIE SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_DYNAMIC_FUNCTION_CODE auf einem anderen als einem Anweisungshandle aufrufen, wird SQL_ERROR zurückgegeben. Der Wert dieses Felds ist vor einem Aufruf von **SQLExecute** oder **SQLExecDirect**nicht definiert.|  
|SQL_DIAG_NUMBER|SQLINTEGER|Die Anzahl der Statusdatensätze, die für das angegebene Handle verfügbar sind.|  
|SQL_DIAG_RETURNCODE|SQLRETURN|Rückgabecode, der von der Funktion zurückgegeben wird. Eine Liste der Rückgabecodes finden Sie unter [Rückgabecodes](../../../odbc/reference/develop-app/return-codes-odbc.md). Der Treiber muss keine SQL_DIAG_RETURNCODE implementieren. es wird immer vom Treiber-Manager implementiert. Wenn noch keine Funktion für den *Handle*aufgerufen wurde, werden SQL_SUCCESS für SQL_DIAG_RETURNCODE zurückgegeben.|  
|SQL_DIAG_ROW_COUNT|SQLLEN|Die Anzahl der Zeilen, die von einem Einfügen, Löschen oder Aktualisieren von **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos**betroffen sind. Sie ist treiberdefiniert, nachdem eine *Cursorspezifikation* ausgeführt wurde. Der Inhalt dieses Feldes wird nur für Anweisungshandles definiert. Wenn **SIE SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_ROW_COUNT auf einem anderen als einem Anweisungshandle aufrufen, wird SQL_ERROR zurückgegeben. Die Daten in diesem Feld werden auch im *RowCountPtr-Argument* von **SQLRowCount**zurückgegeben. Die Daten in diesem Feld werden nach jedem nicht-diagnostischen Funktionsaufruf zurückgesetzt, während die von **SQLRowCount** zurückgegebene Zeilenanzahl unverändert bleibt, bis die Anweisung auf den vorbereiteten oder zugewiesenen Zustand zurückgesetzt wird.|  
  
## <a name="record-fields"></a>Record Fields  
 Die in der folgenden Tabelle aufgeführten Datensatzfelder können in das *Argument DiagIdentifier* aufgenommen werden.  
  
|DiagIdentifier|Rückgabetyp|Rückgabe|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CLASS_ORIGIN|SQLCHAR *|Eine Zeichenfolge, die das Dokument angibt, das den Klassenteil des SQLSTATE-Werts in diesem Datensatz definiert. Sein Wert ist "ISO 9075" für alle SQLSTATEs, die von Open Group und ISO Call-Level Interface definiert werden. Für ODBC-spezifische SQLSTATEs (alle, deren SQLSTATE-Klasse "IM" ist), ist ihr Wert "ODBC 3.0".|  
|SQL_DIAG_COLUMN_NUMBER|SQLINTEGER|Wenn das feld SQL_DIAG_ROW_NUMBER eine gültige Zeilennummer in einem Rowset oder einem Satz von Parametern ist, enthält dieses Feld den Wert, der die Spaltennummer im Resultset oder die Parameternummer im Parametersatz darstellt. Die Spaltennummern des Ergebnissatzes beginnen immer bei 1; Wenn sich dieser Statusdatensatz auf eine Lesezeichenspalte bezieht, kann das Feld Null sein. Parameternummern beginnen bei 1. Der Wert SQL_NO_COLUMN_NUMBER, wenn der Statusdatensatz keiner Spaltennummer oder Parameternummer zugeordnet ist. Wenn der Treiber die Spaltennummer oder Parameternummer, der dieser Datensatz zugeordnet ist, nicht ermitteln kann, hat dieses Feld den Wert SQL_COLUMN_NUMBER_UNKNOWN.<br /><br /> Der Inhalt dieses Feldes wird nur für Anweisungshandles definiert.|  
|SQL_DIAG_CONNECTION_NAME|SQLCHAR *|Eine Zeichenfolge, die den Namen der Verbindung angibt, auf die sich der Diagnosedatensatz bezieht. Dieses Feld ist treiberdefiniert. Für Diagnosedatenstrukturen, die dem Umgebungshandle zugeordnet sind, und für Diagnosen, die sich nicht auf eine Verbindung beziehen, ist dieses Feld eine Zeichenfolge mit einer Länge von Null.|  
|SQL_DIAG_MESSAGE_TEXT|SQLCHAR *|Eine Informationsmeldung zum Fehler oder der Warnung. Dieses Feld ist wie unter [Diagnosemeldungen](../../../odbc/reference/develop-app/diagnostic-messages.md)beschrieben formatiert. Der Diagnosenachrichtentext hat keine maximale Länge.|  
|SQL_DIAG_NATIVE|SQLINTEGER|Ein treiber-/datenquellenspezifischer systemeigener Fehlercode. Wenn kein systemeigener Fehlercode vorhanden ist, gibt der Treiber 0 zurück.|  
|SQL_DIAG_ROW_NUMBER|SQLLEN|Dieses Feld enthält die Zeilennummer im Rowset oder die Parameternummer im Parametersatz, dem der Statusdatensatz zugeordnet ist. Zeilennummern und Parameternummern beginnen mit 1. Dieses Feld hat den Wert SQL_NO_ROW_NUMBER, wenn dieser Statusdatensatz keiner Zeilennummer oder Parameternummer zugeordnet ist. Wenn der Treiber die Zeilennummer oder Parameternummer, der dieser Datensatz zugeordnet ist, nicht ermitteln kann, hat dieses Feld den Wert SQL_ROW_NUMBER_UNKNOWN.<br /><br /> Der Inhalt dieses Feldes wird nur für Anweisungshandles definiert.|  
|SQL_DIAG_SERVER_NAME|SQLCHAR *|Eine Zeichenfolge, die den Servernamen angibt, auf den sich der Diagnosedatensatz bezieht. Er entspricht dem Wert, der für einen Aufruf von **SQLGetInfo** mit der Option SQL_DATA_SOURCE_NAME zurückgegeben wird. Für Diagnosedatenstrukturen, die dem Umgebungshandle zugeordnet sind, und für Diagnosen, die sich nicht auf einen Server beziehen, ist dieses Feld eine Zeichenfolge mit einer Länge von Null.|  
|SQL_DIAG_SQLSTATE|SQLCHAR *|Ein fünfstelliger SQLSTATE-Diagnosecode. Weitere Informationen finden Sie unter [SQLSTATEs](../../../odbc/reference/develop-app/sqlstates.md).|  
|SQL_DIAG_SUBCLASS_ORIGIN|SQLCHAR *|Eine Zeichenfolge mit demselben Format und gültigen Werten wie SQL_DIAG_CLASS_ORIGIN, die den definierenden Teil des Unterklassenteils des SQLSTATE-Codes identifiziert. Die ODBC-spezifischen SQLSTATES, für die "ODBC 3.0" zurückgegeben wird, umfassen Folgendes:<br /><br /> 01S00, 01S01, 01S02, 01S06, 01S07, 07S01, 08S01, 21S01, 21S02, 25S01, 25S02, 25S03, 42S01, 42S02, 42S12, 42S21, 42S22, HY095, HY097, HY098, HY099 HY100, HY101, HY105, HY107, HY109, HY110, HY111, HYT00, HYT01, IM001, IM002, IM003, IM004, IM005, IM006, IM007, IM008, IM010, IM011, IM012.|  
  
## <a name="values-of-the-dynamic-function-fields"></a>Werte der dynamischen Funktionsfelder  
 In der folgenden Tabelle werden die Werte von SQL_DIAG_DYNAMIC_FUNCTION und SQL_DIAG_DYNAMIC_FUNCTION_CODE beschrieben, die für jeden SQL-Anweisungstyp gelten, der von einem Aufruf von **SQLExecute** oder **SQLExecDirect**ausgeführt wird. Der Treiber kann den aufgeführten Werten, die vom Treiber definiert sind, treiberdefinierte Werte hinzufügen.  
  
|SQL-Anweisung<br /><br /> Ausgeführt|Wert von <br /><br /> SQL_DIAG_DYNAMIC_FUNCTION|Wert von <br /><br /> SQL_DIAG_DYNAMIC_FUNCTION_CODE|  
|--------------------------------|-----------------------------------------------|-----------------------------------------------------|  
|*alter-domain-statement*|"DOMÄNE ÄNDERN"|SQL_DIAG_ALTER_DOMAIN|  
|*alter-table-Statement*|"ALTER TABLE"|SQL_DIAG_ALTER_TABLE|  
|*Assertion-Definition*|"ASSERTION ERSTELLEN"|SQL_DIAG_CREATE_ASSERTION|  
|*Zeichen-Set-Definition*|"ZEICHENSATZ ERSTELLEN"|SQL_DIAG_CREATE_CHARACTER_SET|  
|*Kollatierungsdefinition*|"SORTIERUNG ERSTELLEN"|SQL_DIAG_CREATE_COLLATION|  
|*Domänendefinition*|"DOMÄNE ERSTELLEN"|SQL_DIAG_CREATE_DOMAIN|
|*create-index-statement*|"INDEX ERSTELLEN"|SQL_DIAG_CREATE_INDEX|  
|*create-table-statement*|"TABELLE ERSTELLEN"|SQL_DIAG_CREATE_TABLE|  
|*create-view-statement*|"ANSICHT ERSTELLEN"|SQL_DIAG_CREATE_VIEW|  
|*Cursor-Spezifikation*|"SELECT-CURSOR"|SQL_DIAG_SELECT_CURSOR|  
|*delete-statement-positioniert*|"DYNAMISCHER LÖSCHCURSOR"|SQL_DIAG_DYNAMIC_DELETE_CURSOR|  
|*delete-statement-searched*|"WO LÖSCHEN"|SQL_DIAG_DELETE_WHERE|  
|*drop-assertion-statement*|"DROP ASSERTION"|SQL_DIAG_DROP_ASSERTION|  
|*drop-character-set-stmt*|"DROP-ZEICHENSATZ"|SQL_DIAG_DROP_CHARACTER_SET|  
|*Drop-Collation-Anweisung*|"DROP-KOLLATIERUNG"|SQL_DIAG_DROP_COLLATION|  
|*Drop-Domain-Anweisung*|"DROP-DOMAIN"|SQL_DIAG_DROP_DOMAIN|  
|*Drop-Index-Anweisung*|"DROP-INDEX"|SQL_DIAG_DROP_INDEX|  
|*Drop-Schema-Anweisung*|"DROP-SCHEMA"|SQL_DIAG_DROP_SCHEMA|  
|*Drop-Table-Anweisung*|"DROP-TABELLE"|SQL_DIAG_DROP_TABLE|  
|*Drop-Translation-Statement*|"DROP-ÜBERSETZUNG"|SQL_DIAG_DROP_TRANSLATION|  
|*Drop-View-Anweisung*|"DROP-ANSICHT"|SQL_DIAG_DROP_VIEW|  
|*Grantstatement*|"GRANT"|SQL_DIAG_GRANT|
|*Insert-Anweisung*|"EINFÜGEN"|SQL_DIAG_INSERT|  
|*ODBC-Prozedur-Erweiterung*|"ANRUF"|SQL_DIAG_ CALL|  
|*widerrufserklärung*|"REVOKE"|SQL_DIAG_REVOKE|  
|*Schema-Definition*|"SCHEMA ERSTELLEN"|SQL_DIAG_CREATE_SCHEMA|  
|*Übersetzungsdefinition*|"ÜBERSETZUNG ERSTELLEN"|SQL_DIAG_CREATE_TRANSLATION|  
|*update-statement-positioniert*|"DYNAMISCHER AKTUALISIERUNGSCURSOR"|SQL_DIAG_DYNAMIC_UPDATE_CURSOR|  
|*update-statement-searched*|"AKTUALISIEREN WO"|SQL_DIAG_UPDATE_WHERE|  
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

 Statusdatensätze werden in einer Reihenfolge basierend auf der Zeilennummer und dem Typ der Diagnose positioniert. Der Treiber-Manager bestimmt die endgültige Reihenfolge, in der Statusdatensätze zurückgegeben werden sollen, die er generiert. Der Treiber bestimmt die endgültige Reihenfolge, in der Statusdatensätze zurückgegeben werden sollen, die er generiert.  
  
 Wenn Diagnosedatensätze sowohl vom Treiber-Manager als auch vom Treiber gebucht werden, ist der Treiber-Manager für deren Bestellung verantwortlich.  
  
 Wenn zwei oder mehr Statusdatensätze vorhanden sind, wird die Reihenfolge der Datensätze zuerst durch Zeilennummer bestimmt. Die folgenden Regeln gelten für die Bestimmung der Reihenfolge der Diagnosedatensätze nach Zeile:  
  
-   Datensätze, die keiner Zeile entsprechen, werden vor Datensätzen angezeigt, die einer bestimmten Zeile entsprechen, da SQL_NO_ROW_NUMBER als -1 definiert ist.  
  
-   Datensätze, für die die Zeilennummer unbekannt ist, werden vor allen anderen Datensätzen angezeigt, da SQL_ROW_NUMBER_UNKNOWN als -2 definiert ist.  
  
-   Für alle Datensätze, die sich auf bestimmte Zeilen beziehen, werden Datensätze nach dem Wert im Feld SQL_DIAG_ROW_NUMBER sortiert. Alle Fehler und Warnungen der ersten betroffenen Zeile werden aufgelistet, und dann alle Fehler und Warnungen der nächsten betroffenen Zeile usw.  
  
> [!NOTE]
>  Der ODBC 3 *.x* Driver Manager ordnet keine Statusdatensätze in der Diagnosewarteschlange an, wenn SQLSTATE 01S01 (Fehler in der Zeile) von einem ODBC 2 *.x-Treiber* zurückgegeben wird oder wenn SQLSTATE 01S01 (Fehler in der Zeile) von einem ODBC 3 *.x-Treiber* zurückgegeben wird, wenn **SQLExtendedFetch** aufgerufen wird oder **SQLSetPos** auf einem Cursor aufgerufen wird, der mit **SQLFetchExtended**positioniert wurde.  
  
 Innerhalb jeder Zeile oder für alle Datensätze, die keiner Zeile entsprechen oder für die die Zeilennummer unbekannt ist, oder für alle Datensätze mit einer Zeilennummer, die SQL_NO_ROW_NUMBER entspricht, wird der erste aufgeführte Datensatz mithilfe eines Satzes von Sortierregeln bestimmt. Nach dem ersten Datensatz ist die Reihenfolge der anderen Datensätze, die eine Zeile betreffen, nicht definiert. Eine Anwendung kann nicht davon ausgehen, dass Fehler Warnungen nach dem ersten Datensatz vorausgehen. Anwendungen sollten die vollständige Diagnosedatenstruktur scannen, um vollständige Informationen über einen fehlgeschlagenen Aufruf einer Funktion zu erhalten.  
  
 Die folgenden Regeln werden verwendet, um den ersten Datensatz innerhalb einer Zeile zu bestimmen. Der Rekord mit dem höchsten Rang ist der erste Datensatz. Die Quelle eines Datensatzes (Treiber-Manager, Treiber, Gateway usw.) wird beim Rangieren von Datensätzen nicht berücksichtigt.  
  
-   **Fehler** Statusdatensätze, die Fehler beschreiben, haben den höchsten Rang. Die folgenden Regeln werden angewendet, um Fehler zu sortieren:  
  
    -   Datensätze, die auf einen Transaktionsfehler oder einen möglichen Transaktionsfehler hinweisen, übersteigen alle anderen Datensätze.  
  
    -   Wenn zwei oder mehr Datensätze dieselbe Fehlerbedingung beschreiben, übertrifft SQLSTATEs, die durch die OPEN Group CLI-Spezifikation (Klassen 03 bis HZ) definiert sind, ODBC- und treiberdefinierte SQLSTATEs.  
  
-   **Implementierungsdefinierte Keine Datenwerte** Statusdatensätze, die treiberdefinierte No Data-Werte (Klasse 02) beschreiben, haben den zweithöchsten Rang.  
  
-   **Warnungen** Statusdatensätze, die Warnungen beschreiben (Klasse 01), haben den niedrigsten Rang. Wenn zwei oder mehr Datensätze dieselbe Warnbedingung beschreiben, übertrifft die Warnung SQLSTATEs, die durch die CLI-Spezifikation "Open Group" definiert wurden, ODBC-definierte und treiberdefinierte SQLSTATEs.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abrufen mehrerer Felder einer Diagnosedatenstruktur|[SQLGetDiagRec-Funktion](sqlgetdiagrec-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
