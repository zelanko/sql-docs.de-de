---
title: Verwenden der integrierten Kerberos-Authentifizierung für Verbindungen mit SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 894da21c079b776524c07cab8b8f223bae769aee
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916233"
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Herstellen von Verbindungen mit SQL Server mit der integrierten Kerberos-Authentifizierung

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Ab [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] können Anwendungen mithilfe der Verbindungseigenschaft **authenticationScheme** angeben, dass eine Verbindung mit einer Datenbank unter Verwendung der integrierten Kerberos-Authentifizierung Typ 4 hergestellt werden soll. Weitere Informationen zu Verbindungs Eigenschaften finden Sie unter [Festlegen der Verbindungs Eigenschaften](../../connect/jdbc/setting-the-connection-properties.md) . Weitere Informationen zu Kerberos finden Sie unter [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkID=100758).

Bei Verwendung der integrierten Authentifizierung mit dem Java-**Krb5LoginModule** können Sie das Modul mithilfe der [Klasse Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html) konfigurieren.

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] legt für Java-VMs von IBM die folgenden Eigenschaften fest:

- **useDefaultCcache = true**
- **modulebanner = false**

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] legt für alle anderen Java-VMs die folgenden Eigenschaften fest:

- **useTicketCache = true**
- **doNotPrompt = true**

## <a name="remarks"></a>Remarks

Vor konnten Anwendungen die integrierte Authentifizierung (unter Verwendung von Kerberos oder NTLM, je nach Verfügbarkeit) mithilfe der **IntegratedSecurity** -Verbindungs Eigenschaft und durch Verweis auf **sqljdbc_auth. dll angeben.** [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] wird unter [aufbauen der Verbindungs-URL](../../connect/jdbc/building-the-connection-url.md)beschrieben.

Ab [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] können Anwendungen mit der Verbindungseigenschaft **authenticationScheme** angeben, dass eine Verbindung mit einer Datenbank mithilfe der integrierten Kerberos-Authentifizierung hergestellt werden soll, unter Verwendung der reinen Java-Kerberos-Implementierung:

- Wenn Sie die integrierte Authentifizierung mit **Krb5LoginModule**verwenden möchten, müssen Sie trotzdem die " **IntegratedSecurity = true** "-Verbindungs Eigenschaft angeben. Anschließend geben Sie auch die Verbindungs Eigenschaft **authenticationScheme = javakerberos** an.

- Wenn Sie die integrierte Authentifizierung mit **sqljdbc_auth. dll**weiterhin verwenden möchten, geben Sie einfach die Verbindungs Eigenschaft **IntegratedSecurity = true** (und optional **authenticationScheme = nativeauthentication**) an.

- Wenn Sie **authenticationScheme = javakerberos** angeben, aber nicht auch **IntegratedSecurity = true**angeben, ignoriert der Treiber die **authenticationScheme** -Verbindungs Eigenschaft, und es wird erwartet, dass Benutzername und Kennwort gefunden werden. Anmelde Informationen in der Verbindungs Zeichenfolge.

Wenn Verbindungen mit einer Datenquelle erstellt werden, können Sie das Authentifizierungsschema programmgesteuert mit **setAuthenticationScheme** und optional den SPN für Kerberos mithilfe von **setServerSpn** festlegen.

Zur Unterstützung der Kerberos-Authentifizierung wurde eine neue Protokollierung eingeführt: com.microsoft.sqlserver.jdbc.internals.KerbAuthentication. Weitere Informationen finden Sie unter [Tracing Driver Operation (Ablaufverfolgung für Treibervorgänge)](../../connect/jdbc/tracing-driver-operation.md).

Befolgen Sie beim Konfigurieren von Kerberos die folgenden Richtlinien:

1. Legen Sie **allowtgtessionkey** in der Registrierung für Windows auf 1 fest. Weitere Informationen finden Sie unter [Kerberos protocol registry entries and KDC configuration keys in Windows Server 2003 (KDC-Konfigurationsschlüssel in Windows Server 2003 und Kerberos-Protokoll-Registrierungseinträge)](https://support.microsoft.com/kb/837361).
2. Stellen Sie sicher, dass die Kerberos-Konfiguration (krb5.conf in UNIX-Umgebungen) auf den richtigen Bereich und KDC für Ihre Umgebung zeigt.
3. Initialisieren Sie den TGT-Cache mit "kinit" oder indem Sie sich bei der Domäne anmelden.
4. Bei Ausführung einer Anwendung, die **authenticationScheme=JavaKerberos** verwendet, unter dem Betriebssystem Windows Vista bzw. Windows 7 muss ein Standardbenutzerkonto verwendet werden. Wenn Sie jedoch die Anwendung unter einem Administratorkonto ausführen, muss sie mit Administratorberechtigungen ausgeführt werden.

> [!NOTE]  
> Das Verbindungsattribut „serverSpn“ wird nur vom Microsoft JDBC-Treiber 4.2 und höher unterstützt.

## <a name="service-principal-names"></a>Dienstprinzipalnamen

Ein Dienstprinzipalname (SPN, Service Principal Name) ist der Name, über den ein Client eine Instanz eines Diensts eindeutig identifiziert.

Sie können den SPN mithilfe der Verbindungseigenschaft **serverSpn** angeben oder ihn einfach vom Treiber erstellen lassen (Standardeinstellung). Diese Eigenschaft kann in der Form „MSSQLSvc/fqdn:port\@REALM“ angegeben werden, wobei „fqdn“ den vollqualifizierten Domänennamen, „Port“ die Portnummer und „REALM“ den Kerberos-Bereich des SQL Server-Computers in Großbuchstaben darstellen. Der Bereichsteil dieser Eigenschaft ist optional, wenn der Standardbereich Ihrer Kerberos-Konfiguration der gleiche Bereich wie der des Servers ist, und wird standardmäßig nicht angegeben. Wenn Sie ein bereichsübergreifendes Authentifizierungsszenario unterstützen möchten, in dem sich der Standardbereich der Kerberos-Konfiguration vom Bereich des Servers unterscheidet, müssen Sie den SPN mithilfe der Eigenschaft „serverSpn“ angeben.

Der SPN könnte beispielsweise wie folgt aussehen: "MSSQLSvc/some-Server. zzz. Corp. CSO. com: 1433\@zzzz. Rettung. CONTOSO.com "

Weitere Informationen zu Dienstprinzipalnamen (SPNs) finden Sie in folgendem Thema:

- [Verwenden der Kerberos-Authentifizierung in SQL Server](https://support.microsoft.com/kb/319723)

- [Verwenden von Kerberos mit SQL Server](https://go.microsoft.com/fwlink/?LinkId=207814)

> [!NOTE]  
> Vor der 6,2-Version des JDBC-Treibers müssen Sie den **ServerSPN**explizit festlegen, um die bereichsübergreifende Kerberos ordnungsgemäß zu verwenden.
>
> Ab Version 6,2 kann der Treiber den **ServerSPN** standardmäßig erstellen, auch wenn bereichsübergreifendes Kerberos verwendet wird. Obwohl **ServerSPN** auch explizit verwendet werden kann.

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

Ab dem Microsoft JDBC-Treiber 6,2 kann der Name der Anmelde Modul-Konfigurationsdatei optional mithilfe der Connection `jaasConfigurationName`-Eigenschaft übermittelt werden, sodass jede Verbindung über eine eigene Anmelde Konfiguration verfügen kann.

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

Sie können eine Domänenkonfigurationsdatei mit -Djava.security.krb5.conf aktivieren. Sie können eine Anmelde Modul-Konfigurationsdatei mit **-Djava. Security. auth. Login. config**aktivieren.

Beispielsweise kann der folgende Befehl zum Starten der Anwendung verwendet werden:

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

Ab dem Microsoft JDBC-Treiber 6,2 unterstützt der Treiber die eingeschränkte Kerberos-Delegierung. Die Delegierten Anmelde Informationen können als "org. ietf. JGSS. gsscredential"-Objekt übergeben werden. diese Anmelde Informationen werden vom Treiber verwendet, um eine Verbindung herzustellen.

```java
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>Kerberos-Verbindung unter Verwendung von Prinzipal Namen und Kennwort

Ab dem Microsoft JDBC Driver 6,2 kann der Treiber die Kerberos-Verbindung mithilfe des Prinzipal namens und des Kennworts herstellen, die in der Verbindungs Zeichenfolge angegeben sind.

```java
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```

Die UserName-Eigenschaft erfordert keinen Bereich, wenn der Benutzer zu dem in der Datei krb5. conf festgelegten default_realm gehört. Wenn `userName` und `password` zusammen `authenticationScheme=JavaKerberos;` mit `integratedSecurity=true;` der-Eigenschaft und der-Eigenschaft festgelegt wird, wird die Verbindung mit dem Wert Benutzername als Kerberos-Prinzipal zusammen mit dem angegebenen Kennwort hergestellt.

## <a name="using-kerberos-authentication-from-unix-machines-on-the-same-domain"></a>Verwenden der Kerberos-Authentifizierung von UNIX-Computern in derselben Domäne

Diese Anleitung setzt voraus, dass bereits ein funktionierendes Kerberos-Setup vorhanden ist. Führen Sie den folgenden Code auf einem Windows-Computer mit einer funktionierenden Kerberos-Authentifizierung aus, um zu überprüfen, ob die oben genannte true Wenn der Code erfolgreich ausgeführt wird, wird "Authentifizierungsschema: Kerberos" in der Konsole gedruckt. Außerhalb der bereitgestellten sind keine weiteren Laufzeitflags, Abhängigkeiten oder Treibereinstellungen erforderlich. Der gleiche Codeblock kann unter Linux ausgeführt werden, um erfolgreiche Verbindungen zu überprüfen.

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

1. Domäne verbinden Sie den Client Computer mit derselben Domäne wie der Server.
2. Optionale Legen Sie den Standard Speicherort des Kerberos-Tickets fest. Dies wird am bequemsten durch Festlegen der `KRB5CCNAME` Umgebungsvariablen erreicht.
3. Rufen Sie das Kerberos-Ticket ab, indem Sie entweder eine neue erstellen oder eine vorhandene an den Standard Speicherort des Kerberos-Tickets platzieren. Verwenden Sie zum Generieren eines Tickets einfach ein Terminal, und initialisieren Sie das `kinit USER@DOMAIN.AD` Ticket über "User" und "Domain". AD ist der Prinzipal bzw. die Domäne. Zum Beispiel `kinit SQL_SERVER_USER03@MICROSOFT.COM`. Das Ticket wird am standardmäßigen Ticket Speicherort oder im `KRB5CCNAME` Pfad generiert, sofern festgelegt.
4. Das Terminal fordert zur Eingabe eines Kennworts auf, und geben Sie das Kennwort ein.
5. Überprüfen Sie die Anmelde Informationen im `klist` Ticket über, und bestätigen Sie die Anmelde Informationen, die Sie für die Authentifizierung verwenden möchten.
6. Führen Sie den obigen Beispielcode aus, und bestätigen Sie, dass die Kerberos-Authentifizierung erfolgreich war.

## <a name="see-also"></a>Weitere Informationen

[Verbinden von SQL Server mit dem JDBC-Treiber](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
