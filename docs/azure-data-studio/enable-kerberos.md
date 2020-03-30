---
title: Verwenden der Azure Active Directory-Authentifizierung (Kerberos)
titleSuffix: Azure Data Studio
description: Erfahren Sie, wie Sie Kerberos zur Verwendung für die Active Directory-Authentifizierung für Azure Data Studio aktivieren.
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: meet-bhagdev
ms.author: meetb
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 8aa4502fca51ef8dc15fceb119297915a64bc682
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "74957064"
---
# <a name="connect-name-sos-to-your-sql-server-using-windows-authentication---kerberos"></a>Stellen Sie eine Verbindung von [!INCLUDE[name-sos](../includes/name-sos-short.md)] mit Ihrer SQL Server-Instanz mithilfe der Windows-Authentifizierung (Kerberos) her. 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] unterstützt das Herstellen der Verbindung mit SQL Server mithilfe von Kerberos.

Um die integrierte Authentifizierung (Windows-Authentifizierung) unter macOS oder Linux verwenden zu können, müssen Sie ein **Kerberos-Ticket** einrichten, mit dem Ihr aktueller Benutzer mit einem Windows-Domänenkonto verknüpft wird. 

## <a name="prerequisites"></a>Voraussetzungen

- Zugriff auf einen in die Windows-Domäne eingebundenen Computer, um den Kerberos-Domänencontroller abzufragen.
- SQL Server sollte so konfiguriert werden, dass die Kerberos-Authentifizierung zulässig ist. Für den Clienttreiber, der unter UNIX ausgeführt wird, wird die integrierte Authentifizierung nur mit Kerberos unterstützt. Weitere Informationen finden Sie unter [Verwenden der integrierten Kerberos-Authentifizierung für Verbindungen mit SQL Server](../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md). Für jede Instanz von SQL Server, mit der Sie eine Verbindung herstellen möchten, müssen SPNs registriert sein. Weitere Informationen finden Sie unter [Registrieren eines Dienstprinzipalnamens](https://technet.microsoft.com/library/ms191153%28v=sql.105%29.aspx#SPN%20Formats).


## <a name="checking-if-sql-server-has-kerberos-setup"></a>Überprüfen, ob SQL Server ein Kerberos-Setup aufweist

Melden Sie sich beim Hostcomputer von SQL Server an. Verwenden Sie in der Windows-Eingabeaufforderung `setspn -L %COMPUTERNAME%`, um alle Dienstprinzipalnamen für den Host aufzulisten. Es sollten Einträge angezeigt werden, die mit „MSSQLSvc/HostName.Domain.com“ beginnen. Dies bedeutet, dass SQL Server einen SPN registriert hat und bereit ist, die Kerberos-Authentifizierung zu akzeptieren. 
- Wenn Sie keinen Zugriff auf den Host von SQL Server haben, könnten Sie von allen anderen Windows-Betriebssystemen aus, die mit derselben Active Directory-Instanz verknüpft sind, den Befehl `setspn -L <SQLSERVER_NETBIOS>` verwenden, wobei <SQLSERVER_NETBIOS> der Computername des Hosts von SQL Server ist.


## <a name="get-the-kerberos-key-distribution-center"></a>Abrufen des Kerberos-Schlüsselverteilungscenters

Suchen Sie den Kerberos-KDC-Konfigurationswert (Key Distribution Center, Schlüsselverteilungscenter). Führen Sie den folgenden Befehl auf einem Windows-Computer aus, der mit Ihrer Active Directory-Domäne verknüpft ist: 

Starten Sie `cmd.exe`, und führen Sie `nltest` aus.

```
nltest /dsgetdc:DOMAIN.COMPANY.COM (where "DOMAIN.COMPANY.COM" maps to your domain's name)

Sample Output
DC: \\dc-33.domain.company.com
Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
...
The command completed successfully
```
Kopieren Sie den DC-Namen, der der erforderliche KDC-Konfigurationswert ist, in diesem Fall „dc-33.domain.company.com“.

## <a name="join-your-os-to-the-active-directory-domain-controller"></a>Verknüpfen Ihres Betriebssystems mit dem Active Directory-Domänencontroller

### <a name="ubuntu"></a>Ubuntu
```bash
sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
```

Bearbeiten Sie die `/etc/network/interfaces`-Datei so, dass die IP-Adresse Ihres AD-Domänencontrollers als DNS-Namensserver aufgeführt ist. Beispiel: 

```/etc/network/interfaces
<...>
# The primary network interface
auth eth0
iface eth0 inet dhcp
dns-nameservers **<AD domain controller IP address>**
dns-search **<AD domain name>**
```

> [!NOTE]
> Die Netzwerkschnittstelle (eth0) kann für verschiedene Computer unterschiedlich sein. Um herauszufinden, welche Sie verwenden, führen Sie ifconfig aus, und kopieren Sie die Schnittstelle, die über eine IP-Adresse verfügt und Bytes übermittelt und empfangen hat.

Nachdem Sie diese Datei bearbeitet haben, sollten Sie den Netzwerkdienst neu starten:

```bash
sudo ifdown eth0 && sudo ifup eth0
```

Überprüfen Sie nun, ob die `/etc/resolv.conf`-Datei eine Zeile wie die folgende enthält:  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
```
   
### <a name="redhat-enterprise-linux"></a>Red Hat Enterprise Linux
```bash
sudo yum install realmd krb5-workstation
```

Bearbeiten Sie die `/etc/sysconfig/network-scripts/ifcfg-eth0`-Datei (oder eine andere entsprechende Schnittstellenkonfigurations-Datei), sodass die IP-Adresse Ihres AD-Domänencontrollers als DNS-Server aufgeführt wird:

```/etc/sysconfig/network-scripts/ifcfg-eth0
<...>
PEERDNS=no
DNS1=**<AD domain controller IP address>**
```

Nachdem Sie diese Datei bearbeitet haben, sollten Sie den Netzwerkdienst neu starten:

```bash
sudo systemctl restart network
```

Überprüfen Sie nun, ob die `/etc/resolv.conf`-Datei eine Zeile wie die folgende enthält:  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
   
```

### <a name="macos"></a>macOS

- Verknüpfen Sie Ihr macOS mit dem Active Directory-Domänencontroller ein, indem Sie die folgenden Schritte ausführen:



## <a name="configure-kdc-in-krb5conf"></a>Konfigurieren von KDC in „krb5.conf“

Bearbeiten Sie `/etc/krb5.conf` in einem Editor Ihrer Wahl. Konfigurieren Sie die folgenden Schlüssel

```bash
sudo vi /etc/krb5.conf

[libdefaults]
  default_realm = DOMAIN.COMPANY.COM
 
[realms]
DOMAIN.COMPANY.COM = {
   kdc = dc-33.domain.company.com
}
```

Speichern Sie dann die Datei „krb5.conf“, und beenden Sie den Editor.

> [!NOTE]
> Die Domäne muss VOLLSTÄNDIG IN GROSSBUCHSTABEN angegeben werden.


## <a name="test-the-ticket-granting-ticket-retrieval"></a>Testen des Ticket Granting Ticket-Abrufs

Rufen Sie ein Ticket Granting Ticket (TGT) aus dem KDC ab.

```bash
kinit username@DOMAIN.COMPANY.COM
```

Zeigen Sie die verfügbaren Tickets mithilfe von „klist“ an. Wenn „kinit“ erfolgreich war, sollte ein Ticket angezeigt werden. 

```bash
klist

krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.
```

## <a name="connect-using-name-sos"></a>Herstellen einer Verbindung mit [!INCLUDE[name-sos](../includes/name-sos-short.md)]

* Erstellen Sie ein neues Verbindungsprofil.

* Wählen Sie **Windows-Authentifizierung** als Authentifizierungstyp aus.

* Vervollständigen Sie das Verbindungsprofil, und klicken Sie auf **Verbinden**.

Nachdem die Verbindung erfolgreich hergestellt wurde, wird Ihr Server in der Randleiste *Server* angezeigt.
