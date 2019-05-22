---
title: SQLServerCallableStatement-Elemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apitype: Assembly
ms.assetid: 5ebdc186-e50f-4d14-bbf4-95af5051e4a4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6dc7a5a5e19f7baa335055d1f6c2038b4660f721
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642808"
---
# <a name="sqlservercallablestatement-members"></a>SQLServerCallableStatement-Elemente
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Die folgenden Tabellen enthalten die Elemente, die von der [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Klasse verfügbar gemacht werden.  
  
## <a name="constructors"></a>Konstruktoren  
 Keine.  
  
## <a name="fields"></a>Felder  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="inherited-fields"></a>Geerbte Felder  
 Keine.  
  
## <a name="methods"></a>Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)|(Geerbt von SQLServerPreparedStatement.) Fügt einen Satz von Parametern für den Batch von Befehlen für dieses CallableStatement-Objekt.|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Bricht die SQL-Anweisung ab, die derzeit von diesem CallableStatement-Objekt ausgeführt wird.|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Leert die aktuelle Liste mit SQL-Befehlen für dieses CallableStatement-Objekt.|  
|[clearParameters](../../../connect/jdbc/reference/clearparameters-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Löscht umgehend die aktuellen Parameterwerte.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Löscht alle für dieses CallableStatement-Objekt gemeldeten Warnungen.|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Gibt die Datenbank- und JDBC-Ressourcen dieses CallableStatement-Objekts umgehend frei, sodass nicht auf deren automatische Freigabe gewartet werden muss.|  
|[execute](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Führt die SQL-Anweisung in diesem CallableStatement-Objekt aus. Hierbei kann es sich um eine beliebige Art von SQL-Anweisung handeln.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Übermittelt einen Befehlsbatch zur Ausführung an die Datenbank. Werden alle Befehle erfolgreich ausgeführt, wird ein Array mit Updatezählungen zurückgegeben.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Führt die SQL-Abfrage in diesem CallableStatement-Objekt aus und gibt das durch die Abfrage generierte [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt zurück.|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Führt die SQL-Anweisung in diesem CallableStatement-Objekt aus. Hierbei muss es sich um eine SQL-Anweisung vom Typ „INSERT“, „UPDATE“, „MERGE“ oder „DELETE“ oder um eine SQL-Anweisung handeln, von der nichts zurückgegeben wird (z. B. eine DDL-Anweisung).|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft das [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt ab, von dem dieses CallableStatement-Objekt erstellt wurde.|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)|Ruft den Wert der angegebenen Spalte als eine [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md) Objekt.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die Richtung zum Abrufen von Zeilen aus Datenbanktabellen ab, die standardmäßig für Resultsets verwendet wird, die auf der Grundlage dieses CallableStatement-Objekts generiert werden.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die Anzahl von Resultsetzeilen ab, bei der es sich um die standardmäßige Abrufgröße für Resultsetobjekte handelt, die auf der Grundlage dieses CallableStatement-Objekts generiert werden.|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft sämtliche automatisch generierte Schlüssel ab, die aufgrund der Ausführung dieses CallableStatement-Objekts erstellt werden.|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die maximale Anzahl von Bytes ab, die für Zeichen- und Binärspaltenwerte in einem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt zurückgegeben werden können, das von diesem CallableStatement-Objekt erstellt wird.|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die maximale Anzahl von Zeilen ab, die ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt enthalten kann, das von diesem CallableStatement-Objekt erstellt wurde.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Ruft ein [SQLServerResultSetMetaData Class](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)-Objekt mit Informationen zu den Spalten des [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts ab, das beim Ausführen dieses CallableStatement-Objekts zurückgegeben wird.|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|(Geerbt von SQLServerStatement.) Wechselt zum nächsten Ergebnis dieses CallableStatement-Objekt.|  
|[getParameterMetaData](../../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Ruft Anzahl, Typ und Eigenschaften der Parameter für dieses CallableStatement-Objekt ab.|  
|[getArray](../../../connect/jdbc/reference/getarray-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Array-Objekt ab.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als **ASCII**-Zeichendatenstrom ab.|  
|[getBigDecimal](../../../connect/jdbc/reference/getbigdecimal-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als "java.math.BigDecimal" ab.|  
|[getBinaryStream](../../../connect/jdbc/reference/getbinarystream-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Binärdatenstrom mit unterbrechungsfreien Bytes ab.|  
|[getBlob](../../../connect/jdbc/reference/getblob-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen JDBC-BLOB-Parameters als Blobobjekt in der Programmiersprache Java ab.|  
|[getboolean](../../../connect/jdbc/reference/getboolean-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Wert vom Typ **Boolean** ab.|  
|[getByte](../../../connect/jdbc/reference/getbyte-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Wert vom Typ **byte** ab.|  
|[getBytes](../../../connect/jdbc/reference/getbytes-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Bytearray ab.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als java.io.Reader-Objekt ab.|  
|[getClob](../../../connect/jdbc/reference/getclob-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen JDBC-BLOB-Parameters als CLOB-Objekt in der Programmiersprache Java ab.|  
|[getDate](../../../connect/jdbc/reference/getdate-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als java.sql.Date-Objekt in der Programmiersprache Java ab.|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)|Ruft den Wert der angegebenen Spalte als eine[DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md) Objekt.|  
|[getDouble](../../../connect/jdbc/reference/getdouble-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Wert vom Typ **double** in der Programmiersprache Java ab.|  
|[getFloat](../../../connect/jdbc/reference/getfloat-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Wert vom Typ **float** in der Programmiersprache Java ab.|  
|[getInt](../../../connect/jdbc/reference/getint-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als **int**-Wert in der Programmiersprache Java ab.|  
|[getLong](../../../connect/jdbc/reference/getlong-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Wert vom Typ **long** in der Programmiersprache Java ab.|  
|[getNCharacterStream](../../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Readerobjekt ab.|  
|[getNClob](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen JDBC-**NCLOB**-Parameters als **NClob**-Objekt in der Programmiersprache Java ab.|  
|[getNString](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)|Ruft den Wert der festgelegten **NCHAR**, **NVARCHAR** oder **LONGNVARCHAR** Parameters als Zeichenfolge im Java-Programmiersprache.|  
|[getObject](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Objekt in der Programmiersprache Java ab.|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die Anzahl von Sekunden ab, die von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] auf die Ausführung dieses CallableStatement-Objekts gewartet wird.|  
|[getRef](../../../connect/jdbc/reference/getref-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Ref-Objekt in der Programmiersprache Java ab.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft den Antwortpuffermodus für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt ab.|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft das aktuelle Ergebnis als [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt ab.|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die Resultsetparallelität für [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte ab, die von diesem CallableStatement-Objekt generiert werden.|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die Resultsethaltbarkeit für [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte ab, die von diesem CallableStatement-Objekt generiert werden.|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft den Resultsettyp für [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte ab, die von diesem CallableStatement-Objekt generiert werden.|  
|[getShort](../../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Wert vom Typ **short** in der Programmiersprache Java ab.|  
|[getString](../../../connect/jdbc/reference/getstring-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als Wert vom Typ **Zeichenfolge** in der Programmiersprache Java ab.|  
|[getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als java.sql.SQLXML-Objekt ab.|  
|[getTime](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als java.sql.Time-Objekt in der Programmiersprache Java ab.|  
|[getTimestamp](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als java.sql.Timestamp-Objekt in der Programmiersprache Java ab.|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft das aktuelle Ergebnis als Updatezählung ab.|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlservercallablestatement.md)|Ruft den Wert des angegebenen Parameters als URL-Objekt in der Programmiersprache Java ab.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die erste Warnung ab, die von Aufrufen für dieses CallableStatement-Objekt gemeldet wurde.|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Gibt an, ob dieses Statement-Objekt geschlossen wurde.|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Gibt einen Wert zurück, durch den angegeben wird, ob dem vom Benutzer bereitgestellten Anwendungspool eine Anweisung hinzugefügt werden kann.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)|Gibt an, ob es sich bei diesem Anweisungsobjekt um einen Wrapper für die angegebene Schnittstelle handelt.|  
|[registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)|Registriert den OUT-Parameter.|  
|[setArray](../../../connect/jdbc/reference/setarray-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Legt die angegebene Parameternummer auf das angegebene Array-Objekt fest.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen Eingabedatenstrom fest.|  
|[setBigDecimal](../../../connect/jdbc/reference/setbigdecimal-method-sqlservercallablestatement.md)|Legt die angegebene Parameternummer auf das angegebene BigDecimal-Objekt fest.|  
|[setBinaryStream](../../../connect/jdbc/reference/setbinarystream-sqlservercallablestatement.md)|Legt die angegebenen Parameter auf den angegebenen Eingabedatenstrom fest.|  
|[setBlob](../../../connect/jdbc/reference/setblob-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Legt den angegebenen Parameter auf das angegebene Blobobjekt fest.|  
|[setboolean](../../../connect/jdbc/reference/setboolean-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen Wert vom Typ **Boolean** fest.|  
|[setByte](../../../connect/jdbc/reference/setbyte-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen **byte**-Wert fest.|  
|[setBytes](../../../connect/jdbc/reference/setbytes-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf das angegebene Array aus **byte**-Werten fest.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf das angegebene Readerobjekt fest.|  
|[setClob](../../../connect/jdbc/reference/setclob-method-sqlservercallablestatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Legt den angegebenen Parameter auf das angegebene Objekt fest.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Legt den SQL-Cursornamen auf die angegebene Zeichenfolge fest, die dann für nachfolgende Ausführungsmethoden verwendet wird.|  
|[setDate](../../../connect/jdbc/reference/setdate-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen Datumswert fest.|  
|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md)|Legt den Wert der angegebenen Spalte auf die [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md) Wert.|  
|[setDouble](../../../connect/jdbc/reference/setdouble-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen **double**-Wert fest.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Legt den Escapeverarbeitungsmodus fest.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Gibt für den JDBC-Treiber die Richtung an, in der die Resultsetzeilen verarbeitet werden sollen.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Gibt für den JDBC-Treiber an, wie viele Zeilen aus der Datenbank abgerufen werden sollen, wenn weitere Zeilen benötigt werden.|  
|[setFloat](../../../connect/jdbc/reference/setfloat-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen **float**-Wert fest.|  
|[setInt](../../../connect/jdbc/reference/setint-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen **int**-Wert fest.|  
|[setLong](../../../connect/jdbc/reference/setlong-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen **long**-Wert fest.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Legt das Limit für die maximale Anzahl von Bytes in einer [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Spalte, in der Zeichen- oder Binärwerte gespeichert werden, auf die angegebene Anzahl von Bytes fest.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Legt das Limit für die maximale Anzahl von Zeilen, die ein beliebiges [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt enthalten kann, auf die angegebene Anzahl fest.|  
|[setNCharacterStream](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf das angegebene Readerobjekt fest.|  
|[setNClob](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf das angegebene Objekt fest.|  
|[setNString](../../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf das angegebene Zeichenfolgenobjekt fest.|  
|[setNull](../../../connect/jdbc/reference/setnull-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter unter Berücksichtigung des festzulegenden Parametertyps auf einen NULL-Wert fest.|  
|[setObject](../../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)|Legt den Wert des angegebenen Parameters unter Verwendung des angegebenen Objekts fest.|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Sendet eine Anforderung, dass dem Pool eine Anweisung hinzugefügt bzw. nicht hinzugefügt werden soll. Standardmäßig ist ein SQLServerCallableStatement-Objekt dem Pool hinzugefügt werden, wenn erstellt.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Legt die Anzahl von Sekunden, die vom Treiber auf die Ausführung eines CallableStatement-Objekts gewartet wird, auf die angegebene Anzahl von Sekunden fest.|  
|[setRef](../../../connect/jdbc/reference/setref-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Legt den angegebenen Parameter auf das angegebene Ref-Objekt fest.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Legt den Antwortpuffermodus für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt auf **String full** oder auf **adaptive** (jeweils ohne Berücksichtigung der Groß-/Kleinschreibung) fest.|  
|[setShort](../../../connect/jdbc/reference/setshort-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen Java-Wert vom Typ **short** fest.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen Java-Wert vom Typ **Zeichenfolge** fest.|  
|[setSQLXML](../../../connect/jdbc/reference/setsqlxml-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf das angegebene **SQLXML**-Objekt fest.|  
|[setTime](../../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen Uhrzeitwert fest.|  
|[setTimestamp](../../../connect/jdbc/reference/settimestamp-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen Zeitstempelwert fest.|  
|[setUnicodeStream](../../../connect/jdbc/reference/setunicodestream-method-sqlserverpreparedstatement.md)|(Geerbt von [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).) Legt die angegebene Parameternummer auf den angegebenen Eingabedatenstrom mit der angegebenen Anzahl von Bytes fest.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlservercallablestatement.md)|Legt den angegebenen Parameter auf den angegebenen URL-Wert fest.|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)|Gibt ein Objekt zurück, das die angegebene Schnittstelle implementiert, um den Zugriff auf die [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-spezifischen Methoden zu ermöglichen.|  
|[wasNull](../../../connect/jdbc/reference/wasnull-method-sqlservercallablestatement.md)|Ruft ab, ob der letzte gelesene OUT-Parameter den Wert "SQL NULL" besaß.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPreparedStatement|addBatch, clearBatch, clearParameters, close, execute, executeBatch, executeQuery, executeUpdate, getMetaData, getParameterMetaData, setArray, setAsciiStream, setBigDecimal, setBinaryStream, setBlob, setboolean, setByte, setBytes, setCharacterStream, setClob, setDate, setDouble, setFloat, setInt, setLong, setNull, setObject, setRef, setShort, setString, setTime, setTimestamp, setUnicodeStream, setURL|  
|com.microsoft.sqlserver.jdbc.SQLServerStatement|cancel, clearWarnings, execute, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, isPoolable, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setPoolable, setQueryTimeout|  
|class java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait,|  
|java.sql.PreparedStatement|addBatch, clearParameters, execute, executeQuery, executeUpdate, getMetaData, getParameterMetaData, getSQLXML, setArray, setAsciiStream, setBigDecimal, setBinaryStream, setBlob, setboolean, setByte, setBytes, setCharacterStream, setClob, setDate, setDate, setDouble, setFloat, setInt, setLong, setNull, setObject, setRef, setShort, setString, setSQLXML, setTime, setTimestamp, setUnicodeStream, setURL|  
|java.sql.Statement|addBatch, cancel, clearBatch, clearWarnings, close, execute, executeBatch, executeQuery, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setQueryTimeout|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
