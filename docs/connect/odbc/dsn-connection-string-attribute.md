---
title: Schlüsselwörter für DSN und Verbindungszeichenfolgen für den ODBC-Treiber – SQL Server | Microsoft Dokumentation
ms.custom: ''
ms.date: 02/04/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: MightyPen
ms.author: v-jizho2
author: karinazhou
ms.openlocfilehash: 7350fd7556040cded7f84db3ab9112ddfe7f816d
ms.sourcegitcommit: e821cd8e5daf95721caa1e64c2815a4523227aa4
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702795"
---
# <a name="dsn-and-connection-string-keywords-and-attributes"></a>Schlüsselwörter und Attribute von DNS- und Verbindungszeichenfolgen

Auf dieser Seite sind die Schlüsselwörter für Verbindungszeichenfolgen und für DSN sowie Verbindungsattribute für die Funktionen „SQLSetConnectAttr“ und „SQLGetConnectAttr“ aufgelistet, die im Rahmen des ODBC-Treibers für SQL Server verfügbar sind.

## <a name="supported-dsnconnection-string-keywords-and-connection-attributes"></a>Unterstützte Schlüsselwörter für DSN/Verbindungszeichenfolgen und Verbindungsattribute

In der folgenden Tabelle sind die verfügbaren Schlüsselwörter und Attribute nach Plattform aufgelistet (L: Linux, M: Max, W: Windows). Klicken Sie auf das Schlüsselwort oder das Attribut, um detailliertere Informationen zu erhalten.

| DSN / Verbindungszeichenfolgen-Schlüsselwort | Verbindungsattribut | Platform |
|-|-|-|
| [Addr](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [Adresse](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [AnsiNPW](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_ANSI_NPW](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssansinpw) | LMW |
| [APP](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [ApplicationIntent](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_APPLICATION_INTENT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssapplicationintent) | LMW |
| [AttachDBFileName](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_ATTACHDBFILENAME](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssattachdbfilename) | LMW |
| [Authentifizierung](../../connect/odbc/dsn-connection-string-attribute.md#authentication---sql_copt_ss_authentication) | [SQL_COPT_SS_AUTHENTICATION](../../connect/odbc/dsn-connection-string-attribute.md#authentication---sql_copt_ss_authentication) | LMW |
| [AutoTranslate](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_TRANSLATE](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsstranslate) | LMW |
| [ColumnEncryption](../../connect/odbc/dsn-connection-string-attribute.md#columnencryption---sql_copt_ss_column_encryption) | [SQL_COPT_SS_COLUMN_ENCRYPTION](../../connect/odbc/dsn-connection-string-attribute.md#columnencryption---sql_copt_ss_column_encryption) | LMW |
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
| [KeepAlive](../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md) (v 17.4 und höher, nur DSN)| | LMW |
| [Keepaliveingeterval](../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md) (v 17.4 und höher, nur DSN) | | LMW |
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
| [TransparentNetworkIPResolution](../../connect/odbc/dsn-connection-string-attribute.md#transparentnetworkipresolution---sql_copt_ss_tnir) | [SQL_COPT_SS_TNIR](../../connect/odbc/dsn-connection-string-attribute.md#transparentnetworkipresolution---sql_copt_ss_tnir) | LMW |
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
| | [SQL_COPT_SS_ACCESS_TOKEN](dsn-connection-string-attribute.md#sql_copt_ss_access_token) | LMW |
| | [SQL_COPT_SS_ANSI_OEM](dsn-connection-string-attribute.md#sql_copt_ss_ansi_oem)| W |
| | [SQL_COPT_SS_BCP](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssbcp) | LMW |
| | [SQL_COPT_SS_BROWSE_CACHE_DATA](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) | LMW |
| | [SQL_COPT_SS_BROWSE_CONNECT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssbrowseconnect) | LMW |
| | [SQL_COPT_SS_BROWSE_SERVER](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssbrowseserver) | LMW |
| | [SQL_COPT_SS_CEKEYSTOREDATA](dsn-connection-string-attribute.md#sql_copt_ss_cekeystoredata) | LMW |
| | [SQL_COPT_SS_CEKEYSTOREPROVIDER](dsn-connection-string-attribute.md#sql_copt_ss_cekeystoreprovider) | LMW |
| | [SQL_COPT_SS_CLIENT_CONNECTION_ID](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) | LMW |
| | [SQL_COPT_SS_CONCAT_NULL](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssconcatnull) | LMW |
| | [SQL_COPT_SS_CONNECTION_DEAD](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssconnectiondead) | LMW |
| | [SQL_COPT_SS_ENLIST_IN_DTC](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssenlistindtc) | W |
| | [SQL_COPT_SS_ENLIST_IN_XA](dsn-connection-string-attribute.md#sql_copt_ss_enlist_in_xa) | LMW |
| | [SQL_COPT_SS_FALLBACK_CONNECT](dsn-connection-string-attribute.md#sql_copt_ss_fallback_connect) | LMW |
| | [SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | LMW |
| | [SQL_COPT_SS_MUTUALLY_AUTHENTICATED](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | LMW |
| | [SQL_COPT_SS_OLDPWD](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssoldpwd) | LMW |
| | [SQL_COPT_SS_PERF_DATA_LOG_NOW](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfdatalognow) | W |
| | [SQL_COPT_SS_PRESERVE_CURSORS](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsspreservecursors) | LMW |
| | [SQL_COPT_SS_TXN_ISOLATION](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsstxnisolation) | LMW |
| | [SQL_COPT_SS_USER_DATA](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssuserdata) | LMW |
| | [SQL_COPT_SS_WARN_ON_CP_ERROR](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsswarnoncperror) | LMW |


Hier sind einige Schlüsselwörter für Verbindungszeichenfolgen und Verbindungsattribute aufgeführt, die nicht in den Artikeln [Using Connection String Keywords with SQL Server Native Client (Verwenden von Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client)](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md), [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) und [SQLSetConnectAttr Function (SQLSetConnectAttr-Funktion)](../../odbc/reference/syntax/sqlsetconnectattr-function.md) dokumentiert sind.

### <a name="description"></a>und Beschreibung

Wird zum Beschreiben der Datenquelle verwendet.

### <a name="sqlcoptssansioem"></a>SQL_COPT_SS_ANSI_OEM

Steuert die ANSI-in-OEM-Konvertierung. 

| Attributwert | und Beschreibung |
|-|-|
| SQL_AO_OFF | (Standard) Keine Zeichenübersetzung wird durchgeführt. |
| SQL_AO_ON | Zeichenübersetzung wird durchgeführt. |

### <a name="sqlcoptssfallbackconnect"></a>SQL_COPT_SS_FALLBACK_CONNECT

Steuert die Verwendung von SQL Server-Fallbackverbindungen. Wird nicht mehr unterstützt.

| Attributwert | und Beschreibung |
|-|-|
| SQL_FB_OFF | (Standard) Fallbackverbindungen sind deaktiviert. |
| SQL_FB_ON | Fallbackverbindungen sind aktiviert. |



## <a name="new-connection-string-keywords-and-connection-attributes"></a>Neue Schlüsselwörter für Verbindungszeichenfolgen sowie Verbindungsattribute

###  <a name="authentication---sqlcoptssauthentication"></a>Authentifizierung – SQL_COPT_SS_AUTHENTICATION

Legt den Authentifizierungsmodus für die Verbindung mit SQL Server fest. Weitere Informationen finden Sie unter [Using Azure Active Directory (Verwenden von Azure Active Directory)](using-azure-active-directory.md).

| Schlüsselwortwert | Attributwert | und Beschreibung |
|-|-|-|
| |SQL_AU_NONE|(Standard) Nicht festgelegt. Die Kombination anderer Attribute bestimmt den Authentifizierungsmodus.|
|SqlPassword|SQL_AU_PASSWORD|SQL Server-Standardauthentifizierung mit Benutzername und Kennwort.|
|ActiveDirectoryIntegrated|SQL_AU_AD_INTEGRATED|Integrierte Azure Active Directory-Authentifizierung.|
|ActiveDirectoryPassword|SQL_AU_AD_PASSWORD|Azure Active Directory-Kennwortauthentifizierung.|
|ActiveDirectoryInteractive|SQL_AU_AD_INTERACTIVE|Interaktive Azure Active Directory-Authentifizierung.|
|ActiveDirectoryMsi|SQL_AU_AD_MSI|Authentifizierung bei Azure Active Directory mit einer verwalteten Dienstidentität. Für die Identität, die dem Benutzer zugewiesen wurde, ist die Benutzer-ID auf die Objekt-ID der Benutzeridentität festgelegt. |
| |SQL_AU_RESET|Nicht festgelegt. Überschreibt jeglichen DSN oder jegliche Verbindungszeichenfolgeeinstellung.|

> [!NOTE]
> Wenn das `Authentication`-Schlüsselwort oder -Attribut verwendet werden, legen Sie die `Encrypt`-Einstellung für die Verbindungszeichenfolge, DSN bzw. das Verbindungsattribut explizit auf den gewünschten Wert fest. Weitere Informationen finden Sie unter [Using Connection String Keywords with SQL Server Native Client (Verwenden von Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client)](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).

### <a name="columnencryption---sqlcoptsscolumnencryption"></a>ColumnEncryption - SQL_COPT_SS_COLUMN_ENCRYPTION

Steuert transparente Spaltenverschlüsselung (Always Encrypted). Weitere Informationen finden Sie unter [Using Always Encrypted with the ODBC Driver for SQL Server (Verwenden von Always Encrypted mit dem ODBC-Treiber für SQL Server)](using-always-encrypted-with-the-odbc-driver.md).

| Schlüsselwortwert | Attributwert | und Beschreibung |
|-|-|-|
|Aktiviert|SQL_CE_ENABLED|Aktiviert Always Encrypted.|
|Disabled|SQL_CE_DISABLED|(Standard) Deaktiviert Always Encrypted.|
| |SQL_CE_RESULTSETONLY|Aktiviert nur die Entschlüsselung (Ergebnisse und Rückgabewerte).|

### <a name="transparentnetworkipresolution---sqlcoptsstnir"></a>TransparentNetworkIPResolution - SQL_COPT_SS_TNIR

Steuert das Feature zur transparenten Netzwerk-IP-Adressauflösung, das mit MultiSubnetFailover interagiert, um erneute Verbindungsversuche zu beschleunigen. Weitere Informationen finden Sie unter [Using Transparent Network IP Resolution (Verwenden der transparenten Netzwerk-IP-Adressauflösung)](using-transparent-network-ip-resolution.md).

| Schlüsselwortwert | Attributwert| und Beschreibung |
|-|-|-|
|Ja|SQL_IS_ON|(Standard) Aktiviert die transparente Netzwerk-IP-Adressauflösung.|
|Nein|SQL_IS_OFF|Deaktiviert die transparente Netzwerk-IP-Adressauflösung.|

### <a name="usefmtonly"></a>UseFMTONLY

Steuert die Verwendung von „SET FMTONLY“ für Metadaten bei der Verbindung mit SQL Server 2012 und höheren Versionen.

| Schlüsselwortwert | und Beschreibung |
|-|-|
|Nein|(Standard) Verwenden von „sp_describe_first_result_set“ für Metadaten, wenn verfügbar. |
|Ja| Verwenden von „SET FMTONLY“ für Metadaten. |

### <a name="sqlcoptssaccesstoken"></a>SQL_COPT_SS_ACCESS_TOKEN

Ermöglicht die Verwendung eines Zugriffstokens für Azure Active Directory zur Authentifizierung. Weitere Informationen finden Sie unter [Using Azure Active Directory (Verwenden von Azure Active Directory)](using-azure-active-directory.md).

| Attributwert | und Beschreibung |
|-|-|
| NULL | (Standard) Kein Zugriffstoken steht zur Verfügung. |
| ACCESSTOKEN* | Zeiger zu einem Zugriffstoken. |

### <a name="sqlcoptsscekeystoredata"></a>SQL_COPT_SS_CEKEYSTOREDATA

Kommuniziert mit einer geladenen Keystore-Anbieterbibliothek. Steuert transparente Spaltenverschlüsselung (Always Encrypted). Dieses Attribut hat keinen Standardwert. Weitere Informationen finden Sie unter [Custom Keystore Providers (Benutzerdefinierte Keystore-Anbieter)](custom-keystore-providers.md).

| Attributwert | und Beschreibung |
|-|-|
| CEKEYSTOREDATA * | Kommunikationsdatenstruktur für die Keystore-Anbieterbibliothek |

### <a name="sqlcoptsscekeystoreprovider"></a>SQL_COPT_SS_CEKEYSTOREPROVIDER

Lädt eine Keystore-Anbieterbibliothek für Always Encrypted oder ruft die Namen der geladenen Keystore-Anbieterbibliotheken ab. Weitere Informationen finden Sie unter [Custom Keystore Providers (Benutzerdefinierte Keystore-Anbieter)](custom-keystore-providers.md). Dieses Attribut hat keinen Standardwert.

| Attributwert | und Beschreibung |
|-|-|
| char * | Pfad zur Keystore-Anbieterbibliothek |

### <a name="sqlcoptssenlistinxa"></a>SQL_COPT_SS_ENLIST_IN_XA

Wenn XA-Transaktionen mit einem XA-konformen Transaktionsprozessor (TP) aktiviert werden sollen, muss die Anwendung mit „SQL_COPT_SS_ENLIST_IN_XA“ die Funktion **SQLSetConnectAttr** sowie einen Zeiger zu einem `XACALLPARAM`-Objekt aufrufen. Diese Option wird unter Windows (ab 17.3), Linux und Mac unterstützt.
```
SQLSetConnectAttr(hdbc, SQL_COPT_SS_ENLIST_IN_XA, param, SQL_IS_POINTER);  // XACALLPARAM *param
``` 
 Wenn eine XA-Transaktion nur einer ODBC-Verbindung zugeordnet werden soll, stellen Sie mit „SQL_COPT_SS_ENLIST_IN_XA“ beim Aufrufen von **SQLSetConnectAttr** entweder TRUE oder FALSE statt des Zeigers bereit. Dies ist nur unter Windows gültig und kann nicht dazu verwendet werden, um XA-Vorgänge über eine Clientanwendung anzugeben. 
 ```
SQLSetConnectAttr(hdbc, SQL_COPT_SS_ENLIST_IN_XA, (SQLPOINTER)TRUE, 0);
``` 

|value|und Beschreibung|Plattformen|  
|-----------|-----------------|-----------------|  
|XACALLPARAM object*|Der Zeiger auf das `XACALLPARAM`-Objekt.|Windows, Linux und Mac|
|TRUE|Ordnet die XA-Transaktion der ODBC-Verbindung zu. Alle entsprechenden Datenbankaktivitäten werden unter dem Schutz der XA-Transaktion durchgeführt.|Windows|  
|FALSE|Hebt die Zuordnung der XA-Transaktion zur ODBC-Verbindung auf.|Windows|

 Weitere Informationen zu XA-Transaktionen finden Sie unter [Using XA Tansactions (Verwenden von XA-Transaktionen)](../../connect/odbc/use-xa-with-dtc.md).
