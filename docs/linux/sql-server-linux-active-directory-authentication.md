---
title: 'Tutorial: Verwenden von AD-Authentifizierung für SQL Server unter Linux'
titleSuffix: SQL Server
description: Dieses Tutorial enthält die Konfigurationsschritte für AD-Authentifizierung für SQL Server unter Linux.
author: Dylan-MSFT
ms.author: Dylan.Gray
ms.reviewer: rothja
ms.date: 04/01/2019
manager: craigg
ms.topic: tutorial
ms.prod: sql
ms.custom: seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 5e75a0315c0e632e9637ad1f1467acc90dc586cf
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2019
ms.locfileid: "59240778"
---
# <a name="tutorial-use-active-directory-authentication-with-sql-server-on-linux"></a>Tutorial: Verwenden Sie Active Directory-Authentifizierung mit SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Tutorial wird erläutert, wie so konfigurieren Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Linux zur Unterstützung der Active Directory (AD)-Authentifizierung, auch bekannt als integrierte Authentifizierung. Eine Übersicht finden Sie unter [Active Directory-Authentifizierung für SQL Server unter Linux](sql-server-linux-active-directory-auth-overview.md).

In diesem Tutorial umfasst die folgenden Aufgaben:

> [!div class="checklist"]
> * Join [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Host mit AD-Domäne
> * Erstellen Sie AD-Benutzer für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und Festlegen des SPN
> * Konfigurieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Service Keytab-Datei
> * Die Keytab-Datei sichern
> * Konfigurieren von SQL Server, um die Keytab-Datei für die Kerberos-Authentifizierung zu verwenden.
> * Erstellen von AD-basierte Anmeldungen in Transact-SQL
> * Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] AD-Authentifizierung

## <a name="prerequisites"></a>Erforderliche Komponenten

Bevor Sie AD-Authentifizierung konfigurieren, müssen Sie:

* Richten Sie eine AD-Domänencontroller (Windows) in Ihrem Netzwerk  
* Installieren [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
  * [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server (SLES)](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> Join [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Host mit AD-Domäne

Sie müssen Ihren SQL Server-Linux-Host mit einem Active Directory-Domänencontroller verknüpfen. Informationen zum active Directory-Domäne zu verknüpfen, finden Sie unter [Join von SQL Server auf einem Linux-Host zu einer Active Directory-Domäne](sql-server-linux-active-directory-join-domain.md).

## <a id="createuser"></a> Erstellen von AD-Benutzer (oder MSA) für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und Festlegen des SPN

> [!NOTE]
> Die folgenden Schritte verwenden Ihre [vollständig qualifizierten Domänennamen](https://en.wikipedia.org/wiki/Fully_qualified_domain_name). Bei **Azure**, müssen Sie **[erstellen Sie eine](https://docs.microsoft.com/azure/virtual-machines/linux/portal-create-fqdn)** bevor Sie fortfahren.

1. Führen Sie auf dem Domänencontroller die [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx) PowerShell-Befehl, um einen neuen AD-Benutzer mit einem Kennwort zu erstellen, das nicht abläuft. Das folgende Beispiel benennt das Konto `mssql`, aber der Kontoname kann beliebig sein. Sie werden aufgefordert, ein neues Kennwort für das Konto einzugeben.

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > Es ist eine bewährte Sicherheitsmethode, ein dediziertes AD-Konto für SQL Server, zu verwenden, damit SQL Server Anmeldeinformationen mit anderen Diensten, die mit dem gleichen Konto freigegeben werden. Allerdings können Sie optional ein vorhandenes AD-Konto wiederverwenden, wenn Sie wissen, dass das Kennwort des Kontos (der erforderlich ist, generiert eine Keytab-Datei im nächsten Schritt).

2. Legen Sie den ServicePrincipalName (SPN) für dieses Konto verwenden die **setspn.exe** Tool. Der SPN muss genau wie im folgenden Beispiel angegeben formatiert sein. Sie finden den vollqualifizierten Domänennamen des der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Hostcomputer mit `hostname --all-fqdns` auf die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Host. Muss der TCP-Port 1433, es sei denn, Sie konfiguriert haben [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eine andere Portnummer zu verwenden.

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   setspn -A MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > Wenn Sie eine Fehlermeldung `Insufficient access rights`, mit den Domänenadministrator bitten, überprüfen Sie, dass Sie über ausreichende Berechtigungen zum Festlegen eines SPN für dieses Konto verfügen.
   >
   > Wenn Sie den TCP-Port in der Zukunft ändern, müssen Sie Ausführen den **Setspn** Befehl erneut mit die neue Portnummer. Sie müssen auch die Keytab-Datei für SQL Server-Dienst den neuen SPN hinzufügen, indem Sie die Schritte im nächsten Abschnitt.

Weitere Informationen finden Sie unter [Registrieren eines Dienstprinzipalnamens für Kerberos-Verbindungen](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).

## <a id="configurekeytab"></a> Konfigurieren von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Service Keytab-Datei

Es gibt zwei Möglichkeiten zum Konfigurieren der SQL Server-Dienst-Dateien mit Schlüsseltabellen. Die erste Option ist, verwenden ein Computerkonto (UPN), während die zweite Option einen verwalteten Dienst-Konto (MSA) verwendet, in der Konfiguration der Keytab-Datei. Beide Mechanismen sind gleichermaßen funktionsfähig, und können Sie die Methode, die am besten für Ihre Umgebung.

In beiden Fällen muss der SPN, der im vorherigen Schritt erstellt haben, und der SPN registriert werden muss, in die Keytab-Datei.

So konfigurieren Sie die SQL Server-Dienst Keytab-Datei:

1. Konfigurieren der [SPN Keytab-Einträgen](#spn) im nächsten Abschnitt.

1. Und dann entweder [hinzufügen UPN](#upn) (option 1) oder [MSA](#msa) (Option 2)-Einträge in der Datei keytab-Datei anhand der Schritte in den jeweiligen Abschnitten.

> [!IMPORTANT]
> Wenn das Kennwort für den UPN/MSA geändert wird, oder das Kennwort für das Konto, dem die SPN zugewiesen sind geändert wird, müssen Sie die Keytab-Datei mit dem neuen Kennwort und die Schlüssel Version Anzahl (KVNO) aktualisieren. Einige Dienste möglicherweise auch die Kennwörter automatisch gedreht werden. Überprüfen Sie alle Richtlinien zur Kennwortrotation, für die betreffenden Konten aus, und richten Sie diese mit geplanten Wartungsaktivitäten um unerwartete Ausfallzeiten zu vermeiden.

### <a id="spn"></a> SPN-Keytab-Einträgen

1. Überprüfen Sie die Schlüssel-Version-Anzahl (KVNO) für die AD-Konto, das im vorherigen Schritt erstellt haben. Es ist in der Regel 2, aber es konnte eine andere ganze Zahl sein, wenn Sie das Kennwort des Kontos mehrfach geändert haben. Führen Sie auf dem SQL Server-Hostcomputer die folgenden Befehle aus:

   ```bash
   kinit user@CONTOSO.COM
   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**
   ```

   > [!NOTE]
   > SPNs dauert einige Minuten, durchlaufen Ihre Domäne aus, insbesondere dann, wenn die Domäne groß ist. Wenn Sie die Fehlermeldung `kvno: Server not found in Kerberos database while getting credentials for MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM`, bitte warten Sie einige Minuten, und versuchen Sie es erneut.  

1. Start **ktutil**:

   ```bash
   sudo ktutil
   ```

1. Fügen Sie Keytab-Einträge für jede SPN mithilfe der folgenden Befehle hinzu:

   ```bash
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac -sha1-96
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac -sha1-96
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   ```

1. Schreiben Sie die Keytab-Datei in eine Datei und beenden Sie den Ktutil:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

   > [!NOTE]
   > Die **Ktutil** Tool überprüft nicht das Kennwort, um sicherzustellen, dass Sie Sie bei Aufforderung richtig eingeben.

### <a id="upn"></a> Option 1: Mit eindeutigen persönlichen Namen so konfigurieren Sie die Keytab-Datei

Das Computerkonto hinzufügen, um Ihre Keytab-Datei mit **Ktutil**. Das Computerkonto (auch als "UPN" bezeichnet) befindet sich im **/etc/krb5.keytab** im Formular `<hostname>$@<realm.com>` (z. B. `sqlhost$@CONTOSO.COM`). Kopieren Sie diese Einträge von **/etc/krb5.keytab** zu **mssql.keytab**.

1. Starten Sie **Ktuil** mit den folgenden Befehl aus:

   ```bash
   sudo ktutil
   ```

1. Verwenden der **Rkt** Befehl aus, um alle Einträge aus lesen **/etc/krb5.keytab**.

   ```bash
   rkt /etc/krb5.keytab
   ```

1. Als Nächstes Listen Sie die Eingaben.

   ```bash
   list
   ```

1. Löschen Sie alle Einträge nach Slotnummer, die nicht den UPN. Führen Sie diese einzeln nacheinander durch wiederholen den folgenden Befehl ein:

   ```bash
   delent <slot num>
   ```

   > [!IMPORTANT]
   > Wenn ein Eintrag, z. B. Platz 1, alle Werte Folie sich von einem an dessen Stelle tritt gelöscht wird. Dies bedeutet, dass der Eintrag in Einschubfach 2 wird verschoben, 1 Slot, wenn Steckplatz 1 im Eintrag gelöscht wird.

1. Listen Sie die Eingaben erneut bleiben nur UPN-Einträge.

   ```bash
   list
   ```

1. Wenn nur UPN-Einträge sind, fügen Sie diese Werte zu **mssql.keytab**:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   ```

1. Quit **ktutil**.

   ```bash
   quit
   ```

### <a id="msa"></a> Option 2:  Verwendung von Account, MSA so konfigurieren Sie die Keytab-Datei

Für die MSA-Option verwenden müssen Sie SQL Server Kerberos-schlüsseltabellendatei erstellen. Es enthält alle von der [Dienstprinzipalnamen im ersten Schritt](#spn) und die Anmeldeinformationen für das verwaltete, bei dem die SPN registriert werden. 

1. Nach der SPN mit Schlüsseltabellen werden Einträge erstellt, führen die folgenden Befehle von einem Linux-Computer, der eine Domäne eingebunden ist:

   ```bash
   kinit <AD user>
   kvno <any SPN registered in step 1>
      <spn>@CONTOSO.COM: kvno = <KVNO>
   ```

   Dieser Schritt zeigt das KVNO für das Benutzerkonto, das der SPN den Besitz zuweisen. Für diesen Schritt funktioniert muss der SPN das MSA-Konto bei der Erstellung zugewiesen wurden. Wenn der SPN nicht MSA zugewiesen wurde, wird die KVNO angezeigt des aktuellen SPN-Kontos werden und werden nicht korrekt, verwenden für die Konfiguration.  

1. Start **ktutil**:

   ```bash
   sudo ktutil
   ```

1. Fügen Sie den MSA mithilfe der folgenden zwei Befehle hinzu:

   ```bash
   addent -password -p <MSA> -k <kvno from command above> -e aes256-cts-hmac-sha1-96
   addent -password -p <MSA> -k <kvno from command above> -e rc4-hmac
   ```

1. Schreiben Sie die Keytab-Datei in eine Datei und beenden Sie den Ktutil:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

1. Wenn Sie den MSA-Ansatz zu verwenden, muss eine Konfigurationsoption mit festgelegt werden die **Mssql-Conf** Tool, um die MSA verwendet werden, beim Zugriff auf die Keytab-Datei festzulegen. Sicherstellen, dass die folgenden Werte sind **/var/opt/mssql/mssql.conf**.

   ```bash
   sudo mssql-conf set network.privilegedadaccount <MSA_Name>
   ```

   > [!NOTE]
   > Nur enthalten Sie, der MSA-Name und nicht mit dem Namen "Domäne\Konto".

## <a id="securekeytab"></a> Die Keytab-Datei sichern

Jede Person mit Zugriff auf die Datei keytab-Datei kann SQL Server in der Domäne annehmen, also stellen Sie sicher, dass Sie den Zugriff auf die Datei einschränken, so, dass nur das Mssql-Konto Lesezugriff besitzt:

```bash
sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
```

## <a id="keytabkerberos"></a> Konfigurieren von SQL Server, um die Keytab-Datei für die Kerberos-Authentifizierung zu verwenden.

Verwenden Sie die Schritte zum Konfigurieren des SQL Servers zum Einstieg in die schlüsseltabellendatei mit für die Kerberos-Authentifizierung.

```bash
sudo mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
sudo systemctl restart mssql-server
```

Optionales Deaktivieren der UDP-Verbindungen mit dem Domänencontroller zur Verbesserung der Leistung. In vielen Fällen UDP-Verbindungen wiederholt Fehler auftreten, wenn auf einem Domänencontroller zu verbinden, dass Sie Konfigurationsoptionen, in festlegen können **/etc/krb5.conf** UDP-Aufrufe zu überspringen. Bearbeiten Sie **/etc/krb5.conf** und die folgenden Optionen festlegen:

```/etc/krb5.conf
[libdefaults]
udp_preference_limit=0
```

An diesem Punkt können Sie die AD-basierte Anmeldungen in SQL Server wie folgt zu verwenden.

## <a id="createsqllogins"></a> Erstellen von AD-basierte Anmeldungen in Transact-SQL

1. Verbinden mit SQL Server, und erstellen Sie eine neue, AD-basierte Anmeldung:

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

1. Stellen Sie sicher, dass die Anmeldung jetzt, in aufgeführt ist der [Sys. server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) Systemkatalogsicht:

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a id="connect"></a> Verbinden Sie mit SQL Server mit AD-Authentifizierung

Melden Sie sich bei einem Clientcomputer, die über Ihre Domänenanmeldeinformationen an. Jetzt können Sie mit SQL Server verbinden, ohne Ihr Kennwort mithilfe von AD-Authentifizierung her. Wenn Sie eine Anmeldung für eine AD-Gruppe erstellen, kann alle AD-Benutzer, die Mitglied dieser Gruppe ist auf die gleiche Weise verbinden.

Spezifischen Verbindungszeichenfolgen-Parameter für die Clients die Verwendung von AD-Authentifizierung abhängig ist, welcher Treiber Sie verwenden. Betrachten Sie die Beispiele in den folgenden Abschnitten.

### <a name="sqlcmd-on-a-domain-joined-linux-client"></a>Sqlcmd auf eine Domäne eingebundenen Linux-client

Melden Sie sich in eine Domäne eingebundenen Linux-Clientcomputer mit **ssh** und Anmeldeinformationen für die Domäne:

```bash
ssh -l user@contoso.com client.contoso.com
```

Stellen Sie sicher, dass Sie installiert haben die [Mssql-Tools](sql-server-linux-setup-tools.md) Paket und das Herstellen einer Verbindung mit **Sqlcmd** ohne Angabe von Anmeldeinformationen:

```bash
sqlcmd -S mssql-host.contoso.com
```

### <a name="ssms-on-a-domain-joined-windows-client"></a>SSMS auf einem Client für die Domäne eingebundenen Windows

Melden Sie sich eine Domäne eingebundenen Windows-Client über Ihre Domänenanmeldeinformationen an. Stellen Sie sicher, dass SQL Server Management Studio installiert ist, und klicken Sie dann eine Verbindung mit Ihrer SQL Server-Instanz (z. B. `mssql-host.contoso.com`) durch Angabe **Windows-Authentifizierung** in die **Herstellen einer Verbindung mit Server** Dialogfeld.

### <a name="ad-authentication-using-other-client-drivers"></a>AD-Authentifizierung mit anderen Clienttreibern

In der folgende Tabelle werden die Empfehlungen für andere Clienttreiber beschrieben:

| Client-Treiber | Empfehlung |
|---|---|
| **JDBC** | Verwenden Sie integrierte Kerberos-Authentifizierung, SqlServer zu verbinden. |
| **ODBC** | Verwenden Sie integrierte Authentifizierung. |
| **ADO.NET** | Syntax für Verbindungszeichenfolgen. |

## <a id="additionalconfig"></a> Zusätzliche Konfigurationsoptionen

Wenn Sie z. B. Drittanbieter-Dienstprogramme verwenden [PBIS](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), oder [Centrify](https://www.centrify.com/) zum Hinzufügen des Linux-Hosts mit AD-Domäne, und Sie möchten erzwingen, dass SQLServer mithilfe der Openldap Bibliothek direkt verwenden, können Sie konfigurieren die **Disablesssd** mit option **Mssql-Conf** wie folgt:

```bash
sudo mssql-conf set network.disablesssd true
systemctl restart mssql-server
```

> [!NOTE]
> Gibt es Hilfsprogramme wie z. B. **Realmd** die einrichten, SSSD, während andere Tools wie z. B. PBIS, VAS und Centrify SSSD nicht eingerichtet. Wenn das Hilfsprogramm verwendet, um AD-Domäne nicht SSSD eingerichtet ist, es wird empfohlen, konfigurieren Sie **Disablesssd** option `true`. Obwohl es nicht erforderlich ist, wie SQL Server versucht SSSD für AD vor dem Fallback auf Openldap-Mechanismus verwenden, wäre es bieten eine bessere Leistung konfigurieren, damit SQL Server Openldap direkt unter Umgehung des SSSD-Mechanismus aufruft.

Wenn Ihr Domänencontroller LDAPS unterstützt, können Sie alle Verbindungen zwischen SQL Server und den Domänencontrollern über LDAPS erzwingen. Überprüfen der Client kann wenden Sie sich an den Domänencontroller über Ldaps, führen Sie den folgenden Bash-Befehl, `ldapsearch -H ldaps://contoso.com:3269`. Um SQL Server zur Verwendung von LDAPS festzulegen, führen Sie Folgendes ein:

```bash
sudo mssql-conf set network.forceldaps true
systemctl restart mssql-server
```

Hiermit wird LDAPS über SSSD verwendet, wenn AD-Domäne auf Host über SSSD-Paket ausgeführt wurde und **Disablesssd** ist nicht festgelegt auf "true". Wenn **Disablesssd** nastaven NA hodnotu True, zusammen mit **Forceldaps** festgelegt auf "true", dann LDAPS-Protokoll über Openldap-Bibliothek-Aufrufe, die von SQL Server verwenden.

### <a name="post-sql-server-2017-cu14"></a>SQL Server 2017 CU14 Posten

Ab SQL Server 2017 CU14, wenn SQL Server verknüpft wurde, mit einem AD-Domänencontroller, die mithilfe von Drittanbietern und Openldap-Aufrufe für allgemeine AD-Suche verwendet werden, durch Festlegen von konfiguriert ist **Disablesssd** auf "true", können Sie auch **enablekdcfromkrb5** Option zum Erzwingen von SQL Server krb5-Bibliothek für die KDC-Suche, anstelle von reverse-DNS-Lookup für die KDC-Server zu verwenden.

Dies kann für das Szenario nützlich sein, in denen Domänencontroller manuell zu konfigurieren, denen Kommunikation mit SQL Server versucht werden soll. Und Sie verwenden den Openldap-Bibliothek-Mechanismus, indem Sie der KDC-Liste in **krb5.conf**.

Legen Sie zuerst die **Disablessd** und **enablekdcfromkrb5conf** auf "true", und klicken Sie dann SQL Server neu starten:

```bash
sudo mssql-conf set network.disablesssd true
sudo mssql-conf set network.enablekdcfromkrb5conf true
systemctl restart mssql-server
```

Konfigurieren Sie dann die KDC-Liste in **/etc/krb5.conf** wie folgt:

```/etc/krb5.conf
[realms]
CONTOSO.COM = {
  kdc = dcWithGC1.contoso.com
  kdc = dcWithGC2.contoso.com
}
```

> [!NOTE]
> Zwar wird nicht empfohlen, ist es möglich,-Hilfsprogramme, z. B. verwenden **Realmd**, SSSD beim Verknüpfen des Linux-Hosts mit der Domäne während der Konfiguration eingerichtet **Disablesssd** auf "true", damit SQL Server verwendet. OpenLDAP Aufrufe im Zusammenhang mit stattdessen von SSSD für Active Directory aufrufen.

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
