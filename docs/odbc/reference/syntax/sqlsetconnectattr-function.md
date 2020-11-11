---
description: SQLSetConnectAttr-Funktion
title: SQLSetConnectAttr-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConnectAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectAttr
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC]
ms.assetid: 97fc7445-5a66-4eb9-8e77-10990b5fd685
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0e6e3e9722510b7a1a563de8546b2e4190696e10
ms.sourcegitcommit: 3bde506b2fa3bc82813dbe658d567b1b9eb4278b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94498453"
---
# <a name="sqlsetconnectattr-function"></a>SQLSetConnectAttr-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0 Standards Compliance: ISO 92  
  
 **Zusammenfassung**  
 **SQLSetConnectAttr** legt Attribute fest, die die Aspekte von Verbindungen steuern.  
  
> [!NOTE]
>  Weitere Informationen dazu, wie der Treiber-Manager diese Funktion zuordnet, wenn eine ODBC 3 *. x* -Anwendung mit einem ODBC 2 *. x* -Treiber arbeitet, finden Sie unterzuordnen [von Ersetzungs Funktionen für die Abwärtskompatibilität von Anwendungen](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLSetConnectAttr(  
     SQLHDBC       ConnectionHandle,  
     SQLINTEGER    Attribute,  
     SQLPOINTER    ValuePtr,  
     SQLINTEGER    StringLength);  
```  
  
## <a name="arguments"></a>Argumente  
 *ConnectionHandle*  
 [Eingabe] Verbindungshandle.  
  
 *Attribut*  
 Der Das festzulegende Attribut, aufgelistet in "comments".  
  
 *ValuePtr*  
 Der Zeiger auf den Wert, der dem *Attribut* zugeordnet werden soll. Abhängig vom Wert des *Attributs* ist *ValuePtr* ein ganzzahliger Wert ohne Vorzeichen oder zeigt auf eine mit NULL endende Zeichenfolge. Beachten Sie, dass der ganzzahlige Typ des *Attribut* Arguments möglicherweise nicht eine festgelegte Länge hat. Einzelheiten finden Sie im Abschnitt "Kommentare".  
  
 *StringLength*  
 Der Wenn *Attribute* ein ODBC-definiertes Attribut ist und *ValuePtr* auf eine Zeichenfolge oder einen binären Puffer zeigt, sollte dieses Argument die Länge von * *ValuePtr* aufweisen. Für Zeichen folgen Daten sollte dieses Argument die Anzahl der Bytes in der Zeichenfolge enthalten.  
  
 Wenn *Attribute* ein ODBC-definiertes Attribut und *ValuePtr* eine ganze Zahl ist, wird *StringLength* ignoriert.  
  
 Wenn *Attribute* ein Treiber definiertes Attribut ist, gibt die Anwendung die Art des Attributs für den Treiber-Manager an, indem das *StringLength* -Argument festgelegt wird. *StringLength* kann die folgenden Werte aufweisen:  
  
-   Wenn *ValuePtr* ein Zeiger auf eine Zeichenfolge ist, ist *StringLength* die Länge der Zeichenfolge oder SQL_NTS.  
  
-   Wenn *ValuePtr* ein Zeiger auf einen binären Puffer ist, platziert die Anwendung das Ergebnis des SQL_LEN_BINARY_ATTR ( *length* )-Makros in *StringLength*. Dadurch wird ein negativer Wert in *StringLength* platziert.  
  
-   Wenn *ValuePtr* ein Zeiger auf einen anderen Wert als eine Zeichenfolge oder eine binäre Zeichenfolge ist, sollte *StringLength* den Wert SQL_IS_POINTER haben.  
  
-   Wenn *ValuePtr* einen Wert mit fester Länge enthält, ist *StringLength* entweder SQL_IS_INTEGER oder SQL_IS_UINTEGER.  
  
## <a name="returns"></a>Gibt zurück  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE oder SQL_STILL_EXECUTING.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLSetConnectAttr** SQL_ERROR oder SQL_SUCCESS_WITH_INFO zurückgibt, kann ein zugeordneter SQLSTATE-Wert durch Aufrufen von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_DBC und einem *handle* von *connectionHandle* abgerufen werden. In der folgenden Tabelle werden die SQLSTATE-Werte aufgelistet, die häufig von **SQLSetConnectAttr** zurückgegeben werden, und die einzelnen Werte werden im Kontext dieser Funktion erläutert. die Notation "(DM)" geht vor den Beschreibungen von Sqlstates vor, die vom Treiber-Manager zurückgegeben werden. Der Rückgabecode, der den einzelnen SQLSTATE-Werten zugeordnet ist, ist SQL_ERROR, sofern nichts anderes angegeben ist.  
  
 Der Treiber kann SQL_SUCCESS_WITH_INFO zurückgeben, um Informationen zum Ergebnis der Einstellung einer Option bereitzustellen.  
  
|SQLSTATE|Fehler|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|01000|Allgemeine Warnung|Treiber spezifische Informations Meldung. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|01s02 entsprechen|Optionswert geändert|Der Treiber hat den in *ValuePtr* angegebenen Wert nicht unterstützt und ersetzt einen ähnlichen Wert. (Die Funktion gibt SQL_SUCCESS_WITH_INFO zurück.)|  
|08002|Der Verbindungs Name wird verwendet.|Das *Attribut* Argument wurde SQL_ATTR_ODBC_CURSORS, und der Treiber war bereits mit der Datenquelle verbunden.|  
|08003|Verbindung nicht geöffnet|(DM) ein *Attribut* Wert wurde angegeben, der eine geöffnete Verbindung erforderte, aber *connectionHandle* befand sich nicht in einem verbundenen Zustand.|  
|08S01|Kommunikations Verbindungsfehler|Die Kommunikationsverbindung zwischen dem Treiber und der Datenquelle, mit der der Treiber verbunden war, ist fehlgeschlagen, bevor die Funktion die Verarbeitung abgeschlossen hat.|  
|24.000|Ungültiger Cursorstatus|Das *Attribut* Argument wurde SQL_ATTR_CURRENT_CATALOG, und ein Resultset war ausstehend.|  
|25000|Ungültiger Vorgang in einer lokalen Transaktion.|Eine Verbindung befand sich in einer lokalen Transaktion beim Eintragen in eine DTC-Verbindung (DTC), indem das Verbindungs Attribut SQL_ATTR_ENLIST_IN_DTC festgelegt wurde.<br /><br /> Eine Verbindung ist bereits in einem DTC eingetragen.<br /><br /> Eine Verbindung wurde in eine verteilte Transaktions Verbindung eingetragen, und eine lokale Transaktion wurde gestartet, indem SQL_ATTR_AUTOCOMMIT auf SQL_AUTOCOMMIT_OFF festgelegt wurde.|  
|3D000|Ungültiger Katalog Name.|Das *Attribut* Argument wurde SQL_CURRENT_CATALOG, und der angegebene Katalog Name war ungültig.|  
|HY000|Allgemeiner Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer SQLSTATE vorhanden war und für den kein Implementierungs spezifischer SQLSTATE definiert wurde. Die von **SQLGetDiagRec** im *\* MessageText* -Puffer zurückgegebene Fehlermeldung beschreibt den Fehler und die Ursache.|  
|HY001|Fehler bei der Speicher Belegung|Der Treiber konnte keinen Arbeitsspeicher zuweisen, der zur Unterstützung der Ausführung oder Beendigung der Funktion erforderlich ist.|  
|HY008|Vorgang abgebrochen|Die asynchrone Verarbeitung wurde für *connectionHandle* aktiviert. Die **SQLSetConnectAttr** -Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde die [sqlcancelhandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) für *connectionHandle* aufgerufen, und anschließend wurde die **SQLSetConnectAttr** -Funktion für *connectionHandle* erneut aufgerufen.<br /><br /> Oder die  **SQLSetConnectAttr** -Funktion wurde aufgerufen, und vor Abschluss der Ausführung wurde **sqlcancelhandle** für *connectionHandle* von einem anderen Thread in einer Multithread-Anwendung aufgerufen.|  
|HY009|Ungültige Verwendung des NULL-Zeigers|Das *Attribut* Argument hat ein Verbindungs Attribut identifiziert, das einen Zeichen folgen Wert erforderte, und das *ValuePtr* -Argument war ein NULL-Zeiger.|  
|HY010|Funktions Sequenz Fehler|(DM) eine asynchron ausgeführte Funktion wurde für ein *StatementHandle* aufgerufen, das dem *connectionHandle* zugeordnet ist, und wurde noch ausgeführt, als **SQLSetConnectAttr** aufgerufen wurde.<br /><br /> (DM) eine asynchron ausgeführte Funktion (nicht diese) wurde für *connectionHandle* aufgerufen und ausgeführt, als diese Funktion aufgerufen wurde.<br /><br /> (DM) **SQLExecute** , **SQLExecDirect** oder **SQLMoreResults** wurde für eines der Anweisungs Handles aufgerufen, die dem *connectionHandle* zugeordnet sind, und SQL_PARAM_DATA_AVAILABLE zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle gestreuten Parameter abgerufen wurden.<br /><br /> (DM) **SQLExecute** , **SQLExecDirect** , **SQLBulkOperations** oder **SQLSetPos** wurde für ein *StatementHandle* aufgerufen, das dem *connectionHandle* zugeordnet ist, und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor Daten für alle Data-at-Execution-Parameter oder-Spalten gesendet wurden.<br /><br /> (DM) **sqlbrowseconnetct** wurde für *connectionHandle* aufgerufen und SQL_NEED_DATA zurückgegeben. Diese Funktion wurde aufgerufen, bevor **sqlbrowseconnct** SQL_SUCCESS_WITH_INFO oder SQL_SUCCESS zurückgegeben hat.|  
|HY011|Das Attribut kann jetzt nicht festgelegt werden|Das *Attribut* Argument wurde SQL_ATTR_TXN_ISOLATION, und eine Transaktion war geöffnet.|  
|HY013|Speicher Verwaltungsfehler|Der Funktions Aufrufwert konnte nicht verarbeitet werden, da auf die zugrunde liegenden Speicher Objekte nicht zugegriffen werden konnte, möglicherweise aufgrund von wenig Arbeitsspeicher.|  
|HY024|Ungültiger Attribut Wert|Bei Angabe des angegebenen *Attribut* Werts wurde in *ValuePtr* ein ungültiger Wert angegeben. (Der Treiber-Manager gibt diesen SQLSTATE nur für Verbindungs-und Anweisungs Attribute zurück, die einen diskreten Satz von Werten akzeptieren, z. b. SQL_ATTR_ACCESS_MODE oder SQL_ATTR_ASYNC_ENABLE. Für alle anderen Verbindungs-und Anweisungs Attribute muss der Treiber den in *ValuePtr* angegebenen Wert überprüfen.)<br /><br /> Das *Attribut* Argument war SQL_ATTR_TRACEFILE oder SQL_ATTR_TRANSLATE_LIB, und *ValuePtr* war eine leere Zeichenfolge.|  
|HY090|Ungültige Zeichen folgen-oder Pufferlänge|*(DM) \* ValuePtr* ist eine Zeichenfolge, und das *StringLength* -Argument war kleiner als 0 (null), war aber nicht SQL_NTS.|  
|HY092|Ungültiger Attribut/Options Bezeichner|(DM) der für das Argument *Attribut* angegebene Wert war für die vom Treiber unterstützte ODBC-Version ungültig.<br /><br /> (DM) der für das Argument *Attribut* angegebene Wert war ein Schreib geschütztes Attribut.|  
|HY114|Der Treiber unterstützt keine asynchrone Funktions Ausführung auf Verbindungs Ebene.|(DM) eine Anwendung hat versucht, die asynchrone Funktions Ausführung mit SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE für einen Treiber zu aktivieren, der asynchrone Verbindungs Vorgänge nicht unterstützt.|  
|HY117|Die Verbindung wurde aufgrund eines unbekannten Transaktions Zustands angehalten. Nur Disconnect-und Read-Only-Funktionen sind zulässig.|(DM) Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HY121|Die Cursor Bibliothek und das Driver-Aware Pooling können nicht gleichzeitig aktiviert werden.|Weitere Informationen finden Sie unter [Treiber fähiges Verbindungs Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|HYC00|Optionales Feature nicht implementiert|Der für das Argument- *Attribut* angegebene Wert war ein gültiges ODBC-Verbindungs-oder-Anweisungs Attribut für die Version von ODBC, die vom Treiber unterstützt, jedoch nicht vom Treiber unterstützt wurde.|  
|HYT01|Verbindungs Timeout abgelaufen|Der Verbindungs Timeout Zeitraum ist abgelaufen, bevor die Datenquelle auf die Anforderung geantwortet hat. Der Timeout Zeitraum für die Verbindung wird über **SQLSetConnectAttr** , SQL_ATTR_CONNECTION_TIMEOUT festgelegt.|  
|IM001|Der Treiber unterstützt diese Funktion nicht.|(DM) der dem *connectionHandle* zugeordnete Treiber unterstützt die-Funktion nicht.|  
|IM009|Übersetzungs-DLL kann nicht geladen werden.|Der Treiber war nicht in der Lage, die für die Verbindung angegebene Übersetzungs-DLL zu laden. Dieser Fehler kann nur zurückgegeben werden, wenn das *Attribut* SQL_ATTR_TRANSLATE_LIB ist.|  
|IM017|Der Abruf ist im asynchronen Benachrichtigungs Modus deaktiviert.|Wenn das Benachrichtigungs Modell verwendet wird, ist das Abrufen deaktiviert.|  
|IM018|**Sqlcompleteasync** wurde nicht aufgerufen, um den vorherigen asynchronen Vorgang für dieses Handle abzuschließen.|Wenn der vorherige Funktionsaufruf für das Handle SQL_STILL_EXECUTING zurückgibt und der Benachrichtigungs Modus aktiviert ist, muss **sqlcompleteasync** für das Handle aufgerufen werden, um die Nachbearbeitung auszuführen und den Vorgang abzuschließen.|  
|S1118|Der Treiber unterstützt keine asynchrone Benachrichtigung.|SQL_ATTR_ASYNC_DBC_EVENT wurde festgelegt (nachdem die Verbindung hergestellt wurde), aber die asynchrone Benachrichtigung wird vom Treiber nicht unterstützt.|  
  
 Wenn *Attribute* ein Anweisungs Attribut ist, kann **SQLSetConnectAttr** alle von **SQLSetStmtAttr** zurückgegebenen Sqlstates zurückgeben.  
  
## <a name="comments"></a>Kommentare  
 Allgemeine Informationen zu Verbindungs Attributen finden Sie unter [Verbindungs Attribute](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Die aktuell definierten Attribute und die Version von ODBC, in der Sie eingeführt wurden, werden in der Tabelle weiter unten in diesem Abschnitt angezeigt. Es wird erwartet, dass mehr Attribute definiert werden, um unterschiedliche Datenquellen zu nutzen. Ein Bereich von Attributen wird von ODBC reserviert. Treiber Entwickler müssen Werte für Ihre eigene Treiber spezifische Verwendung in der geöffneten Gruppe reservieren.  
  
> [!NOTE]
>  Die Möglichkeit, Anweisungs Attribute auf Verbindungs Ebene durch Aufrufen von **SQLSetConnectAttr** festzulegen, wurde in ODBC 3 *. x* als veraltet markiert. ODBC 3 *. x* -Anwendungen sollten nie Anweisungs Attribute auf Verbindungs Ebene festlegen. ODBC 3 *. x* -Anweisungs Attribute können nicht auf Verbindungs Ebene festgelegt werden, mit Ausnahme der Attribute "SQL_ATTR_METADATA_ID" und "SQL_ATTR_ASYNC_ENABLE", bei denen es sich um Verbindungs Attribute und Anweisungs Attribute handelt und die entweder auf der Verbindungs Ebene oder auf der Anweisungs Ebene festgelegt werden können.  
> 
>  ODBC 3 *. x* -Treiber müssen diese Funktionalität nur unterstützen, wenn Sie mit ODBC 2 *. x* -Anwendungen arbeiten sollten, die ODBC 2 *. x* -Anweisungs Optionen auf Verbindungs Ebene festlegen. Weitere Informationen finden Sie unter [SQLSetConnectOption-Zuordnung](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) in Anhang G: Treiber Richtlinien für Abwärtskompatibilität.  
  
 Eine Anwendung kann **SQLSetConnectAttr** jederzeit zwischen dem Zeitpunkt, zu dem die Verbindung zugeordnet und freigegeben wird, aufrufen. Alle Verbindungs-und Anweisungs Attribute, die von der Anwendung für die Verbindung erfolgreich festgelegt wurden, bleiben erhalten, bis **SQLFreeHandle** für die Verbindung aufgerufen wird. Wenn eine Anwendung z. b. **SQLSetConnectAttr** aufruft, bevor eine Verbindung mit einer Datenquelle hergestellt wird, bleibt das Attribut auch dann erhalten, wenn **SQLSetConnectAttr** im Treiber ausfällt, wenn die Anwendung eine Verbindung mit der Datenquelle herstellt. Wenn eine Anwendung ein Treiber spezifisches Attribut festlegt, bleibt das Attribut auch dann erhalten, wenn die Anwendung eine Verbindung mit einem anderen Treiber für die Verbindung herstellt.  
  
 Einige Verbindungs Attribute können nur festgelegt werden, bevor eine Verbindung hergestellt wurde. andere können erst festgelegt werden, nachdem eine Verbindung hergestellt wurde. In der folgenden Tabelle sind die Verbindungs Attribute angegeben, die entweder vor oder nach dem Herstellen einer Verbindung festgelegt werden müssen. Gibt *entweder* an, dass das Attribut entweder vor oder nach der Verbindung festgelegt werden kann.  
  
|attribute|Wird vor oder nach der Verbindung festgelegt?|  
|---------------|-------------------------------------|  
|SQL_ATTR_ACCESS_MODE|Entweder [1]|  
|SQL_ATTR_ASYNC_DBC_EVENT|Sowohl als auch|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE|Entweder [4]|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK|Sowohl als auch|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT|Sowohl als auch|  
|SQL_ATTR_ASYNC_ENABLE|Entweder [2]|  
|SQL_ATTR_AUTO_IPD|Sowohl als auch|  
|SQL_ATTR_AUTOCOMMIT|Entweder [5]|  
|SQL_ATTR_CONNECTION_DEAD|Nach|  
|SQL_ATTR_CONNECTION_TIMEOUT|Sowohl als auch|  
|SQL_ATTR_CURRENT_CATALOG|Entweder [1]|  
|SQL_ATTR_DBC_INFO_TOKEN|Nach|  
|SQL_ATTR_ENLIST_IN_DTC|Nach|  
|SQL_ATTR_LOGIN_TIMEOUT|Vorher|  
|SQL_ATTR_METADATA_ID|Sowohl als auch|  
|SQL_ATTR_ODBC_CURSORS|Vorher|  
|SQL_ATTR_PACKET_SIZE|Vorher|  
|SQL_ATTR_QUIET_MODE|Sowohl als auch|  
|SQL_ATTR_TRACE|Sowohl als auch|  
|SQL_ATTR_TRACEFILE|Sowohl als auch|  
|SQL_ATTR_TRANSLATE_LIB|Nach|  
|SQL_ATTR_TRANSLATE_OPTION|Nach|  
|SQL_ATTR_TXN_ISOLATION|Entweder [3]|  
  
 [1] SQL_ATTR_ACCESS_MODE und SQL_ATTR_CURRENT_CATALOG können vor oder nach dem Herstellen der Verbindung festgelegt werden, abhängig vom Treiber. Allerdings werden von interoperablen Anwendungen diese vor der Verbindungs Herstellung festgelegt, da einige Treiber das Ändern dieser nach der Verbindung nicht unterstützen.  
  
 [2] SQL_ATTR_ASYNC_ENABLE muss festgelegt werden, bevor eine aktive Anweisung vorhanden ist.  
  
 [3] SQL_ATTR_TXN_ISOLATION kann nur festgelegt werden, wenn keine geöffneten Transaktionen für die Verbindung vorhanden sind. Einige Verbindungs Attribute unterstützen die Ersetzung eines ähnlichen Werts, wenn die Datenquelle den in \* *ValuePtr* angegebenen Wert nicht unterstützt. In solchen Fällen gibt der Treiber SQL_SUCCESS_WITH_INFO und SQLSTATE 01s02 (Optionswert geändert) zurück. Wenn das *Attribut* beispielsweise SQL_ATTR_PACKET_SIZE und \* *ValuePtr* die maximale Paketgröße überschreitet, ersetzt der Treiber die maximale Größe. Um den ersetzten Wert zu bestimmen, ruft eine Anwendung **SQLGetConnectAttr** auf.  
  
 [4] Wenn SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE festgelegt wird, bevor eine Verbindung geöffnet ist, legt der Treiber-Manager das-Attribut des Treibers fest, wenn der Treiber während eines Aufladens von **sqlbrowseconnetct** , **SQLCONNECT** oder **SQLDriverConnect** geladen wird. Vor einem **sqlbrowseconnetct** -, **SQLCONNECT** -oder **SQLDriverConnect** -Befehl weiß der Treiber-Manager nicht, mit welchem Treiber eine Verbindung hergestellt werden soll, und weiß nicht, ob der Treiber asynchrone Verbindungs Vorgänge unterstützt. Daher gibt der Treiber-Manager immer SQL_SUCCESS zurück. Wenn der Treiber jedoch keine asynchronen Verbindungs Vorgänge unterstützt, schlägt der **sqlbrowseconnetct** -, **SQLCONNECT** -oder **SQLDriverConnect** -Befehl fehl.  
  
 [5] Wenn SQL_ATTR_AUTOCOMMIT auf false festgelegt ist, sollten Anwendungen SQLEndTran (SQL_ROLLBACK) aufzurufen, wenn eine API SQL_ERROR zurückgibt, um die Transaktions Konsistenz sicherzustellen.  
  
 Das Format der Informationen, die im \* *ValuePtr* -Puffer festgelegt sind, hängt vom angegebenen *Attribut* ab. **SQLSetConnectAttr** akzeptiert Attributinformationen in einem von zwei verschiedenen Formaten: einer null-terminierten Zeichenfolge oder einem ganzzahligen Wert. Das Format der einzelnen wird in der Beschreibung des Attributs angegeben. Zeichen folgen, auf die vom *ValuePtr* -Argument von **SQLSetConnectAttr** verwiesen wird, haben eine Länge von *StringLength* bytes.  
  
 Das *StringLength* -Argument wird ignoriert, wenn die Länge durch das-Attribut definiert ist, wie dies bei allen Attributen der Fall ist, die in ODBC 2 *. x* oder früher eingeführt wurden.  
  
|*Attribut*|*ValuePtr* -Inhalt|  
|-----------------|-------------------------|  
|SQL_ATTR_ACCESS_MODE (ODBC 1,0)|Ein SQLUINTEGER-Wert. SQL_MODE_READ_ONLY wird vom Treiber oder der Datenquelle als Indikator verwendet, dass die Verbindung nicht erforderlich ist, um SQL-Anweisungen zu unterstützen, die zu Updates führen. Dieser Modus kann verwendet werden, um Sperr Strategien, Transaktions Verwaltung oder andere Bereiche entsprechend dem Treiber oder der Datenquelle zu optimieren. Der Treiber ist nicht erforderlich, um zu verhindern, dass solche Anweisungen an die Datenquelle übermittelt werden. Das Verhalten des Treibers und der Datenquelle, wenn Sie aufgefordert werden, SQL-Anweisungen zu verarbeiten, die während einer schreibgeschützten Verbindung nicht schreibgeschützt sind, wird durch die Implementierung definiert. SQL_MODE_READ_WRITE ist die Standardeinstellung.|  
|SQL_ATTR_ASYNC_DBC_EVENT (ODBC 3,8)|Ein SQLPOINTER-Wert, der ein Ereignis Handle ist.<br /><br /> Die Benachrichtigung über den Abschluss von asynchronen Funktionen wird durch Aufrufen von **SQLSetConnectAttr** mit dem SQL_ATTR_ASYNC_STMT_EVENT-Attribut und durch Angeben des Ereignis Handles aktiviert. **Hinweis:**  Die Benachrichtigungs Methode wird mit der Cursor Bibliothek nicht unterstützt. Eine Anwendung empfängt eine Fehlermeldung, wenn Sie versucht, die Cursor Bibliothek über SQLSetConnectAttr zu aktivieren, wenn die Benachrichtigungs Methode aktiviert ist.|  
|SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE (ODBC 3,8)|Ein SQLUINTEGER-Wert, der die asynchrone Ausführung ausgewählter Funktionen für das Verbindungs Handle aktiviert oder deaktiviert. Weitere Informationen finden Sie unter [asynchrone Ausführung (Abruf Methode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md).<br /><br /> SQL_ASYNC_DBC_ENABLE_ON = asynchroner Vorgang für angegebene verbindungsbezogene Funktionen aktivieren.<br /><br /> SQL_ASYNC_DBC_ENABLE_OFF = (Standard) deaktivieren Sie den asynchronen Vorgang für angegebene verbindungsbezogene Funktionen.<br /><br /> Das Festlegen von SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE ist immer synchron (d. h., es wird nie SQL_STILL_EXECUTING zurückgegeben).<br /><br /> Die asynchrone Ausführung von Anweisungs Vorgängen wird mit SQL_ATTR_ASYNC_ENABLE aktiviert.|  
|SQL_ATTR_ASYNC_DBC_PCALLBACK (ODBC 3,8)|Ein SQLPOINTER-Wert, der auf die Kontext Struktur zeigt.<br /><br /> Nur der Treiber-Manager kann die **SQLSetStmtAttr** -Funktion eines Treibers mit diesem Attribut aufrufen.|  
|SQL_ATTR_ASYNC_DBC_PCONTEXT (ODBC 3,8)|Ein SQLPOINTER-Wert, der auf die Kontext Struktur zeigt.<br /><br /> Nur der Treiber-Manager kann die **SQLSetStmtAttr** -Funktion eines Treibers mit diesem Attribut aufrufen.|  
|SQL_ATTR_ASYNC_ENABLE (ODBC 3,0)|Ein SQLULEN-Wert, der angibt, ob eine Funktion, die mit einer-Anweisung für die angegebene Verbindung aufgerufen wurde, asynchron ausgeführt wird:<br /><br /> SQL_ASYNC_ENABLE_OFF = asynchrone Ausführungs Unterstützung auf Verbindungs Ebene für Anweisungs Vorgänge (Standard) deaktivieren.<br /><br /> SQL_ASYNC_ENABLE_ON = asynchrone Ausführungs Unterstützung auf Verbindungs Ebene für Anweisungs Vorgänge aktivieren.<br /><br /> Dieses Attribut kann festgelegt werden, ob **SQLGetInfo** mit dem SQL_ASYNC_MODE Informationstyp SQL_AM_CONNECTION oder SQL_AM_STATEMENT zurückgibt.|  
|SQL_ATTR_AUTO_IPD (ODBC 3,0)|Ein Schreib geschützter SQLUINTEGER-Wert, der angibt, ob die automatische Auffüllung der IPD nach einem **SQLPrepare** -Befehl unterstützt wird:<br /><br /> SQL_TRUE = die automatische Auffüllung der IPD nach einem **SQLPrepare** -Auffüllung wird vom Treiber unterstützt.<br /><br /> SQL_FALSE = die automatische Auffüllung der IPD nach einem **SQLPrepare** -Auffüllung wird vom Treiber nicht unterstützt. Server, die vorbereitete Anweisungen nicht unterstützen, können die IPD nicht automatisch auffüllen.<br /><br /> Wenn SQL_TRUE für das SQL_ATTR_AUTO_IPD Connection-Attribut zurückgegeben wird, kann das Anweisungs Attribut SQL_ATTR_ENABLE_AUTO_IPD festgelegt werden, um die automatische Auffüllung der IPD zu aktivieren oder zu deaktivieren. Wenn SQL_ATTR_AUTO_IPD SQL_FALSE ist, kann SQL_ATTR_ENABLE_AUTO_IPD nicht auf SQL_TRUE festgelegt werden. Der Standardwert von SQL_ATTR_ENABLE_AUTO_IPD ist gleich dem Wert von SQL_ATTR_AUTO_IPD.<br /><br /> Dieses Verbindungs Attribut kann von **SQLGetConnectAttr** zurückgegeben werden, kann jedoch nicht von **SQLSetConnectAttr** festgelegt werden.|  
|SQL_ATTR_AUTOCOMMIT (ODBC 1,0)|Ein SQLUINTEGER-Wert, der angibt, ob der Autocommit-Modus oder der manuelle Commitmodus verwendet werden soll:<br /><br /> SQL_AUTOCOMMIT_OFF = der Treiber verwendet den manuellen Commit-Modus, und die Anwendung muss mit **SQLEndTran** explizit ein Commit oder ein Rollback für Transaktionen ausführen.<br /><br /> SQL_AUTOCOMMIT_ON = der Treiber verwendet den Autocommit-Modus. Für jede-Anweisung wird unmittelbar nach der Ausführung ein Commit ausgeführt. Dies ist die Standardoption. Für alle geöffneten Transaktionen der Verbindung wird ein Commit ausgeführt, wenn SQL_ATTR_AUTOCOMMIT auf SQL_AUTOCOMMIT_ON festgelegt ist, um vom manuellen Commitmodus in den Autocommit-Modus zu wechseln.<br /><br /> Weitere Informationen finden Sie unter [Commit-Modus](../../../odbc/reference/develop-app/commit-mode.md). **Wichtig:**  Einige Datenquellen löschen die Zugriffs Pläne und schließen die Cursor für alle Anweisungen über eine Verbindung, wenn ein Commit für eine-Anweisung ausgeführt wird. der Autocommit-Modus kann dazu führen, dass die Anweisung nicht ausgeführt wird, oder wenn der Cursor für eine Abfrage geschlossen wird. Weitere Informationen finden Sie in den SQL_CURSOR_COMMIT_BEHAVIOR-und SQL_CURSOR_ROLLBACK_BEHAVIOR-Informationstypen in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) und [Auswirkung von Transaktionen auf Cursor und vorbereitete Anweisungen](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md). <br /><br /> Wenn ein Batch im Autocommit-Modus ausgeführt wird, sind zwei Dinge möglich. Der gesamte Batch kann als eine automatisch commitbare Einheit behandelt werden, oder jede Anweisung in einem Batch wird als eine automatisch commitbare Einheit behandelt. Bestimmte Datenquellen unterstützen beide diese Verhaltensweisen und können eine Möglichkeit zum Auswählen eines oder eines anderen darstellen. Es ist Treiber definiert, ob ein Batch als eine automatisch commitbare Einheit behandelt wird oder ob jede einzelne Anweisung innerhalb des Batches autocommitfähig ist.|  
|SQL_ATTR_CONNECTION_DEAD<br /><br /> (ODBC 3,5)|Ein Schreib geschützter SQLUINTEGER-Wert, der den Status der Verbindung angibt. Wenn SQL_CD_TRUE, ist die Verbindung verloren gegangen. Wenn SQL_CD_FALSE, ist die Verbindung noch aktiv.|  
|SQL_ATTR_CONNECTION_TIMEOUT (ODBC 3,0)|Ein SQLUINTEGER-Wert, der der Anzahl der Sekunden entspricht, die auf den Abschluss einer Anforderung der Verbindung gewartet werden soll, bevor Sie an die Anwendung zurückgegeben wird. Der Treiber sollte SQLSTATE HYT00 (Timeout abgelaufen) immer dann zurückgeben, wenn es möglich ist, einen Timeout in einer Situation zu haben, die nicht mit der Abfrage Ausführung oder der Anmeldung verknüpft ist.<br /><br /> Wenn *ValuePtr* gleich 0 (Standard) ist, gibt es kein Timeout.|  
|SQL_ATTR_CURRENT_CATALOG (ODBC 2,0)|Eine Zeichenfolge mit dem Namen des Katalogs, der von der Datenquelle verwendet werden soll. In SQL Server ist der Katalog beispielsweise eine Datenbank, sodass der Treiber eine **use** _Database_ -Anweisung an die Datenquelle sendet, wobei *Database* die in \* *ValuePtr* angegebene Datenbank ist. Bei einem einzelnen-Ebenen-Treiber kann der Katalog ein Verzeichnis sein, sodass der Treiber das aktuelle Verzeichnis in das in * *ValuePtr* angegebene Verzeichnis ändert.|  
|SQL_ATTR_DBC_INFO_TOKEN (ODBC 3,8|Ein SQLPOINTER-Wert, der verwendet wird, um das Verbindungs Informations Token in das DBC-handle zurückzusetzen, wenn der Parameter [sqlrateconnetction](../../../odbc/reference/syntax/sqlrateconnection-function.md)( \* *prating* ) nicht gleich 100 ist.<br /><br /> SQL_ATTR_DBC_INFO_TOKEN ist nur festgelegt. Zum Abrufen dieses Werts ist es nicht möglich, **SQLGetConnectAttr** oder **SQLGetConnectOption** zu verwenden. **SQLSetConnectAttr** des Treiber-Managers akzeptiert SQL_ATTR_DBC_INFO_TOKEN nicht, da diese Attribut von einer Anwendung nicht festgelegt werden sollte.<br /><br /> Wenn ein Treiber SQL_ERROR zurückgibt, nachdem er SQL_ATTR_DBC_INFO_TOKEN festgelegt hat, wird die soeben aus dem Pool erhaltene Verbindung freigegeben. Der Treiber-Manager versucht dann, eine weitere Verbindung aus dem Pool zu erhalten. Weitere Informationen finden Sie [unter Entwickeln von Connection-Pool Awareness in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md) .|  
|SQL_ATTR_ENLIST_IN_DTC (ODBC 3,0)|Ein SQLPOINTER-Wert, der angibt, ob der ODBC-Treiber in verteilten Transaktionen verwendet werden soll, die von Microsoft-Komponenten Diensten koordiniert werden.<br /><br /> Übergeben Sie ein DTC OLE Transaction-Objekt, das die Transaktion angibt, die in SQL Server exportiert werden soll, oder SQL_DTC_DONE, um die DTC-Zuordnung der Verbindung zu beenden.<br /><br /> Der Client ruft die OLE-Methode von Microsoft Distributed Transaction Coordinator (MS DTC) OLE itransaktiondispenser:: BeginTransaction auf, um eine MS DTC-Transaktion zu starten und ein MS DTC-Transaktions Objekt zu erstellen, das die Transaktion darstellt. Die Anwendung ruft dann SQLSetConnectAttr mit der SQL_ATTR_ENLIST_IN_DTC-Option auf, um das Transaktions Objekt der ODBC-Verbindung zuzuordnen. Alle entsprechenden Datenbankaktivitäten werden unter dem Schutz der MS DTC-Transaktion durchgeführt. Die Anwendung ruft SQLSetConnectAttr mit SQL_DTC_DONE auf, um die DTC-Zuordnung der Verbindung zu beenden. Weitere Informationen finden Sie in der MS DTC-Dokumentation.|  
|SQL_ATTR_LOGIN_TIMEOUT (ODBC 1,0)|Ein SQLUINTEGER-Wert, der der Anzahl der Sekunden entspricht, die auf den Abschluss einer Anmelde Anforderung gewartet werden soll, bevor Sie an die Anwendung zurückgegeben wird. Der Standardwert ist Treiber abhängig. Wenn *ValuePtr* den Wert 0 hat, ist das Timeout deaktiviert, und ein Verbindungsversuch wartet unbegrenzt.<br /><br /> Wenn das angegebene Timeout den maximalen Anmeldungs Timeout in der Datenquelle überschreitet, ersetzt der Treiber diesen Wert und gibt SQLSTATE 01s02 (Optionswert geändert) zurück.|  
|SQL_ATTR_METADATA_ID (ODBC 3,0)|Ein SQLUINTEGER-Wert, der bestimmt, wie die Zeichen folgen Argumente von Katalog Funktionen behandelt werden.<br /><br /> Wenn SQL_TRUE, wird das Zeichen folgen Argument der Katalog Funktionen als Bezeichner behandelt. Die Groß-/Kleinschreibung ist nicht signifikant. Bei nicht durch Trennzeichen getrennten Zeichen folgen entfernt der Treiber alle nachfolgenden Leerzeichen, und die Zeichenfolge wird in Großbuchstaben gefaltet. Beim durch Trennzeichen getrennten Zeichen folgen entfernt der Treiber alle führenden oder nachfolgenden Leerzeichen und nimmt buchstäblich die gleichen zwischen den Trennzeichen auf. Wenn eines der Argumente auf einen NULL-Zeiger festgelegt ist, gibt die Funktion SQL_ERROR und SQLSTATE HY009 zurück (Ungültige Verwendung des NULL-Zeigers).<br /><br /> Wenn SQL_FALSE, werden die Zeichen folgen Argumente von Katalog Funktionen nicht als Bezeichner behandelt. Der Fall ist wichtig. Abhängig vom-Argument können Sie entweder ein Muster für die Zeichen folgen Suche oder nicht enthalten.<br /><br /> Der Standardwert ist SQL_FALSE.<br /><br /> Das *TABLETYPE* -Argument von **SQLTables** , das eine Liste von Werten annimmt, ist von diesem Attribut nicht betroffen.<br /><br /> SQL_ATTR_METADATA_ID können auch auf Anweisungs Ebene festgelegt werden. (Es ist das einzige Verbindungs Attribut, bei dem es sich auch um ein Anweisungs Attribut handelt.)<br /><br /> Weitere Informationen finden Sie unter [Argumente in Katalog Funktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).|  
|SQL_ATTR_ODBC_CURSORS (ODBC 2,0)|Ein SQLULEN-Wert, der angibt, wie der Treiber-Manager die ODBC-Cursor Bibliothek verwendet:<br /><br /> SQL_CUR_USE_IF_NEEDED = der Treiber-Manager verwendet die ODBC-Cursor Bibliothek nur, wenn Sie benötigt wird. Wenn der Treiber die Option SQL_FETCH_PRIOR in **SQLFetchScroll** unterstützt, verwendet der Treiber-Manager die scrollfunktionen des Treibers. Andernfalls wird die ODBC-Cursor Bibliothek verwendet.<br /><br /> SQL_CUR_USE_ODBC = der Treiber-Manager verwendet die ODBC-Cursor Bibliothek.<br /><br /> SQL_CUR_USE_DRIVER = der Treiber-Manager verwendet die scrollfunktionen des Treibers. Dies ist die Standardeinstellung.<br /><br /> Weitere Informationen zur ODBC-Cursor Bibliothek finden Sie unter [Anhang F: ODBC-Cursor Bibliothek](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md). **Warnung:**  Die Cursor Bibliothek wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.|  
|SQL_ATTR_PACKET_SIZE (ODBC 2,0)|Ein SQLUINTEGER-Wert, der die Netzwerk Paketgröße in Bytes angibt. **Hinweis:**  Viele Datenquellen unterstützen diese Option nicht, oder Sie können nur die Netzwerk Paketgröße zurückgeben, jedoch nicht festlegen. <br /><br /> Wenn die angegebene Größe die maximale Paketgröße überschreitet oder kleiner ist als die minimale Paketgröße, ersetzt der Treiber diesen Wert und gibt SQLSTATE 01s02 (Optionswert geändert) zurück.<br /><br /> Wenn die Anwendung die Paketgröße festlegt, nachdem bereits eine Verbindung hergestellt wurde, gibt der Treiber SQLSTATE HY011 zurück (das Attribut kann jetzt nicht festgelegt werden).|  
|SQL_ATTR_QUIET_MODE (ODBC 2,0)|Ein Fenster Handle (HWND).<br /><br /> Wenn das Fenster Handle ein NULL-Zeiger ist, zeigt der Treiber keine Dialogfelder an.<br /><br /> Wenn das Fenster Handle kein NULL-Zeiger ist, sollte es das übergeordnete Fenster Handle der Anwendung sein. Dies ist die Standardoption. Der Treiber verwendet dieses Handle zum Anzeigen von Dialogfeldern. **Hinweis:**  Das SQL_ATTR_QUIET_MODE Verbindungs Attribut gilt nicht für Dialogfelder, die von **SQLDriverConnect** angezeigt werden.|  
|SQL_ATTR_TRACE (ODBC 1,0)|Ein SQLUINTEGER-Wert, der dem Treiber-Manager mitteilt, ob die Ablauf Verfolgung durchgeführt<br /><br /> SQL_OPT_TRACE_OFF = Ablauf Verfolgung deaktiviert (Standard)<br /><br /> SQL_OPT_TRACE_ON = Ablauf Verfolgung auf<br /><br /> Wenn die Ablauf Verfolgung aktiviert ist, schreibt der Treiber-Manager jeden ODBC-Funktionsaufrufe in die Ablauf Verfolgungs Datei. **Hinweis:**  Wenn die Ablauf Verfolgung aktiviert ist, kann der Treiber-Manager SQLSTATE IM013 (Fehler bei der Ablauf Verfolgungs Datei) von jeder Funktion zurückgeben. <br /><br /> Eine Anwendung gibt eine Ablauf Verfolgungs Datei mit der SQL_ATTR_TRACEFILE-Option an. Wenn die Datei bereits vorhanden ist, fügt der Treiber-Manager die Datei an. Andernfalls wird die Datei erstellt. Wenn die Ablauf Verfolgung aktiviert ist und keine Ablauf Verfolgungs Datei angegeben wurde, schreibt der Treiber-Manager in die SQL-Datei. Melden Sie sich im Stammverzeichnis an.<br /><br /> Eine Anwendung kann die Variable **odbcsharedtraceflag** festlegen, um die Ablauf Verfolgung dynamisch zu aktivieren. Die Ablauf Verfolgung wird dann für alle derzeit laufenden ODBC-Anwendungen aktiviert. Wenn eine Anwendung die Ablauf Verfolgung deaktiviert, wird Sie nur für diese Anwendung deaktiviert.<br /><br /> Wenn das **Trace** -Schlüsselwort in den Systeminformationen auf 1 festgelegt ist, wenn eine Anwendung **sqlzuordchandle** mit einem Handlertyp von SQL_HANDLE_ENV aufruft, wird die Ablauf Verfolgung für alle Handles aktiviert. *HandleType* Er ist nur für die Anwendung aktiviert, die **sqlzugewiesene CHandle** aufgerufen hat.<br /><br /> Das Aufrufen von **SQLSetConnectAttr** mit dem SQL_ATTR_TRACE- *Attribut* erfordert nicht, dass das *connectionHandle* -Argument gültig ist und keine SQL_ERROR zurückgibt, wenn *connectionHandle* NULL ist. Dieses Attribut gilt für alle Verbindungen.|  
|SQL_ATTR_TRACEFILE (ODBC 1,0)|Eine mit NULL endenden Zeichenfolge, die den Namen der Ablauf Verfolgungs Datei enthält.<br /><br /> Der Standardwert des SQL_ATTR_TRACEFILE Attributs wird in den Systeminformationen mit dem **Tracefile** -Schlüsselwort angegeben. Weitere Informationen finden Sie [unter ODBC-Unterschlüssel](../../../odbc/reference/install/odbc-subkey.md).<br /><br /> Beim Aufrufen von **SQLSetConnectAttr** mit dem- *Attribut* SQL_ATTR_TRACEFILE muss das *connectionHandle* -Argument nicht gültig sein, und es wird SQL_ERROR nicht zurückgegeben, wenn *connectionHandle* ungültig ist. Dieses Attribut gilt für alle Verbindungen.|  
|SQL_ATTR_TRANSLATE_LIB (ODBC 1,0)|Eine auf NULL endenden Zeichenfolge, die den Namen einer Bibliothek mit den Funktionen **sqldriverdedatasource** und **sqldatasourcededriver** enthält, auf die der Treiber zugreift, um Aufgaben wie die Zeichensatz Übersetzung auszuführen. Diese Option kann nur angegeben werden, wenn der Treiber eine Verbindung mit der Datenquelle hergestellt hat. Die Einstellung dieses Attributs wird über mehrere Verbindungen hinweg beibehalten. Weitere Informationen zum Übersetzen von Daten finden Sie unter [Translation DLLs](../../../odbc/reference/develop-app/translation-dlls.md) und [Translation dll-Funktionsreferenz](../../../odbc/reference/syntax/translation-dll-api-reference.md).|  
|SQL_ATTR_TRANSLATE_OPTION (ODBC 1,0)|Ein 32-Bit-Flagwert, der an die Konvertierungs-DLL übermittelt wird. Dieses Attribut kann nur angegeben werden, wenn der Treiber eine Verbindung mit der Datenquelle hergestellt hat. Weitere Informationen zum Übersetzen von Daten finden Sie unter [Translation DLLs](../../../odbc/reference/develop-app/translation-dlls.md).|  
|SQL_ATTR_TXN_ISOLATION (ODBC 1,0)|Eine 32-Bit-Bitmaske, die die Transaktions Isolationsstufe für die aktuelle Verbindung festlegt. Eine Anwendung muss **SQLEndTran** aufrufen, um einen Commit oder Rollback für alle geöffneten Transaktionen in einer Verbindung auszuführen, bevor **SQLSetConnectAttr** mit dieser Option aufgerufen wird.<br /><br /> Die gültigen Werte für *ValuePtr* können durch Aufrufen von **SQLGetInfo** mit dem *InfoType* -Wert SQL_TXN_ISOLATION_OPTIONS bestimmt werden.<br /><br /> Eine Beschreibung der Transaktions Isolations Stufen finden Sie in der Beschreibung des SQL_DEFAULT_TXN_ISOLATION-Informations Typs in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) und [Transaktions Isolations Stufen](../../../odbc/reference/develop-app/transaction-isolation-levels.md).|  
  
 [1] diese Funktionen können nur dann asynchron aufgerufen werden, wenn es sich bei dem Deskriptor um einen Implementierungs Deskriptor, nicht um einen Anwendungs Deskriptor handelt.  
  
## <a name="code-example"></a>Codebeispiel  
 Siehe [SQLCONNECT](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zuordnen eines Handles|[SQLAllocHandle-Funktion](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Zurückgeben der Einstellung eines Verbindungs Attributs|[SQLGetConnectAttr-Funktion](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
