---
description: SQLServerPreparedStatement-Elemente
title: SQLServerPreparedStatement-Elemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2363902f-d4c6-4cd4-a5fc-86079eb9e418
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b5025d8a7387777de1d95861fa6b2d09f436b68
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458272"
---
# <a name="sqlserverpreparedstatement-members"></a>SQLServerPreparedStatement-Elemente
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Die folgenden Tabellen enthalten die Elemente, die von der [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse verfügbar gemacht werden.  
  
## <a name="constructors"></a>Konstruktoren  
 Keine  
  
## <a name="fields"></a>Felder  
 Keine.  
  
## <a name="inherited-fields"></a>Geerbte Felder  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="methods"></a>Methoden  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)|Fügt dem Befehlsbatch für dieses Statement-Objekt einen Parametersatz hinzu.|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Bricht die SQL-Anweisung ab, die derzeit von diesem Statement-Objekt ausgeführt wird.|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md)|Leert die aktuelle Liste mit SQL-Befehlen für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt.|  
|[clearParameters](../../../connect/jdbc/reference/clearparameters-method-sqlserverpreparedstatement.md)|Löscht umgehend die aktuellen Parameterwerte.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Löscht alle für dieses Statement-Objekt gemeldeten Warnungen.|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverpreparedstatement.md)|Gibt die Datenbank- und JDBC-Ressourcen dieses Statement-Objekts umgehend frei, sodass nicht auf deren automatische Freigabe gewartet werden muss.|  
|[execute](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)|Führt die SQL-Anweisung in diesem Statement-Objekt aus. Hierbei kann es sich um eine beliebige Art von SQL-Anweisung handeln.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverpreparedstatement.md)|Übermittelt einen Befehlsbatch zur Ausführung an die Datenbank. Werden alle Befehle erfolgreich ausgeführt, wird ein Array mit Updatezählungen zurückgegeben.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)|Führt die SQL-Abfrage in diesem Statement-Objekt aus und gibt das durch die Abfrage generierte [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt zurück.|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)|Führt die SQL-Anweisung in diesem Statement-Objekt aus. Hierbei muss es sich um eine SQL-Anweisung vom Typ „INSERT“, „UPDATE“, „MERGE“ oder „DELETE“ oder um eine SQL-Anweisung handeln, von der nichts zurückgegeben wird (z. B. eine DDL-Anweisung).|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft das [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt ab, von dem dieses Statement-Objekt erstellt wurde.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die Richtung zum Abrufen von Zeilen aus Datenbanktabellen ab, die standardmäßig für Resultsets verwendet wird, die auf der Grundlage dieses Statement-Objekts generiert werden.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die Anzahl von Resultsetzeilen ab, bei der es sich um die standardmäßige Abrufgröße für Resultsetobjekte handelt, die auf der Grundlage dieses Statement-Objekts generiert werden.|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft sämtliche automatisch generierte Schlüssel ab, die aufgrund der Ausführung dieses Statement-Objekts erstellt werden.|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die maximale Anzahl von Bytes ab, die für Zeichen- und Binärspaltenwerte in einem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt zurückgegeben werden können, das von diesem Statement-Objekt erstellt wird.|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die maximale Anzahl von Zeilen ab, die ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt enthalten kann, das von diesem Statement-Objekt erstellt wurde.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverpreparedstatement.md)|Ruft ein [SQLServerResultSetMetaData Class](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)-Objekt mit Informationen zu den Spalten des [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts ab, das beim Ausführen dieses Statement-Objekts zurückgegeben wird.|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Mit dieser Methode wird zum nächsten Ergebnis dieses Statement-Objekts gewechselt.|  
|[getParameterMetaData](../../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md)|Ruft Anzahl, Typ und Eigenschaften der Parameter für dieses Statement-Objekt ab.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft den Antwortpuffermodus für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt ab.|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die Anzahl von Sekunden ab, die von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] auf die Ausführung dieses Statement-Objekts gewartet wird.|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft das aktuelle Ergebnis als [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt ab.|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die Resultsetparallelität für [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte ab, die von diesem Statement-Objekt generiert werden.|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die Resultsethaltbarkeit für [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte ab, die von diesem Statement-Objekt generiert werden.|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft den Resultsettyp für [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte ab, die von diesem Statement-Objekt generiert werden.|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft das aktuelle Ergebnis als Updatezählung ab.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Ruft die erste Warnung ab, die von Aufrufen für dieses Statement-Objekt gemeldet wurde.|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Gibt an, ob dieses Statement-Objekt geschlossen wurde.|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Gibt einen Wert zurück, durch den angegeben wird, ob dem vom Benutzer bereitgestellten Anwendungspool eine Anweisung hinzugefügt werden kann.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)|Gibt an, ob es sich bei diesem Anweisungsobjekt um einen Wrapper für die angegebene Schnittstelle handelt.|  
|[setArray](../../../connect/jdbc/reference/setarray-method-sqlserverpreparedstatement.md)|Legt die angegebene Parameternummer auf das angegebene Array-Objekt fest.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlserverpreparedstatement.md)|Legt die angegebene Parameternummer auf das angegebene InputStream-Objekt fest.|  
|[setBigDecimal](../../../connect/jdbc/reference/setbigdecimal-method-sqlserverpreparedstatement.md)|Legt die angegebene Parameternummer auf das angegebene BigDecimal-Objekt fest.|  
|[setBinaryStream](../../../connect/jdbc/reference/setbinarystream-method-sqlserverpreparedstatement.md)|Legt die angegebenen Parameter auf den angegebenen Eingabedatenstrom fest.|  
|[setBlob](../../../connect/jdbc/reference/setblob-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf das angegebene Blobobjekt fest.|  
|[setboolean](../../../connect/jdbc/reference/setboolean-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf den angegebenen **Boolean**-Wert fest.|  
|[setByte](../../../connect/jdbc/reference/setbyte-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf den angegebenen **byte**-Wert fest.|  
|[setBytes](../../../connect/jdbc/reference/setbytes-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf das angegebene Bytearray fest.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf das angegebene Readerobjekt fest.|  
|[setClob](../../../connect/jdbc/reference/setclob-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf das angegebene CLOB-Objekt fest.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Legt den SQL-Cursornamen auf die angegebene Zeichenfolge fest, die dann für nachfolgende Ausführungsmethoden verwendet wird.|  
|[setDate](../../../connect/jdbc/reference/setdate-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf den angegebenen Datumswert fest.|  
|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md)|Mit dieser Methode wird der Wert der angegebenen Spalte auf den Wert der Klasse [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) festgelegt.|  
|[setDouble](../../../connect/jdbc/reference/setdouble-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf den angegebenen **double**-Wert fest.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Legt den Escapeverarbeitungsmodus fest.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Gibt für den JDBC-Treiber die Richtung an, in der die Resultsetzeilen verarbeitet werden sollen.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Gibt für den JDBC-Treiber an, wie viele Zeilen aus der Datenbank abgerufen werden sollen, wenn weitere Zeilen benötigt werden.|  
|[setFloat](../../../connect/jdbc/reference/setfloat-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf den angegebenen **float**-Wert fest.|  
|[setInt](../../../connect/jdbc/reference/setint-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf den angegebenen **int**-Wert fest.|  
|[setLong](../../../connect/jdbc/reference/setlong-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf den angegebenen **long**-Wert fest.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Legt das Limit für die maximale Anzahl von Bytes in einer [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Spalte, in der Zeichen- oder Binärwerte gespeichert werden, auf die angegebene Anzahl von Bytes fest.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Legt den Grenzwert für die maximale Anzahl von Zeilen, die ein beliebiges [SQLServerResultSet-Objekt](../../../connect/jdbc/reference/sqlserverresultset-class.md) enthalten kann, auf die angegebene Anzahl fest.|  
|[setNCharacterStream](../../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf das angegebene Readerobjekt fest.|  
|[setNClob](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf das angegebene Objekt fest.|  
|[setNull](../../../connect/jdbc/reference/setnull-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter unter Berücksichtigung des festzulegenden Parametertyps auf einen NULL-Wert fest.|  
|[setNString](../../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md)|Legt den angegebenen Parameter auf das angegebene **Zeichenfolgenobjekt** fest.|  
|[setObject](../../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)|Legt den Wert des angegebenen Parameters unter Verwendung des angegebenen Objekts fest.|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Sendet eine Anforderung, dass dem Pool eine Anweisung hinzugefügt bzw. nicht hinzugefügt werden soll. Standardmäßig kann ein SQLServerPreparedStatement-Objekt bei der Erstellung einem Pool hinzugefügt werden.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Legt die Anzahl von Sekunden, die vom Treiber auf die Ausführung eines Statement-Objekts gewartet wird, auf die angegebene Anzahl von Sekunden fest.|  
|[setRef](../../../connect/jdbc/reference/setref-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf das angegebene Ref-Objekt fest.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|(Geerbt von [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).) Legt den Antwortpuffermodus für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt auf **String full** oder auf **adaptive** (jeweils ohne Berücksichtigung der Groß-/Kleinschreibung) fest.|  
|[setShort](../../../connect/jdbc/reference/setshort-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf den angegebenen Java-Wert vom Typ **short** fest.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf den angegebenen Java-Wert vom Typ **Zeichenfolge** fest.|  
|[setSQLXML](../../../connect/jdbc/reference/setsqlxml-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf das angegebene **SQLXML**-Objekt fest.|  
|[setTime](../../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf den angegebenen Uhrzeitwert fest.|  
|[setTimestamp](../../../connect/jdbc/reference/settimestamp-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf den angegebenen Zeitstempelwert fest.|  
|[setUnicodeStream](../../../connect/jdbc/reference/setunicodestream-method-sqlserverpreparedstatement.md)|Legt die angegebene Parameternummer auf den angegebenen Eingabedatenstrom mit der angegebenen Anzahl von Bytes fest.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverpreparedstatement.md)|Legt den angegebenen Parameter auf den angegebenen URL-Wert fest.|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)|Gibt ein Objekt zurück, das die angegebene Schnittstelle implementiert, um den Zugriff auf die [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-spezifischen Methoden zu ermöglichen.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerStatement|cancel, clearWarnings, execute, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, isPoolable, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setPoolable, setQueryTimeout|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Statement|cancel, clearWarnings, execute, executeUpdate, getConnection, getFetchDirection, getFetchSize, getGeneratedKeys, getMaxFieldSize, getMaxRows, getMoreResults, getQueryTimeout, getResultSet, getResultSetConcurrency, getResultSetHoldability, getResultSetType, getUpdateCount, getWarnings, setCursorName, setEscapeProcessing, setFetchDirection, setFetchSize, setMaxFieldSize, setMaxRows, setQueryTimeout|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
