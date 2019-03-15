---
title: 'Tutorial: Active Directory-Authentifizierung für SQL Server unter Linux'
titleSuffix: SQL Server
description: Dieses Tutorial enthält die Konfigurationsschritte für die AAD-Authentifizierung für SQL Server unter Linux.
author: meet-bhagdev
ms.date: 02/23/2018
ms.author: meetb
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: d3b3aaf9688d3517127495fe4b963f5b6de56f0f
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57973589"
---
# <a name="tutorial-use-active-directory-authentication-with-sql-server-on-linux"></a>Tutorial: Verwenden Sie Active Directory-Authentifizierung mit SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Tutorial wird erläutert, wie so konfigurieren Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Linux zur Unterstützung der Active Directory (AD)-Authentifizierung, auch bekannt als integrierte Authentifizierung. Eine Übersicht finden Sie unter [Active Directory-Authentifizierung für SQL Server unter Linux](sql-server-linux-active-directory-auth-overview.md).

In diesem Tutorial umfasst die folgenden Aufgaben:

> [!div class="checklist"]
> * Join [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Host mit AD-Domäne
> * Erstellen Sie AD-Benutzer für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und Festlegen des SPN
> * Konfigurieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Service Keytab-Datei
> * Erstellen von AD-basierte Anmeldungen in Transact-SQL
> * Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] AD-Authentifizierung

> [!NOTE]
>
> Wenn Sie konfigurieren möchten [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Linux, um einen AD-Anbieter von Drittanbietern verwenden, finden Sie unter [Drittanbieter Active Directory mit SQL Server unter Linux verwenden](./sql-server-linux-active-directory-third-party-providers.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

Bevor Sie AD-Authentifizierung konfigurieren, müssen Sie:

* Richten Sie eine AD-Domänencontroller (Windows) in Ihrem Netzwerk  
* Installieren Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
  * [Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> Join [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Host mit AD-Domäne

Verwenden Sie die folgenden Schritte aus, um das Verknüpfen einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Host zu Active Directory-Domäne:

1. Verwendung **[Realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join.html)** auf den Hostcomputer aus Ihrer AD-Domäne beitreten. Wenn noch nicht geschehen, installieren Sie das Realmd und die Kerberos-Client-Pakete auf den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Hostcomputer, die mit Ihrer Linux-Distribution-Paket-Manager:

   ```bash
   # RHEL
   sudo yum install realmd krb5-workstation

   # SUSE
   sudo zypper install realmd krb5-client

   # Ubuntu
   sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
   ```

1. Wenn die Installation des Kerberos-Client-Pakets für den ein Bereichsname aufgefordert werden, geben Sie Ihren Domänennamen in Großbuchstaben.

   > [!NOTE]
   > In dieser exemplarischen Vorgehensweise verwendet "contoso.com" und "CONTOSO.COM" als Beispielnamen Domäne und dem Bereich, bzw. Ersetzen Sie dies durch Ihre eigenen Werte. Mit diesen Befehlen werden Groß-/Kleinschreibung beachtet, also stellen Sie sicher, dass Sie verwenden in Großbuchstaben egal wo sie in dieser exemplarischen Vorgehensweise verwendet wird.

1. Konfigurieren Ihrer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Hostcomputer Ihrer Active Directory-Domänencontroller-IP-Adresse als eine DNS-Namenserver zu verwenden. 

   - **Ubuntu**:

      Bearbeiten der `/etc/network/interfaces` Datei, damit Ihre AD-Domänencontroller-IP-Adresse als eine Dns-Namenserver aufgeführt ist. Beispiel: 

      ```/etc/network/interfaces
      <...>
      # The primary network interface
      auto eth0
      iface eth0 inet dhcp
      dns-nameservers **<AD domain controller IP address>**
      dns-search **<AD domain name>**
      ```

      > [!NOTE]
      > Die Netzwerkschnittstelle ("eth0") kann für verschiedene Computer abweichen. Um herauszufinden, welche, die Sie verwenden, führen Sie "ifconfig" aus, und kopieren Sie die Schnittstelle, die eine IP-Adresse und die gesendeten und empfangenen Bytes hat.

      Starten Sie nach der Bearbeitung dieser Datei den Netzwerkdienst neu:

      ```bash
      sudo ifdown eth0 && sudo ifup eth0
      ```

      Nun überprüfen Sie, ob Ihre `/etc/resolv.conf` Datei enthält eine Zeile wie im folgenden Beispiel:  

      ```/etc/resolv.conf
      nameserver **<AD domain controller IP address>**
      ```

   - **RHEL**:

     Bearbeiten der `/etc/sysconfig/network-scripts/ifcfg-eth0` Datei (oder andere Schnittstelle Config-Datei nach Bedarf), damit die IP-Adresse Ihrer Active Directory-Domänencontroller als DNS-Server aufgeführt ist:

     ```/etc/sysconfig/network-scripts/ifcfg-eth0
     <...>
     PEERDNS=no
     DNS1=**<AD domain controller IP address>**
     ```

     Starten Sie nach der Bearbeitung dieser Datei den Netzwerkdienst neu:

     ```bash
     sudo systemctl restart network
     ```

     Nun überprüfen Sie, ob Ihre `/etc/resolv.conf` Datei enthält eine Zeile wie im folgenden Beispiel:  

     ```/etc/resolv.conf
     nameserver **<AD domain controller IP address>**
     ```

   - **SLES**:

     Bearbeiten der `/etc/sysconfig/network/config` Datei, damit Ihre AD-Domäne-Controller-IP-Adresse für DNS-Abfragen verwendet wird und Ihre AD-Domäne ist, in der Liste der Domäne suchen:

     ```/etc/sysconfig/network/config
     <...>
     NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
     ```

     Starten Sie nach der Bearbeitung dieser Datei den Netzwerkdienst neu:

     ```bash
     sudo systemctl restart network
     ```

     Nun überprüfen Sie, ob Ihre `/etc/resolv.conf` Datei enthält eine Zeile wie im folgenden Beispiel:

     ```/etc/resolv.conf
     nameserver **<AD domain controller IP address>**
     ```

1. Treten Sie zur Domäne bei

   Nachdem Sie bestätigt haben, dass DNS ordnungsgemäß konfiguriert ist, treten Sie der Domäne, indem Sie den folgenden Befehl ausführen. Sie müssen zur Authentifizierung verwenden ein AD-Konto, das über ausreichende Berechtigungen in AD, um das Hinzufügen eines neuen Computers zur Domäne verfügt.

   Insbesondere dieser Befehl erstellt ein neues Computerkonto in Active Directory, erstellen Sie die `/etc/krb5.keytab` hosten Keytab-Datei, und konfigurieren Sie die Domäne in `/etc/sssd/sssd.conf`:

   ```bash
   sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
   <...>
   * Successfully enrolled machine in realm
   ```

   > [!NOTE]
   > Wenn Sie eine Fehlermeldung angezeigt, "die erforderlichen Pakete nicht installiert werden", und installieren Sie diese Pakete, die mit Ihrer Linux-Distribution-Paket-Manager vor dem Ausführen der `realm join` -Befehl erneut aus.
   >
   > Wenn Sie einen Fehler "Nicht genügend Berechtigungen für den Domänenbeitritt" erhalten, müssen Sie einen Domänenadministrator überprüfen Sie, ob Sie über ausreichende Berechtigungen zum Linux-Computer in Ihrer Domäne einbinden.
   >
   > Wenn Sie eine Fehlermeldung, "KDC Antwort entsprach nicht Erwartungen," klicken Sie dann Sie möglicherweise nicht den richtigen Bereichsnamen für den Benutzer angegeben. Bereichsnamen Groß-/Kleinschreibung beachtet werden, in der Regel in Großbuchstaben und identifiziert werden können, mit dem Befehl `realm discover contoso.com`.
   
   > SQL Server verwendet SSSD und NSS für die Zuordnung von Benutzerkonten und-Gruppen zu Sicherheits-IDs (SIDS). SSSD muss konfiguriert und wird ausgeführt, damit SQL Server zum erfolgreichen Erstellen von AD-Anmeldungen. Realmd in der Regel wird automatisch als Teil der Domäne beizutreten, aber in einigen Fällen müssen Sie diese separat.
   >
   > Sehen Sie sich die folgende Einstellung [SSSD manuell](https://access.redhat.com/articles/3023951), und [Konfigurieren des NSS mit SSSD arbeiten](https://access.redhat.com/documentation/red_hat_enterprise_linux/7/html/system-level_authentication_guide/configuring_services#Configuration_Options-NSS_Configuration_Options)

5. Stellen Sie sicher, dass Ihre Domäne konfiguriert ist `/etc/krb5.conf`
    ```/etc/krb5.conf
    [libdefaults]
    default_realm = CONTOSO.COM

    [realms]
    CONTOSO.COM = {
    }

    [domain_realm]
    contoso.com = CONTOSO.COM
    .contoso.com = CONTOSO.COM
    ```

  
6. Stellen Sie sicher, dass Sie jetzt Informationen zu einem Benutzer in der Domäne erfasst werden können und Sie ein Kerberos-Ticket als dieser Benutzer abrufen können.

   Im folgenden Beispiel wird **Id**,  **[Kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html)**, und **[Klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html)** Befehle für diese.

   ```bash
   id user@contoso.com
   uid=1348601103(user@contoso.com) gid=1348600513(domain group@contoso.com) groups=1348600513(domain group@contoso.com)

   kinit user@CONTOSO.COM
   Password for user@CONTOSO.COM:

   klist
   Ticket cache: FILE:/tmp/krb5cc_1000
   Default principal: user@CONTOSO.COM
   <...>
   ```

   > [!NOTE]
   > Wenn `id user@contoso.com` zurückgegeben wird, "Keine solche Benutzer," Stellen Sie sicher, dass der SSSD-Dienst erfolgreich gestartet werden, mithilfe des Befehls `sudo systemctl status sssd`. Wenn der Dienst ausgeführt wird und immer noch den Fehler "Keine solche Benutzer" angezeigt wird, versuchen Sie es Aktivieren der ausführlichen Protokollierung für SSSD. Weitere Informationen finden Sie auf die Red Hat-Dokumentation für [Problembehandlung SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting).
   >
   > Wenn `kinit user@CONTOSO.COM` zurückgegeben wird, "KDC Antwort Erwartungen entsprach nicht beim Abrufen der anfänglichen Anmeldeinformationen" Stellen Sie sicher, dass Sie den Bereich in Großbuchstaben angegeben haben.

Weitere Informationen finden Sie auf die Red Hat-Dokumentation für [Ermitteln von und Identität beitreten zu Domänen](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html). 

## <a id="createuser"></a> Erstellen Sie AD-Benutzer für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und Festlegen des SPN

  > [!NOTE]
  > Den nächsten Schritten verwenden Ihre [vollständig qualifizierten Domänennamen](https://en.wikipedia.org/wiki/Fully_qualified_domain_name). Bei **Azure**, müssen Sie **[erstellen Sie eine](https://docs.microsoft.com/azure/virtual-machines/linux/portal-create-fqdn)** bevor Sie fortfahren.

1. Führen Sie auf dem Domänencontroller die [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx) PowerShell-Befehl, um einen neuen AD-Benutzer mit einem Kennwort zu erstellen, das nicht abläuft. In diesem Beispiel gibt das Konto "Mssql", aber der Kontoname kann beliebig sein. Sie werden aufgefordert, ein neues Kennwort für das Konto einzugeben:

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > Es ist eine bewährte Sicherheitsmethode, ein dediziertes AD-Konto für SQL Server, zu verwenden, damit SQL Server Anmeldeinformationen mit anderen Diensten, die mit dem gleichen Konto freigegeben werden. Allerdings können Sie ein vorhandenes AD-Konto wiederverwenden, wenn Sie es vorziehen, wenn Sie wissen, dass das Kennwort des Kontos (generiert eine Keytab-Datei im nächsten Schritt erforderlich).

2. Legen Sie den ServicePrincipalName (SPN) für dieses Konto verwenden die `setspn.exe` Tool. Der SPN muss genau wie im folgenden Beispiel angegeben formatiert sein. Finden Sie den vollqualifizierten Domänennamen des der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Hostcomputer mit `hostname --all-fqdns` auf die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Host und den TCP-Port muss 1433, sofern Sie konfiguriert haben [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eine andere Portnummer zu verwenden.

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > Wenn Sie einen Fehler "nicht genügend Zugriffsrechte," erhalten, müssen Sie einen Domänenadministrator überprüfen Sie, dass Sie über ausreichende Berechtigungen zum Festlegen eines SPN für dieses Konto verfügen.
   >
   > Wenn Sie den TCP-Port in der Zukunft ändern, müssen Sie den Befehl "Setspn", die mit die neue Portnummer erneut ausgeführt. Sie müssen auch die Keytab-Datei für SQL Server-Dienst den neuen SPN hinzufügen, indem Sie die Schritte im nächsten Abschnitt.

3. Weitere Informationen finden Sie unter [Registrieren eines Dienstprinzipalnamens für Kerberos-Verbindungen](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).

## <a id="configurekeytab"></a> Konfigurieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Service Keytab-Datei

1. Überprüfen Sie die Schlüssel-Versionsnummer (Kvno) für die AD-Konto, das im vorherigen Schritt erstellt haben. Es ist in der Regel 2, aber es konnte eine andere ganze Zahl sein, wenn Sie das Kennwort des Kontos mehrfach geändert haben. Auf der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Hostcomputer, führen Sie Folgendes:

   ```bash
   kinit user@CONTOSO.COM

   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**
   ```

   > [!NOTE]
   > SPNs dauert einige Minuten, durchlaufen Ihre Domäne aus, insbesondere dann, wenn die Domäne groß ist. Wenn Sie die Fehlermeldung "Kvno: Server in Kerberos-Datenbank nicht gefunden werden, beim Abrufen von Anmeldeinformationen für die MSSQLSvc /\*\*\<vollständig qualifizierten Domänennamen des Hostcomputers\>\*\*:\* \* \< TCP-Port\>\*\*\@"contoso.com" ", bitte warten Sie einige Minuten, und versuchen Sie es erneut.

2. Erstellen Sie eine Keytab-Datei mit **[Ktutil](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/admin_commands/ktutil.html)** für den AD-Benutzer, die Sie im vorherigen Schritt erstellt haben. Wenn Sie aufgefordert werden, geben Sie das Kennwort für das AD-Konto ein.

   ```bash
   sudo ktutil

   ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96

   ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac

   ktutil: wkt /var/opt/mssql/secrets/mssql.keytab

   quit
   ```

   > [!NOTE]
   > Das Tool Ktutil überprüft das Kennwort nicht, also stellen Sie sicher, dass Sie ordnungsgemäß eingegeben werden.

3. Das Computerkonto hinzufügen, um Ihre Keytab-Datei mit  **[Ktutil](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/admin_commands/ktutil.html)**. Das Computerkonto (auch als "UPN" bezeichnet) befindet sich im `/etc/krb5.keytab` in der Form "\<Hostname\>$\@\<realm.com\>" (z. B. Sqlhost$\@"contoso.com"). Wir werden diese Einträge von kopiert `/etc/krb5.keytab` zu `mssql.keytab`.

   ```bash
   sudo ktutil

   # Read all entries from /etc/krb5.keytab
   ktutil: rkt /etc/krb5.keytab

   # List all entries
   ktutil: list

   # Delete all entries by their slot number which are not the UPN one at a
   # time.
   # Warning: when an entry is deleted (e.g. slot 1), all values slide up by
   # one to take its place (e.g. the entry in slot 2 moves to slot 1 when slot
   # 1's entry is deleted)
   ktutil: delent <slot num>
   ktutil: delent <slot num>
   ...

   # List all entries to ensure only UPN entries are left
   ktutil: list

   # When only UPN entries are left, append these values to mssql.keytab
   ktutil: wkt /var/opt/mssql/secrets/mssql.keytab

   quit
   ```

4. Jede Person mit Zugriff auf diese `keytab` Datei kann die Identität annehmen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf die Domäne, stellen Sie daher Sie sicher, dass Sie den Zugriff auf die Datei, z. B., dass nur die `mssql` Konto Lesezugriff besitzt:

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
   sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
   ```

5. Konfigurieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dieses `keytab` -Datei für die Kerberos-Authentifizierung:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
   sudo systemctl restart mssql-server
   ```

6. Optional: Deaktivieren Sie die UDP-Verbindungen mit dem Domänencontroller zur Verbesserung der Leistung. In vielen Fällen UDP-Verbindungen schlägt immer fehl, wenn auf einem Domänencontroller zu verbinden, dass Sie Konfigurationsoptionen, in festlegen können `/etc/krb5.conf` UDP-Aufrufe zu überspringen. Bearbeiten Sie `/etc/krb5.conf` und die folgenden Optionen festlegen:

   ```/etc/krb5.conf
   [libdefaults]
   udp_preference_limit=0
   ```

## <a id="createsqllogins"></a> Erstellen von AD-basierte Anmeldungen in Transact-SQL

1. Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und erstellen Sie eine neue, AD-basierte Anmeldung:

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

2. Stellen Sie sicher, dass die Anmeldung jetzt, in aufgeführt ist der [Sys. server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) Systemkatalogsicht:

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a id="connect"></a> Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] AD-Authentifizierung

Melden Sie sich bei einem Clientcomputer, die über Ihre Domänenanmeldeinformationen an. Nun können Sie mit verbinden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ohne Neustart Ihr Kennwort mithilfe von AD-Authentifizierung. Wenn Sie eine Anmeldung für eine AD-Gruppe erstellen, kann alle AD-Benutzer, die Mitglied dieser Gruppe ist auf die gleiche Weise verbinden.

Spezifischen Verbindungszeichenfolgen-Parameter für die Clients die Verwendung von AD-Authentifizierung abhängig ist, welcher Treiber Sie verwenden. Betrachten Sie die folgenden Beispiele:

* `sqlcmd` auf eine Domäne eingebundenen Linux-client

   Melden Sie sich in eine Domäne eingebundenen Linux-Clientcomputer mit `ssh` und Anmeldeinformationen für die Domäne:

   ```bash
   ssh -l user@contoso.com client.contoso.com
   ```

   Stellen Sie sicher, dass Sie installiert haben die [Mssql-Tools](sql-server-linux-setup-tools.md) Paket und das Herstellen einer Verbindung mit `sqlcmd` ohne Angabe von Anmeldeinformationen:

   ```bash
   sqlcmd -S mssql-host.contoso.com
   ```

* SSMS auf einem Client für die Domäne eingebundenen Windows

   Melden Sie sich eine Domäne eingebundenen Windows-Client über Ihre Domänenanmeldeinformationen an. Stellen Sie sicher, dass [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] installiert ist, wird die Verbindung mit Ihrem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Instanz (z. B. "Mssql-host.contoso.com") durch Angabe **Windows-Authentifizierung** in die **Herstellen einer Verbindung mit Server** Dialogfeld.

* AD-Authentifizierung mit anderen Clienttreibern

  * JDBC: [Mithilfe der integrierten Kerberos-Authentifizierung, SqlServer verbinden](https://docs.microsoft.com/sql/connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server)
  * ODBC: [Nutzung der Integrierten Authentifizierung](https://docs.microsoft.com/sql/connect/odbc/linux/using-integrated-authentication)
  * ADO.NET: [Syntax für Verbindungszeichenfolgen](https://msdn.microsoft.com/library/system.data.sqlclient.sqlauthenticationmethod(v=vs.110).aspx)

## <a name="performance-improvements"></a>Leistungsverbesserungen
AD-Konfiguration ist mit den Schritten unter gültig, wenn Sie feststellen, dass AD-Konto-Suchvorgänge werden eine Weile dauert, und Sie Sie sichergestellt haben [verwenden Active Directory-Authentifizierung mit SQL Server unter Linux über AD-Anbieter für Drittanbieter-](sql-server-linux-active-directory-third-party-providers.md), hinzufügbaren den unten auf Zeilen `/var/opt/mssql/mssql.conf` SSSD-Aufrufe zu überspringen und direkt die LDAP-Aufrufe verwenden.

```/var/opt/mssql/mssql.conf
[network]
disablesssd = true
```

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial wurde erläutert, wie wir durch die Schritte zum Einrichten von Active Directory-Authentifizierung mit SQL Server unter Linux. Sie haben gelernt, wie auf:
> [!div class="checklist"]
> * Join [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Host mit AD-Domäne
> * Erstellen Sie AD-Benutzer für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und Festlegen des SPN
> * Konfigurieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Service Keytab-Datei
> * Erstellen von AD-basierte Anmeldungen in Transact-SQL
> * Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] AD-Authentifizierung

Als Nächstes untersuchen Sie andere Szenarien für SQL Server unter Linux.

> [!div class="nextstepaction"]
>[Verschlüsseln von Verbindungen zu SQLServer unter Linux](sql-server-linux-encrypted-connections.md)
