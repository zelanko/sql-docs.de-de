---
title: SQLServerDataSource-Elemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7e749bc5-d765-4864-be2b-7822d4c20c09
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 74dea806465d8f1d011f5318eb4ed1571a6ba734
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800513"
---
# <a name="sqlserverdatasource-members"></a>SQLServerDataSource-Elemente
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  In den folgenden Tabellen sind die Elemente aufgeführt, die von der [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Klasse verfügbar gemacht werden.  
  
## <a name="constructors"></a>Konstruktoren  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|[SQLServerDataSource ()](../../../connect/jdbc/reference/sqlserverdatasource-constructor.md)|Initialisiert eine neue Instanz der [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Klasse.|  
  
## <a name="fields"></a>Felder  
 Keine.  
  
## <a name="inherited-fields"></a>Geerbte Felder  
 Keine.  
  
## <a name="methods"></a>Methoden  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|[getApplicationIntent](../../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)|Gibt den Wert des der **ApplicationIntent** Connection-Eigenschaft.|  
|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|Gibt den Anwendungsnamen zurück.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)|Stellt eine Verbindung mit der Datenquelle her, für die dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekt steht.|  
|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|Gibt den Datenbanknamen zurück.|  
|[getDisableStatementPooling](../../../connect/jdbc/reference/getdisablestatementpooling-method-sqlserverdatasource.md)|Gibt den Wert der **DisableStatementPooling** Connection-Eigenschaft. Diese Einstellung steuert, ob die Anweisung Verbindungspooling aktiviert ist oder nicht für diese Verbindung.|  
|[getEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource.md)|Gibt den Wert der **EnablePrepareOnFirstPreparedStatementCall** Connection-Eigenschaft.|  
|[getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md)|Gibt den **booleschen** Wert zurück, mit dem angegeben wird, ob die encrypt-Eigenschaft aktiviert ist.|  
|[getDescription](../../../connect/jdbc/reference/getdescription-method-sqlserverdatasource.md)|Gibt eine Beschreibung der Datenquelle zurück.|  
|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|Gibt den Namen des Failoverservers zurück, der in einer Datenbankspiegelungskonfiguration verwendet wird.|  
|[getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md)|Gibt den Hostnamen zurück, der bei der Überprüfung des Secure Sockets Layer (SSL)-Zertifikats von SQL Server verwendet wird.|  
|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|Gibt den Namen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz zurück.|  
|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|Gibt den **booleschen** Wert zurück, mit dem angegeben wird, ob die lastUpdateCount-Eigenschaft aktiviert ist.|  
|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|Gibt einen Wert vom Typ **int** zurück, mit dem angegeben wird, wie lange von der Datenbank bis zum Melden eines Sperrtimeouts gewartet wird (in Millisekunden).|  
|[getLoginTimeout](../../../connect/jdbc/reference/getlogintimeout-method-sqlserverdatasource.md)|Gibt die Anzahl von Sekunden zurück, die vom [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekt bei der Verbindungsherstellung gewartet wird.|  
|[getLogWriter](../../../connect/jdbc/reference/getlogwriter-method-sqlserverdatasource.md)|Gibt einen Zeichenausgabedatenstrom für alle Protokollierungs- und Ablaufverfolgungsmeldungen zurück.|  
|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|Gibt den Wert des der **MultiSubnetFailover** Connection-Eigenschaft.|  
|[getPacketSize](../../../connect/jdbc/reference/getpacketsize-method-sqlserverdatasource.md)|Gibt die aktuelle Netzwerkpaketgröße (in Bytes) für die Kommunikation mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurück.|  
|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|Gibt die aktuelle Portnummer für die Kommunikation mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurück.|  
|[getReference](../../../connect/jdbc/reference/getreference-method-sqlserverdatasource.md)|Gibt einen Verweis auf dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekt zurück.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverdatasource.md)|Gibt den Antwortpuffermodus für dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekt zurück.|  
|[getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|Gibt den Standardcursortyp zurück, der für alle Resultsets verwendet wird, die mithilfe dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekts erstellt werden.|  
|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|Gibt einen **booleschen** Wert zurück, mit dem angegeben wird, ob das Senden von Zeichenfolgenparametern an den Server im Unicode-Format aktiviert ist.|  
|[getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|Gibt die Einstellung der **SendTimeAsDatetime** Connection-Eigenschaft.|  
|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|Gibt den Namen des Computers zurück, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird.|  
|[getServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/getserverpreparedstatementdiscardthreshold-method-sqlserverdatasource.md)|Gibt den Wert der **ServerPreparedStatementDiscardThreshold** Connection-Eigenschaft.|  
|[getStatementPoolingCacheSize](../../../connect/jdbc/reference/getstatementpoolingcachesize-method-sqlserverdatasource.md)|Gibt die Größe des Caches für vorbereitete Anweisungen für diese Verbindung zurück.|  
|[getTrustManagerClass](../../../connect/jdbc/reference/gettrustmanagerclass-method-sqlserverdatasource.md)|Gibt den Zeichenfolgenwert der TrustManagerClass Verbindungseigenschaft zurück.|  
|[getTrustManagerConstructorArg](../../../connect/jdbc/reference/gettrustmanagerconstructorarg-method-sqlserverdatasource.md)|Gibt den Zeichenfolgenwert der TrustManagerConstructorArg Verbindungseigenschaft zurück.|  
|[getTrustServerCertificate](../../../connect/jdbc/reference/gettrustservercertificate-method-sqlserverdatasource.md)|Gibt einen **booleschen** Wert zurück, mit dem angegeben wird, ob die trustServerCertificate-Eigenschaft aktiviert ist.|  
|[getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md)|Gibt den Pfad (einschließlich Dateiname) zur trustStore-Zertifikatsdatei zurück.|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|Gibt die URL zurück, die zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.|  
|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|Gibt den Benutzernamen zurück, der zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.|  
|[getUseSQLServerBaseDate](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|Sie gibt die Einstellung der useSQLServerBaseDate-Verbindungseigenschaft zurück.|  
|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|Gibt den Namen des Clientcomputers zurück, der zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.|  
|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|Gibt einen **booleschen** Wert zurück, mit dem angegeben wird, ob das Konvertieren von SQL-Status in XOPEN-kompatible Status aktiviert ist.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)|Gibt an, ob es sich bei diesem Datenquellenobjekt um einen Wrapper für die angegebene Schnittstelle handelt.|  
|[setApplicationIntent](../../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)|Legt den Wert für die **ApplicationIntent** Connection-Eigenschaft.|  
|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|Legt den Anwendungsnamen fest.|  
|[setAuthenticationScheme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|Gibt die Art der integrierten Sicherheit an, die für die Anwendung verwendet werden soll.|  
|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|Legt den Namen der Datenbank fest, mit der eine Verbindung hergestellt werden soll.|  
|[setDescription](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|Legt die Beschreibung der Datenquelle fest.|  
|[setDisableStatementPooling](../../../connect/jdbc/reference/setdisablestatementpooling-method-sqlserverdatasource.md)|Legt fest, anweisungspools "true" oder "false".|  
|[setEnablePrepareOnFirstPreparedStatementCall](../../../connect/jdbc/reference/setenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource.md)|Gibt den neuen Wert, der die **EnablePrepareOnFirstPreparedStatementCall** Connection-Eigenschaft.|  
|[setEncrypt](../../../connect/jdbc/reference/setencrypt-method-sqlserverdatasource.md)|Legt einen **booleschen** Wert fest, mit dem angegeben wird, ob die encrypt-Eigenschaft aktiviert ist.|  
|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|Legt den Namen des Failoverservers fest, der in einer Datenbankspiegelungskonfiguration verwendet wird.|  
|[setHostNameInCertificate](../../../connect/jdbc/reference/sethostnameincertificate-method-sqlserverdatasource.md)|Legt den Hostnamen fest, der bei der Überprüfung des Secure Sockets Layer (SSL)-Zertifikats von SQL Server verwendet werden soll.|  
|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|Legt den Namen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz fest.|  
|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|Legt einen **booleschen** Wert fest, mit dem angegeben wird, ob die integratedSecurity-Eigenschaft aktiviert ist.|  
|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|Legt einen **booleschen** Wert fest, mit dem angegeben wird, ob die lastUpdateCount-Eigenschaft aktiviert ist.|  
|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|Legt einen Wert vom Typ **int** fest, mit dem angegeben wird, wie lange von der Datenbank bis zum Melden eines Sperrtimeouts gewartet wird (in Millisekunden).|  
|[setLoginTimeout](../../../connect/jdbc/reference/setlogintimeout-method-sqlserverdatasource.md)|Legt die Anzahl von Sekunden fest, die vom [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekt bei der Verbindungsherstellung gewartet wird.|  
|[setLogWriter](../../../connect/jdbc/reference/setlogwriter-method-sqlserverdatasource.md)|Legt einen Zeichenausgabedatenstrom für alle Protokollierungs- und Ablaufverfolgungsmeldungen fest.|  
|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|Legt den Wert für die **MultiSubnetFailover** Connection-Eigenschaft.|  
|[setPacketSize](../../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md)|Legt die aktuelle Netzwerkpaketgröße (in Bytes) für die Kommunikation mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fest.|  
|[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|Legt das Kennwort fest, das für die Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet wird.|  
|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|Legt die Portnummer für die Kommunikation mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fest.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)|Legt den Antwortpuffermodus für Verbindungen fest, die unter Verwendung dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekts erstellt werden.|  
|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|Legt den Standardcursortyp fest, der für alle Resultsets verwendet wird, die mithilfe dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekts erstellt werden.|  
|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|Legt einen **booleschen** Wert fest, mit dem angegeben wird, ob das Senden von Zeichenfolgenparametern an den Server im Unicode-Format aktiviert ist.|  
|[setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)|Gibt die Art und Weise an, wie java.sql.Time-Werte an den Server gesendet werden.|  
|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|Legt den Namen des Computers fest, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird.|  
|[setServerPreparedStatementDiscardThreshold](../../../connect/jdbc/reference/setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource.md)|Legt den neuen Wert für die **ServerPreparedStatementDiscardThreshold** Connection-Eigenschaft.|  
|[setStatementPoolingCacheSize](../../../connect/jdbc/reference/setstatementpoolingcachesize-method-sqlserverdatasource.md)|Legt die Größe des Caches für vorbereitete Anweisungen für diese Verbindung fest.|  
|[setTrustManagerClass](../../../connect/jdbc/reference/settrustmanagerclass-method-sqlserverdatasource.md)|Legt den Zeichenfolgenwert der-Verbindungseigenschaft TrustManagerClass fest.|  
|[setTrustManagerConstructorArg](../../../connect/jdbc/reference/settrustmanagerconstructorarg-method-sqlserverdatasource.md)|Legt den Zeichenfolgenwert der-Verbindungseigenschaft TrustManagerConstructorArg fest.|  
|[setTrustServerCertificate](../../../connect/jdbc/reference/settrustservercertificate-method-sqlserverdatasource.md)|Legt einen **booleschen** Wert fest, mit dem angegeben wird, ob die trustServerCertificate-Eigenschaft aktiviert ist.|  
|[setTrustStore](../../../connect/jdbc/reference/settruststore-method-sqlserverdatasource.md)|Legt den Pfad (einschließlich Dateiname) zur trustStore-Zertifikatsdatei fest.|  
|[setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md)|Legt das Kennwort fest, das zum Überprüfen der Integrität der trustStore-Daten verwendet wird.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)|Legt die URL fest, die zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.|  
|[setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)|Legt den Benutzernamen fest, der zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.|  
|[setWorkstationID](../../../connect/jdbc/reference/setworkstationid-method-sqlserverdatasource.md)|Legt den Namen des Clientcomputers fest, der zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.|  
|[setXopenStates](../../../connect/jdbc/reference/setxopenstates-method-sqlserverdatasource.md)|Legt einen **booleschen** Wert fest, mit dem angegeben wird, ob das Konvertieren von SQL-Status in XOPEN-kompatible Status aktiviert ist.|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)|Gibt ein Objekt zurück, das die angegebene Schnittstelle implementiert, um den Zugriff auf die [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-spezifischen Methoden zu ermöglichen.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
