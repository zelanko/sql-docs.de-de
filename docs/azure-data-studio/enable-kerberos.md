---
title: Verwenden Sie Active Directory-Authentifizierung (Kerberos)
titleSuffix: Azure Data Studio
description: Informationen Sie zum Aktivieren von Kerberos verwendet Active Directory-Authentifizierung für Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: meet-bhagdev
ms.author: meetb
manager: craigg
ms.openlocfilehash: b73e144dd362691ea93b3312f6dc10ce542f1c43
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030214"
---
# <a name="connect-includename-sosincludesname-sos-shortmd-to-your-sql-server-using-windows-authentication---kerberos"></a>Herstellen einer mit [!INCLUDE[name-sos](../includes/name-sos-short.md)] zu Ihrem SQL Server mithilfe der Windows-Authentifizierung – Kerberos 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] unterstützt das Herstellen einer Verbindung mit SQL Server mithilfe von Kerberos.

Um die integrierte Authentifizierung (Windows-Authentifizierung) unter MacOS oder Linux verwenden zu können, müssen Sie richten eine **Kerberos-Ticket** verknüpfen Ihres aktuellen Benutzers zu einem Windows-Domänenkonto. 

## <a name="prerequisites"></a>Erforderliche Komponenten

- Zugriff auf ein Windows-Domäne eingebundenen Computer zum Abfragen von Ihrem Kerberos-Domänencontroller.
- SQL Server sollte für die Kerberos-Authentifizierung können konfiguriert werden. Für den Clienttreiber auf Unix ausgeführt wird wird nur der integrierten Authentifizierung unterstützt mithilfe von Kerberos. Weitere Informationen zum Einrichten von Sql Server für die Authentifizierung mit Kerberos finden Sie [hier](https://support.microsoft.com/en-us/help/319723/how-to-use-kerberos-authentication-in-sql-server). Es sollte Dienstprinzipalnamen für jede Instanz von Sql Server, die Sie herstellen möchten. Finden Sie Informationen über das Format von SQL Server-SPNs [hier](https://technet.microsoft.com/library/ms191153%28v=sql.105%29.aspx#SPN%20Formats)


## <a name="checking-if-sql-server-has-kerberos-setup"></a>Überprüft, ob Sql Server auf Kerberos-Einrichtung ist

Melden Sie sich den Hostcomputer des Sql Server. Verwenden von Windows-Eingabeaufforderung die `setspn -L %COMPUTERNAME%` zum Auflisten aller Dienstprinzipalnamen für den Host. Sie sollte Einträge, die mit MSSQLSvc/HostName.Domain.com, was bedeutet beginnen, dass Sql Server einen SPN registriert hat und zum Annehmen von Kerberos-Authentifizierung bereit ist. 
- Wenn Sie keinen Zugriff auf den Host des Sql Servers, von einem beliebigen anderen Windows Betriebssystem mit der gleichen Active Directory verknüpft, können Sie den Befehl `setspn -L <SQLSERVER_NETBIOS>` , in denen < SQLSERVER_NETBIOS > ist der Computername des von Sql Server-Hosts.


## <a name="get-the-kerberos-key-distribution-center"></a>Abrufen von Kerberos Key Distribution Center

Suchen Sie den Konfigurationswert für die Kerberos-KDC (Key Distribution Center). Führen Sie den folgenden Befehl auf einem Windows-Computer, der mit Ihrer Active Directory-Domäne verknüpft ist: 

Starten Sie `cmd.exe` , und führen Sie `nltest`.

```
nltest /dsgetdc:DOMAIN.COMPANY.COM (where "DOMAIN.COMPANY.COM" maps to your domain's name)

Sample Output
DC: \\dc-33.domain.company.com
Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
...
The command completed successfully
```
Kopieren Sie den DC-Namen, die den Wert der erforderlichen KDC-Konfiguration, in diesem Fall dc-33.domain.company.com

## <a name="join-your-os-to-the-active-directory-domain-controller"></a>Verknüpfen Sie Ihr Betriebssystem, mit der Active Directory-Domänencontroller

### <a name="ubuntu"></a>Ubuntu
```bash
sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
```

Bearbeiten der `/etc/network/interfaces` Datei, damit Ihre AD-Domänencontroller-IP-Adresse als eine Dns-Namenserver aufgeführt ist. Beispiel: 

```/etc/network/interfaces
<...>
# The primary network interface
auth eth0
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

Nun überprüfen Sie, ob Ihre `/etc/resolv.conf` Datei enthält eine Zeile wie folgt:  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
```
   
### <a name="redhat-enterprise-linux"></a>RedHat Enterprise Linux
```bash
sudo yum install realmd krb5-workstation
```

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

Nun überprüfen Sie, ob Ihre `/etc/resolv.conf` Datei enthält eine Zeile wie folgt:  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
   
```

### <a name="macos"></a>macOS

- Verbinden Sie Ihr MacOS mit der Active Directory-Domänencontroller, mit folgenden Schritten:



## <a name="configure-kdc-in-krb5conf"></a>Konfigurieren von KDC in krb5.conf

Bearbeiten der `/etc/krb5.conf` in einem Editor Ihrer Wahl. Konfigurieren Sie die folgenden Schlüssel

```bash
sudo vi /etc/krb5.conf

[libdefaults]
  default_realm = DOMAIN.COMPANY.COM
 
[realms]
DOMAIN.COMPANY.COM = {
   kdc = dc-33.domain.company.com
}
```

Speichern Sie die Datei krb5.conf, und beenden

> [!NOTE]
> Domäne muss in Großbuchstaben sein.


## <a name="test-the-ticket-granting-ticket-retrieval"></a>Testen Sie das Ticket-Granting-Ticket abrufen

Rufen Sie ein Ticket, das Ticket (TGT) vom KDC gewähren.

```bash
kinit username@DOMAIN.COMPANY.COM
```

Zeigen Sie die verfügbaren Tickets Kinit verwenden. Wenn die Kinit erfolgreich war, sehen Sie ein Ticket. 

```bash
klist

krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.
```

## <a name="connect-using-includename-sosincludesname-sos-shortmd"></a>Herstellen einer Verbindung mit [!INCLUDE[name-sos](../includes/name-sos-short.md)]

* Erstellen Sie ein neues Verbindungsprofil

* Wählen Sie **Windows-Authentifizierung** als Authentifizierungstyp

* Das Verbindungsprofil abgeschlossen ist, klicken Sie auf **verbinden**

Nach der erfolgreichen Verbindung, auf dem Server, wird Sie der *Server* Randleiste.
