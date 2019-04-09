---
title: SQLServer unter Linux mit Active Directory Join
titleSuffix: SQL Server
description: ''
author: Dylan-MSFT
ms.author: Dylan.Gray
ms.reviewer: rothja
ms.date: 04/01/2019
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 6ccc94acb42fa7043912099c4888834cf4ff3e71
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2019
ms.locfileid: "59243584"
---
# <a name="join-sql-server-on-a-linux-host-to-an-active-directory-domain"></a>SQL Server auf einem Linux-Host zu einer Active Directory-Domäne beitreten

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel enthält allgemeine Hinweise dazu, wie auf einen SQL Server Linux-Host-Computer mit einer Active Directory (AD)-Domäne zu verknüpfen. Es gibt zwei Methoden: Verwenden Sie eine integrierte SSSD-Paket oder dritten Active Directory-Anbieter. Beispiele für Drittanbieter-Domänendienst-Join-Produkte sind [PowerBroker Identität Dienste (PBIS)](https://www.beyondtrust.com/), [eine Identität](https://www.oneidentity.com/products/authentication-services/), und [Centrify](https://www.centrify.com/). Dieses Handbuch enthält die Schritte aus, um Ihre Active Directory-Konfiguration zu überprüfen. Es ist jedoch nicht vorgesehen, Anweisungen dazu, wie Sie einen Computer in eine Domäne einbinden, bei Verwendung der Hilfsprogramme bereitstellen.

## <a name="prerequisites"></a>Erforderliche Komponenten

Bevor Sie die Active Directory-Authentifizierung konfigurieren, müssen Sie eine Active Directory-Domänencontroller, Windows, in Ihrem Netzwerk eingerichtet. Anschließend verknüpfen Sie Ihre SQL Server auf Linux-Host zu einer Active Directory-Domäne.

> [!IMPORTANT]
> Die in diesem Artikel beschriebenen Schritte sind nur zur Erklärung zur. Tatsächlichen Schritte können leicht abweichen, in Ihrer Umgebung je nach Ihrer gesamten Umgebung Konfiguration. Nutzen Sie Ihre Administratoren System- und Domänennamen für Ihre Umgebung für bestimmte Konfiguration, Anpassung und alle erforderlichen Problembehandlung zu erreichen.

## <a name="check-the-connection-to-a-domain-controller"></a>Überprüfen Sie die Verbindung zu einem Domänencontroller

Überprüfen Sie, dass Sie den Domänencontroller mit den kurz- und den vollqualifizierten Namen der Domäne herstellen können:

```bash
ping contoso
ping contoso.com
```

> [!TIP]
> Dieses Tutorial verwendet **"contoso.com"** und **"contoso.com"** als Beispielnamen Domäne und dem Bereich, bzw. Darüber hinaus verwendet er **DC1. "Contoso.com"** wie im Beispiel Domänenname des Domänencontrollers vollqualifizierte. Sie müssen diese Namen durch Ihre eigenen Werte ersetzen.

Wenn entweder der Name Überprüfungen ein Fehler auftritt, aktualisieren Sie die Suchliste für Ihre Domäne. Die folgenden Abschnitte enthalten Anweisungen für Ubuntu, Red Hat Enterprise Linux (RHEL) und SUSE Linux Enterprise Server (SLES).

### <a name="ubuntu"></a>Ubuntu

1. Bearbeiten der **/etc/network/interfaces** Datei, damit Active Directory-Domäne in der Domänenliste für die Suche ist:

   ```/etc/network/interfaces
   # The primary network interface
   auto eth0
   iface eth0 inet dhcp
   dns-nameservers **<AD domain controller IP address>**
   dns-search **<AD domain name>**
   ```

   > [!NOTE]
   > Die Netzwerkschnittstelle `eth0`, unterscheiden sich für verschiedene Computer. Um herauszufinden, welche Sie verwenden, führen Sie **"ifconfig"**. Kopieren Sie die Schnittstelle, die eine IP-Adresse und die gesendeten und empfangenen Bytes hat.

1. Starten Sie nach der Bearbeitung dieser Datei den Netzwerkdienst neu:

   ```bash
   sudo ifdown eth0 && sudo ifup eth0
   ```

1. Als Nächstes überprüfen Sie, ob Ihre **/etc/resolv.conf** Datei enthält eine Zeile wie im folgenden Beispiel:

   ```/etc/resolv.conf
   search contoso.com com  
   nameserver **<AD domain controller IP address>**
   ```

### <a name="rhel"></a>RHEL

1. Bearbeiten der **/etc/sysconfig/network-scripts/ifcfg-eth0** Datei, damit Active Directory-Domäne in der Suchliste für die Domäne ist. Oder Bearbeiten einer anderen Schnittstelle Config-Datei nach Bedarf:

   ```/etc/sysconfig/network-scripts/ifcfg-eth0
   PEERDNS=no
   DNS1=**<AD domain controller IP address>**
   DOMAIN="contoso.com com"
   ```

1. Starten Sie nach der Bearbeitung dieser Datei den Netzwerkdienst neu:

   ```bash
   sudo systemctl restart network
   ```

1. Nun überprüfen Sie, ob Ihre **/etc/resolv.conf** Datei enthält eine Zeile wie im folgenden Beispiel:

   ```/etc/resolv.conf
   search contoso.com com  
   nameserver **<AD domain controller IP address>**
   ```

1. Wenn Sie dennoch den Domänencontroller pingen können, finden Sie den vollqualifizierten Domänennamen und IP-Adresse des Domänencontrollers aus. Eine Beispiel-Domänenname ist **DC1. "Contoso.com"**. Fügen Sie den folgenden Eintrag **/Etc/Hosts**:

   ```/etc/hosts
   **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
   ```

### <a name="sles"></a>SLES

1. Bearbeiten der **/etc/sysconfig/network/config** Datei, damit die Active Directory Domain Controller-IP-Adresse, für die DNS-Abfragen verwendet wird und Active Directory-Domäne in der Liste der Domäne suchen:

   ```/etc/sysconfig/network/config
   NETCONFIG_DNS_STATIC_SEARCHLIST=""
   NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
   ```

1. Starten Sie nach der Bearbeitung dieser Datei den Netzwerkdienst neu:

   ```bash
   sudo systemctl restart network
   ```

1. Als Nächstes überprüfen Sie, ob Ihre **/etc/resolv.conf** Datei enthält eine Zeile wie im folgenden Beispiel:

   ```/etc/resolv.conf
   search contoso.com com
   nameserver **<AD domain controller IP address>**
   ```

## <a name="join-to-the-ad-domain"></a>Fügen Sie die AD-Domäne

Nachdem die Basiskonfiguration und die Verbindung mit dem Domänencontroller wird überprüft, gibt es zwei Optionen für das Beitreten zu einer SQL Server Linux-Host-Computer mit Active Directory-Domänencontroller:

- [Option 1: Verwenden Sie eine SSSD-Paket](#option1)
- [Option 2: Verwenden von Drittanbietern Openldap-Anbieter-Hilfsprogramme](#option2)

### <a id="option1"></a> Option 1: Verwenden Sie SSSD-Paket, um AD-Domäne

Diese Methode verknüpft, die SQL Server-Host auf ein AD-Domäne mit **Realmd** und **Sssd** Pakete.

> [!NOTE]
> Dies ist die bevorzugte Methode für das Beitreten zu einem Linux-Host mit einem AD-Domänencontroller.

Verwenden Sie die folgenden Schritte aus, um eine SQL Server-Host zu einer Active Directory-Domäne zu verknüpfen:

1. Verwendung [Realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join.md) auf den Hostcomputer aus Ihrer AD-Domäne beitreten. Sie müssen zuerst beide installieren die **Realmd** und Kerberos-Client-Pakete auf dem SQL Server-Hostcomputer, die mit Ihrer Linux-Distribution-Paket-Manager:

   **RHEL:**

   ```base
   sudo yum install realmd krb5-workstation
   ```

   **SUSE:**

   ```bash
   sudo zypper install realmd krb5-client
   ```

   **Ubuntu:**

   ```bash
   sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
   ```

1. Wenn die Installation des Kerberos-Client-Pakets für den ein Bereichsname aufgefordert werden, geben Sie Ihren Domänennamen in Großbuchstaben.

1. Nachdem Sie bestätigt haben, dass DNS ordnungsgemäß konfiguriert ist, treten Sie der Domäne mithilfe des folgenden Befehls. Sie müssen zur Authentifizierung verwenden ein AD-Konto, das über ausreichende Berechtigungen in AD, um das Hinzufügen eines neuen Computers zur Domäne verfügt. Dieser Befehl erstellt ein neues Computerkonto in AD, die **/etc/krb5.keytab** Keytab-Datei zu hosten, konfiguriert die Domäne in **/etc/sssd/sssd.conf**, und Updates **/etc/krb5.conf**.

   ```bash
   sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
   ```

   Daraufhin sollte die Meldung `Successfully enrolled machine in realm`.

   Die folgende Tabelle enthält einige Fehlermeldungen, die Sie empfangen konnte und Vorschläge zur Behebung an:

   | Fehlermeldung | Empfehlung |
   |---|---|
   | `Necessary packages are not installed` | Installieren Sie diese Pakete mit Ihrer Linux-Distribution-Paket-Manager vor dem erneuten Ausführen des Realm Join-Befehls. |
   | `Insufficient permissions to join the domain` | Überprüfen Sie einen Domänenadministrator, dass Sie über ausreichende Berechtigungen zum Verknüpfen von Linux-Computer mit der Domäne verfügen. |
   | `KDC reply did not match expectations` | Sie können nicht den richtigen Bereichsnamen für den Benutzer angegeben haben. Bereichsnamen Groß-/Kleinschreibung beachtet werden, in der Regel in Großbuchstaben und mit dem Befehl Bereich identifiziert werden können "contoso.com" zu ermitteln. |

   SQL Server verwendet SSSD und NSS für die Zuordnung von Benutzerkonten und-Gruppen zu Sicherheits-IDs (SIDs). SSSD muss konfiguriert und für SQL Server zum erfolgreichen Erstellen von AD-Anmeldungen wird ausgeführt. **Realmd** in der Regel wird automatisch als Teil der Domäne beizutreten, aber in einigen Fällen müssen Sie diese separat.

   Weitere Informationen finden Sie unter Vorgehensweise [Manuelles Konfigurieren des SSSD](https://access.redhat.com/articles/3023951), und [Konfigurieren des NSS zum Arbeiten mit SSSD](https://access.redhat.com/documentation/red_hat_enterprise_linux/7/html/system-level_authentication_guide/configuring_services#Configuration_Options-NSS_Configuration_Options).

1. Stellen Sie sicher, dass Sie jetzt Informationen zu einem Benutzer in der Domäne erfasst werden können und Sie ein Kerberos-Ticket als dieser Benutzer abrufen können. Im folgenden Beispiel wird **Id**, [Kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html), und [Klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html) Befehle für diese.

   ```bash
   id user@contoso.com

   uid=1348601103(user@contoso.com) gid=1348600513(domain group@contoso.com) groups=1348600513(domain group@contoso.com)

   kinit user@CONTOSO.COM

   Password for user@CONTOSO.COM:

   klist
   Ticket cache: FILE:/tmp/krb5cc_1000
   Default principal: user@CONTOSO.COM
   ```

   > [!NOTE]
   > - Wenn **Id user@contoso.com**  zurückgibt, `No such user`, stellen Sie sicher, dass der SSSD-Dienst erfolgreich gestartet werden, mithilfe des Befehls `sudo systemctl status sssd`. Wenn der Dienst wird ausgeführt, und den Fehler weiterhin angezeigt, versuchen Sie die ausführlichen Protokollierung für SSSD zu aktivieren. Weitere Informationen finden Sie auf die Red Hat-Dokumentation für [Problembehandlung SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting).
   >
   > - Wenn **Kinit user@CONTOSO.COM**  zurückgibt, `KDC reply did not match expectations while getting initial credentials`, stellen Sie sicher, dass Sie den Bereich in Großbuchstaben angegeben haben.

Weitere Informationen finden Sie auf die Red Hat-Dokumentation für [Ermitteln von und Identität beitreten zu Domänen](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html).

### <a id="option2"></a> Option 2: Verwenden von Drittanbietern Openldap-Anbieter-Hilfsprogramme

Können Sie Hilfsprogramme wie z. B. [PBIS](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), oder [Centrify](https://www.centrify.com/). Dieser Artikel deckt die Schritte für jedes einzelne Dienstprogramm nicht. Sie müssen zunächst eines dieser Dienstprogramme verwenden, den Linux-Host für SQL Server in die Domäne zu verknüpfen, bevor Sie fortfahren, weiterleiten.  

SQL Server ist nicht der Drittanbieter-Integrator oder die Bibliotheksdatei für AD-bezogene Abfragen verwenden. SQL Server fragt immer AD Openldap-Bibliotheksaufrufe direkte Verwendung in diesem Setup. Die Integratoren, die von Drittanbietern werden nur verwendet, um die Linux-Server mit AD-Domäne zu verknüpfen, und SQL Server verfügt nicht über eine direkte Kommunikation mit diesen Dienstprogrammen.

> [!IMPORTANT]
> Informieren Sie sich die Empfehlungen für die Verwendung der **Mssql-Conf** `network.disablesssd` Konfigurationsoption in der **zusätzliche Konfigurationsoptionen** Abschnitt des Artikels [verwenden Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md#additionalconfig).

Überprüfen Sie, ob Ihre **/etc/krb5.conf** ordnungsgemäß konfiguriert ist. Für die meisten Drittanbieter-Active Directory-Dienstanbietern erfolgt diese Konfiguration automatisch. Vergewissern Sie sich jedoch **/etc/krb5.conf** für die folgenden Werte ein, um zukünftige Probleme zu vermeiden:

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

## <a name="check-that-the-reverse-dns-is-properly-configured"></a>Überprüfen Sie, dass der reverse-DNS ordnungsgemäß konfiguriert ist

Der folgende Befehl sollte den vollständig qualifizierten Domänennamen (FQDN) des Hosts zurück, die SQL Server ausgeführt wird. Ein Beispiel hierfür ist **SqlHost.contoso.com**.

```bash
host **<IP address of SQL Server host>**
```

Die Ausgabe dieses Befehls sollte etwa wie `**<reversed IP address>**.in-addr.arpa domain name pointer SqlHost.contoso.com`. Wenn dieser Befehl kein FQDN des Hosts zurückgibt oder wenn der FQDN falsch ist, fügen Sie eine reverse-DNS-Eintrag für Ihre SQL Server auf Linux-Host auf einen DNS-Server hinzu.

## <a name="next-steps"></a>Nächste Schritte

Dieser Artikel behandelt die Voraussetzung dafür, wie eine SQL Server auf einem Linux-Host-Computer mit Active Directory-Authentifizierung zu konfigurieren. Um SQL Server unter Linux zur Unterstützung von Active Directory-Konten konfiguriert haben, befolgen Sie die Anweisungen unter [verwenden Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md).