---
title: 'DSN-Verbindung Zeichenfolgen-Schlüsselwörter für die ODBC-Treibers: SQL Server | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/04/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: MightyPen
ms.author: v-jizho2
author: karinazhou
manager: craigg
ms.openlocfilehash: e2db3b8df9ea63c16e0e96af9df42b7c22adaf80
ms.sourcegitcommit: b3d84abfa4e2922951430772c9f86dce450e4ed1
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56662874"
---
# <a name="dsn-and-connection-string-keywords-and-attributes"></a>Schlüsselwörter und Attribute von DNS- und Verbindungszeichenfolgen

Diese Seite listet die Schlüsselwörter für Verbindungszeichenfolgen und DSNs sowie die Verbindungsattribute, SQLSetConnectAttr und SQLGetConnectAttr, in der ODBC-Treiber für SQL Server verfügbar.

## <a name="supported-dsnconnection-string-keywords-and-connection-attributes"></a>Unterstützt die Schlüsselwörter für Verbindungszeichenfolgen DSN-Verbindung sowie die Verbindungsattribute

Die folgende Tabelle enthält die verfügbaren Schlüsselwörter und die Attribute für jede Plattform (Linux L:; M: Mac W-Windows). Klicken Sie auf das Schlüsselwort oder das Attribut für weitere Details.

| DSN / Verbindungszeichenfolgen-Schlüsselwort | Verbindungsattribut | Platform |
|-|-|-|
| [Addr](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [Adresse](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [AnsiNPW](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_ANSI_NPW](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssansinpw) | LMW |
| [APP](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [ApplicationIntent](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_APPLICATION_INTENT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssapplicationintent) | LMW |
| [AttachDBFileName](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_ATTACHDBFILENAME](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssattachdbfilename) | LMW |
| [Authentifizierung](../../connect/odbc/dsn-connection-string-attribute.md#authentication---sqlcoptssauthentication) | [SQL_COPT_SS_AUTHENTICATION](../../connect/odbc/dsn-connection-string-attribute.md#authentication---sqlcoptssauthentication) | LMW |
| [AutoTranslate](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_TRANSLATE](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsstranslate) | LMW |
| [ColumnEncryption](../../connect/odbc/dsn-connection-string-attribute.md#columnencryption---sqlcoptsscolumnencryption) | [SQL_COPT_SS_COLUMN_ENCRYPTION](../../connect/odbc/dsn-connection-string-attribute.md#columnencryption---sqlcoptsscolumnencryption) | LMW |
| [ConnectRetryCount](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) | [SQL_COPT_SS_CONNECT_RETRY_COUNT](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) | W |
| [ConnectRetryInterval](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) | [SQL_COPT_SS_CONNECT_RETRY_INTERVAL](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) | W |
| [Datenbank](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_ATTR_CURRENT_CATALOG](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | LMW |
| [Beschreibung](../../connect/odbc/dsn-connection-string-attribute.md#description) | | LMW |
| [Treiber](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [DSN](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [Encrypt](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_ENCRYPT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssencrypt) | LMW |
| [Failover_Partner](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_FAILOVER_PARTNER](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssfailoverpartner) | W |
| [FailoverPartnerSPN](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_FAILOVER_PARTNER_SPN](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | W |
| [FileDSN](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [KeystoreAuthentication](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#connection-string-keywords) | | LMW |
| [KeystorePrincipalId](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#connection-string-keywords) | | LMW |
| [KeystoreSecret](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#connection-string-keywords) | | LMW |
| [Sprache](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [MARS_Connection](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_MARS_ENABLED](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssmarsenabled) | LMW |
| [MultiSubnetFailover](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_MULTISUBNET_FAILOVER](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssmultisubnetfailover) | LMW |
| [Net](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [Network](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [PWD](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [QueryLog_On](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_QUERY](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfquery) | W |
| [QueryLogFile](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_QUERY_LOG](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfquerylog) | W |
| [QueryLogTIme](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_QUERY_INTERVAL](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfqueryinterval) | W |
| [QuotedId](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_QUOTED_IDENT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssquotedident) | LMW |
| [Regional](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [SaveFile](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [Server](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [ServerSPN](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_SERVER_SPN](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | LMW |
| [StatsLog_On](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_DATA](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfdata) | W |
| [StatsLogFile](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_DATA_LOG](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfdatalog) | W |
| [TransparentNetworkIPResolution](../../connect/odbc/dsn-connection-string-attribute.md#transparentnetworkipresolution---sqlcoptsstnir) | [SQL_COPT_SS_TNIR](../../connect/odbc/dsn-connection-string-attribute.md#transparentnetworkipresolution---sqlcoptsstnir) | LMW |
| [Trusted_Connection](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_INTEGRATED_SECURITY](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssintegratedsecurity) | LMW |
| [TrustServerCertificate](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_TRUST_SERVER_CERTIFICATE](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsstrustservercertificate) | LMW |
| [UID](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [UseFMTONLY](../../connect/odbc/dsn-connection-string-attribute.md#usefmtonly) | | LMW |
| [WSID](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| | [SQL_ATTR_ACCESS_MODE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_ACCESS_MODE) | LMW |
| | [SQL_ATTR_ASYNC_DBC_EVENT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_ASYNC_DBC_PCALLBACK](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_ASYNC_DBC_PCONTEXT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_ASYNC_ENABLE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_AUTO_IPD](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | LMW |
| | [SQL_ATTR_AUTOCOMMIT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_AUTOCOMMIT) | LMW |
| | [SQL_ATTR_CONNECTION_DEAD](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | LMW |
| | [SQL_ATTR_CONNECTION_TIMEOUT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | LMW |
| | [SQL_ATTR_DBC_INFO_TOKEN](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | LMW |
| | [SQL_ATTR_LOGIN_TIMEOUT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_LOGIN_TIMEOUT) | LMW |
| | [SQL_ATTR_METADATA_ID](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | LMW |
| | [SQL_ATTR_ODBC_CURSORS](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_ODBC_CURSORS) | LMW |
| | [SQL_ATTR_PACKET_SIZE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_PACKET_SIZE) | LMW |
| | [SQL_ATTR_QUIET_MODE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_QUIET_MODE) | LMW |
| | [SQL_ATTR_RESET_CONNECTION](../../odbc/reference/develop-driver/upgrading-a-3-5-driver-to-a-3-8-driver.md#connection-pooling) <br> (SQL_COPT_SS_RESET_CONNECTION) | LMW |  
| | [SQL_ATTR_TRACE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_OPT_TRACE) | LMW |
| | [SQL_ATTR_TRACEFILE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_OPT_TRACEFILE) | LMW |
| | [SQL_ATTR_TRANSLATE_LIB](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_TRANSLATE_DLL) | LMW |
| | [SQL_ATTR_TRANSLATE_OPTION](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_TRANSLATE_OPTION) | LMW |
| | [SQL_ATTR_TXN_ISOLATION](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_TXN_ISOLATION) | LMW |
| | [SQL_COPT_SS_ACCESS_TOKEN](dsn-connection-string-attribute.md#sqlcoptssaccesstoken) | LMW |
| | [SQL_COPT_SS_ANSI_OEM](dsn-connection-string-attribute.md#sqlcoptssansioem)| W |
| | [SQL_COPT_SS_BCP](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssbcp) | LMW |
| | [SQL_COPT_SS_BROWSE_CACHE_DATA](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) | LMW |
| | [SQL_COPT_SS_BROWSE_CONNECT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssbrowseconnect) | LMW |
| | [SQL_COPT_SS_BROWSE_SERVER](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssbrowseserver) | LMW |
| | [SQL_COPT_SS_CEKEYSTOREDATA](dsn-connection-string-attribute.md#sqlcoptsscekeystoredata) | LMW |
| | [SQL_COPT_SS_CEKEYSTOREPROVIDER](dsn-connection-string-attribute.md#sqlcoptsscekeystoreprovider) | LMW |
| | [SQL_COPT_SS_CLIENT_CONNECTION_ID](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) | LMW |
| | [SQL_COPT_SS_CONCAT_NULL](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssconcatnull) | LMW |
| | [SQL_COPT_SS_CONNECTION_DEAD](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssconnectiondead) | LMW |
| | [SQL_COPT_SS_ENLIST_IN_DTC](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssenlistindtc) | W |
| | [SQL_COPT_SS_ENLIST_IN_XA](dsn-connection-string-attribute.md#sql_copt_ss_enlist_in_xa) | LMW |
| | [SQL_COPT_SS_FALLBACK_CONNECT](dsn-connection-string-attribute.md#sqlcoptssfallbackconnect) | LMW |
| | [SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | LMW |
| | [SQL_COPT_SS_MUTUALLY_AUTHENTICATED](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | LMW |
| | [SQL_COPT_SS_OLDPWD](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssoldpwd) | LMW |
| | [SQL_COPT_SS_PERF_DATA_LOG_NOW](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfdatalognow) | W |
| | [SQL_COPT_SS_PRESERVE_CURSORS](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsspreservecursors) | LMW |
| | [SQL_COPT_SS_TXN_ISOLATION](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsstxnisolation) | LMW |
| | [SQL_COPT_SS_USER_DATA](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssuserdata) | LMW |
| | [SQL_COPT_SS_WARN_ON_CP_ERROR](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsswarnoncperror) | LMW |


Hier sind einige Schlüsselwörter für Verbindungszeichenfolgen und Verbindungsattribute, die in nicht dokumentiert sind [Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md), [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) und [SQLSetConnectAttr-Funktion](../../odbc/reference/syntax/sqlsetconnectattr-function.md).

### <a name="description"></a>und Beschreibung

Dient zum Beschreiben der Datenquelle.

### <a name="sqlcoptssansioem"></a>SQL_COPT_SS_ANSI_OEM

Steuert, ANSI, OEM-Konvertierung von Daten. 

| Attributwert | und Beschreibung |
|-|-|
| SQL_AO_OFF | (Standard) Übersetzung wird nicht ausgeführt. |
| SQL_AO_ON | Übersetzung erfolgt. |

### <a name="sqlcoptssfallbackconnect"></a>SQL_COPT_SS_FALLBACK_CONNECT

Steuert die Verwendung von SQL Server-Fallback-Verbindungen. Diese wird nicht mehr unterstützt.

| Attributwert | und Beschreibung |
|-|-|
| SQL_FB_OFF | (Standard) Fallback-Verbindungen sind deaktiviert. |
| SQL_FB_ON | Fallback-Verbindungen aktiviert sind. |



## <a name="new-connection-string-keywords-and-connection-attributes"></a>Neue Schlüsselwörter für Verbindungszeichenfolgen und Verbindungsattribute

###  <a name="authentication---sqlcoptssauthentication"></a>Authentifizierung – SQL_COPT_SS_AUTHENTICATION

Legt fest, den Authentifizierungsmodus zu verwenden, wenn die Verbindung mit SQL Server. Finden Sie unter [mithilfe von Azure Active Directory](using-azure-active-directory.md) für Weitere Informationen.

| Schlüsselwortwert | Attributwert | und Beschreibung |
|-|-|-|
| |SQL_AU_NONE|(Standard) Nicht festgelegt werden. Kombination aus anderen Attributen bestimmt den Authentifizierungsmodus an.|
|SqlPassword|SQL_AU_PASSWORD|SQL Server-Standardauthentifizierung mit Benutzername und Kennwort.|
|ActiveDirectoryIntegrated|SQL_AU_AD_INTEGRATED|Integrierte Azure Active Directory-Authentifizierung.|
|ActiveDirectoryPassword|SQL_AU_AD_PASSWORD|Azure Active Directory-Kennwortauthentifizierung.|
|ActiveDirectoryInteractive|SQL_AU_AD_INTERACTIVE|Interaktive Azure Active Directory-Authentifizierung.|
|ActiveDirectoryMsi|SQL_AU_AD_MSI|Azure Active Directory-MSI-Authentifizierung. Für die vom Benutzer zugewiesene Identität wird Benutzer-ID auf die Objekt-ID, der die Identität des Benutzers festgelegt. |
| |SQL_AU_RESET|Nicht festgelegt ist. Überschreibt alle DSN- oder Verbindungszeichenfolge.|

> [!NOTE]
> Bei Verwendung `Authentication` -Schlüsselwort oder das Attribut, explizit angeben `Encrypt` auf den gewünschten Wert in der Verbindungszeichenfolge festlegen / DSN / Verbindungsattribut. Finden Sie unter [Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) Details.

### <a name="columnencryption---sqlcoptsscolumnencryption"></a>ColumnEncryption - SQL_COPT_SS_COLUMN_ENCRYPTION

Steuert die transparente spaltenverschlüsselung (Always Encrypted). Finden Sie unter [mithilfe von Always Encrypted (ODBC)](using-always-encrypted-with-the-odbc-driver.md) für Weitere Informationen.

| Schlüsselwortwert | Attributwert | und Beschreibung |
|-|-|-|
|Aktiviert|SQL_CE_ENABLED|Ermöglicht, die immer verschlüsselt.|
|Disabled|SQL_CE_DISABLED|(Standard) Deaktiviert die immer verschlüsselt.|
| |SQL_CE_RESULTSETONLY|Ermöglicht die Entschlüsselung nur (Ergebnisse und Rückgabe von Werten).|

### <a name="transparentnetworkipresolution---sqlcoptsstnir"></a>TransparentNetworkIPResolution - SQL_COPT_SS_TNIR

Steuerelemente, versucht die transparente Netzwerk-IP-Adressauflösung-Funktion, die Interaktion mit MultiSubnetFailover um schnellere wiederverbindung zu ermöglichen. Finden Sie unter [mithilfe transparente Netzwerk-IP-Adressauflösung](using-transparent-network-ip-resolution.md) für Weitere Informationen.

| Schlüsselwortwert | Attributwert| und Beschreibung |
|-|-|-|
|Ja|SQL_IS_ON|(Standard) Aktiviert die transparente Netzwerk-IP-Adressauflösung.|
|Nein|SQL_IS_OFF|Deaktiviert die transparente Netzwerk-IP-Adressauflösung.|

### <a name="usefmtonly"></a>UseFMTONLY

Steuert die Verwendung von SET FMTONLY für Metadaten an, beim Herstellen einer Verbindung mit SQL Server 2012 und höher.

| Schlüsselwortwert | und Beschreibung |
|-|-|
|Nein|(Standard) Verwenden Sie Sp_describe_first_result_set für Metadaten, falls verfügbar. |
|Ja| Verwenden Sie SET FMTONLY für Metadaten. |

### <a name="sqlcoptssaccesstoken"></a>SQL_COPT_SS_ACCESS_TOKEN

Ermöglicht die Verwendung eines Zugriffstokens für Azure Active Directory zur Authentifizierung. Finden Sie unter [mithilfe von Azure Active Directory](using-azure-active-directory.md) für Weitere Informationen.

| Attributwert | und Beschreibung |
|-|-|
| NULL | (Standard) Kein Zugriffstoken angegeben wird. |
| ACCESSTOKEN* | Zeiger auf ein Zugriffstoken. |

### <a name="sqlcoptsscekeystoredata"></a>SQL_COPT_SS_CEKEYSTOREDATA

Kommuniziert mit einem geladenen Keystore-Anbieterbibliothek. Finden Sie unter transparent spaltenverschlüsselung für Steuerelemente (Always Encrypted). Dieses Attribut hat keinen Standardwert. Finden Sie unter [benutzerdefinierte Keystore-Anbieter](custom-keystore-providers.md) für Weitere Informationen.

| Attributwert | und Beschreibung |
|-|-|
| CEKEYSTOREDATA * | Kommunikation-Datenstruktur für die Keystore-Anbieterbibliothek |

### <a name="sqlcoptsscekeystoreprovider"></a>SQL_COPT_SS_CEKEYSTOREPROVIDER

Lädt eine Keystore-Anbieterbibliothek für Always Encrypted, oder ruft die Namen der geladenen Keystore-Anbieter-Bibliotheken. Finden Sie unter [benutzerdefinierte Keystore-Anbieter](custom-keystore-providers.md) für Weitere Informationen. Dieses Attribut hat keinen Standardwert.

| Attributwert | und Beschreibung |
|-|-|
| char * | Pfad zu einem Keystore-Anbieterbibliothek |

### <a name="sqlcoptssenlistinxa"></a>SQL_COPT_SS_ENLIST_IN_XA

Um XA-Transaktionen mit einem XA-kompatiblen Transaktion Prozessor (TP) zu aktivieren, muss die Anwendung aufrufen **SQLSetConnectAttr** mit SQL_COPT_SS_ENLIST_IN_XA und einen Zeiger auf ein `XACALLPARAM` Objekt. Diese Option wird unter Windows, (17.3 und höher) Linux und Mac unterstützt.
```
SQLSetConnectAttr(hdbc, SQL_COPT_SS_ENLIST_IN_XA, param, SQL_IS_POINTER);  // XACALLPARAM *param
``` 
 Um eine XA-Transaktion mit einer ODBC-Verbindung verknüpfen möchten, geben Sie "true" oder "false" mit SQL_COPT_SS_ENLIST_IN_XA anstelle der Zeiger beim Aufrufen **SQLSetConnectAttr**. Dies gilt nur für Windows und nicht zum Angeben von XA-Vorgänge durch eine Clientanwendung verwendet werden. 
 ```
SQLSetConnectAttr(hdbc, SQL_COPT_SS_ENLIST_IN_XA, (SQLPOINTER)TRUE, 0);
``` 

|value|und Beschreibung|Plattformen|  
|-----------|-----------------|-----------------|  
|XACALLPARAM Objekt *|Der Zeiger auf das `XACALLPARAM`-Objekt.|Windows, Linux und Mac|
|TRUE|Ordnet die ODBC-Verbindung die XA-Transaktion zu. Alle entsprechenden Datenbankaktivitäten werden unter dem Schutz der XA-Transaktion durchgeführt.|Windows|  
|FALSE|Hebt die Zuordnung für die Transaktion mit der ODBC-Verbindung.|Windows|

 Finden Sie unter [mithilfe der XA-Transaktionen](../../connect/odbc/use-xa-with-dtc.md) für Weitere Informationen zu XA-Transaktionen.
