---
title: SQLServerStatement-Member | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 828cbaa9-ea7a-4986-95c3-5ba0d7d01d83
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 72eededd01cd61d6845cc92bbdfbfd073668dd76
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970355"
---
# <a name="sqlserverstatement-members"></a>SQLServerStatement-Elemente
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Die folgenden Tabellen enthalten die Elemente, die von der [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse verfügbar gemacht werden.  
  
## <a name="constructors"></a>Konstruktoren  
 Keine.  
  
## <a name="fields"></a>Felder  
 Keine.  
  
## <a name="inherited-fields"></a>Geerbte Felder  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="methods"></a>Methoden  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverstatement.md)|Fügt den angegebenen SQL-Befehl der aktuellen Liste mit Befehlen für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt hinzu.|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|Bricht die SQL-Anweisung ab, die derzeit von diesem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt ausgeführt wird.|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverstatement.md)|Leert die aktuelle Liste mit SQL-Befehlen für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|Löscht alle für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt gemeldeten Warnungen.|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverstatement.md)|Gibt die Datenbank- und JDBC-Ressourcen dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts umgehend frei, sodass nicht auf deren automatische Freigabe gewartet werden muss.|  
|[execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)|Führt die angegebene SQL-Anweisung aus. Hierbei können mehrere Ergebnisse zurückgegeben werden.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md)|Übermittelt einen Befehlsbatch zur Ausführung an die Datenbank. Werden alle Befehle erfolgreich ausgeführt, wird ein Array mit Updatezählungen zurückgegeben.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)|Führt die angegebene SQL-Anweisung aus und gibt ein einzelnes [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt zurück.|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)|Führt die angegebene SQL-Anweisung aus. Hierbei kann es sich um eine Anweisung vom Typ "INSERT", "UPDATE", "MERGE" oder "DELETE" oder um eine SQL-Anweisung handeln, von der nichts zurückgegeben wird (beispielsweise eine SQL-DDL-Anweisung).|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|Ruft das [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt ab, von dem dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt erstellt wurde.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|Ruft die Richtung zum Abrufen von Zeilen aus Datenbanktabellen ab, die standardmäßig für Resultsets verwendet wird, die auf der Grundlage dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts generiert werden.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|Ruft die Anzahl von Resultsetzeilen ab, bei der es sich um die standardmäßige Abrufgröße für Resultsetobjekte handelt, die auf der Grundlage dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts generiert werden.|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|Ruft sämtliche automatisch generierte Schlüssel ab, die aufgrund der Ausführung dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts erstellt werden.|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|Ruft die maximale Anzahl von Bytes ab, die für Zeichen- und Binärspaltenwerte in einem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt zurückgegeben werden können, das von diesem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt erstellt wird.|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|Ruft die maximale Anzahl von Zeilen ab, die ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt enthalten kann, das von diesem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt erstellt wird.|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|Wechselt zum nächsten Ergebnis dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts.|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|Ruft die Anzahl von Sekunden ab, die von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] auf die Ausführung dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts gewartet wird.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|Ruft den Antwortpuffermodus für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt ab.|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|Ruft das aktuelle Ergebnis als [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt ab.|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|Ruft die Resultsetparallelität für [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte ab, die von diesem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt generiert werden.|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|Ruft die Holdability für Resultsets für [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte ab, die von diesem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt generiert werden.|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|Ruft den Resultsettyp für [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekte ab, die von diesem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt generiert werden.|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|Ruft das aktuelle Ergebnis als Updatezählung ab.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|Ruft die erste Warnung ab, die von Aufrufen für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt gemeldet wurde.|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|Gibt an, ob dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt geschlossen wurde.|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|Gibt einen Wert zurück, durch den angegeben wird, ob dem vom Benutzer bereitgestellten Anwendungspool eine Anweisung hinzugefügt werden kann.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)|Gibt an, ob es sich bei diesem Anweisungsobjekt um einen Wrapper für die angegebene Schnittstelle handelt.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|Legt den SQL-Cursornamen auf die angegebene Zeichenfolge fest, die dann für nachfolgende Ausführungsmethoden verwendet wird.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|Legt den Escapeverarbeitungsmodus fest.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|Gibt für den JDBC-Treiber die Richtung an, in der die Resultsetzeilen verarbeitet werden sollen.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|Gibt für den JDBC-Treiber an, wie viele Zeilen aus der Datenbank abgerufen werden sollen, wenn weitere Zeilen benötigt werden.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|Legt das Limit für die maximale Anzahl von Bytes in einer [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Spalte, in der Zeichen- oder Binärwerte gespeichert werden, auf die angegebene Anzahl von Bytes fest.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|Legt den Grenzwert für die maximale Anzahl von Zeilen, die ein beliebiges [SQLServerResultSet-Objekt](../../../connect/jdbc/reference/sqlserverresultset-class.md) enthalten kann, auf die angegebene Anzahl fest.|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|Sendet eine Anforderung, dass dem Pool eine Anweisung hinzugefügt bzw. nicht hinzugefügt werden soll.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|Legt die Anzahl von Sekunden, die vom Treiber auf die Ausführung eines [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts gewartet wird, auf die angegebene Anzahl von Sekunden fest.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|Legt den Antwortpuffermodus für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt auf **String full** oder auf **adaptive** (jeweils ohne Berücksichtigung der Groß-/Kleinschreibung) fest.|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)|Gibt ein Objekt zurück, das die angegebene Schnittstelle implementiert, um den Zugriff auf die [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-spezifischen Methoden zu ermöglichen.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
