---
title: 'Lernprogramm: Verwenden der Active Directory-Authentifizierung für SQL Server für Linux'
titleSuffix: SQL Server
description: In diesem Tutorial werden die Konfigurationsschritte für die Active Directory-Authentifizierung für SQL Server für Linux beschrieben.
author: Dylan-MSFT
ms.author: dygray
ms.reviewer: vanto
ms.date: 04/01/2019
ms.topic: tutorial
ms.prod: sql
ms.custom: seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 69bbeb31f8da4023bd0630ae0d944165407e2dec
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68027329"
---
# <a name="tutorial-use-active-directory-authentication-with-sql-server-on-linux"></a>Lernprogramm: Verwenden der Active Directory-Authentifizierung für SQL Server für Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Tutorial wird erläutert, wie Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Linux konfigurieren, um die Active Directory-Authentifizierung (AD) zu unterstützen, die auch als integrierte Authentifizierung bezeichnet wird. Eine Übersicht dazu finden Sie unter [Active Directory-Authentifizierung für SQL Server für Linux](sql-server-linux-active-directory-auth-overview.md).

Dieses Tutorial umfasst die folgenden Aufgaben:

> [!div class="checklist"]
> * Verknüpfen des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Hosts mit der AD-Domäne
> * Erstellen eines AD-Benutzers für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und Festlegen eines SPN
> * Konfigurieren der KEYTAB-Datei für den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dienst
> * Sichern der KEYTAB-Datei
> * Konfigurieren von SQL Server für die Verwendung der KEYTAB-Datei für die Kerberos-Authentifizierung
> * Erstellen von AD-basierten Anmeldeinformationen in Transact-SQL
> * Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] über die AD-Authentifizierung

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie die AD-Authentifizierung konfigurieren können, müssen Sie Folgendes tun:

* Richten Sie einen AD-Domänencontroller (Windows) auf Ihrem Netzwerk ein.  
* Installieren Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].
  * [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server (SLES)](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> Verknüpfen des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Hosts mit der AD-Domäne

Sie müssen Ihren Linux-Host für SQL Server mit einem AD-Domänencontroller verknüpfen. Informationen dazu finden Sie unter [Verknüpfen von eines Linux-Hosts für SQL Server mit einer Active Directory-Domäne](sql-server-linux-active-directory-join-domain.md).

## <a id="createuser"></a> Erstellen eines AD-Benutzers (oder -MSA) für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und Festlegen eines SPN

> [!NOTE]
> Verwenden Sie für die folgenden Schritte Ihren [vollqualifizierten Domänennamen](https://en.wikipedia.org/wiki/Fully_qualified_domain_name). Wenn Sie in **Azure** arbeiten, müssen Sie **[einen erstellen](https://docs.microsoft.com/azure/virtual-machines/linux/portal-create-fqdn)** ,bevor Sie fortfahren können.

1. Führen Sie auf Ihrem Domänencontroller den PowerShell-Befehl [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx) aus, um einen neuen AD-Benutzer mit einem Kennwort zu erstellen, das niemals abläuft. Im folgenden Beispiel hat das Konto den Namen `mssql`. Sie können aber jeden beliebigen Namen auswählen. Sie werden aufgefordert, ein neues Kennwort für das Konto einzugeben.

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > Es hat sich als Sicherheitsmethode bewährt, ein dediziertes AD-Konto für SQL Server zu verwenden, damit die Anmeldeinformationen für SQL Server nicht für andere Dienste freigegeben werden, die dasselbe Konto verwenden. Sie können jedoch als Alternative auch ein vorhandenes AD-Konto wiederverwenden, wenn Sie das Kennwort für das Konto kennen. Sie benötigen dieses, um im nächsten Schritt eine KEYTAB-Datei zu erstellen.

2. Legen Sie den Dienstprinzipalnamen (Service Principle Name, SPN) für dieses Konto mithilfe des Tools **setspn.exe** fest. Der SPN muss genau wie im folgenden Beispiel angegeben formatiert werden. Sie können den vollqualifizierten Domänennamen des Hostcomputers für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ermitteln, indem Sie `hostname --all-fqdns` auf de Host [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ausführen. In der Regel wird der TCP-Port 1433 verwendet, es sei denn, Sie haben [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] so konfiguriert, dass eine andere Portnummer verwendet wird.

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   setspn -A MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > Wenn Sie die Fehlermeldung `Insufficient access rights` erhalten, prüfen Sie zusammen mit Ihrem Domänenadministrator, ob Sie über die nötigen Berechtigungen verfügen, um einen SPN für dieses Konto festzulegen.
   >
   > Wenn Sie den TCP-Port später ändern, müssen Sie den Befehl **setspn** noch einmal mit der neuen Portnummer ausführen. Außerdem müssen Sie den neuen SPN zur KEYTAB-Datei des SQL Server-Diensts hinzufügen, indem Sie die im nächsten Abschnitt beschriebenen Schritte ausführen.

Weitere Informationen finden Sie unter [Registrieren eines Dienstprinzipalnamens für Kerberos-Verbindungen](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).

## <a id="configurekeytab"></a> Konfigurieren der KEYTAB-Datei für den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dienst

Es gibt zwei Möglichkeiten, KEYTAB-Dateien für den SQL Server-Dienst zu konfigurieren. Sie können entweder ein Computerkonto (User Principal Name, UPN) oder ein verwaltetes Dienstkonto (Managed Service Account, MSA) für die KEYTAB-Konfiguration verwenden. Beide Methoden funktionieren gleich gut. Daher können Sie die Option auswählen, die für Ihre Umgebung am besten geeignet ist.

Für beide Methoden benötigen Sie den SPN, der im vorherigen Schritt erstellt wurde. Dieser muss in der KEYTAB-Datei registriert sein.

So konfigurieren Sie die KEYTAB-Datei für den SQL Server-Dienst:

1. Konfigurieren Sie die [KEYTAB-Einträge für den SPN](#spn) im nächsten Abschnitt.

1. Fügen Sie dann entweder [UPN](#upn)- (Methode 1) oder [MSA](#msa)-Einträge (Methode 2) zur KEYTAB-Datei hinzu. Führen Sie dazu die Schritte aus, die in den entsprechenden Abschnitten beschrieben werden.

> [!IMPORTANT]
> Wenn das Kennwort für den UPN bzw. das MSA oder das Kennwort für das Konto geändert wird, dem die SPNs zugewiesen sind, müssen Sie die KEYTAB-Datei mit dem neuen Kennwort und der Schlüsselversionsnummer (Key Version Number, KVNO) aktualisieren. Einige Dienste rotieren die Kennwörter möglicherweise auch automatisch. Überprüfen Sie sämtliche Richtlinien für die Kennwortrotation, die für die betreffenden Konten gelten, und passen Sie geplante Wartungsaktivitäten an diese an, um unerwartete Ausfallzeiten zu vermeiden.

### <a id="spn"></a> KEYTAB-Einträge für den SPN

1. Überprüfen Sie die KVNO des AD-Kontos, das Sie im vorherigen Schritt erstellt haben. Normalerweise lautet diese 2, aber es kann auch ein anderer Integerwert sein, wenn Sie das Kennwort des Kontos mehrmals geändert haben. Führen Sie auf dem Hostcomputer für SQL Server die folgenden Befehle aus:

   ```bash
   kinit user@CONTOSO.COM
   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM
   ```

   > [!NOTE]
   > Es kann einige Minuten dauern, bis die SPNs für Ihre Domäne übernommen werden, insbesondere, wenn die Domäne groß ist. Wenn Sie die Fehlermeldung `kvno: Server not found in Kerberos database while getting credentials for MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM` erhalten, warten Sie einige Minuten, und versuchen Sie es noch mal.  

1. Starten Sie das Tool **ktutil**:

   ```bash
   sudo ktutil
   ```

1. Fügen Sie mithilfe der folgenden Befehle KEYTAB-Einträge für jeden SPN hinzu:

   ```bash
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   ```

1. Schreiben Sie die Einträge in eine Datei, und beenden Sie dann das Tool ktutil:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

   > [!NOTE]
   > Das Tool **ktutil** überprüft das Kennwort nicht. Vergewissern Sie sich daher, dass Sie es bei entsprechender Aufforderung korrekt eingeben.

### <a id="upn"></a> Option 1: Verwenden des UPN zum Konfigurieren der KEYTAB-Datei

Fügen Sie mithilfe von **ktutil** das Computerkonto zu Ihrer KEYTAB-Datei. Das Computerkonto (auch als UPN bezeichnet) ist in der Datei **/etc/krb5.keytab** in der Form `<hostname>$@<realm.com>` enthalten (z. B. `sqlhost$@CONTOSO.COM`). Kopieren Sie diese Einträge aus der Datei **/etc/krb5.keytab** in die Datei **mssql.keytab**.

1. Starten Sie **ktuil** mithilfe des folgenden Befehls:

   ```bash
   sudo ktutil
   ```

1. Verwenden Sie den Befehl **rkt**, um alle Einträge aus der Datei **/etc/krb5.keytab** zu lesen.

   ```bash
   rkt /etc/krb5.keytab
   ```

1. Listen Sie als Nächstes die Einträge auf.

   ```bash
   list
   ```

1. Löschen Sie alle Einträge anhand ihrer Slotnummern (nicht der UPN). Löschen Sie einen Eintrag nach dem anderen, indem Sie den folgenden Befehl wiederholen:

   ```bash
   delent <slot num>
   ```

   > [!IMPORTANT]
   > Wenn ein Eintrag gelöscht wird, z. B. Slot 1, rücken alle Werte um einen Platz nach oben. Das heißt: Der Eintrag in Slot 2 wechselt zu Slot 1, wenn der Eintrag in Slot 1 gelöscht wird.

1. Listen Sie die Einträge so lange neu auf, bis nur noch UPN-Einträge übrig sind.

   ```bash
   list
   ```

1. Wenn nur noch UPN-Einträge übrig sind, sollten Sie diese Werte an die Datei **mssql.keytab** anfügen:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   ```

1. Beenden Sie **ktutil**.

   ```bash
   quit
   ```

### <a id="msa"></a> Option 2:  Verwenden des MSA zum Konfigurieren der KEYTAB-Datei

Wenn Sie sich für die MSA-Methode entscheiden, müssen Sie die Kerberos-KEYTAB-Datei für SQL Server erstellen. In dieser sollten alle [im ersten Schritt registrierten SPNs](#spn) und die Anmeldeinformationen für das MSA enthalten sein, für das die SPNs registriert sind. 

1. Führen Sie nach dem Erstellen der KEYTAB-Einträge für die SPNs die folgenden Befehle auf einem Linux-Computer aus, der in eine Domäne eingebunden ist:

   ```bash
   kinit <AD user>
   kvno <any SPN registered in step 1>
      <spn>@CONTOSO.COM: kvno = <KVNO>
   ```

   In diesem Schritt wird die KVNO für das Benutzerkonto angezeigt, das dem SPN als Besitzer zugewiesen ist. Damit dieser Schritt funktioniert, muss der SPN bei seiner Erstellung dem MSA zugewiesen worden sein. Wenn der SPN nicht dem MSA zugewiesen wurde, stammt die angezeigte KVNO vom aktuellen SPN-Besitzerkonto und kann nicht für die Konfiguration verwendet werden.  

1. Starten Sie das Tool **ktutil**:

   ```bash
   sudo ktutil
   ```

1. Fügen Sie das MSA mithilfe der folgenden zwei Befehlen hinzu:

   ```bash
   addent -password -p <MSA> -k <kvno from command above> -e aes256-cts-hmac-sha1-96
   addent -password -p <MSA> -k <kvno from command above> -e rc4-hmac
   ```

1. Schreiben Sie die Einträge in eine Datei, und beenden Sie dann das Tool ktutil:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

1. Wenn Sie sich für die MSA-Methode entscheiden, muss mithilfe des Tools **mssql-conf** eine Konfigurationsoption festgelegt werden, um das MSA anzugeben, das beim Zugreifen auf die KEYTAB-Datei verwendet werden soll. Stellen Sie sicher, dass die folgenden Werte in der Datei **/var/opt/mssql/mssql.conf** enthalten sind.

   ```bash
   sudo mssql-conf set network.privilegedadaccount <MSA_Name>
   ```

   > [!NOTE]
   > Fügen Sie nur den MSA-Namen und nicht den Namen oder Domäne oder des Kontos ein.

## <a id="securekeytab"></a> Sichern der KEYTAB-Datei

Jeder Benutzer mit Zugriff auf diese KEYTAB-Datei kann die Identität von SQL Server in der Domäne annehmen. Stellen Sie daher sicher, dass Sie den Zugriff auf die Datei so einschränken, dass nur das MSSQL-Konto über Lesezugriff verfügt:

```bash
sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
```

## <a id="keytabkerberos"></a> Konfigurieren von SQL Server für die Verwendung der KEYTAB-Datei für die Kerberos-Authentifizierung

Gehen Sie wie im Folgenden beschrieben vor, um die SQL Server-Instanz so zu konfigurieren, dass die KEYTAB-Datei für die Kerberos-Authentifizierung verwendet werden kann.

```bash
sudo mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
sudo systemctl restart mssql-server
```

Optional können Sie die UDP-Verbindungen mit dem Domänencontroller deaktivieren, um die Leistung zu verbessern. In vielen Fällen schlagen UDP-Verbindungen beim Herstellen einer Verbindung mit einem Domänencontroller immer wieder fehl. Sie können deshalb in den Konfigurationsoptionen in der Datei **/etc/krb5.conf** festlegen, dass UDP-Aufrufe übersprungen werden sollen. Bearbeiten Sie die Datei **/etc/krb5.conf**, und legen Sie die folgenden Optionen fest:

```/etc/krb5.conf
[libdefaults]
udp_preference_limit=0
```

Nun können Sie AD-basierte Anmeldeinformationen in SQL Server verwenden. Gehen Sie dafür wie im Folgenden Abschnitt beschrieben vor.

## <a id="createsqllogins"></a> Erstellen von AD-basierten Anmeldeinformationen in Transact-SQL

1. Stellen Sie eine Verbindung mit SQL Server her, und erstellen Sie neue AD-basierte Anmeldeinformationen:

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

1. Überprüfen Sie danach, ob diese Anmeldeinformationen in der Systemkatalogsicht [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) aufgeführt werden:

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a id="connect"></a> Herstellen einer Verbindung mit SQL Server über die AD-Authentifizierung

Melden Sie sich über Ihre Domänenanmeldeinformationen bei einem Clientcomputer an. Nun können Sie eine Verbindung mit SQL Server herstellen, ohne Ihr Kennwort über die AD-Authentifizierung erneut eingeben zu müssen. Wenn Sie Anmeldeinformationen für eine AD-Gruppe erstellen, kann jeder AD-Benutzer, der Mitglied dieser Gruppe ist, auf die gleiche Weise eine Verbindung herstellen.

Der genaue Verbindungszeichenfolgenparameter, den die Clients benötigen, um die AD-Authentifizierung verwenden zu können, ist davon abhängig, welchen Treiber Sie verwenden. Beispiele dazu finden Sie in den folgenden Abschnitten.

### <a name="sqlcmd-on-a-domain-joined-linux-client"></a>sqlcmd auf einem in die Domäne eingebundenen Linux-Client

Melden Sie sich mithilfe von **ssh** und Ihren Domänenanmeldeinformationen bei einem in die Domäne eingebundenen Linux-Client an:

```bash
ssh -l user@contoso.com client.contoso.com
```

Stellen Sie sicher, dass das Paket [mssql-tools](sql-server-linux-setup-tools.md) installiert wurde, und stellen Sie dann mithilfe von **sqlcmd** eine Verbindung her, ohne die Anmeldeinformationen anzugeben:

```bash
sqlcmd -S mssql-host.contoso.com
```

### <a name="ssms-on-a-domain-joined-windows-client"></a>SSMS auf einem in die Domäne eingebundenen Windows-Client

Melden Sie sich mithilfe Ihrer Domänenanmeldeinformationen bei einem in die Domäne eingebundenen Windows-Client an. Vergewissern Sie sich, dass SQL Server Management Studio installiert ist, und stellen Sie dann eine Verbindung mit Ihrer SQL Server-Instanz her (z. B. `mssql-host.contoso.com`), indem Sie im Dialogfeld **Mit Server verbinden** **Windows-Authentifizierung** angeben.

### <a name="ad-authentication-using-other-client-drivers"></a>AD-Authentifizierung mit anderen Clienttreibern

In der folgenden Tabelle werden die Empfehlungen für andere Clienttreiber beschrieben:

| Clienttreiber | Empfehlung |
|---|---|
| **JDBC** | Verwenden Sie die integrierte Kerberos-Authentifizierung, um eine Verbindung mit der SQL Server-Instanz herzustellen. |
| **ODBC** | Verwenden Sie die integrierte Authentifizierung. |
| **ADO.NET** | Verwenden Sie die Syntax der Verbindungszeichenfolge. |

## <a id="additionalconfig"></a> Zusätzliche Konfigurationsoptionen

Wenn Sie Hilfsprogramme von Drittanbietern wie [PBIS](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/) oder [Centrify](https://www.centrify.com/) verwenden, um den Linux-Host mit der AD-Domäne zu verknüpfen, und Sie erzwingen möchten, dass die SQL Server-Instanz die OpenLDAP-Bibliothek direkt verwendet, können Sie die Option **disablesssd** wie folgt mithilfe des Tools **mssql-conf** konfigurieren:

```bash
sudo mssql-conf set network.disablesssd true
systemctl restart mssql-server
```

> [!NOTE]
> Einige Hilfsprogramme wie **realmd** richten die SSSD ein, wohingegen andere Tools wie PBIS, VAS und Centrify dies nicht tun. Wenn das Hilfsprogramm, das verwendet wird, um die AD-Domäne zu verknüpfen, nicht SSSD einrichtet, empfiehlt es sich, die Option **disablesssd** auf `true` festzulegen. Dies ist zwar nicht zwingend notwendig, weil die SQL Server-Instanz versucht, SSSD zu verwenden, bevor sie auf den OpenLDAP-Mechanismus zurückgreift, aber Sie würden dadurch die Leistung verbessern, weil die Instanz dann direkt OpenLDAP-Aufrufe durchführt und den SSSD-Mechanismus umgeht.

Wenn Ihr Domänencontroller LDAPS unterstützt, können Sie erzwingen, dass alle Verbindungen der SQL Server-Instanz mit den Domänencontrollern über LDAPS erfolgen. Führen Sie den Bash-Befehl `ldapsearch -H ldaps://contoso.com:3269` aus, um zu überprüfen, ob der Client den Domänencontroller über LDAPS kontaktieren kann. Wenn Sie festlegen möchten, dass SQL Server nur LDAPS verwendet, führen Sie Folgendes aus:

```bash
sudo mssql-conf set network.forcesecureldap true
systemctl restart mssql-server
```

Dann wird LDAPS vor SSSD verwendet, wenn der Domänenbeitritt auf dem Host über das SSSD-Paket erfolgt ist und die Option **disablesssd** nicht auf TRUE festgelegt wurde. Wenn sowohl **disablesssd** als auch **forcesecureldap** auf TRUE festgelegt sind, wird das LDAPS-Protokoll gegenüber Aufrufen der OpenLDAP-Bibliothek bevorzugt, die von der SQL Server-Instanz ausgeführt werden.

### <a name="post-sql-server-2017-cu14"></a>Vorgehensweise ab Version SQL Server 2017 CU14

Ab SQL Server 2017 CU14, können Sie auch die Option **enablekdcfromkrb5** verwenden, um zu erzwingen, dass die SQL Server-Instanz anstelle eines DNS-Reverse-Lookups für den KDC-Server die krb5-Bibliothek für die KDC-Suche verwendet. Voraussetzung dafür ist, dass die SQL Server-Instanz mithilfe eines Drittanbieters mit der Domäne verknüpft und die Option **disablesssd** auf TRUE festgelegt wurde, sodass OpenLDAP-Aufrufe für die allgemeine AD-Suche verwendet werden.

Dies kann in Szenarios nützlich sein, in denen Sie die Domänencontroller, mit denen die SQL Server-Instanz kommuniziert, manuell konfigurieren möchten. Sie können den OpenLDAP-Bibliotheksmechanismus mithilfe der KDC-Liste in der Datei **krb5.conf** verwenden.

Legen Sie zunächst die Optionen **disablessd** und **enablekdcfromkrb5conf** auf TRUE fest, und starten Sie dann die SQL Server-Instanz neu:

```bash
sudo mssql-conf set network.disablesssd true
sudo mssql-conf set network.enablekdcfromkrb5conf true
systemctl restart mssql-server
```

Konfigurieren Sie anschließend wie folgt die KDC-Liste in der Datei **/etc/krb5.conf**:

```/etc/krb5.conf
[realms]
CONTOSO.COM = {
  kdc = dcWithGC1.contoso.com
  kdc = dcWithGC2.contoso.com
}
```

> [!NOTE]
> Es wird zwar nicht empfohlen, aber es ist trotzdem möglich, Hilfsprogramme wie **realmd** zu verwenden, die SSSD einrichten, während der Linux-Host der Domäne beitritt, wenn Sie die Option **disablesssd** auf TRUE festlegen, sodass die SQL Server-Instanz OpenLDAP-Aufrufe anstelle von SSSD für Aufrufe im Zusammenhang mit AD verwendet.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben wir erläutert, wie Sie die Active Directory-Authentifizierung mit SQL Server für Linux einrichten können. Sie haben Folgendes gelernt:
> [!div class="checklist"]
> * Verknüpfen des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Hosts mit der AD-Domäne
> * Erstellen eines AD-Benutzers für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und Festlegen eines SPN
> * Konfigurieren der KEYTAB-Datei für den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dienst
> * Erstellen von AD-basierten Anmeldeinformationen in Transact-SQL
> * Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] über die AD-Authentifizierung

Lernen Sie als Nächstes weitere Sicherheitsszenarios für SQL Server für Linux kennen.

> [!div class="nextstepaction"]
> [Verschlüsseln von Verbindungen mit SQL Server](sql-server-linux-encrypted-connections.md)
