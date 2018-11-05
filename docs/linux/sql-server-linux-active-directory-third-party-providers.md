---
title: Verwenden Sie Active Directory-Anbieter von Drittanbietern mit SQL Server unter Linux | Microsoft-Dokumentation
description: Dieses Tutorial bietet die Konfigurationsschritte für die Active Directory-Authentifizierung mit Anbietern von Drittanbietern
author: dylan-MSFT
ms.date: 07/25/2018
ms.author: dygray
manager: mikehab
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
helpviewer_keywords:
- Linux, AD authentication
ms.openlocfilehash: 0ffe146de3a842f9c273b4dbba2a9fe4d9ff7ff5
ms.sourcegitcommit: 41979c9d511b3eeb45134d30ccb0dbc6bba70f1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50757995"
---
# <a name="use-third-party-active-directory-providers-with-sql-server-on-linux"></a>Verwenden Sie Active Directory-Anbieter von Drittanbietern mit SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel erläutert das Konfigurieren einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf einem Linux-Host-Computer mit Active Directory-Authentifizierung bei Active Directory-Anbieter von Drittanbietern verwenden. Beispiele sind [PowerBroker Identität Dienste (PBIS)](https://www.beyondtrust.com/), [eine Identität](https://www.oneidentity.com/products/authentication-services/), und [Centrify](https://www.centrify.com/). Dieses Handbuch enthält die Schritte aus, um Ihre Active Directory-Konfiguration zu überprüfen. Es ist nicht vorgesehen, um anzuweisen, wie Sie einen Computer in eine Domäne einbinden. Ausführliche Anweisungen zum Verknüpfen einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zu einer Domäne mithilfe von Realmd und SSSD hosten, finden Sie unter [verwenden Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

Bevor Sie die Active Directory-Authentifizierung konfigurieren, müssen Sie eine Active Directory-Domänencontroller, Windows, in Ihrem Netzwerk eingerichtet. Treten Sie dann Ihre [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf Linux-Host zu einer Active Directory-Domäne. Sie können [PBIS](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), oder [Centrify](https://www.centrify.com/).

> [!NOTE]
>
>Dieses Tutorial verwendet **`contoso.com`** und **`CONTOSO.COM`** als Beispielnamen Domäne und dem Bereich, bzw. Darüber hinaus verwendet er **`DC1.CONTOSO.COM`** wie im Beispiel Domänenname des Domänencontrollers vollqualifizierte. Sie sollten diese Namen durch Ihre eigenen Werte ersetzen.

## <a name="check-the-connection-to-a-domain-controller"></a>Überprüfen Sie die Verbindung zu einem Domänencontroller

Überprüfen Sie, dass Sie den Domänencontroller mit den kurz- und den vollqualifizierten Namen der Domäne herstellen können:

```bash
ping contoso

ping contoso.com
```

Wenn entweder der Name Überprüfungen ein Fehler auftritt, aktualisieren Sie die Suchliste für Ihre Domäne:

- **Ubuntu**

  Bearbeiten der `/etc/network/interfaces` Datei, damit Active Directory-Domäne in der Domänenliste für die Suche ist: 

  ```/etc/network/interfaces
  <...>
  # The primary network interface
  auto eth0
  iface eth0 inet dhcp
  dns-nameservers **<AD domain controller IP address>**
  dns-search **<AD domain name>**
  ```

  > [!NOTE]  
  > Die Netzwerkschnittstelle **"eth0"**, unterscheiden sich für verschiedene Computer. Um herauszufinden, welche Sie verwenden, führen Sie **"ifconfig"**. Kopieren Sie die Schnittstelle, die eine IP-Adresse und die gesendeten und empfangenen Bytes hat.

  Starten Sie nach der Bearbeitung dieser Datei den Netzwerkdienst neu:

  ```bash
  sudo ifdown eth0 && sudo ifup eth0
  ```

  Nun überprüfen Sie, ob Ihre `/etc/resolv.conf` Datei enthält eine Zeile wie im folgenden Beispiel:  

  ```/etc/resolv.conf
  search contoso.com com  
  nameserver **<AD domain controller IP address>**
  ```

- **RHEL**

  Bearbeiten der `/etc/sysconfig/network-scripts/ifcfg-eth0` Datei, damit Active Directory-Domäne in der Suchliste für die Domäne ist. Oder Bearbeiten einer anderen Schnittstelle Config-Datei nach Bedarf:

  ```/etc/sysconfig/network-scripts/ifcfg-eth0
  <...>
  PEERDNS=no
  DNS1=**<AD domain controller IP address>**
  DOMAIN="contoso.com com"
  ```

  Starten Sie nach der Bearbeitung dieser Datei den Netzwerkdienst neu:

  ```bash
  sudo systemctl restart network
  ```

  Nun überprüfen Sie, ob Ihre `/etc/resolv.conf` Datei enthält eine Zeile wie im folgenden Beispiel:  

  ```/etc/resolv.conf
  search contoso.com com  
  nameserver **<AD domain controller IP address>**
  ```

  Wenn Sie dennoch den Domänencontroller pingen können, finden Sie den vollqualifizierten Domänennamen und IP-Adresse des Domänencontrollers aus. Eine Beispiel-Domänenname ist `DC1.CONTOSO.COM`. Fügen Sie den folgenden Eintrag `/etc/hosts`:

  ```/etc/hosts
  **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
  ```

- **SLES**

  Bearbeiten der `/etc/sysconfig/network/config` Datei, damit die Active Directory Domain Controller-IP-Adresse wird für DNS-Abfragen verwendet, und Active Directory-Domäne in der Liste der Domäne suchen:

  ```/etc/sysconfig/network/config
  <...>
  NETCONFIG_DNS_STATIC_SEARCHLIST=""
  NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
  ```

  Starten Sie nach der Bearbeitung dieser Datei den Netzwerkdienst neu:

  ```bash
  sudo systemctl restart network
  ```

  Nun überprüfen Sie, ob Ihre `/etc/resolv.conf` Datei enthält eine Zeile wie im folgenden Beispiel:

  ```/etc/resolv.conf
  search contoso.com com
  nameserver **<AD domain controller IP address>**
  ```

## <a name="check-that-the-reverse-dns-is-properly-configured"></a>Überprüfen Sie, dass der reverse-DNS ordnungsgemäß konfiguriert ist

Der folgende Befehl sollte den vollqualifizierten Domänennamen des Hosts zurück, die SQL Server ausgeführt wird. Ein Beispiel hierfür ist **`SqlHost.contoso.com`**.

```bash
host **<IP address of SQL Server host>**
# **<reversed IP address>**.in-addr.arpa domain name pointerSqlHost.contoso.com.
```

Wenn mit diesem Befehl keinen FQDN des Hosts zurückgibt oder wenn der FQDN falsch ist, fügen Sie einen reverse-DNS-Eintrag für Sie sind [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf Linux-Host auf einen DNS-Server.

## <a name="check-that-your-krb5-configuration-is-correct"></a>Überprüfen Sie, dass Ihre krb5-Konfiguration korrekt ist.

Überprüfen Sie, ob Ihre `/etc/krb5.conf` ordnungsgemäß konfiguriert ist. Für die meisten Drittanbieter-Active Directory-Dienstanbietern erfolgt diese Konfiguration automatisch. Vergewissern Sie sich jedoch `/etc/krb5.conf` für die folgenden Werte ein, um zukünftige Probleme zu vermeiden:

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

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel wird beschrieben, wie so konfigurieren Sie eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf einem Linux-Host-Computer mit Active Directory-Authentifizierung bei Active Directory-Anbieter von Drittanbietern verwenden. Um die Konfiguration von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Linux, um Active Directory-Konten zu unterstützen, befolgen Sie die Anweisungen unter [verwenden Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md).

> [!div class="nextstepaction"]
> [Verwenden Sie Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md)

> [!NOTE]
>
> Sie können fortfahren der **Join von SQL Server-Host, auf Active Directory-Domäne** im Abschnitt [verwenden Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md) , wie Sie damit nur in diesem Lernprogramm fertig sind.
