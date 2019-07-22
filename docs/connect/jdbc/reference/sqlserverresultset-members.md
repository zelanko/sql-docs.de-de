---
title: SQLServerResultSet-Member | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2a438d5d-2d6a-46a0-a2ae-f35fbae4a472
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fed1b515d6e003f00cebbaf3f3a9306572e2ad2b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970563"
---
# <a name="sqlserverresultset-members"></a>SQLServerResultSet-Elemente
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  In den folgenden Tabellen werden die Elemente aufgeführt, die von der Klasse [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) zur Verfügung gestellt werden.  
  
## <a name="constructors"></a>Konstruktoren  
 Keine.  
  
## <a name="fields"></a>Felder  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|[CONCUR_SS_OPTIMISTIC_CC](../../../connect/jdbc/reference/concur-ss-optimistic-cc-field-sqlserverresultset.md)|Dient zum Angeben eines Typs der optimistischen Nebenläufigkeit (Lese-/Schreibzugriff) für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ohne Zeilensperre.|  
|[CONCUR_SS_OPTIMISTIC_CCVAL](../../../connect/jdbc/reference/concur-ss-optimistic-ccval-field-sqlserverresultset.md)|Dient zum Angeben eines Typs der optimistischen Nebenläufigkeit (Lese-/Schreibzugriff) für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ohne Zeilensperre.|  
|[CONCUR_SS_SCROLL_LOCKS](../../../connect/jdbc/reference/concur-ss-scroll-locks-field-sqlserverresultset.md)|Dient zum Angeben eines Typs der optimistischen Nebenläufigkeit (Lese-/Schreibzugriff) für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit Zeilensperre.|  
|[TYPE_SS_DIRECT_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-direct-forward-only-field-sqlserverresultset.md)|Dient zum Angeben eines schnellen schreibgeschützten Vorwärtscursortyps für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[TYPE_SS_SCROLL_DYNAMIC](../../../connect/jdbc/reference/type-ss-scroll-dynamic-field-sqlserverresultset.md)|Wird zum Angeben eines dynamischen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cursortyps verwendet.|  
|[TYPE_SS_SCROLL_KEYSET](../../../connect/jdbc/reference/type-ss-scroll-keyset-field-sqlserverresultset.md)|Dient zum Angeben eines Keysetcursortyps für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[TYPE_SS_SCROLL_STATIC](../../../connect/jdbc/reference/type-ss-scroll-static-field-sqlserverresultset.md)|Dient zum Angeben eines statischen Cursortyps für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[TYPE_SS_SERVER_CURSOR_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-server-cursor-forward-only-field-sqlserverresultset.md)|Dient zum Angeben eines schnellen schreibgeschützten Vorwärtscursortyps für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
## <a name="inherited-fields"></a>Geerbte Felder  
  
|Klasse geerbt von:|und Beschreibung|  
|---------------------------|-----------------|  
|java.sql.ResultSet|CLOSE_CURSORS_AT_COMMIT, CONCUR_READ_ONLY, CONCUR_UPDATABLE, FETCH_FORWARD, FETCH_REVERSE, FETCH_UNKNOWN, HOLD_CURSORS_OVER_COMMIT, TYPE_FORWARD_ONLY, TYPE_SCROLL_INSENSITIVE, TYPE_SCROLL_SENSITIVE|  
  
## <a name="methods"></a>Methoden  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|[absolute](../../../connect/jdbc/reference/absolute-method-sqlserverresultset.md)|Versetzt den Cursor in die angegebene Zeile in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.|  
|[afterLast](../../../connect/jdbc/reference/afterlast-method-sqlserverresultset.md)|Versetzt den Cursor an eine Position nach der letzten Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts.|  
|[beforeFirst](../../../connect/jdbc/reference/beforefirst-method-sqlserverresultset.md)|Versetzt den Cursor an eine Position vor der ersten Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts.|  
|[cancelRowUpdates](../../../connect/jdbc/reference/cancelrowupdates-method-sqlserverresultset.md)|Bricht die Aktualisierungen ab, die an der aktuellen Zeile in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt vorgenommen wurden.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverresultset.md)|Löscht alle für dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt gemeldeten Warnungen.|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverresultset.md)|Gibt die Datenbank- und JDBC-Ressourcen dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts umgehend frei, sodass nicht darauf gewartet werden muss, bis dieser Vorgang beim automatischen Schließen ausgeführt wird.|  
|[deleteRow](../../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md)|Löscht die aktuelle Zeile aus diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt sowie aus der zugrunde liegenden Datenbank.|  
|[finalize](../../../connect/jdbc/reference/finalize-method-sqlserverresultset.md)|Schließt dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt explizit.|  
|[findColumn](../../../connect/jdbc/reference/findcolumn-method-sqlserverresultset.md)|Ruft für den angegebenen Spaltennamen den Index der ersten übereinstimmenden Spalte in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt ab.|  
|[first](../../../connect/jdbc/reference/first-method-sqlserverresultset.md)|Versetzt den Cursor in die erste Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts.|  
|[getArray](../../../connect/jdbc/reference/getarray-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Array-Objekt ab.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als ASCII-Zeichendatenstrom ab.|  
|[getBigDecimal](../../../connect/jdbc/reference/getbigdecimal-method-sqlserverresultset.md)|Ruft den Wert des angegebenen Spaltenindexes in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als „java.math.BigDecimal“ ab.|  
|[getBinaryStream](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Binärdatenstrom nicht interpretierter Bytes ab.|  
|[getBlob](../../../connect/jdbc/reference/getblob-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Blob in der Programmiersprache Java ab.|  
|[getBoolean](../../../connect/jdbc/reference/getboolean-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als **booleschen** Wert in der Programmiersprache Java ab.|  
|[getByte](../../../connect/jdbc/reference/getbyte-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Wert vom Typ **byte** in der Programmiersprache Java ab.|  
|[getBytes](../../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Array vom Typ **byte** in der Programmiersprache Java ab.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als java.io.Reader-Objekt ab.|  
|[getClob](../../../connect/jdbc/reference/getclob-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Clob-Objekt in der Programmiersprache Java ab.|  
|[getConcurrency](../../../connect/jdbc/reference/getconcurrency-method-sqlserverresultset.md)|Ruft den Parallelitätsmodus dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts ab.|  
|[getCursorName](../../../connect/jdbc/reference/getcursorname-method-sqlserverresultset.md)|Ruft den Namen des von diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt verwendeten SQL-Cursors ab.|  
|[getDate](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als java.sql.Date-Objekt in der Programmiersprache Java ab.|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte als[DateTimeOffset-Klassen](../../../connect/jdbc/reference/datetimeoffset-class.md) Objekt ab.|  
|[getDouble](../../../connect/jdbc/reference/getdouble-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Wert vom Typ **double** in der Programmiersprache Java ab.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverresultset.md)|Ruft die Abrufrichtung für dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt ab.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md)|Ruft die Abrufgröße für dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt ab.|  
|[getFloat](../../../connect/jdbc/reference/getfloat-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Wert vom Typ **float** in der Programmiersprache Java ab.|  
|[getHoldability](../../../connect/jdbc/reference/getholdability-method-sqlserverresultset.md)|Ruft die Haltbarkeit dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts ab.|  
|[getInt](../../../connect/jdbc/reference/getint-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als **int**-Wert der Programmiersprache Java ab.|  
|[getLong](../../../connect/jdbc/reference/getlong-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als **long**-Wert der Programmiersprache Java ab.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md)|Ruft Anzahl, Typen und Eigenschaften der Spalten dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts ab.|  
|[getNCharacterStream](../../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Reader-Objekt ab.|  
|[getNClob](../../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile des [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als **NClob**-Objekt in der Programmiersprache Java ab.|  
|[getNString](../../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile des [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als String-Objekt in der Programmiersprache Java ab.|  
|[getObject](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Objekt in der Programmiersprache Java ab.|  
|[getRef](../../../connect/jdbc/reference/getref-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Ref-Objekt in der Programmiersprache Java ab.|  
|[getRow](../../../connect/jdbc/reference/getrow-method-sqlserverresultset.md)|Ruft die aktuelle Zeilennummer ab.|  
|[getShort](../../../connect/jdbc/reference/getshort-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als **short**-Wert in der Programmiersprache Java ab.|  
|[getStatement](../../../connect/jdbc/reference/getstatement-method-sqlserverresultset.md)|Ruft das [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt ab, von dem dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt erstellt wurde.|  
|[getString](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile des [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als **String**-Objekt in der Programmiersprache Java ab.|  
|[getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als **SQLXML**-Objekt ab.|  
|[getTime](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als java.sql.Time-Objekt in der Programmiersprache Java ab.|  
|[getTimestamp](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als java.sql.Timestamp-Objekt in der Programmiersprache Java ab.|  
|[getType](../../../connect/jdbc/reference/gettype-method-sqlserverresultset.md)|Ruft den Cursortyp dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts ab.|  
|[getUnicodeStream](../../../connect/jdbc/reference/getunicodestream-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Unicode-Zeichendatenstrom ab.|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverresultset.md)|Ruft den Wert der angegebenen Spalte in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als URL-Objekt ab.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverresultset.md)|Ruft die erste Warnung ab, die von Aufrufen für dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt gemeldet wurde.|  
|[insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md)|Fügt den Inhalt der Einfügezeile in dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt und in die Datenbank ein.|  
|[isAfterLast](../../../connect/jdbc/reference/isafterlast-method-sqlserverresultset.md)|Ruft ab, ob sich der Cursor an einer Position nach der letzten Zeile in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt befindet.|  
|[isBeforeFirst](../../../connect/jdbc/reference/isbeforefirst-method-sqlserverresultset.md)|Ruft ab, ob sich der Cursor an einer Position vor der ersten Zeile in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt befindet.|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverresultset.md)|Gibt an, ob dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt geschlossen wurde.|  
|[isFirst](../../../connect/jdbc/reference/isfirst-method-sqlserverresultset.md)|Ruft ab, ob sich der Cursor in der ersten Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts befindet.|  
|[isLast](../../../connect/jdbc/reference/islast-method-sqlserverresultset.md)|Ruft ab, ob sich der Cursor in der letzten Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts befindet.|  
|[last](../../../connect/jdbc/reference/last-method-sqlserverresultset.md)|Versetzt den Cursor in die letzte Zeile in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.|  
|[moveToCurrentRow](../../../connect/jdbc/reference/movetocurrentrow-method-sqlserverresultset.md)|Versetzt den Cursor an die gespeicherte Cursorposition (üblicherweise die aktuelle Zeile).|  
|[moveToInsertRow](../../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md)|Versetzt den Cursor in die Einfügezeile.|  
|[next](../../../connect/jdbc/reference/next-method-sqlserverresultset.md)|Versetzt den Cursor von seiner aktuellen Position aus um eine Zeile nach unten.|  
|[previous](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md)|Versetzt den Cursor in die vorherige Zeile in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.|  
|[refreshRow](../../../connect/jdbc/reference/refreshrow-method-sqlserverresultset.md)|Aktualisiert die aktuelle Zeile mit dem aktuellen Wert aus der Datenbank.|  
|[relative](../../../connect/jdbc/reference/relative-method-sqlserverresultset.md)|Versetzt den Cursor relativ zur aktuellen Zeile um die angegebene (positive oder negative) Anzahl von Zeilen.|  
|[rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)|Ruft ab, ob eine Zeile gelöscht wurde.|  
|[rowInserted](../../../connect/jdbc/reference/rowinserted-method-sqlserverresultset.md)|Ruft ab, ob in der aktuellen Zeile eine Einfügung vorgenommen wurde.|  
|[rowUpdated](../../../connect/jdbc/reference/rowupdated-method-sqlserverresultset.md)|Ruft ab, ob die aktuelle Zeile aktualisiert wurde.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md)|Gibt Aufschluss über die Richtung, in der die Zeilen in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt verarbeitet werden.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)|Gibt für den JDBC-Treiber an, wie viele Zeilen aus der Datenbank abgerufen werden sollen, wenn für dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt weitere Zeilen benötigt werden.|  
|[updateArray](../../../connect/jdbc/reference/updatearray-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem Array-Objekt.|  
|[updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem ASCII-Datenstromwert.|  
|[updateBigDecimal](../../../connect/jdbc/reference/updatebigdecimal-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem BigDecimal-Objekt.|  
|[updateBinaryStream](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem Binärdatenstromwert.|  
|[updateBlob](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem java.sql.Blob-Wert.|  
|[updateBoolean](../../../connect/jdbc/reference/updateboolean-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem **booleschen** Wert.|  
|[updateByte](../../../connect/jdbc/reference/updatebyte-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem **byte**-Wert.|  
|[updateBytes](../../../connect/jdbc/reference/updatebytes-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem Array von **byte**-Werten.|  
|[updateCharacterStream](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem Zeichendatenstromwert.|  
|[updateClob](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem java.sql.Clob-Wert.|  
|[updateDate](../../../connect/jdbc/reference/updatedate-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem Datumswert.|  
|[updateDateTimeOffset](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)|Aktualisiert eine [DateTimeOffset-Klassen](../../../connect/jdbc/reference/datetimeoffset-class.md) Spalte.|  
|[updateDouble](../../../connect/jdbc/reference/updatedouble-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem **double**-Wert.|  
|[updateFloat](../../../connect/jdbc/reference/updatefloat-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem **Gleitkommawert**.|  
|[updateInt](../../../connect/jdbc/reference/updateint-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem **int**-Wert.|  
|[updateLong](../../../connect/jdbc/reference/updatelong-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem **long**-Wert.|  
|[updateNCharacterStream](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem Zeichendatenstromwert.|  
|[updateNClob](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit dem angegebenen Objektwert.|  
|[updateNString](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem **Zeichenfolgenwert**.|  
|[updateNull](../../../connect/jdbc/reference/updatenull-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem NULL-Wert.|  
|[updateObject](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)|Aktualisiert die bezeichnete Spalte mit einem **Object**-Wert.|  
|[updateRef](../../../connect/jdbc/reference/updateref-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem java.sql.Ref-Wert.|  
|[updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)|Aktualisiert die zugrunde liegende Datenbank mit dem neuen Inhalt der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts.|  
|[updateShort](../../../connect/jdbc/reference/updateshort-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem **short**-Wert.|  
|[updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem **Zeichenfolgenwert**.|  
|[updateSQLXML](../../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem **SQLXML**-Wert.|  
|[updateTime](../../../connect/jdbc/reference/updatetime-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem Uhrzeitwert.|  
|[updateTimestamp](../../../connect/jdbc/reference/updatetimestamp-method-sqlserverresultset.md)|Aktualisiert die angegebene Spalte mit einem Zeitstempelwert.|  
|[wasNull](../../../connect/jdbc/reference/wasnull-method-sqlserverresultset.md)|Überprüft, ob es sich beim letzten gelesenen Wert um einen NULL-Wert handelt.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
