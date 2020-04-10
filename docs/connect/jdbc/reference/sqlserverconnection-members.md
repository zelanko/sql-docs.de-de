---
title: SQLServerConnection-Elemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3115a533-756b-4c78-aee9-4ba7253c85e0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f7000c8737d8d950968a9074e092a88c738941e
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921055"
---
# <a name="sqlserverconnection-members"></a>SQLServerConnection-Elemente
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Die folgenden Tabellen enthalten die Elemente, die von der [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse verfügbar gemacht werden.  
  
## <a name="constructors"></a>Konstruktoren  
 Keine.  
  
## <a name="fields"></a>Felder  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|Dient zum Angeben der Transaktionsisolationsstufe für Momentaufnahmen.|  
  
## <a name="inherited-fields"></a>Geerbte Felder  
  
|Klasse geerbt von:|BESCHREIBUNG|  
|---------------------------|-----------------|  
|java.sql.Connection|TRANSACTION_NONE, TRANSACTION_READ_COMMITTED, TRANSACTION_READ_UNCOMMITTED, TRANSACTION_REPEATABLE_READ, TRANSACTION_SERIALIZABLE|  
  
## <a name="methods"></a>Methoden  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverconnection.md)|Löscht alle für dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt gemeldeten Warnungen.|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverconnection.md)|Gibt die Datenbank für dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt sowie die JDBC-Ressourcen umgehend frei, sodass nicht auf deren automatische Freigabe gewartet werden muss.|  
|[closeUnreferencedPreparedStatementHandles](../../../connect/jdbc/reference/closeunreferencedpreparedstatementhandles-method-sqlserverconnection.md)|Erzwingt, dass unprepare-Anforderungen für ausstehende verworfene Prepared Statements ausgeführt werden| 
|[commit](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md)|Macht alle Änderungen, die seit dem letzten Commit oder Rollback vorgenommen wurden, zu dauerhaften Änderungen und hebt sämtliche Datenbanksperren auf, die derzeit von diesem [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt aufrecht erhalten werden.|  
|[createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md)|Erstellt ein **java.sql.Blob**-Objekt ohne Daten|  
|[createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md)|Erstellt ein **java.sql.Clob**-Objekt ohne Daten|  
|[createNClob](../../../connect/jdbc/reference/createnclob-method-sqlserverconnection.md)|Erstellt ein **java.sql.NClob**-Objekt ohne Daten|  
|[createStatement](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)|Erstellt ein [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt zum Senden von SQL-Anweisungen an die Datenbank.|  
|[createSQLXML](../../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)|Erstellt **java.sql.SQLXML**-Objekt ohne Daten|  
|[getAutoCommit](../../../connect/jdbc/reference/getautocommit-method-sqlserverconnection.md)|Ruft für dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt den aktuellen Modus für automatische Commits ab.|  
|[getCatalog](../../../connect/jdbc/reference/getcatalog-method-sqlserverconnection.md)|Ruft den aktuellen Katalognamen für dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt ab.|  
|[getClientConnectionID-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|Ruft die Verbindungs-ID des letzten Versuchs der Verbindungsherstellung ab, wobei es keine Rolle spielt, ob dieser Versuch erfolgreich war oder fehlgeschlagen ist.|  
|[getClientInfo](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)|Ruft Informationen zu den Eigenschaften für Clientinformationen ab, die vom JDBC-Treiber unterstützt werden.|  
|[getDisableStatementPooling](../../../connect/jdbc/reference/getdisablestatementpooling-method-sqlserverconnection.md)|Diese Methode gibt den Wert der Verbindungseigenschaft **disableStatementPooling** zurück. Mit dieser Einstellung wird gesteuert, ob für diese Verbindung Anweisungspooling aktiviert ist.|
|[getDiscardedServerPreparedStatementCount](../../../connect/jdbc/reference/getdiscardedserverpreparedstatementcount-method-sqlserverconnection.md)|Gibt die Anzahl der aktuell ausstehenden unprepare-Aktionen für ausstehende Prepared Statements zurück|
|[getEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection.md)|Diese Methode gibt den Wert der Verbindungseigenschaft **enablePrepareOnFirstPreparedStatementCall** zurück.|
|[getHoldability](../../../connect/jdbc/reference/getholdability-method-sqlserverconnection.md)|Ruft die aktuelle Haltbarkeit von [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekten ab, die unter Verwendung dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekts erstellt werden.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md)|Ruft ein [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)-Objekt mit Metadaten zu der Datenbank ab, für die dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt eine Verbindung darstellt.|  
|[getServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/getserverpreparedstatementdiscardthreshold-method-sqlserverconnection.md)|Gibt den Wert der Verbindungseigenschaft **serverPreparedStatementDiscardThreshold** zurück|  
|[getStatementHandleCacheEntryCount](../../../connect/jdbc/reference/getstatementhandlecacheentrycount-method-sqlserverconnection.md)|Gibt die aktuelle Anzahl von Handles für Prepared Statements zurück, die in einem Pool zusammengefasst sind|  
|[getStatementPoolingCacheSize](../../../connect/jdbc/reference/getstatementpoolingcachesize-method-sqlserverconnection.md)|Gibt die Größe des Caches für Prepared Statements für diese Verbindung zurück|  
|[getTransactionIsolation](../../../connect/jdbc/reference/gettransactionisolation-method-sqlserverconnection.md)|Ruft die aktuelle Transaktionsisolationsstufe für dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt ab.|  
|[getTypeMap](../../../connect/jdbc/reference/gettypemap-method-sqlserverconnection.md)|Ruft das Map-Objekt ab, das diesem [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt zugeordnet ist.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md)|Ruft die erste Warnung ab, die von Aufrufen für dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt gemeldet wurde.|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverconnection.md)|Gibt an, ob dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt geschlossen wurde.|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverconnection.md)|Gibt an, ob dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt schreibgeschützt ist.|  
|[isStatementPoolingEnabled](../../../connect/jdbc/reference/isstatementpoolingenabled-method-sqlserverconnection.md)|Gibt zurück, ob für diese Verbindung Anweisungspooling aktiviert ist|  
|[isValid](../../../connect/jdbc/reference/isvalid-method-sqlserverconnection.md)|Gibt an, ob dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt noch geöffnet und gültig ist.|  
|[nativeSQL](../../../connect/jdbc/reference/nativesql-method-sqlserverconnection.md)|Konvertiert die angegebene SQL-Anweisung zur systemeigenen SQL-Grammatik des Datenbankservers.|  
|[prepareCall](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)|Erstellt ein [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Objekt zum Aufrufen von in der Datenbank gespeicherten Prozeduren.|  
|[prepareStatement](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)|Erstellt ein [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Objekt zum Senden von parametrisierten SQL-Anweisungen an die Datenbank.|  
|[releaseSavepoint](../../../connect/jdbc/reference/releasesavepoint-method-sqlserverconnection.md)|Entfernt das angegebene [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)-Objekt aus der aktuellen Transaktion.|  
|[rollback](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)|Macht alle im Rahmen der aktuellen Transaktion vorgenommenen Änderungen rückgängig und hebt sämtliche Datenbanksperren auf, die derzeit von diesem [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt aufrecht erhalten werden.|  
|[setAutoCommit](../../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md)|Legt für dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt den aktuellen Modus für automatische Commits auf den angegebenen Zustand fest.|  
|[setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md)|Legt den angegebenen Katalognamen fest, um einen Teilbereich der Datenbank dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekts auszuwählen, in dem gearbeitet werden soll.|  
|[setClientInfo](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)|Legt den Wert der Eigenschaften für Clientinformationen fest.|  
|[setDisableStatementPooling](../../../connect/jdbc/reference/setdisablestatementpooling-method-sqlserverconnection.md)|Diese Methode legt das Anweisungspooling auf TRUE oder FALSE fest.|  
|[setEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/setenableprepareonfirstpreparedstatementcall-method-sqlserverconnection.md)|Gibt den neuen Wert der Verbindungseigenschaft **enablePrepareOnFirstPreparedStatementCall** an|  
|[setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)|Ändert die Haltbarkeit von [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekten, die unter Verwendung dieses [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)-Objekts erstellt werden, zur angegebenen Haltbarkeit.|  
|[setReadOnly](../../../connect/jdbc/reference/setreadonly-method-sqlserverconnection.md)|Versetzt dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt in den schreibgeschützten Modus, damit vom JDBC-Treiber die Datenbankoptimierungen aktiviert werden.|  
|[setSavepoint](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)|Erstellt in der aktuellen Transaktion einen unbenannten Sicherungspunkt und gibt das neue [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)-Objekt zurück, das für den Sicherungspunkt steht.|  
|[setServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/setserverpreparedstatementdiscardthreshold-method-sqlserverconnection.md)|Diese Methode legt den neuen Wert der Verbindungseigenschaft **serverPreparedStatementDiscardThreshold** fest.|  
|[setStatementPoolingCacheSize](../../../connect/jdbc/reference/setstatementpoolingcachesize-method-sqlserverconnection.md)|Legt die Größe des Caches für Prepared Statements für diese Verbindung fest|  
|[setTransactionIsolation](../../../connect/jdbc/reference/settransactionisolation-method-sqlserverconnection.md)|Ändert die Transaktionsisolationsstufe für dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt zur angegebenen Stufe.|  
|[setTypeMap](../../../connect/jdbc/reference/settypemap-method-sqlserverconnection.md)|Installiert das angegebene TypeMap-Objekt als Typzuordnung für dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.lang.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
