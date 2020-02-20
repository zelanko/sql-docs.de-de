---
title: Herstellen von Verbindungen mit SQL Server mit der integrierten Kerberos-Authentifizierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2215e9f6b6c8cd0e19c220d16ebc7a1520550a42
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026193"
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Herstellen von Verbindungen mit SQL Server mit der integrierten Kerberos-Authentifizierung

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Ab [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] können Anwendungen mithilfe der Verbindungseigenschaft **authenticationScheme** angeben, dass eine Verbindung mit einer Datenbank unter Verwendung der integrierten Kerberos-Authentifizierung Typ 4 hergestellt werden soll. Weitere Informationen zu Verbindungseigenschaften finden Sie unter [Festlegen von Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md). Weitere Informationen zu Kerberos finden Sie unter [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkID=100758).

Bei Verwendung der integrierten Authentifizierung mit dem Java-**Krb5LoginModule** können Sie das Modul mithilfe der [Klasse Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html) konfigurieren.

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] legt für Java-VMs von IBM die folgenden Eigenschaften fest:

- **useDefaultCcache = true**
- **moduleBanner = false**

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] legt für alle anderen Java-VMs die folgenden Eigenschaften fest:

- **useTicketCache = true**
- **doNotPrompt = true**

## <a name="remarks"></a>Bemerkungen

Vor [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] konnten Anwendungen die integrierte Authentifizierung (mit Kerberos oder NTLM, je nach Verfügbarkeit) mithilfe der Verbindungseigenschaft **integratedSecurity** und durch Verweisen auf **sqljdbc_auth.dll** angeben, wie unter [Erstellen der Verbindungs-URL](../../connect/jdbc/building-the-connection-url.md) beschrieben.

Ab [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] können Anwendungen mit der Verbindungseigenschaft **authenticationScheme** angeben, dass eine Verbindung mit einer Datenbank mithilfe der integrierten Kerberos-Authentifizierung hergestellt werden soll, unter Verwendung der reinen Java-Kerberos-Implementierung:

- Wenn die integrierte Authentifizierung mit dem **Krb5LoginModule** ausgeführt werden soll, müssen Sie dennoch die Verbindungseigenschaft **integratedSecurity=true** angeben. Dann müssen Sie auch die Verbindungseigenschaft **authenticationScheme=JavaKerberos** angeben.

- Um weiterhin die integrierte Authentifizierung mit **sqljdbc_auth.dll** zu verwenden, geben Sie einfach die Verbindungseigenschaft **integratedSecurity=true** (und optional **authenticationScheme=NativeAuthentication**) an.

- Wenn Sie **authenticationScheme=JavaKerberos** angeben, ohne gleichzeitig **integratedSecurity=true** anzugeben, ignoriert der Treiber die Verbindungseigenschaft **authenticationScheme** und erwartet, dass der Benutzername und das Kennwort für die Anmeldeinformationen in der Verbindungszeichenfolge enthalten sind.

Wenn Verbindungen mit einer Datenquelle erstellt werden, können Sie das Authentifizierungsschema programmgesteuert mit **setAuthenticationScheme** und optional den SPN für Kerberos mithilfe von **setServerSpn** festlegen.

Zur Unterstützung der Kerberos-Authentifizierung wurde eine neue Protokollierung eingeführt: com.microsoft.sqlserver.jdbc.internals.KerbAuthentication. Weitere Informationen finden Sie unter [Ablaufverfolgung für Treibervorgänge](../../connect/jdbc/tracing-driver-operation.md).

Befolgen Sie beim Konfigurieren von Kerberos die folgenden Richtlinien:

1. Legen Sie **AllowTgtSessionKey** in der Registrierung für Windows auf 1 fest. Weitere Informationen finden Sie unter [Kerberos protocol registry entries and KDC configuration keys in Windows Server 2003 (KDC-Konfigurationsschlüssel in Windows Server 2003 und Kerberos-Protokoll-Registrierungseinträge)](https://support.microsoft.com/kb/837361).
2. Stellen Sie sicher, dass die Kerberos-Konfiguration (krb5.conf in UNIX-Umgebungen) auf den richtigen Bereich und KDC für Ihre Umgebung zeigt.
3. Initialisieren Sie den TGT-Cache mit "kinit" oder indem Sie sich bei der Domäne anmelden.
4. Bei Ausführung einer Anwendung, die **authenticationScheme=JavaKerberos** verwendet, unter dem Betriebssystem Windows Vista bzw. Windows 7 muss ein Standardbenutzerkonto verwendet werden. Wenn Sie jedoch die Anwendung unter einem Administratorkonto ausführen, muss sie mit Administratorberechtigungen ausgeführt werden.

> [!NOTE]  
> Das Verbindungsattribut „serverSpn“ wird nur vom Microsoft JDBC-Treiber 4.2 und höher unterstützt.

## <a name="service-principal-names"></a>Dienstprinzipalnamen

Ein Dienstprinzipalname (SPN, Service Principal Name) ist der Name, über den ein Client eine Instanz eines Diensts eindeutig identifiziert.

Sie können den SPN mithilfe der Verbindungseigenschaft **serverSpn** angeben oder ihn einfach vom Treiber erstellen lassen (Standardeinstellung). Diese Eigenschaft weist folgende Form auf: "MSSQLSvc/fqdn:port\@REALM", wobei „fqdn“ der vollqualifizierte Domänenname, „port“ die Portnummer und „REALM“ der Kerberos-Bereich der SQL Server-Instanz in Großbuchstaben ist. Der Bereichsteil dieser Eigenschaft ist optional, wenn der Standardbereich Ihrer Kerberos-Konfiguration der gleiche Bereich wie der des Servers ist, und wird standardmäßig nicht angegeben. Wenn Sie ein bereichsübergreifendes Authentifizierungsszenario unterstützen möchten, in dem sich der Standardbereich der Kerberos-Konfiguration vom Bereich des Servers unterscheidet, müssen Sie den SPN mithilfe der Eigenschaft „serverSpn“ angeben.

Der SPN könnte beispielsweise so aussehen: "MSSQLSvc/some-server.zzz.corp.contoso.com:1433\@ZZZZ.CORP.CONTOSO.COM"

Weitere Informationen zu Dienstprinzipalnamen (SPNs) finden Sie in folgendem Thema:

- [Verwenden der Kerberos-Authentifizierung in SQL Server](https://support.microsoft.com/kb/319723)

- [Verwenden von Kerberos mit SQL Server](https://go.microsoft.com/fwlink/?LinkId=207814)

> [!NOTE]  
> Vor Release 6.2 des JDBC-Treibers mussten Sie den **serverSpn** explizit festlegen, damit die bereichsübergreifende Kerberos-Authentifizierung ordnungsgemäß verwendet wurde.
>
> Ab Release 6.2 kann der Treiber den **serverSpn** standardmäßig erstellen, auch bei Verwendung der bereichsübergreifenden Kerberos-Authentifizierung. Sie können **serverSpn** jedoch weiterhin explizit festlegen.

## <a name="creating-a-login-module-configuration-file"></a>Erstellen einer Anmeldemodul-Konfigurationsdatei

Sie können optional eine Kerberos-Konfigurationsdatei angeben. Wenn keine Konfigurationsdatei angegeben wird, gelten die folgenden Einstellungen:

Sun-JVM  
 com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;

IBM-JVM  
 com.ibm.security.auth.module.Krb5LoginModule required useDefaultCcache = true;

Wenn Sie selbstständig eine Anmeldemodul-Konfigurationsdatei erstellen, muss die Datei das folgende Format aufweisen:

```java
<name> {  
    <LoginModule> <flag> <LoginModule options>;  
    <optional_additional_LoginModules, flags_and_options>;  
};  
```

Eine Anmeldemodul-Konfigurationsdatei enthält einen oder mehrere Einträge, die jeweils angeben, welche zugrunde liegende Authentifizierungstechnologie für eine bestimmte Anwendung bzw. für bestimmte Anwendungen verwendet werden soll. Beispiel:

```java
SQLJDBCDriver {  
   com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;  
};  
```

Jeder Eintrag der Anmeldemodul-Konfigurationsdatei besteht aus einem Namen, auf den ein oder mehrere LoginModule-spezifische Einträge folgen. Jeder LoginModule-spezifische Eintrag wird jeweils durch ein Semikolon abgeschlossen, und die gesamte Gruppe von LoginModule-spezifischen Einträgen wird von geschweiften Klammern umschlossen. Jeder Konfigurationsdateieintrag wird durch ein Semikolon abgeschlossen.

Für den Treiber kann nicht nur festgelegt werden, dass Kerberos-Anmeldeinformationen mit den Einstellungen in der Anmeldemodul-Konfigurationsdatei erhalten werden können. Stattdessen kann der Treiber auch vorhandene Anmeldeinformationen verwenden. Dies kann hilfreich sein, wenn die Anwendung Verbindungen mit den Anmeldeinformationen mehrerer Benutzer herstellen muss.

Der Treiber versucht zunächst vorhandene Anmeldeinformationen zu verwenden (sofern diese verfügbar sind), bevor er die Anmeldung mit dem angegebenen Anmeldemodul ausführt. Bei Ausführung von Code unter einem bestimmten Kontext mithilfe der `Subject.doAs`-Methode wird daher eine Verbindung mit den Anmeldeinformationen erstellt, die an den Aufruf von `Subject.doAs` übergeben werden.

Weitere Informationen finden Sie unter [JAAS Login Configuration File (JAAS-Anmeldekonfigurationsdatei)](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html) und [Class Krb5LoginModule (Klasse Krb5LoginModule)](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

Ab Version 6.2 des Microsoft-JDBC-Treibers kann der Name der Konfigurationsdatei für das Anmeldemodul optional mithilfe der Verbindungseigenschaft `jaasConfigurationName` übergeben werden. So kann jede Verbindung über eine eigene Anmeldekonfiguration verfügen.

## <a name="creating-a-kerberos-configuration-file"></a>Erstellen einer Kerberos-Konfigurationsdatei

Weitere Informationen zu Kerberos-Konfigurationsdateien finden Sie unter [Kerberos Requirements (Kerberos-Anforderungen)](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html).

Dies ist eine Konfiguration für eine Beispieldomäne. YYYY und ZZZZ sind durch die Domänennamen zu ersetzen.

```ini
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  

[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  

[realms]  
        YYYY.CORP.CONTOSO.COM = {  
  kdc = krbtgt/YYYY.CORP. CONTOSO.COM @ YYYY.CORP. CONTOSO.COM  
  default_domain = YYYY.CORP. CONTOSO.COM  
}  

        ZZZZ.CORP. CONTOSO.COM = {  
  kdc = krbtgt/ZZZZ.CORP. CONTOSO.COM @ ZZZZ.CORP. CONTOSO.COM  
  default_domain = ZZZZ.CORP. CONTOSO.COM  
}  

```

## <a name="enabling-the-domain-configuration-file-and-the-login-module-configuration-file"></a>Aktivieren der Domänenkonfigurationsdatei und der Anmeldemodul-Konfigurationsdatei

Sie können eine Domänenkonfigurationsdatei mit -Djava.security.krb5.conf aktivieren. Sie können eine Konfigurationsdatei für das Anmeldemodul mit **-Djava.security.auth.login.config** aktivieren.

Zum Starten der Anwendung kann beispielsweise der folgende Befehl verwendet werden:

```bash
Java.exe -Djava.security.auth.login.config=SQLJDBCDriver.conf -Djava.security.krb5.conf=krb5.ini <APPLICATION_NAME>  

```

## <a name="verifying-that-sql-server-can-be-accessed-via-kerberos"></a>Überprüfen des Zugriffs auf SQL Server über Kerberos

Führen Sie in SQL Server Management Studio die folgende Abfrage aus:

```sql
select auth_scheme from sys.dm_exec_connections where session_id=\@\@spid
```

Vergewissern Sie sich, dass Sie über die erforderliche Berechtigung zum Ausführen dieser Abfrage verfügen.

## <a name="constrained-delegation"></a>Eingeschränkte Delegierung

Ab Version 6.2 unterstützt der Microsoft-JDBC-Treiber die eingeschränkte Delegierung von Kerberos. Die delegierten Anmeldeinformationen können als org.ietf.jgss.GSSCredential-Objekt übergeben werden. Diese Anmeldeinformationen werden vom Treiber zum Herstellen der Verbindung verwendet.

```java
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>Kerberos-Verbindung mit Prinzipalname und Kennwort

Ab Version 6.2 kann der Microsoft-JDBC-Treiber eine Kerberos-Verbindung mithilfe des in der Verbindungszeichenfolge übergebenen Prinzipalnamens und Kennworts herstellen.

```java
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```

Die username-Eigenschaft erfordert keine Festlegung von REALM, wenn der Benutzer zum in der krb5.conf-Datei festgelegten „default_realm“ gehört. Wenn `userName` und `password` zusammen mit den Eigenschaften `integratedSecurity=true;` und `authenticationScheme=JavaKerberos;` festgelegt sind, wird die Verbindung mit „Kerberos-Prinzipal“ als Wert von „userName“ und dem bereitgestellten Kennwort hergestellt.

## <a name="using-kerberos-authentication-from-unix-machines-on-the-same-domain"></a>Verwenden der Kerberos-Authentifizierung auf UNIX-Computern in derselben Domäne

In diesem Leitfaden wird davon ausgegangen, dass bereits eine funktionierende Kerberos-Einrichtung vorhanden ist. Führen Sie den folgenden Code auf einem Windows-Computer mit funktionierender Kerberos-Authentifizierung aus, um zu überprüfen, ob diese Aussage zutreffend ist. Der Code gibt "Authentifizierungsschema: KERBEROS" an der Konsole aus, wenn die Ausführung erfolgreich war. Außer den bereitgestellten Laufzeitflags, Abhängigkeiten und Treibereinstellungen werden keine weiteren Einstellungen benötigt. Der gleiche Codeblock kann unter Linux ausgeführt werden, um erfolgreiche Verbindungen zu verifizieren.

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(1433); // change if necessary
ds.setIntegratedSecurity(true);
ds.setAuthenticationScheme("JavaKerberos");
ds.setDatabaseName("<database>");

try (Connection c = ds.getConnection(); Statement s = c.createStatement();
        ResultSet rs = s.executeQuery("select auth_scheme from sys.dm_exec_connections where session_id=@@spid")) {
    while (rs.next()) {
        System.out.println("Authentication Scheme: " + rs.getString(1));
    }
}
```

1. Binden Sie den Clientcomputer in dieselbe Domäne ein, in der sich der Server befindet.
2. (Optional) Legen Sie den Standardspeicherort für Kerberos-Tickets fest. Die bequemste Methode hierfür ist das Festlegen der Umgebungsvariable `KRB5CCNAME`.
3. Rufen Sie das Kerberos-Ticket ab, indem Sie ein neues Ticket generieren oder ein vorhandenes Ticket im Standardspeicherort für Kerberos-Tickets ablegen. Um ein Ticket zu generieren, verwenden Sie einfach ein Terminal, und initialisieren Sie das Ticket über `kinit USER@DOMAIN.AD`, wobei es sich bei "USER" und "DOMAIN.AD" um den Prinzipal bzw. die Domäne handelt. Zum Beispiel `kinit SQL_SERVER_USER03@MICROSOFT.COM`. Das Ticket wird im Standardspeicherort oder im Pfad `KRB5CCNAME` generiert, falls dieser festgelegt wurde.
4. Geben Sie das Kennwort ein, wenn Sie im Terminal dazu aufgefordert werden.
5. Überprüfen Sie die Anmeldeinformationen im Ticket über `klist`, und vergewissern Sie sich, dass es sich um die Anmeldeinformationen handelt, die Sie für die Authentifizierung verwenden möchten.
6. Führen Sie den obigen Beispielcode aus, und vergewissern Sie sich, dass die Kerberos-Authentifizierung erfolgreich war.

## <a name="see-also"></a>Weitere Informationen

[Verbinden mit SQL Server mit dem JDBC-Treiber](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
