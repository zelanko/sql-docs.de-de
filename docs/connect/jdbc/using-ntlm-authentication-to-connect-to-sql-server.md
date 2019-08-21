---
title: Verwenden der NTLM-Authentifizierung zum Herstellen einer Verbindung mit SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: lilgreenbird
ms.author: v-susanh
manager: kenvh
ms.openlocfilehash: 2fab4794544ada07e0bf5e690da35b72ad6b7421
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026101"
---
# <a name="using-ntlm-authentication-to-connect-to-sql-server"></a>Verwenden der NTLM-Authentifizierung zum Herstellen einer Verbindung mit SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Ermöglicht es einer Anwendung, mithilfe der Verbindungs Eigenschaft **authenticationScheme** anzugeben, dass eine Verbindung mit einer Datenbank mithilfe der NTLM v2-Authentifizierung hergestellt werden soll. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 

Die folgenden Eigenschaften werden auch für die NTLM-Authentifizierung verwendet:

- **Domain = Domänen Name** optionale
- **Benutzer = Benutzername**
- **password = password**
- **IntegratedSecurity = true**

Abgesehen von der **Domäne**sind die anderen Eigenschaften obligatorisch. der Treiber löst einen Fehler aus, wenn ein beliebiger Wert vorhanden ist, wenn die **NTLM** authenticationScheme-Eigenschaft verwendet wird. 

Weitere Informationen zu Verbindungs Eigenschaften finden Sie unter [Festlegen der Verbindungs Eigenschaften](../../connect/jdbc/setting-the-connection-properties.md). Weitere Informationen zum Microsoft NTLM-Authentifizierungsprotokoll finden Sie unter [Microsoft NTLM](https://docs.microsoft.com/windows/desktop/SecAuthN/microsoft-ntlm).

## <a name="remarks"></a>Remarks

Informationen zur Beschreibung der SQL Server-Einstellungen, die das Verhalten der NTLM-Authentifizierung steuern, finden Sie unter [Netzwerksicherheit: LAN Manager-Authentifizierungs Ebene](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-security-lan-manager-authentication-level) . 

## <a name="logging"></a>Protokollierung

Zur Unterstützung der NTLM-Authentifizierung wurde eine neue Protokollierung hinzugefügt: com.microsoft.sqlserver.jdbc.internals.NTLMAuthentication. Weitere Informationen finden Sie unter [Tracing Driver Operation (Ablaufverfolgung für Treibervorgänge)](../../connect/jdbc/tracing-driver-operation.md).

## <a name="datasource"></a>DataSource

Wenn Sie eine Datenquelle zum Erstellen von Verbindungen verwenden, können die NTLM-Eigenschaften Programm gesteuert mithilfe von **setauthenticationscheme**, **setdomain**und (optional) **setserverspn**festgelegt werden.

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(1433); // change if necessary
ds.setIntegratedSecurity(true);
ds.setAuthenticationScheme("NTLM");
ds.setDomain("<domainName>");
ds.setUser("<userName>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setServerSpn("<serverSpn");

try (Connection c = ds.getConnection(); Statement s = c.createStatement();
        ResultSet rs = s.executeQuery("select auth_scheme from sys.dm_exec_connections where session_id=@@spid")) {
    while (rs.next()) {
        System.out.println("Authentication Scheme: " + rs.getString(1));
    }
}
```

## <a name="service-principal-names"></a>Dienstprinzipalnamen

Ein Dienstprinzipalname (SPN, Service Principal Name) ist der Name, über den ein Client eine Instanz eines Diensts eindeutig identifiziert.

Sie können den SPN mithilfe der Verbindungseigenschaft **serverSpn** angeben oder ihn vom Treiber erstellen lassen (Standardeinstellung). Diese Eigenschaft kann in der Form „MSSQLSvc/fqdn:port\@REALM“ angegeben werden, wobei „fqdn“ den vollqualifizierten Domänennamen, „port“ die Portnummer und „REALM“ den Bereich des SQL Server-Computers in Großbuchstaben darstellen. Der Bereichs Teil dieser Eigenschaft ist optional, da der Standardbereich mit dem Bereich des Servers identisch ist.

Der SPN könnte beispielsweise wie folgt aussehen: "MSSQLSvc/some-Server. zzz. Corp. CSO. com: 1433"

Weitere Informationen zu Dienstprinzipalnamen (SPNs) finden Sie in folgendem Thema:

- [Unterstützung von Dienstprinzipalnamen (SPN) in Clientverbindungen](https://docs.microsoft.com/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections?view=sql-server-2017)

> [!NOTE]  
> Das Verbindungsattribut „serverSpn“ wird nur vom Microsoft JDBC-Treiber 4.2 und höher unterstützt.

> Vor der Version 6,2 des JDBC-Treibers müssen Sie den **ServerSPN**explizit festlegen. Ab Version 6,2 kann der Treiber den **Server-SPN** standardmäßig erstellen, obwohl **ServerSPN** auch explizit verwendet werden kann.

## <a name="security-risks"></a>Sicherheitsrisiken

Das NTLM-Protokoll ist ein altes Authentifizierungsprotokoll mit unterschiedlichen Sicherheitsrisiken, das ein Sicherheitsrisiko darstellt. Es basiert auf einem relativ schwachen kryptografieschema und ist anfällig für verschiedene Angriffe. Es wird durch Kerberos ersetzt, das viel sicherer und empfehlenswert ist. Die NTLM-Authentifizierung sollte nur in einer sicheren vertrauenswürdigen Umgebung oder nicht verwendet werden, wenn Kerberos nicht verwendet werden kann.

Unter [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] stützt nur NTLM v2, das über einige Sicherheitsverbesserungen im Vergleich zum ursprünglichen v1-Protokoll verfügt. Außerdem wird empfohlen, den erweiterten Schutz zu aktivieren oder die SSL-Verschlüsselung zu verwenden, um die Sicherheit zu erhöhen. 

Weitere Informationen zum Aktivieren von erweiterter Schutz und finden Sie unter:

- [Herstellen einer Verbindung mit der Datenbank-Engine unter Verwendung von Erweiterter Schutz](../../database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection.md)

Weitere Informationen zum Herstellen einer Verbindung mit der SSL-Verschlüsselung finden Sie unter:

- [Herstellen von Verbindungen mit SSL-Verschlüsselung](../../connect/jdbc/connecting-with-ssl-encryption.md)

> [!NOTE]
> Bei Version 7,4 wird das Aktivieren **von** erweiterter Schutz und Verschlüsselung nicht unterstützt.

## <a name="see-also"></a>Siehe auch

[Verbinden mit SQL Server mit dem JDBC-Treiber](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
