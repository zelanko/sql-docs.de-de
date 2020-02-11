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
ms.openlocfilehash: 620ccce9a035139482b2d9b4630bb2242f720af8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103775"
---
# <a name="sqlgetdiagfield-function"></a>SQLGetDiagField-Funktion

**Konformitäts**  
 Eingeführte Version: ODBC 3,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLGetDiagField** gibt den aktuellen Wert eines Felds eines Datensatzes der Diagnosedaten Struktur (die einem angegebenen Handle zugeordnet ist) zurück, die Fehler-, Warn-und Statusinformationen enthält.  
  
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
 Der Ein Handle-Typbezeichner, der den Typ des Handles beschreibt, für den eine Diagnose erforderlich ist. Dies muss eine der folgenden Ressourcen sein:  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN Handle wird nur vom Treiber-Manager und vom Treiber verwendet. Anwendungen sollten diesen Handlertyp nicht verwenden. Weitere Informationen zu SQL_HANDLE_DBC_INFO_TOKEN finden Sie unter [entwickeln von Verbindungs Pool Informationen in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Bewältigen*  
 Der Ein Handle für die Diagnosedaten Struktur des Typs, der durch den *Handlertyp*angegeben wird. Wenn " *Lenker Type* " SQL_HANDLE_ENV ist, kann *handle* entweder ein frei Gegebenes oder ein nicht gemeinsam genutztes Umgebungs Handle sein.  
  
 *RecNumber*  
 Der Gibt den Statusdaten Satz an, von dem die Anwendung Informationen sucht. Status Datensätze sind von 1 nummeriert. Wenn das *DiagIdentifier* -Argument ein beliebiges Feld des Diagnose Headers angibt, wird " *RecNumber* " ignoriert. Wenn dies nicht der Fall ist, sollte der Wert größer als 0 sein.  
  
 *DiagIdentifier*  
 Der Gibt das Feld der Diagnose an, dessen Wert zurückgegeben werden soll. Weitere Informationen finden Sie im Abschnitt "*DiagIdentifier* -Argument" in "comments".  
  
 *Diaginfoptr*  
 Ausgeben Zeiger auf einen Puffer, in den die Diagnoseinformationen zurückgegeben werden sollen. Der Datentyp hängt vom Wert von *DiagIdentifier*ab. Wenn *diaginfoptr* ein ganzzahliger Typ ist, sollten Anwendungen einen Puffer von SQLULEN verwenden und den Wert vor dem Aufrufen dieser Funktion auf 0 initialisieren, da einige Treiber möglicherweise nur den unteren 32-Bit-oder 16-Bit-Wert eines Puffers schreiben und das Bit höherer Ordnung unverändert lassen.  
  
 Wenn *diaginfoptr* gleich NULL ist, gibt *stringlengthptr* weiterhin die Gesamtzahl der Bytes (ausgenommen des NULL-Beendigungs Zeichens für Zeichendaten) zurück, die im Puffer zurückgegeben werden können, auf den *diaginfoptr*zeigt.  
  
 *Pufferlänge*  
 Der Wenn *DiagIdentifier* eine ODBC-definierte Diagnose ist und *diaginfoptr* auf eine Zeichenfolge oder einen binären Puffer zeigt, sollte dieses Argument die Länge von \* *diaginfoptr*sein. Wenn *DiagIdentifier* ein ODBC-definiertes Feld und \* *diaginfoptr* eine ganze Zahl ist, wird *BufferLength* ignoriert. Wenn der Wert in * \*diaginfoptr* eine Unicode-Zeichenfolge ist (beim Aufrufen von **sqlgetdiagfieldw**), muss das *BufferLength* -Argument eine gerade Zahl sein.  
  
 Wenn *DiagIdentifier* ein Treiber definiertes Feld ist, gibt die Anwendung die Art des Felds für den Treiber-Manager an, indem das *BufferLength* -Argument festgelegt wird. *BufferLength* kann die folgenden Werte aufweisen:  
  
-   Wenn *diaginfoptr* ein Zeiger auf eine Zeichenfolge ist, entspricht *BufferLength* der Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn *diaginfoptr* ein Zeiger auf einen binären Puffer ist, platziert die Anwendung das Ergebnis des SQL_LEN_BINARY_ATTR (*length*)-Makros in *BufferLength*. Dadurch wird ein negativer Wert in *BufferLength*platziert.  
  
-   Wenn *diaginfoptr* ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder Binär Zeichenfolge ist, sollte *BufferLength* den Wert SQL_IS_POINTER.  
  
-   Wenn * \*diaginfoptr* einen Datentyp mit fester Länge enthält, wird *BufferLength* nach Bedarf SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT oder SQL_IS_USMALLINT.  
  
 *Stringlengthptr*  
 Ausgeben Ein Zeiger auf einen Puffer, in dem die Gesamtzahl der Bytes (ausgenommen der Anzahl der Bytes, die für das NULL-Terminierungs Zeichen erforderlich sind \*) zurückgegeben werden soll, die in *diaginfoptr*für Zeichendaten zurückgegeben werden können. Wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *BufferLength*ist, wird \*der Text in *diaginfoptr* auf *BufferLength* abzüglich der Länge eines NULL-Beendigungs Zeichens gekürzt.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_NO_DATA.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLGetDiagField** sendet keine Diagnosedaten Sätze für sich selbst. Die folgenden Rückgabewerte werden verwendet, um das Ergebnis der eigenen Ausführung zu melden:  
  
-   SQL_SUCCESS: die Funktion hat erfolgreich Diagnoseinformationen zurückgegeben.  
  
-   SQL_SUCCESS_WITH_INFO: \* *diaginfoptr* war zu klein, um das angeforderte Diagnose Feld zu speichern. Daher wurden die Daten im Feld "Diagnose" abgeschnitten. Um zu ermitteln, ob ein Abschneiden aufgetreten ist, muss die Anwendung *BufferLength* mit der tatsächlichen Anzahl der verfügbaren Bytes vergleichen, die in **stringlengthptr*geschrieben wird.  
  
-   SQL_INVALID_HANDLE: das Handle, das von " *Lenker Type* " und " *handle* " angegeben wird, war kein gültiges Handle.  
  
-   SQL_ERROR: eine der folgenden Fehler ist aufgetreten:  
  
    -   *Das DiagIdentifier* -Argument war keiner der gültigen-Werte.  
  
    -   *Das DiagIdentifier* -Argument war SQL_DIAG_CURSOR_ROW_COUNT, SQL_DIAG_DYNAMIC_FUNCTION, SQL_DIAG_DYNAMIC_FUNCTION_CODE oder SQL_DIAG_ROW_COUNT, das *handle* war jedoch kein Anweisungs Handle. (Der Treiber-Manager gibt diese Diagnose zurück.)  
  
    -   *Das RecNumber* -Argument war negativ oder 0, wenn *DiagIdentifier* ein Feld aus einem Diagnosedaten Satz angibt. " *RecNumber* " wird für Header Felder ignoriert.  
  
    -   Der angeforderte Wert war eine Zeichenfolge, und *BufferLength* war kleiner als 0 (null).  
  
    -   Bei Verwendung der asynchronen Benachrichtigung war der asynchrone Vorgang für das Handle nicht beendet.  
  
-   SQL_NO_DATA: *die Anzahl der* Diagnosedaten Sätze, die für das in handle angegebene Handle vorhanden waren, war größer als die Anzahl der Diagnosedaten Sätze *.* Die Funktion gibt auch SQL_NO_DATA für jede positive *remenge* zurück, wenn keine Diagnosedaten Sätze für das *handle*vorhanden sind.  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung ruft normalerweise **SQLGetDiagField** auf, um eines der drei Ziele zu erreichen:  
  
1.  Zum Abrufen spezifischer Fehler-oder Warnungs Informationen, wenn ein Funktions aufrufSQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgegeben wurde (oder SQL_NEED_DATA für die **sqlbrowseconnetct** -Funktion).  
  
2.  So bestimmen Sie die Anzahl der Zeilen in der Datenquelle, die beim Einfügen aufgetreten sind DELETE-oder Update-Vorgänge wurden durch einen aufrufsvorgang von **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos** (aus dem Feld SQL_DIAG_ROW_COUNT-Header) oder durchgeführt, um die Anzahl der Zeilen zu bestimmen, die im aktuellen geöffneten Cursor vorhanden sind, wenn der Treiber diese Informationen (aus dem SQL_DIAG_CURSOR_ROW_COUNT Header Feld) bereitstellen kann.  
  
3.  , Um zu bestimmen, welche Funktion durch einen-Befehl von **SQLExecDirect** oder **SQLExecute** (aus den Header Feldern SQL_DIAG_DYNAMIC_FUNCTION und SQL_DIAG_DYNAMIC_FUNCTION_CODE) ausgeführt wurde.  
  
 Jede ODBC-Funktion kann bei jedem Aufruf NULL oder mehr Diagnosedaten Sätze veröffentlichen, sodass eine Anwendung **SQLGetDiagField** nach jedem ODBC-Funktionsaufruf aufrufen kann. Es gibt keine Beschränkung für die Anzahl der Diagnosedaten Sätze, die zu einem beliebigen Zeitpunkt gespeichert werden können. **SQLGetDiagField** ruft nur die Diagnoseinformationen ab, die zuletzt der im *handle* -Argument angegebenen Diagnosedaten Struktur zugeordnet sind. Wenn die Anwendung eine andere ODBC-Funktion als **SQLGetDiagField** oder **SQLGetDiagRec**aufruft, gehen alle Diagnoseinformationen eines vorherigen Aufrufs mit dem gleichen handle verloren.  
  
 Eine Anwendung kann alle Diagnosedaten Sätze durch Erhöhen der *RecNumber*Scannen, sofern **SQLGetDiagField** SQL_SUCCESS zurückgibt. Die Anzahl der Statusdaten Sätze wird im Feld SQL_DIAG_NUMBER Header angezeigt. Aufrufe von **SQLGetDiagField** sind nicht destruktiv für die Header-und Daten Satz Felder. Die Anwendung kann **SQLGetDiagField** später erneut aufrufen, um ein Feld aus einem Datensatz abzurufen, sofern eine andere Funktion als die Diagnosefunktionen nicht in der Zwischenzeit aufgerufen wurde, die Datensätze im gleichen handle veröffentlichen würde.  
  
 Eine Anwendung kann **SQLGetDiagField** aufrufen, um ein beliebiges Diagnose Feld zu einem beliebigen Zeitpunkt zurückzugeben, mit Ausnahme von SQL_DIAG_CURSOR_ROW_COUNT oder SQL_DIAG_ROW_COUNT, die SQL_ERROR zurückgibt, wenn *handle* kein Anweisungs Handle ist. Wenn ein anderes Diagnose Feld nicht definiert ist, wird beim Aufrufen von **SQLGetDiagField** SQL_SUCCESS (sofern keine andere Diagnose gefunden wird) zurückgegeben, und für das Feld wird ein nicht definierter Wert zurückgegeben.  
  
 Weitere Informationen finden Sie unter [Verwenden von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md) und [Implementieren von SQLGetDiagRec und SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md).  
  
 Wenn eine andere API aufgerufen wird, als die, die asynchron ausgeführt wird, wird HY010 "Function Sequence Error" generiert. Der Fehler Daten Satz kann jedoch erst abgerufen werden, wenn der asynchrone Vorgang abgeschlossen ist.  
  
## <a name="handletype-argument"></a>Lenker-Typargument  
 Jedem Handlertyp können Diagnoseinformationen zugeordnet werden. Das " *Lenker Type* "-Argument gibt den Handle-Typ des *Handles*an.  
  
 Einige Header-und Daten Satz Felder können für die Umgebungs-, Verbindungs-, Anweisungs-und Deskriptorhandles nicht zurückgegeben werden. Die Handles, für die ein Feld nicht anwendbar ist, werden in den Abschnitten "Header Felder" und "Datensatz-Felder" aufgeführt.  
  
 Wenn " *Lenker Type* " SQL_HANDLE_ENV ist, kann *handle* entweder ein frei Gegebenes oder nicht frei gegebenes Umgebungs Handle sein.  
  
 Einem Umgebungs Handle sollten keine treiberspezifischen Header Diagnose Felder zugeordnet werden.  
  
 Die einzigen Diagnose Header Felder, die für ein Deskriptorhandle definiert sind, sind SQL_DIAG_NUMBER und SQL_DIAG_RETURNCODE.  
  
## <a name="diagidentifier-argument"></a>DiagIdentifier-Argument  
 Dieses Argument gibt den Bezeichner des Felds an, das von der Diagnosedaten Struktur benötigt wird. Wenn " *RecNumber* " größer oder gleich 1 ist, werden die von einer Funktion zurückgegebenen Diagnoseinformationen von den Daten im Feld beschrieben. Wenn " *RecNumber* " den Wert "0" hat, befindet sich das Feld im Header der Diagnosedaten Struktur und enthält daher Daten, die sich auf den Funktions aufgerufen haben, der die Diagnoseinformationen zurückgegeben hat, und nicht an die spezifischen Informationen.  
  
 Treiber können Treiber spezifische Header-und Daten Satz Felder in der Diagnosedaten Struktur definieren.  
  
 Eine ODBC 3 *. x* -Anwendung, die mit einem ODBC 2 *. x* -Treiber arbeitet, kann **SQLGetDiagField** nur mit einem *DiagIdentifier* -Argument von SQL_DIAG_CLASS_ORIGIN, SQL_DIAG_CLASS_SUBCLASS_ORIGIN, SQL_DIAG_CONNECTION_NAME, SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_NUMBER, SQL_DIAG_RETURNCODE, SQL_DIAG_SERVER_NAME oder SQL_DIAG_SQLSTATE aufrufen. Alle anderen Diagnose Felder geben SQL_ERROR zurück.  
  
## <a name="header-fields"></a>Header Felder  
 Die Header Felder, die in der folgenden Tabelle aufgeführt sind, können in das *DiagIdentifier* -Argument eingefügt werden.  
  
|DiagIdentifier|Rückgabetyp|Rückgabe|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CURSOR_ROW_COUNT|SQLLEN|Dieses Feld enthält die Anzahl der Zeilen im Cursor. Die Semantik ist abhängig von den **SQLGetInfo** -Informationstypen SQL_DYNAMIC_CURSOR_ATTRIBUTES2, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2 und SQL_STATIC_CURSOR_ATTRIBUTES2, die angeben, welche Zeilen Anzahl für jeden Cursortyp (in den SQL_CA2_CRC_EXACT-und SQL_CA2_CRC_APPROXIMATE Bits) verfügbar ist.<br /><br /> Der Inhalt dieses Felds wird nur für Anweisungs Handles und nur nach dem Aufruf von **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** definiert. Durch den Aufruf von **SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_CURSOR_ROW_COUNT auf anderen als einem Anweisungs Handle wird SQL_ERROR zurückgegeben.|  
|SQL_DIAG_DYNAMIC_FUNCTION|SQLCHAR|Dies ist eine Zeichenfolge, die die SQL-Anweisung beschreibt, die die zugrunde liegende Funktion ausgeführt hat. (Weitere Informationen finden Sie unter "Werte der dynamischen Funktionsfelder" weiter unten in diesem Abschnitt für bestimmte Werte). Der Inhalt dieses Felds wird nur für Anweisungs Handles und nur nach einem-Befehl von **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults**definiert. Durch den Aufruf von **SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_DYNAMIC_FUNCTION auf anderen als einem Anweisungs Handle wird SQL_ERROR zurückgegeben. Der Wert dieses Felds ist vor einem-Befehl von **SQLExecute** oder **SQLExecDirect**nicht definiert.|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|SQLINTEGER|Dies ist ein numerischer Code, der die von der zugrunde liegenden Funktion ausgeführte SQL-Anweisung beschreibt. (Weitere Informationen finden Sie unter "Werte der dynamischen Funktionsfelder" weiter unten in diesem Abschnitt für einen bestimmten Wert.) Der Inhalt dieses Felds wird nur für Anweisungs Handles und nur nach einem-Befehl von **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults**definiert. Durch den Aufruf von **SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_DYNAMIC_FUNCTION_CODE auf anderen als einem Anweisungs Handle wird SQL_ERROR zurückgegeben. Der Wert dieses Felds ist vor einem-Befehl von **SQLExecute** oder **SQLExecDirect**nicht definiert.|  
|SQL_DIAG_NUMBER|SQLINTEGER|Die Anzahl der für das angegebene Handle verfügbaren Statusdaten Sätze.|  
|SQL_DIAG_RETURNCODE|SQLRETURN|Rückgabecode, der von der Funktion zurückgegeben wird. Eine Liste der Rückgabecodes finden Sie unter [Rückgabecodes](../../../odbc/reference/develop-app/return-codes-odbc.md). Der Treiber muss SQL_DIAG_RETURNCODE nicht implementieren; Sie wird immer vom Treiber-Manager implementiert. Wenn für das *handle*noch keine Funktion aufgerufen wurde, werden SQL_SUCCESS für SQL_DIAG_RETURNCODE zurückgegeben.|  
|SQL_DIAG_ROW_COUNT|SQLLEN|Die Anzahl der Zeilen, die von einem INSERT-, DELETE-oder Update-Vorgang betroffen sind, der von **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**oder **SQLSetPos**ausgeführt wird. Es ist Treiber definiert, nachdem eine *Cursor Spezifikation* ausgeführt wurde. Der Inhalt dieses Felds wird nur für Anweisungs Handles definiert. Durch den Aufruf von **SQLGetDiagField** mit einem *DiagIdentifier* von SQL_DIAG_ROW_COUNT auf anderen als einem Anweisungs Handle wird SQL_ERROR zurückgegeben. Die Daten in diesem Feld werden ebenfalls im *rowzählenptr* -Argument von **SQLRowCount**zurückgegeben. Die Daten in diesem Feld werden nach jedem nicht-Diagnose Funktions Aufrufwert zurückgesetzt, während die von **SQLRowCount** zurückgegebene Zeilen Anzahl gleich bleibt, bis die Anweisung auf den vorbereiteten oder zugewiesenen Zustand zurückgesetzt wird.|  
  
## <a name="record-fields"></a>Daten Satz Felder  
 Die in der folgenden Tabelle aufgeführten Daten Satz Felder können im *DiagIdentifier* -Argument enthalten sein.  
  
|DiagIdentifier|Rückgabetyp|Rückgabe|  
|--------------------|-----------------|-------------|  
|SQL_DIAG_CLASS_ORIGIN|SQLCHAR|Eine Zeichenfolge, die das Dokument angibt, das den Klassen Teil des SQLSTATE-Werts in diesem Datensatz definiert. Der zugehörige Wert ist "ISO 9075" für alle Sqlstates, die von der Open Group-und ISO-Schnittstelle auf der Rufebene definiert werden Bei ODBC-spezifischen Sqlstates (alle, deren SQLSTATE-Klasse "im" ist) lautet der Wert "ODBC 3,0".|  
|SQL_DIAG_COLUMN_NUMBER|SQLINTEGER|Wenn das SQL_DIAG_ROW_NUMBER Feld eine gültige Zeilennummer in einem Rowset oder einer Gruppe von Parametern ist, enthält dieses Feld den Wert, der die Spaltennummer im Resultset darstellt, oder die Parameter Nummer in der Gruppe von Parametern. Ergebnissatz-Spalten Nummern beginnen immer bei 1; Wenn sich dieser Statusdaten Satz auf eine Lesezeichen Spalte bezieht, kann das Feld den Wert 0 (null) aufweisen. Die Parameter Nummern beginnen bei 1. Der Wert SQL_NO_COLUMN_NUMBER, wenn der Statusdaten Satz keiner Spaltennummer oder Parameter Nummer zugeordnet ist. Wenn der Treiber die Spaltennummer oder die Parameter Nummer nicht ermitteln kann, mit der dieser Datensatz verknüpft ist, enthält dieses Feld den Wert SQL_COLUMN_NUMBER_UNKNOWN.<br /><br /> Der Inhalt dieses Felds wird nur für Anweisungs Handles definiert.|  
|SQL_DIAG_CONNECTION_NAME|SQLCHAR|Eine Zeichenfolge, die den Namen der Verbindung angibt, zu der der Diagnosedaten Satz gehört. Dieses Feld ist Treiber definiert. Für diagnostische Datenstrukturen, die dem Umgebungs Handle zugeordnet sind, und für Diagnosen, die sich nicht auf eine Verbindung beziehen, ist dieses Feld eine Zeichenfolge der Länge 0 (null).|  
|SQL_DIAG_MESSAGE_TEXT|SQLCHAR|Eine Informations Meldung zu dem Fehler oder der Warnung. Dieses Feld wird wie in [Diagnosemeldungen](../../../odbc/reference/develop-app/diagnostic-messages.md)beschrieben formatiert. Es gibt keine maximale Länge für den Text der Diagnose Nachricht.|  
|SQL_DIAG_NATIVE|SQLINTEGER|Ein Treiber-/datenquellenspezifischer System eigener Fehlercode. Wenn kein nativer Fehlercode vorhanden ist, gibt der Treiber 0 zurück.|  
|SQL_DIAG_ROW_NUMBER|SQLLEN|Dieses Feld enthält die Zeilennummer im Rowset oder die Parameter Nummer in den Parametern, mit denen der Statusdaten Satz verknüpft ist. Zeilennummern und Parameter Nummern beginnen mit 1. Dieses Feld weist den Wert SQL_NO_ROW_NUMBER auf, wenn dieser Statusdaten Satz keiner Zeilennummer oder Parameter Nummer zugeordnet ist. Wenn der Treiber die Zeilennummer oder die Parameter Nummer nicht ermitteln kann, mit der dieser Datensatz verknüpft ist, enthält dieses Feld den Wert SQL_ROW_NUMBER_UNKNOWN.<br /><br /> Der Inhalt dieses Felds wird nur für Anweisungs Handles definiert.|  
|SQL_DIAG_SERVER_NAME|SQLCHAR|Eine Zeichenfolge, die den Servernamen angibt, mit dem der Diagnosedaten Satz verknüpft ist. Dies entspricht dem Wert, der für einen **SQLGetInfo** -Aufrufwert mit der SQL_DATA_SOURCE_NAME-Option zurückgegeben wird. Für diagnostische Datenstrukturen, die dem Umgebungs Handle zugeordnet sind, und für Diagnosen, die nicht mit einem Server in Beziehung stehen, ist dieses Feld eine Zeichenfolge der Länge 0 (null).|  
|SQL_DIAG_SQLSTATE|SQLCHAR|Ein fünf Zeichen großes SQLSTATE-Diagnosecode. Weitere Informationen finden Sie unter [Sqlstates](../../../odbc/reference/develop-app/sqlstates.md).|  
|SQL_DIAG_SUBCLASS_ORIGIN|SQLCHAR|Eine Zeichenfolge mit dem gleichen Format und den gültigen Werten wie SQL_DIAG_CLASS_ORIGIN, die den definierenden Teil des Unterklassen Teils des SQLSTATE-Codes angibt. Die ODBC-spezifischen Sqlstates, für die "ODBC 3,0" zurückgegeben wird, umfassen Folgendes:<br /><br /> 01s00, 01s01, 01s02, 01s06, 01s07, 07s01, 08s01, 21s01, 21s02, 25s01, 25s02, 25s03, 42s01, 42s02, 42s11, 42s12, 42s21, 42s22, HY095, HY097, HY098, HY099, HY100, HY101, HY105, HY107, HY109, HY110, HY111, HYT00, HYT01, IM001, IM002, IM003, IM004, IM005, IM006, IM007, IM008, IM010, IM011, IM012.|  
  
## <a name="values-of-the-dynamic-function-fields"></a>Werte der dynamischen Funktionsfelder  
 In der folgenden Tabelle werden die Werte SQL_DIAG_DYNAMIC_FUNCTION und SQL_DIAG_DYNAMIC_FUNCTION_CODE beschrieben, die für jeden Typ der SQL-Anweisung gelten, die durch einen-Befehl von **SQLExecute** oder **SQLExecDirect**ausgeführt wird. Der Treiber kann den aufgelisteten Treiber definierte Werte hinzufügen.  
  
|SQL-Anweisung<br /><br /> richteten|Wert von <br /><br /> SQL_DIAG_DYNAMIC_FUNCTION|Wert von <br /><br /> SQL_DIAG_DYNAMIC_FUNCTION_CODE|  
|--------------------------------|-----------------------------------------------|-----------------------------------------------------|  
|*Alter-Domain-Statement*|"Alter Domain"|SQL_DIAG_ALTER_DOMAIN|  
|*ALTER-TABLE-Statement*|"ALTER TABLE"|SQL_DIAG_ALTER_TABLE|  
|*Assert-Definition*|"Assert erstellen"|SQL_DIAG_CREATE_ASSERTION|  
|*Zeichensatz Definition*|"Zeichensatz erstellen"|SQL_DIAG_CREATE_CHARACTER_SET|  
|*Sortierungs Definition*|"Sortierung erstellen"|SQL_DIAG_CREATE_COLLATION|  
|*domainn-Definition*|"Domäne erstellen"|SQL_DIAG_CREATE_DOMAIN|
|*CREATE-INDEX-Anweisung*|"Index erstellen"|SQL_DIAG_CREATE_INDEX|  
|*CREATE-TABLE-Anweisung*|"CREATE TABLE"|SQL_DIAG_CREATE_TABLE|  
|*CREATE-VIEW-Anweisung*|"Ansicht erstellen"|SQL_DIAG_CREATE_VIEW|  
|*Cursor Spezifikation*|"Cursor auswählen"|SQL_DIAG_SELECT_CURSOR|  
|*DELETE-Statement-positioniert*|"dynamischer Lösch Cursor"|SQL_DIAG_DYNAMIC_DELETE_CURSOR|  
|*DELETE-Statement-durchsucht*|"DELETE WHERE"|SQL_DIAG_DELETE_WHERE|  
|*Drop-Assert-Anweisung*|"Drop Assert"|SQL_DIAG_DROP_ASSERTION|  
|*Drop-Character-Set-stmt*|"Drop Character Set"|SQL_DIAG_DROP_CHARACTER_SET|  
|*Drop-COLLATIONS-Anweisung*|"Sortierung löschen"|SQL_DIAG_DROP_COLLATION|  
|*Drop-Domain-Statement*|"Drop Domain"|SQL_DIAG_DROP_DOMAIN|  
|*DROP-INDEX-Anweisung*|"Drop Index"|SQL_DIAG_DROP_INDEX|  
|*Drop-Schema-Anweisung*|"Drop Schema"|SQL_DIAG_DROP_SCHEMA|  
|*DROP-TABLE-Anweisung*|"DROP TABLE"|SQL_DIAG_DROP_TABLE|  
|*Drop-Translation-Anweisung*|"Drop Translation"|SQL_DIAG_DROP_TRANSLATION|  
|*DROP-VIEW-Anweisung*|"Drop View"|SQL_DIAG_DROP_VIEW|  
|*grantstatement*|Schusses|SQL_DIAG_GRANT|
|*INSERT-Anweisung*|Setze|SQL_DIAG_INSERT|  
|*ODBC-Procedure-Extension*|Erfordern|SQL_DIAG_-Aufrufe|  
|*Widerruf-Anweisung*|Erteilte|SQL_DIAG_REVOKE|  
|*Schema Definition*|"Schema erstellen"|SQL_DIAG_CREATE_SCHEMA|  
|*Übersetzungs Definition*|"Create Translation"|SQL_DIAG_CREATE_TRANSLATION|  
|*Update-Anweisungs positioniert*|"Cursor für dynamisches Update"|SQL_DIAG_DYNAMIC_UPDATE_CURSOR|  
|*Update-Anweisung wurde durchsucht*|"Update where"|SQL_DIAG_UPDATE_WHERE|  
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

 Status Datensätze werden in einer Sequenz positioniert, die auf der Zeilennummer und dem Typ der Diagnose basiert. Der Treiber-Manager bestimmt die endgültige Reihenfolge, in der die von ihm generierten Statusdaten Sätze zurückgegeben werden. Der Treiber bestimmt die endgültige Reihenfolge, in der die von ihm generierten Statusdaten Sätze zurückgegeben werden.  
  
 Wenn Diagnosedaten Sätze sowohl vom Treiber-Manager als auch vom Treiber gesendet werden, ist der Treiber-Manager für die Bestellung verantwortlich.  
  
 Wenn zwei oder mehr Statusdaten Sätze vorhanden sind, wird die Reihenfolge der Datensätze zuerst anhand der Zeilennummer bestimmt. Die folgenden Regeln gelten für die Bestimmung der Reihenfolge der Diagnosedaten Sätze nach Zeilen:  
  
-   Datensätze, die keiner Zeile entsprechen, werden vor Datensätzen angezeigt, die einer bestimmten Zeile entsprechen, da SQL_NO_ROW_NUMBER als-1 definiert ist.  
  
-   Datensätze, für die die Zeilennummer unbekannt ist, werden vor allen anderen Datensätzen angezeigt, weil SQL_ROW_NUMBER_UNKNOWN als-2 definiert ist.  
  
-   Für alle Datensätze, die bestimmte Zeilen betreffen, werden Datensätze nach dem Wert im Feld SQL_DIAG_ROW_NUMBER sortiert. Alle Fehler und Warnungen der ersten betroffenen Zeile werden aufgelistet, und es werden alle Fehler und Warnungen der nächsten Zeile angezeigt usw.  
  
> [!NOTE]
>  Der ODBC 3 *. x* -Treiber-Manager sortiert keine Statusdaten Sätze in der Diagnose Warteschlange, wenn SQLSTATE 01s01 (Fehler in Zeile) von ODBC 2 zurückgegeben wird *. der x* -Treiber oder, wenn SQLSTATE 01s01 (Fehler in Zeile) von einem ODBC 3 *. x* -Treiber zurückgegeben wird, wenn **SQLExtendedFetch** aufgerufen wird, oder wenn **SQLSetPos** für einen Cursor aufgerufen wird, der mit **SQLExtendedFetch**positioniert wurde.  
  
 Innerhalb jeder Zeile oder für alle Datensätze, die keiner Zeile entsprechen oder für die die Zeilennummer unbekannt ist, oder für alle Datensätze mit einer Zeilennummer, die SQL_NO_ROW_NUMBER entspricht, wird der erste aufgeführte Datensatz mithilfe eines Satzes von Sortierregeln bestimmt. Nach dem ersten Datensatz ist die Reihenfolge der anderen Datensätze, die sich auf eine Zeile auswirken, nicht definiert. Eine Anwendung kann nicht davon ausgehen, dass vor Warnungen nach dem ersten Datensatz Fehler auftreten. Anwendungen sollten die gesamte Diagnosedaten Struktur Scannen, um umfassende Informationen über einen erfolglosen Funktions aufzurufen.  
  
 Die folgenden Regeln werden verwendet, um den ersten Datensatz innerhalb einer Zeile zu bestimmen. Der Datensatz mit dem höchsten Rang ist der erste Datensatz. Die Quelle eines Datensatzes (Treiber-Manager, Treiber, Gateway usw.) wird bei der Rangfolge von Datensätzen nicht berücksichtigt.  
  
-   **Fehler** Status Datensätze, in denen Fehler beschrieben werden, haben den höchsten Rang. Die folgenden Regeln gelten für Sortier Fehler:  
  
    -   Datensätze, die auf einen Transaktionsfehler oder einen möglichen Transaktionsfehler hinweisen, überstehen alle anderen Datensätze.  
  
    -   Wenn zwei oder mehr Datensätze denselben Fehlerzustand beschreiben, wird Sqlstates durch die Open Group CLI-Spezifikation (Klassen 03 bis Hz) über ODBC-und Treiber definierte Sqlstates durchgesetzt.  
  
-   Von der **Implementierung definierte Datenwerte** Status Datensätze, die vom Treiber definierte No-Data-Werte (Klasse 02) beschreiben, haben den zweiten höchsten Rang.  
  
-   **Warnungen** Status Datensätze, die Warnungen (Class 01) beschreiben, haben den niedrigsten Rang. Wenn zwei oder mehr Datensätze dieselbe Warnungs Bedingung beschreiben, dann wird die Warnung Sqlstates, die von der Open Group CLI-Spezifikation definiert wird, für ODBC-definierte und Treiber definierte Sqlstates angezeigt.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abrufen mehrerer Felder einer Diagnosedaten Struktur|[SQLGetDiagRec-Funktion](sqlgetdiagrec-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
