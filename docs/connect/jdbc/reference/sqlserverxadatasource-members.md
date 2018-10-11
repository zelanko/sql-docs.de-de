---
title: SQLServerXADataSource-Elemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 04178645-915f-4569-8907-d45e299bbe7d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4e9e25a45940304b977623b0f009ed134b56caed
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47672328"
---
# <a name="sqlserverxadatasource-members"></a>SQLServerXADataSource-Elemente
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Die folgenden Tabellen enthalten die Elemente, die von der [SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)-Klasse verfügbar gemacht werden.  
  
## <a name="constructors"></a>Konstruktoren  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|[SQLServerXADataSource ()](../../../connect/jdbc/reference/sqlserverxadatasource-constructor.md)|Initialisiert eine neue Instanz der [SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)-Klasse.|  
  
## <a name="fields"></a>Felder  
 Keine.  
  
## <a name="inherited-fields"></a>Geerbte Felder  
 Keine.  
  
## <a name="methods"></a>Methoden  
  
|Name|und Beschreibung|  
|----------|-----------------|  
|[getApplicationIntent](../../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt den Wert der **applicationIntent**-Verbindungseigenschaft zurück.|  
|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt den Anwendungsnamen zurück.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Stellt eine Verbindung mit der Datenquelle her, für die dieses DataSource-Objekt steht.|  
|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt den Datenbanknamen zurück.|  
|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt den Namen des Failoverservers zurück, der in einer Datenbankspiegelungskonfiguration verwendet wird.|  
|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanznamen zurück.|  
|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt einen **booleschen** Wert zurück, mit dem angegeben wird, ob die lastUpdateCount-Eigenschaft aktiviert ist.|  
|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt einen Wert vom Typ **int** zurück, mit dem angegeben wird, wie lange von der Datenbank bis zum Melden eines Sperrtimeouts gewartet wird (in Millisekunden).|  
|[getLoginTimeout](../../../connect/jdbc/reference/getlogintimeout-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt die Anzahl von Sekunden zurück, die vom DataSource-Objekt bei der Verbindungsherstellung gewartet wird.|  
|[getLogWriter](../../../connect/jdbc/reference/getlogwriter-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt einen Zeichenausgabedatenstrom für alle Protokollierungs- und Ablaufverfolgungsmeldungen zurück.|  
|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Ruft den Wert der **multiSubnetFailover**-Verbindungseigenschaft ab.|  
|[getPooledConnection](../../../connect/jdbc/reference/getpooledconnection-method-sqlserverconnectionpooldatasource.md)|(Geerbt von [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)) Stellt eine physische Datenbankverbindung her, die als Poolverbindung verwendet werden kann.|  
|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt die aktuelle Portnummer zurück, die für die Kommunikation mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet wird.|  
|[getReference](../../../connect/jdbc/reference/getreference-method-sqlserverxadatasource.md)|Gibt einen Verweis auf dieses [SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)-Objekt zurück.|  
|[getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt den Standardcursortyp zurück, der für alle Resultsets verwendet wird, die mithilfe dieses DataSource-Objekts erstellt werden.|  
|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt einen **booleschen** Wert zurück, mit dem angegeben wird, ob das Senden von **String**-Parametern an den Server im Unicode-Format aktiviert ist.|  
|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt den Namen des Computers zurück, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird.|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt die URL zurück, die zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.|  
|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt den Benutzernamen zurück, der zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.|  
|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt den Namen des Clientcomputers zurück, der zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.|  
|[getXAConnection](../../../connect/jdbc/reference/getxaconnection-method-sqlserverxadatasource.md)|Stellt eine physische Datenbankverbindung her, die in einer verteilten Transaktion verwendet werden kann.|  
|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt einen **booleschen** Wert zurück, mit dem angegeben wird, ob das Konvertieren von SQL-Status in XOPEN-kompatible Status aktiviert ist.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md)|Gibt an, ob es sich bei diesem Objekt um einen Wrapper für die angegebene Schnittstelle handelt.|  
|[setApplicationIntent](../../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt den Wert der **applicationIntent**-Verbindungseigenschaft fest.|  
|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt den Anwendungsnamen fest.|  
|[setAuthenticationSceme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Gibt die Art der integrierten Sicherheit an, die für die Anwendung verwendet werden soll.|  
|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt den Datenbanknamen fest, mit dem eine Verbindung hergestellt werden soll.|  
|[setDescription](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt die Beschreibung der Datenquelle fest.|  
|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt den Namen des Failoverservers fest, der in einer Datenbankspiegelungskonfiguration verwendet wird.|  
|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanznamen fest.|  
|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt einen **booleschen** Wert fest, mit dem angegeben wird, ob die integratedSecurity-Eigenschaft aktiviert ist.|  
|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt einen **booleschen** Wert fest, mit dem angegeben wird, ob die lastUpdateCount-Eigenschaft aktiviert ist.|  
|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt einen Wert vom Typ **int** fest, mit dem angegeben wird, wie lange von der Datenbank bis zum Melden eines Sperrtimeouts gewartet werden soll (in Millisekunden).|  
|[setLoginTimeout](../../../connect/jdbc/reference/setlogintimeout-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt die Anzahl von Sekunden fest, die vom DataSource-Objekt bei der Verbindungsherstellung gewartet wird.|  
|[setLogWriter](../../../connect/jdbc/reference/setlogwriter-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt einen Zeichenausgabedatenstrom für alle Protokollierungs- und Ablaufverfolgungsmeldungen fest.|  
|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt den Wert der **multiSubnetFailover**-Verbindungseigenschaft fest.|  
|[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt das Kennwort fest, das zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet wird.|  
|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt die Portnummer fest, die für die Kommunikation mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet werden soll.|  
|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt den Standardcursortyp fest, der für alle Resultsets verwendet wird, die mithilfe dieses DataSource-Objekts erstellt werden.|  
|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt einen **booleschen** Wert fest, mit dem angegeben wird, ob das Senden von **String**-Parametern an den Server im Unicode-Format aktiviert ist.|  
|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt den Namen des Computers fest, auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird.|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt die URL fest, die zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.|  
|[setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt den Benutzernamen fest, der zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.|  
|[setWorkstationID](../../../connect/jdbc/reference/setworkstationid-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt den Namen des Clientcomputers fest, der zum Herstellen einer Verbindung mit der Datenquelle verwendet wird.|  
|[setXopenStates](../../../connect/jdbc/reference/setxopenstates-method-sqlserverdatasource.md)|(Geerbt von [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) Legt einen **booleschen** Wert fest, mit dem angegeben wird, ob das Konvertieren von SQL-Status in XOPEN-kompatible Status aktiviert ist.|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)|Gibt ein Objekt zurück, das die angegebene Schnittstelle implementiert, um den Zugriff auf die [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-spezifischen Methoden zu ermöglichen.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerConnectionPoolDataSource|getPooledConnection|  
|com.microsoft.sqlserver.jdbc.SQLServerDataSource|getApplicationName, getConnection, getDatabaseName, getDescription, getFailoverPartner, getInstanceName, getLastUpdateCount, getLockTimeout, getLoginTimeout, getLogWriter, getPortNumber, getSelectMethod, getSendStringParametersAsUnicode, getServerName, getURL, getUser, getWorkstationID, getXopenStates, setApplicationName, setDatabaseName, setDescription, setFailoverPartner, setInstanceName, setIntegratedSecurity, setLastUpdateCount, setLockTimeout, setLoginTimeout, setLogWriter, setPassword, setPortNumber, setSelectMethod, setSendStringParametersAsUnicode, setServerName, setURL, setUser, setWorkstationID, setXopenStates|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
|javax.sql.XADataSource|getLoginTimeout, getLogWriter, setLoginTimeout, setLogWriter|  
|javax.sql.ConnectionPoolDataSource|getLoginTimeout, getLogWriter, setLoginTimeout, setLogWriter|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerXADataSource-Klasse](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
