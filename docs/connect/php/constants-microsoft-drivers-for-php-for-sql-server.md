---
title: Konstanten (Microsoft-Treiber für PHP für SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- constants
ms.assetid: 9727c944-b645-48d6-9012-18dbde35ee3c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 82fa4ef2f47143afe8f2331469a1eb07fd9b2522
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66796225"
---
# <a name="constants-microsoft-drivers-for-php-for-sql-server"></a>Konstanten (Microsoft-Treiber für PHP für SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In diesem Thema werden die Konstanten erläutert, die durch [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]definiert sind.  
  
## <a name="pdosqlsrv-driver-constants"></a>Konstanten zum Treiber PDO_SQLSRV  
Die Konstanten, die auf der [PDO-Website](https://php.net/manual/book.pdo.php) aufgeführt sind, gelten in [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
Im Folgenden werden die Microsoft-spezifischen Konstanten im PDO_SQLSRV-Treiber beschrieben.  
  
### <a name="transaction-isolation-level-constants"></a>Konstanten der Transaktionsisolationsebene  
Der **TransactionIsolation** -Schlüssel, der mit [PDO::__construct](../../connect/php/pdo-construct.md)verwendet wird, akzeptiert eine der folgenden Konstanten:  
  
-   PDO::SQLSRV_TXN_READ_UNCOMMITTED  
  
-   PDO::SQLSRV_TXN_READ_COMMITTED  
  
-   PDO::SQLSRV_TXN_REPEATABLE_READ  
  
-   PDO::SQLSRV_TXN_SNAPSHOT  
  
-   PDO::SQLSRV_TXN_SERIALIZABLE  
  
Weitere Informationen zum **TransactionIsolation** -Schlüssel finden Sie unter [Connection Options](../../connect/php/connection-options.md).  
  
### <a name="encoding-constants"></a>Codierungskonstanten  
Das PDO::SQLSRV_ATTR_ENCODING-Attribut kann an [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md), [PDO::setAttribut](../../connect/php/pdo-setattribute.md)e, [PDO::prepare](../../connect/php/pdo-prepare.md), [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md) und [PDOStatement::bindParam](../../connect/php/pdostatement-bindparam.md) übergeben werden.  
  
Die verfügbaren Werte, die an PDO::SQLSRV_ATTR_ENCODING übergeben werden können, sind  
  
|Konstanten zum Treiber PDO_SQLSRV|und Beschreibung|  
|-------------------------------|---------------|  
|PDO::SQLSRV_ENCODING_BINARY|Die Daten sind ein einfacher, uncodierter und nicht übersetzter Strom aus unbearbeiteten Bytes.<br /><br />Dies gilt nicht für PDO::setAttribute.|  
|PDO::SQLSRV_ENCODING_SYSTEM|Daten stellen 8-Bit-Zeichen gemäß der Codepage des im System eingestellten Windows-Gebietsschemas dar. Alle Multi-Byte-Zeichen oder Zeichen, die nicht in dieser Codepage enthalten sind, werden durch ein aus einem einzelnen Byte bestehendes Fragezeichen (?) ersetzt.|  
|PDO::SQLSRV_ENCODING_UTF8|Daten sind in UTF-8-Codierung. Diese ist die Standardcodierung.|  
|PDO::SQLSRV_ENCODING_DEFAULT|Verwendet PDO::SQLSRV_ENCODING_SYSTEM, wenn bei der Verbindung angegeben.<br /><br />Verwenden Sie die Codierung der Verbindung, wenn diese in einer Prepare-Anweisung angegeben ist.|  
  
### <a name="query-timeout"></a>Abfragetimeout  
Das PDO::SQLSRV_ATTR_QUERY_TIMEOUT-Attribut ist eine beliebige positive ganze Zahl, die das Timeout in Sekunden darstellt. Null (0) ist die Standardeinstellung und bedeutet kein Timeout.  
  
Sie können das PDO::SQLSRV_ATTR_QUERY_TIMEOUT-Attribut mit [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md), [PDO::setAttribute](../../connect/php/pdo-setattribute.md) und [PDO::prepare](../../connect/php/pdo-prepare.md) angeben.  
  
### <a name="direct-or-prepared-execution"></a>Direkte oder vorbereitete Ausführung  
Sie können die Ausführung von direkten Abfragen oder die vorbereitete Ausführung mit dem Attribut PDO::SQLSRV_ATTR_DIRECT_QUERY auswählen. PDO::SQLSRV_ATTR_DIRECT_QUERY kann mit [PDO::prepare](../../connect/php/pdo-prepare.md) oder [PDO::setAttribute](../../connect/php/pdo-setattribute.md) festgelegt werden. Weitere Informationen zu PDO::SQLSRV_ATTR_DIRECT_QUERY finden Sie unter [Direkte Anweisungsausführung und vorbereitete Anweisungsausführung im PDO_SQLSRV-Treiber](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).  

### <a name="handling-numeric-fetches"></a>Behandeln von numerischen abruft
Das PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE-Attribut kann verwendet werden, numerischen Abrufe aus Spalten mit numerischen SQL-Typen (Bit, Integer, Smallint, Tinyint, Float und Real) behandelt. Wenn PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE festgelegt ist, auf "true", die Ergebnisse aus einer Spalte mit ganzen Zahlen dargestellt als int-Typen, während SQL gleitet und versendeten als Gleitkommawerte dargestellt werden. Dieses Attribut kann festgelegt werden, mit [pdostatement:: setAttribute](../../connect/php/pdostatement-setattribute.md). 

Sie können die Dezimalstellen formatieren Standardverhalten mit den Attributen PDO::SQLSRV_ATTR_FORMAT_DECIMALS und PDO::SQLSRV_ATTR_DECIMAL_PLACES ändern. Das Verhalten dieser Attribute ist identisch mit den entsprechenden Optionen auf der Seite SQLSRV (**FormatDecimals** und **DecimalPlaces**), außer dass die Ausgabe-Parameter für das Formatieren nicht unterstützt werden. Diese Attribute festgelegt werden können, auf die Verbindung oder -Anweisung mit [PDO:: setAttribute](../../connect/php/pdo-setattribute.md) oder [pdostatement:: setAttribute](../../connect/php/pdostatement-setattribute.md), jedoch wird Anweisungsattribut überschreiben Sie die entsprechenden -Verbindungsattribut. Weitere Details finden Sie unter [Formatieren von Dezimalzeichenfolgen und Geldwerten (PDO_SQLSRV-Treiber)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).

### <a name="handling-date-and-time-fetches"></a>Handhabung von Fetches für Datum und Uhrzeit

Die PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE gibt an, ob zum Abrufen von Datums- und Uhrzeittypen als [PHP-DateTime](http://php.net/manual/en/class.datetime.php) Objekte. Bei FALSE werden standardmäßig Zeichenfolgen zurückgegeben. Dieses Attribut kann festgelegt werden, auf die Verbindung oder -Anweisung mit [PDO:: setAttribute](../../connect/php/pdo-setattribute.md) oder [pdostatement:: setAttribute](../../connect/php/pdostatement-setattribute.md), jedoch wird das Anweisungsattribut überschreiben Sie die entsprechenden -Verbindungsattribut. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von Datums- und Uhrzeittypen als PHP-DateTime-Objekte mit dem PDO_SQLSRV-Treiber](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md).

## <a name="sqlsrv-driver-constants"></a>SQLSRV-Treiberkonstanten  
Die folgenden Abschnitte listen die Konstanten auf, die der SQLSRV-Treiber verwendet.  
  
### <a name="err-constants"></a>ERR-Konstanten  
Die folgende Tabelle enthält die Konstanten, die verwendet werden, um anzugeben, ob [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) Fehler, Warnungen oder beides zurückgibt.  
  
|value|und Beschreibung|  
|---------|---------------|  
|SQLSRV_ERR_ALL|Fehler und Warnungen, die beim letzten **sqlsrv** -Funktionsaufruf generiert wurden, werden zurückgegeben. Dies ist der Standardwert.|  
|SQLSRV_ERR_ERRORS|Fehler und Warnungen aus dem letzten **sqlsrv** -Funktionsaufruf werden zurückgegeben.|  
|SQLSRV_ERR_WARNINGS|Warnungen aus dem letzten **sqlsrv** -Funktionsaufruf werden zurückgegeben.|  
  
### <a name="fetch-constants"></a>FETCH-Konstanten  
Die folgende Tabelle enthält die Konstanten, die verwendet werden, um den Typ des von [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)zurückgegebenen Arrays anzugeben.  
  
|SQLSRV-Konstante|und Beschreibung|  
|-------------------|---------------|  
|SQLSRV_FETCH_ASSOC|**sqlsrv_fetch_array** gibt die nächste Datenzeile als assoziatives Array zurück.|  
|SQLSRV_FETCH_BOTH|**sqlsrv_fetch_array** gibt die nächste Datenzeile als Array zurück, das sowohl numerische als auch assoziative Schlüssel aufweist. Dies ist der Standardwert.|  
|SQLSRV_FETCH_NUMERIC|**sqlsrv_fetch_array** gibt die nächste Datenzeile als numerisch indiziertes Array zurück.|  
  
### <a name="logging-constants"></a>Protokollierungskonstanten  
In diesem Abschnitt sind die Konstanten aufgelistet, die verwendet werden, um die Protokollierungseinstellungen mit [sqlsrv_configure](../../connect/php/sqlsrv-configure.md)zu ändern. Weitere Informationen zur Protokollierung von Aktivitäten finden Sie unter [Logging Activity](../../connect/php/logging-activity.md).  
  
Die folgende Tabelle beschreibt die Konstanten, die als Wert für die **LogSubsystems** Einstellung verwendet werden können:  
  
|SQLSRV-Konstante (entsprechende ganze Zahl in Klammern)|und Beschreibung|  
|----------------------------------------------------------|---------------|  
|SQLSRV_LOG_SYSTEM_ALL (-1)|Aktiviert die Protokollierung aller Subsysteme.|  
|SQLSRV_LOG_SYSTEM_CONN (2)|Aktiviert die Protokollierung der Verbindungsaktivität.|  
|SQLSRV_LOG_SYSTEM_INIT (1)|Aktiviert die Protokollierung der Initialisierungsaktivität.|  
|SQLSRV_LOG_SYSTEM_OFF(0)|Deaktiviert die Protokollierung.|  
|SQLSRV_LOG_SYSTEM_STMT (4)|Aktiviert die Protokollierung der Anweisungsaktivität.|  
|SQLSRV_LOG_SYSTEM_UTIL (8)|Aktiviert die Protokollierung der Fehlerfunktionsaktivität (z.B. **handle_error** und **handle_warning**).|  
  
Die folgende Tabelle listet die Konstanten auf, die als Wert für die **LogSeverity** -Einstellung verwendet werden können:  
  
|SQLSRV-Konstante (entsprechende ganze Zahl in Klammern)|und Beschreibung|  
|----------------------------------------------------------|---------------|  
|SQLSRV_LOG_SEVERITY_ALL (-1)|Gibt an, dass Fehler, Warnungen und Hinweise protokolliert werden.|  
|SQLSRV_LOG_SEVERITY_ERROR (1)|Gibt an, dass Fehler protokolliert werden.|  
|SQLSRV_LOG_SEVERITY_NOTICE (4)|Gibt an, dass Hinweise protokolliert werden.|  
|SQLSRV_LOG_SEVERITY_WARNING (2)|Gibt an, dass Warnungen protokolliert werden.|  
  
### <a name="nullable-constants"></a>NULL-Wert-Konstanten  
Die folgende Tabelle enthält die Konstanten, die Sie verwenden können, um zu bestimmen, ob eine Spalte NULL-Werte zulässt oder ob diese Information nicht verfügbar ist. Sie können den Wert des **Nullable** -Schlüssels vergleichen, der von [sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md) zurückgegeben wird, um den Status der NULL-Wert-Behandlung der Spalte zu bestimmen.  
  
|SQLSRV-Konstante (entsprechende ganze Zahl in Klammern)|und Beschreibung|  
|----------------------------------------------------------|---------------|  
|SQLSRV_NULLABLE_YES (0)|In der Spalte ist NULL zulässig.|  
|SQLSRV_NULLABLE_NO (1)|NULL-Werte sind in der Spalte nicht zulässig.|  
|SQLSRV_NULLABLE_UNKNOWN (2)|Es ist nicht bekannt, ob die Spalte NULL-Werte zulässt.|  
  
### <a name="param-constants"></a>PARAM-Konstanten  
Die folgende Liste enthält die Konstanten für die Angabe der Parameterrichtung, wenn Sie [sqlsrv_query](../../connect/php/sqlsrv-query.md) oder [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)aufrufen.  
  
|SQLSRV-Konstante|und Beschreibung|  
|-------------------|---------------|  
|SQLSRV_PARAM_IN|Gibt einen Eingabeparameter an.|  
|SQLSRV_PARAM_INOUT|Gibt einen bidirektionalen Parameter an.|  
|SQLSRV_PARAM_OUT|Gibt einen Ausgabeparameter an.|  
  
### <a name="phptype-constants"></a>PHPTYPE-Konstanten  
Die folgende Tabelle enthält die Konstanten, die verwendet werden, um die PHP-Datentypen zu beschreiben. Informationen zu PHP-Datentypen finden Sie unter [PHP-Typen](https://php.net/manual/en/language.types.php).  
  
|SQLSRV-Konstante|PHP-Datentyp|  
|-------------------|-----------------|  
|SQLSRV_PHPTYPE_INT|Integer|  
|SQLSRV_PHPTYPE_DATETIME|DATETIME|  
|SQLSRV_PHPTYPE_FLOAT|float|  
|SQLSRV_PHPTYPE_STREAM($encoding<sup>1</sup>)|STREAM|  
|SQLSRV_PHPTYPE_STRING($encoding<sup>1</sup>)|Zeichenfolge|  
  
1. **SQLSRV_PHPTYPE_STREAM** und **SQLSRV_PHPTYPE_STRING** akzeptieren einen Parameter, der die Codierung des Streams angibt. Die folgende Tabelle enthält die SQLSRV-Konstanten, die als Parameter akzeptiert werden sowie eine Beschreibung der zugehörigen Codierung.  
  
|SQLSRV-Konstante|und Beschreibung|  
|-------------------|---------------|  
|SQLSRV_ENC_BINARY|Die Daten werden als uncodierter und nicht übersetzter Strom aus unbearbeiteten Bytes vom Server zurückgegeben.|  
|SQLSRV_ENC_CHAR|Daten werden in 8-Bit-Zeichen gemäß der Codepage des Windows-Gebietsschemas zurückgegeben, das auf dem System installiert ist. Alle Multi-Byte-Zeichen oder Zeichen, die nicht in dieser Codepage enthalten sind, werden durch ein aus einem einzelnen Byte bestehendes Fragezeichen (?) ersetzt.<br /><br />Diese ist die Standardcodierung.|  
|„UTF-8“|Die Daten werden in UTF-8-Codierung zurückgegeben. Diese Konstante wurde in Version 1.1 von der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt. Weitere Informationen zur UTF-8-Unterstützung finden Sie unter [Vorgehensweise: Senden und Abrufen von UTF-8-Daten mithilfe der eingebauten UTF-8-Unterstützung](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md).|  
  
> [!NOTE]  
> Bei Verwendung von **SQLSRV_PHPTYPE_STREAM** oder **SQLSRV_PHPTYPE_STRING** muss die Codierung angegeben werden. Wenn kein Parameter angegeben wird, wird ein Fehler zurückgegeben.  
  
Weiter Informationen zu diesen Konstanten finden Sie unter [Gewusst wie: Angeben von PHP-Datentypen](../../connect/php/how-to-specify-php-data-types.md), [Gewusst wie: Abrufen von Zeichendaten als Stream mit dem SQLSRV-Treiber](../../connect/php/how-to-retrieve-character-data-as-a-stream-using-the-sqlsrv-driver.md).  
  
### <a name="sqltype-constants"></a>SQLTYPE-Konstanten  
Die folgende Tabelle enthält die Konstanten, die verwendet werden, um die SQL Server-Datentypen zu beschreiben. Einige Konstanten sind funktionsähnliche und Parameter, die entsprechen, Genauigkeit, Dezimalstellen und/oder der Länge dauert.  Beim Binden von Parametern, sollte die funktionsähnliches Konstanten verwendet werden. Für Vergleiche des Datentyps sind die Konstanten für standard (nicht-Funktion-ähnliche) erforderlich. Informationen zu allen unterstützten SQL Server-Datentypen finden Sie unter [Datentypen (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md). Informationen zu Genauigkeit, Dezimalstellen und Länge finden Sie unter [Genauigkeit, Dezimalstellen und Länge (Transact-SQL)](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
|SQLSRV-Konstante|SQL Server-Datentyp|  
|-------------------|------------------------|  
|SQLSRV_SQLTYPE_BIGINT|BIGINT|  
|SQLSRV_SQLTYPE_BINARY|BINARY|  
|SQLSRV_SQLTYPE_BIT|bit|  
|SQLSRV_SQLTYPE_CHAR|Char<sup>5</sup>|  
|SQLSRV_SQLTYPE_CHAR($charCount)|char|  
|SQLSRV_SQLTYPE_DATE|Datum<sup>4</sup>|  
|SQLSRV_SQLTYPE_DATETIME|DATETIME|  
|SQLSRV_SQLTYPE_DATETIME2|datetime2<sup>4</sup>|  
|SQLSRV_SQLTYPE_DATETIMEOFFSET|datetimeoffset<sup>4</sup>|  
|SQLSRV_SQLTYPE_DECIMAL|Decimal<sup>5</sup>|
|SQLSRV_SQLTYPE_DECIMAL($precision, $scale)|Decimal|  
|SQLSRV_SQLTYPE_FLOAT|FLOAT|  
|SQLSRV_SQLTYPE_IMAGE|image<sup>1</sup>|  
|SQLSRV_SQLTYPE_INT|ssNoversion|  
|SQLSRV_SQLTYPE_MONEY|money| 
|SQLSRV_SQLTYPE_NCHAR|NCHAR<sup>5</sup>|   
|SQLSRV_SQLTYPE_NCHAR($charCount)|NCHAR|  
|SQLSRV_SQLTYPE_NUMERIC|numerische<sup>5</sup>|
|SQLSRV_SQLTYPE_NUMERIC($precision, $scale)|NUMERIC|  
|SQLSRV_SQLTYPE_NVARCHAR,|nvarchar<sup>5</sup>|  
|SQLSRV_SQLTYPE_NVARCHAR($charCount)|NVARCHAR|  
|SQLSRV_SQLTYPE_NVARCHAR('max')|nvarchar(Max)|  
|SQLSRV_SQLTYPE_NTEXT|ntext<sup>2</sup>|  
|SQLSRV_SQLTYPE_REAL|REAL|  
|SQLSRV_SQLTYPE_SMALLDATETIME|smalldatetime|  
|SQLSRV_SQLTYPE_SMALLINT|SMALLINT|  
|SQLSRV_SQLTYPE_SMALLMONEY|SMALLMONEY|  
|SQLSRV_SQLTYPE_TEXT|text<sup>3</sup>|  
|SQLSRV_SQLTYPE_TIME|time<sup>4</sup>|  
|SQLSRV_SQLTYPE_TIMESTAMP|timestamp|  
|SQLSRV_SQLTYPE_TINYINT|TINYINT|  
|SQLSRV_SQLTYPE_UNIQUEIDENTIFIER|UNIQUEIDENTIFIER|  
|SQLSRV_SQLTYPE_UDT|UDT|  
|SQLSRV_SQLTYPE_VARBINARY|varbinary<sup>5</sup>|  
|SQLSRV_SQLTYPE_VARBINARY($byteCount)|varbinary|  
|SQLSRV_SQLTYPE_VARBINARY('max')|varbinary(MAX)|  
|SQLSRV_SQLTYPE_VARCHAR,|Varchar<sup>5</sup>|  
|SQLSRV_SQLTYPE_VARCHAR($charCount)|varchar|  
|SQLSRV_SQLTYPE_VARBINARY('max')|varchar(MAX)|  
|SQLSRV_SQLTYPE_XML|xml|  
  
1.  Dies ist ein veralteter Typ, der dem varbinary(max)-Typ zugeordnet ist.  
  
2.  Dies ist ein veralteter Typ, der dem neueren nvarchar-Typ zugeordnet ist.  
  
3.  Dies ist ein veralteter Typ, der dem neueren varchar-Typ zugeordnet ist.  
  
4.  Unterstützung für diesen Typ wurde in Version 1.1 der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  

5.  Diese Konstanten im Typ Vergleichsvorgänge verwendet werden soll und nicht die Konstanten funktionsähnliches mit ähnlicher Syntax ersetzen. Für das Binden von Parametern, sollten Sie die funktionsähnliches Konstanten verwenden.

  
Die folgende Tabelle enthält die SQLTYPE-Konstanten, die Parameter und den Bereich der zulässigen Werte für den Parameter akzeptieren.  
  
|SQLTYPE|Parameter|Für Parameter zulässiger Bereich|  
|-----------|-------------|---------------------------------|  
|SQLSRV_SQLTYPE_CHAR,<br /><br />SQLSRV_SQLTYPE_VARCHAR,|charCount|1 - 8000|  
|SQLSRV_SQLTYPE_NCHAR,<br /><br />SQLSRV_SQLTYPE_NVARCHAR,|charCount|1 - 4000|  
|SQLSRV_SQLTYPE_BINARY,<br /><br />SQLSRV_SQLTYPE_VARBINARY|byteCount|1 - 8000|  
|SQLSRV_SQLTYPE_DECIMAL<br /><br />SQLSRV_SQLTYPE_NUMERIC|precision|1 - 38|  
|SQLSRV_SQLTYPE_DECIMAL<br /><br />SQLSRV_SQLTYPE_NUMERIC|scale|1 - Genauigkeit|  
  
### <a name="transaction-isolation-level-constants"></a>Konstanten der Transaktionsisolationsebene  
Der **TransactionIsolation** -Schlüssel, der mit [sqlsrv_connect](../../connect/php/sqlsrv-connect.md)verwendet wird, akzeptiert eine der folgenden Konstanten:  
  
-   SQLSRV_TXN_READ_UNCOMMITTED  
  
-   SQLSRV_TXN_READ_COMMITTED  
  
-   SQLSRV_TXN_REPEATABLE_READ  
  
-   SQLSRV_TXN_SNAPSHOT  
  
-   SQLSRV_TXN_SERIALIZABLE  
  
### <a name="cursor-and-scrolling-constants"></a>Konstanten für Cursor und Durchführen eines Bildlaufs  
Die folgenden Konstanten geben die Art des Cursors an, den Sie in einem Resultset verwenden können:  
  
-   SQLSRV_CURSOR_FORWARD  
  
-   SQLSRV_CURSOR_STATIC  
  
-   SQLSRV_CURSOR_DYNAMIC  
  
-   SQLSRV_CURSOR_KEYSET  
  
-   SQLSRV_CURSOR_CLIENT_BUFFERED  
  
Die folgenden Konstanten geben an, welche Zeile im Resultset ausgewählt werden soll:  
  
-   SQLSRV_SCROLL_NEXT  
  
-   SQLSRV_SCROLL_PRIOR  
  
-   SQLSRV_SCROLL_FIRST  
  
-   SQLSRV_SCROLL_LAST  
  
-   SQLSRV_SCROLL_ABSOLUTE  
  
-   SQLSRV_SCROLL_RELATIVE  
  
Weitere Informationen zu diesen Konstanten finden Sie unter [Specifying a Cursor Type and Selecting Rows](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  
  
