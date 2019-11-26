---
title: SQLSetStmtAttr | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSetStmtAttr function
ms.assetid: 799c80fd-c561-4912-8562-9229076dfd19
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fc7744d57ce2bdbad4f0000252999582a8dc37c2
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73785523"
---
# <a name="sqlsetstmtattr"></a>SQLSetStmtAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt das gemischte Cursormodell (keysetgesteuert/dynamisch) nicht. Der Versuch, die Keysetgröße mit SQL_ATTR_KEYSET_SIZE festzulegen, schlägt fehl, wenn der festgelegte Wert ungleich 0 (null) ist.  
  
 Die Anwendung legt SQL_ATTR_ROW_ARRAY_SIZE für alle-Anweisungen fest, um die Anzahl der für einen **SQLFetch** -oder [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) -Funktionsaufrufs zurückgegebenen Zeilen zu deklarieren. Bei Anweisungen, die einen Servercursor angeben, verwendet der Treiber SQL_ATTR_ROW_ARRAY_SIZE, um die Größe des Zeilenblocks zu ermitteln, der vom Server als Reaktion auf eine Abrufanforderung des Cursors generiert wird. Innerhalb der Blockgröße eines dynamischen Cursors sind die Zeilenmitgliedschaft und -reihenfolge festgelegt, wenn die Isolationsstufe der Transaktion ausreichend ist, um wiederholbare Lesevorgänge von Transaktionen sicherzustellen, für die ein Commit ausgeführt wurde. Der Cursor ist außerhalb des von diesem Wert angegebenen Blocks vollkommen dynamisch. Die Blockgröße des Servercursors ist vollkommen dynamisch und kann zu jedem Zeitpunkt während der Abrufverarbeitung geändert werden.  
  
## <a name="sqlsetstmtattr-and-table-valued-parameters"></a>'SQLSetStmtAttr' und Tabellenwertparameter  
 SQLSetStmtAttr kann verwendet werden, um SQL_SOPT_SS_PARAM_FOCUS im Anwendungsparameter Deskriptor (Application Parameter Deskriptor, APD) vor dem Zugriff auf Deskriptorfelder für Tabellenwert Parameter-Spalten festzulegen.  
  
 Wenn versucht wird, SQL_SOPT_SS_PARAM_FOCUS auf die Ordnungszahl eines Parameters festzulegen, bei dem es sich nicht um einen Tabellenwert Parameter handelt, gibt SQLSetStmtAttr SQL_ERROR zurück, und es wird ein Diagnosedaten Satz mit SQLSTATE = HY024 und der Meldung "Ungültiger Attribut Wert" erstellt. SQL_SOPT_SS_PARAM_FOCUS wird nicht geändert, wenn SQL_ERROR zurückgegeben wird.  
  
 Durch das Festlegen von SQL_SOPT_SS_PARAM_FOCUS auf 0 (null) wird der Zugriff auf Deskriptordatensätze für Parameter wiederhergestellt.  
  
 SQLSetStmtAttr kann auch verwendet werden, um SQL_SOPT_SS_NAME_SCOPE festzulegen. Weitere Informationen finden Sie im Abschnitt zu SQL_SOPT_SS_NAME_SCOPE weiter unten in diesem Thema.  
  
 Weitere Informationen finden Sie unter [Tabellenwert Parameter-Metadaten für vorbereitete Anweisungen](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md).  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie unter [Tabellenwert Parameter &#40;(ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)).  
  
## <a name="sqlsetstmtattr-support-for-sparse-columns"></a>Unterstützung von 'SQLSetStmtAttr' für Spalten mit geringer Dichte  
 SQLSetStmtAttr kann verwendet werden, um SQL_SOPT_SS_NAME_SCOPE festzulegen. Weitere Informationen finden Sie im Abschnitt SQL_SOPT_SS_NAME_SCOPE weiter unten in diesem Thema. Weitere Informationen zu sparsespalten finden Sie [unter unter &#40;Stützung&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)für Spalten mit geringer Dichte.  
  
## <a name="statement-attributes"></a>Anweisungsattribute  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt auch die folgenden treiberspezifischen Anweisungsattribute.  
  
### <a name="sql_sopt_ss_cursor_options"></a>SQL_SOPT_SS_CURSOR_OPTIONS  
 Das SQL_SOPT_SS_CURSOR-Attribut gibt an, ob der Treiber treiberspezifische Leistungsoptionen für Cursor verwendet. [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) ist nicht zulässig, wenn diese Optionen festgelegt sind. Die Standardeinstellung ist SQL_CO_OFF. Der *ValuePtr* -Wert ist vom Typ SQLLEN.  
  
|*ValuePtr* -Wert|und Beschreibung|  
|----------------------|-----------------|  
|SQL_CO_OFF|Standard. Deaktiviert schnelle Vorwärts Cursor, schreibgeschützte Cursor und automatische Abruf Vorgänge und ermöglicht **SQLGetData** bei schreibgeschützten Vorwärts Cursor. Wenn SQL_SOPT_SS_CURSOR_OPTIONS auf SQL_CO_OFF festgelegt ist, ändert sich der Cursortyp nicht. Das heißt, ein schneller Vorwärtscursor bleibt ein schneller Vorwärtscursor. Um den Cursortyp zu ändern, muss die Anwendung nun mithilfe von **SQLSetStmtAttr**/SQL_ATTR_CURSOR_TYPE einen anderen Cursortyp festlegen.|  
|SQL_CO_FFO|Aktiviert schnelle Vorwärts Cursor, schreibgeschützte Cursor, deaktiviert **SQLGetData** bei schreibgeschützten Vorwärts Cursor.|  
|SQL_CO_AF|Aktiviert die automatische Abrufoption für jeden Cursortyp. Wenn diese Option für ein Anweisungs Handle festgelegt wird, generiert **SQLExecute** oder **SQLExecDirect** einen impliziten **SQLFetchScroll** (SQL_FIRST). Der Cursor wird geöffnet, und der erste Batch Zeilen wird mit einem einzigen Roundtrip an den Server zurückgegeben.|  
|SQL_CO_FFO_AF|Aktiviert schnelle Vorwärtscursor mit der automatischen Abrufoption. Das entspricht der gleichzeitigen Angabe von SQL_CO_AF und SQL_CO_FFO.|  
  
 Wenn diese Optionen festgelegt sind, schließt der Server den Cursor automatisch, wenn er erkennt, dass die letzte Zeile abgerufen wurde. Die Anwendung muss weiterhin [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) (SQL_CLOSE) oder [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)abrufen, aber der Treiber muss die Close-Benachrichtigung nicht an den Server senden.  
  
 Wenn die SELECT-Liste eine **Text**-, **ntext**-oder **Image** -Spalte enthält, wird der schnelle Vorwärts Cursor in einen dynamischen Cursor konvertiert, und **SQLGetData** ist zulässig.  
  
### <a name="sql_sopt_ss_defer_prepare"></a>SQL_SOPT_SS_DEFER_PREPARE  
 Das SQL_SOPT_SS_DEFER_PREPARE-Attribut bestimmt, ob die Anweisung sofort vorbereitet oder verzögert wird, bis **SQLExecute**, [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) oder [SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md) ausgeführt wird. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 und früheren Versionen wird diese Eigenschaft ignoriert (die Vorbereitung nicht verzögert). Der *ValuePtr* -Wert ist vom Typ SQLLEN.  
  
|*ValuePtr* -Wert|und Beschreibung|  
|----------------------|-----------------|  
|SQL_DP_ON|Standard. Nach dem Aufruf der [SQLPrepare-Funktion](https://go.microsoft.com/fwlink/?LinkId=59360)wird die Anweisungs Vorbereitung verzögert, bis **SQLExecute** aufgerufen oder der Metaeigenschaftsvorgang (**SQLDescribeCol** oder **SQLDescribeParam**) ausgeführt wird.|  
|SQL_DP_OFF|Die-Anweisung wird vorbereitet, sobald **SQLPrepare** ausgeführt wird.|  
  
### <a name="sql_sopt_ss_regionalize"></a>SQL_SOPT_SS_REGIONALIZE  
 Das SQL_SOPT_SS_REGIONALIZE-Attribut wird verwendet, um die Datenkonvertierung auf Anweisungsebene zu bestimmen. Das Attribut bewirkt, dass der Treiber bei der Konvertierung von Datums-, Uhrzeit- und Währungswerten in Zeichenfolgen die Gebietsschemaeinstellung des Clients beachtet. Die Konvertierung erfolgt lediglich von systemeigenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen in Zeichenfolgen.  
  
 Der *ValuePtr* -Wert ist vom Typ SQLLEN.  
  
|*ValuePtr* -Wert|und Beschreibung|  
|----------------------|-----------------|  
|SQL_RE_OFF|Standard. Der Treiber konvertiert Datums-, Uhrzeit- und Währungsdaten nicht gemäß der Gebietsschemaeinstellung des Clients in Zeichenfolgendaten.|  
|SQL_RE_ON|Der Treiber konvertiert Datums-, Uhrzeit- und Währungsdaten gemäß der Gebietsschemaeinstellung des Clients in Zeichenfolgendaten.|  
  
 Regionale Konvertierungseinstellungen gelten für Währungs-, Zahlen-, Datums- und Uhrzeitdatentypen. Die Konvertierungseinstellungen gelten nur für Ausgabekonvertierungen, wenn Währungs-, Zahlen-, Datums- oder Uhrzeitwerte in Zeichenfolgen konvertiert werden.  
  
> [!NOTE]  
>  Wenn die SQL_SOPT_SS_REGIONALIZE-Anweisungsoption aktiviert ist, verwendet der Treiber die lokalen Registrierungseinstellungen für den aktuellen Benutzer. Der Treiber berücksichtigt das Gebiets Schema des aktuellen Threads nicht, wenn es von der Anwendung festgelegt wird, z. b. durch Aufrufen von **SetThreadLocale**.  
  
 Das Verändern des regionalen Verhaltens einer Datenquelle kann Anwendungsfehler verursachen. Eine Anwendung, die Datumszeichenfolgen analysiert und erwartet, dass sie der ODBC-Definition entsprechen, wird durch die Änderung dieses Werts möglicherweise beeinträchtigt.  
  
### <a name="sql_sopt_ss_textptr_logging"></a>SQL_SOPT_SS_TEXTPTR_LOGGING  
 Das SQL_SOPT_SS_TEXTPTR_LOGGING-Attribut schaltet die Protokollierung von Vorgängen für Spalten ein, die **Text** -oder **Bilddaten** enthalten. Der *ValuePtr* -Wert ist vom Typ SQLLEN.  
  
|*ValuePtr* -Wert|und Beschreibung|  
|----------------------|-----------------|  
|SQL_TL_OFF|Deaktiviert die Protokollierung von Vorgängen, die für **Text** -und **Bilddaten** ausgeführt werden.|  
|SQL_TL_ON|Standard. Ermöglicht die Protokollierung von Vorgängen für **Text** -und **Bilddaten** .|  
  
### <a name="sql_sopt_ss_hidden_columns"></a>SQL_SOPT_SS_HIDDEN_COLUMNS  
 Das SQL_SOPT_SS_HIDDEN_COLUMNS-Attribut macht Spalten im Resultset verfügbar, die in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-SELECT FOR BROWSE-Anweisung verborgen sind. Der Treiber macht diese Spalten standardmäßig nicht verfügbar. Der *ValuePtr* -Wert ist vom Typ SQLLEN.  
  
|*ValuePtr* -Wert|und Beschreibung|  
|----------------------|-----------------|  
|SQL_HC_OFF|Standard. FOR BROWSE-Spalten werden aus dem Resultset ausgeblendet.|  
|SQL_HC_ON|Macht FOR BROWSE-Spalten verfügbar.|  
  
### <a name="sql_sopt_ss_querynotification_msgtext"></a>SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 Das SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT-Attribut gibt den Meldungstext für die Abfragebenachrichtigungsanforderung zurück.  
  
### <a name="sql_sopt_ss_querynotification_options"></a>SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS  
 Das SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS-Attribut gibt die Optionen an, die für die Abfragebenachrichtigungsanforderung verwendet werden. Diese werden in einer Zeichenfolge mit der Syntax `name=value` angegeben (siehe Code weiter unten). Die Anwendung ist für das Erstellen des Diensts und Lesen von Benachrichtigungen von der Warteschlange verantwortlich.  
  
 Die Syntax der Zeichenfolge für die Abfragebenachrichtigungsoptionen lautet:  
  
 `service=<service-name>[;(local database=<database>|broker instance=<broker instance>)]`  
  
 Zum Beispiel:  
  
 `service=mySSBService;local database=mydb`  
  
### <a name="sql_sopt_ss_querynotification_timeout"></a>SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT  
 Das SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT-Attribut gibt die Dauer (in Sekunden) an, für die die Abfragebenachrichtigung aktiv bleiben soll. Der Standardwert lautet 432.000 Sekunden (5 Tage). Der *ValuePtr* -Wert ist vom Typ SQLLEN.  
  
### <a name="sql_sopt_ss_param_focus"></a>SQL_SOPT_SS_PARAM_FOCUS  
 Das SQL_SOPT_SS_PARAM_FOCUS-Attribut gibt den Fokus für nachfolgende SQLBindParameter-, SQLGetDescField-, SQLSetDescField-, SQLGetDescRec-und SQLSetDescRec-Aufrufe an.  
  
 Der Typ für SQL_SOPT_SS_PARAM_FOCUS lautet SQLULEN.  
  
 Der Standardwert ist 0 (null). Das bedeutet, dass diese Aufrufe sich an Parameter richten, die Parametermarkierungen in der SQL-Anweisung entsprechen. Wenn diese Aufrufe auf die Parameternummer eines Tabellenwertparameters festgelegt sind, adressieren sie Spalten dieses Tabellenwertparameters. Wenn sie auf einen anderen Wert als die Parameternummer eines Tabellenwertparameters festgelegt sind, geben diese Aufrufe den Fehler IM020 zurück: "Parameterfokus verweist nicht auf einen Tabellenwertparameter."  
  
### <a name="sql_sopt_ss_name_scope"></a>SQL_SOPT_SS_NAME_SCOPE  
 Das SQL_SOPT_SS_NAME_SCOPE-Attribut gibt den Namensbereich für nachfolgende Katalogfunktionsaufrufe an. Das Resultset, das von SQLColumns zurückgegeben wird, hängt von der Einstellung SQL_SOPT_SS_NAME_SCOPE ab.  
  
 Der Typ für SQL_SOPT_SS_NAME_SCOPE lautet SQLULEN.  
  
|*ValuePtr* -Wert|und Beschreibung|  
|----------------------|-----------------|  
|SQL_SS_NAME_SCOPE_TABLE|Standard.<br /><br /> Gibt bei Verwendung von Tabellenwertparametern an, dass Metadaten für tatsächliche Tabellen zurückgegeben werden sollen.<br /><br /> Wenn Sie die Funktion für sparsespalten verwenden, gibt SQLColumns nur Spalten zurück, die keine Elemente des **column_set**mit geringer Dichte sind.|  
|SQL_SS_NAME_SCOPE_TABLE_TYPE|Gibt an, dass die Anwendung Metadaten für einen Tabellentyp anstatt einer tatsächlichen Tabelle erfordert (Katalogfunktionen sollten Metadaten für Tabellentypen zurückgeben). Die Anwendung übergibt dann den TYPE_NAME des Tabellenwert Parameters als *TableName* -Parameter.|  
|SQL_SS_NAME_SCOPE_EXTENDED|Wenn Sie die Funktion für sparsespalten verwenden, gibt SQLColumns unabhängig von der **column_set** Mitgliedschaft alle Spalten zurück.|  
|SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET|Wenn die Funktion für sparsespalten verwendet wird, gibt SQLColumns nur Spalten zurück, die Elemente der **column_set**mit geringer Dichte sind.|  
|SQL_SS_NAME_SCOPE_DEFAULT|Identisch mit SQL_SS_NAME_SCOPE_TABLE|  
  
 SS_TYPE_CATALOG_NAME und SS_TYPE_SCHEMA_NAME werden mit *den Parametern* *CatalogName* bzw. Schema Name verwendet, um den Katalog und das Schema für den Tabellenwert Parameter zu identifizieren. Wenn eine Anwendung das Abrufen von Metadaten für Tabellenwertparameter abgeschlossen hat, muss sie SQL_SOPT_SS_NAME_SCOPE wieder auf den Standardwert SQL_SS_NAME_SCOPE_TABLE festlegen.  
  
 Wenn SQL_SOPT_SS_NAME_SCOPE auf SQL_SS_NAME_SCOPE_TABLE festgelegt ist, schlagen Abfragen von Verbindungsservern fehl. Aufrufe von SQLColumns oder SQLPrimaryKeys mit einem Katalog, der eine Serverkomponente enthält, schlagen fehl.  
  
 Wenn Sie versuchen, SQL_SOPT_SS_NAME_SCOPE auf einen ungültigen Wert festzulegen, wird SQL_ERROR zurückgegeben. Zudem wird ein Diagnosedatensatz mit SQLSTATE HY024 und der Meldung "Ungültiger Attributwert" generiert.  
  
 Wenn eine andere Katalog Funktion als SQLTables, SQLColumns oder SQLPrimaryKeys aufgerufen wird, wenn SQL_SOPT_SS_NAME_SCOPE einen anderen Wert als SQL_SS_NAME_SCOPE_TABLE aufweist, wird SQL_ERROR zurückgegeben. Ein Diagnosedatensatz mit SQLSTATE HY010 und der Meldung "Fehler in der Funktionsreihenfolge (SQL_SOPT_SS_NAME_SCOPE ist nicht auf SQL_SS_NAME_SCOPE_TABLE festgelegt)" wird generiert.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLGetStmtAttr-Funktion](https://go.microsoft.com/fwlink/?LinkId=59355)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
