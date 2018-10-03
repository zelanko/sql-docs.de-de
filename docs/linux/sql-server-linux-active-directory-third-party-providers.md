---
title: Verwenden Sie Active Directory-Anbieter von Drittanbietern mit SQL Server unter Linux | Microsoft-Dokumentation
description: Dieses Tutorial bietet die Konfigurationsschritte für AD-Authentifizierung mit Anbietern von Drittanbietern
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
ms.openlocfilehash: beb342156098ebb5516466ad7fd4a771cc5a0616
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787285"
---
# <a name="use-third-party-active-directory-providers-with-sql-server-on-linux"></a>Verwenden Sie Active Directory-Anbieter von Drittanbietern mit SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel erläutert das Konfigurieren einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf Linux-Host-Computer mit AD-Authentifizierung bei AD-Anbieter von Drittanbietern, wie [PowerBroker Identität Dienste (PBIS)](https://www.beyondtrust.com/), [Vintela Authentication Services (VAS)](https://www.oneidentity.com/products/authentication-services/), und [Centrify](https://www.centrify.com/). Dieses Handbuch enthält die Schritte aus, um die AD-Konfiguration zu überprüfen, und es ist nicht vorgesehen, um anzuweisen, wie Sie einen Computer in eine Domäne einbinden. Ausführliche Anweisungen zum Verknüpfen einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mithilfe Bereich und SSSD in eine Domäne hosten, finden Sie unter [verwenden Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

Bevor Sie AD-Authentifizierung konfigurieren, müssen Sie zum Einrichten der AD-Domänencontroller (Windows), im Netzwerk und Join Ihre [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf Linux-Host mit einer AD-Domäne. Sie können [PBIS](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), oder [Centrify](https://www.centrify.com/).

> [!NOTE]
>
>In diesem Tutorial verwendet "contoso.com" und "CONTOSO.COM" als Beispielnamen Domäne und dem Bereich bzw. Er verwendet auch "DC1. CONTOSO.COM"als Beispiel den vollqualifizierten Domänennamen des Domänencontrollers. Ersetzen Sie dies durch Ihre eigenen Werte.

## <a name="check-connection-to-domain-controller"></a>Überprüfen Sie die Verbindung zum Domänencontroller

Überprüfen Sie, dass Sie den Domänencontroller mit dem kurz und den vollqualifizierten Namen der Domäne herstellen können.

   ```bash
   ping contoso

   ping contoso.com
   ```

   Wenn eines dieser ein Fehler auftritt, aktualisieren Sie die Suchliste für Ihre Domäne.

   - **Ubuntu**:

     Bearbeiten der `/etc/network/interfaces` Datei, damit Ihre AD-Domäne in der Suchliste für die Domäne ist: 

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
     search contoso.com com  
     nameserver **<AD domain controller IP address>**
     ```

   - **RHEL**:

     Bearbeiten der `/etc/sysconfig/network-scripts/ifcfg-eth0` Datei (oder andere Schnittstelle Config-Datei nach Bedarf), damit Ihre AD-Domäne in der Domänenliste für die Suche ist:

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

   Wenn Sie dennoch den Domänencontroller pingen können, finden Sie den vollständig qualifizierten Domänennamen (z. B. "DC1". "Contoso.com") und IP-Adresse des Domänencontrollers, und fügen Sie den folgenden Eintrag hinzu. `/etc/hosts`

   ```/etc/hosts
   **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
   ```

   - **SLES**:

     Bearbeiten der `/etc/sysconfig/network/config` Datei, damit Ihre AD-Domäne-Controller-IP-Adresse für DNS-Abfragen verwendet werden, und Ihre AD-Domäne, in der Liste der Domäne suchen ist:

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

## <a name="check-reverse-dns-is-properly-configured"></a>Überprüfen Sie, dass Reverse-DNS-ordnungsgemäß konfiguriert ist

Der folgende Befehl sollte den vollqualifizierten Domänennamen des Hosts (z. B. mit SQL Server zurück. "SqlHost.contoso.com").

   ```bash
   host **<IP address of SQL Server host>**
   # **<reversed IP address>**.in-addr.arpa domain name pointerSqlHost.contoso.com.
   ```

   Wenn dieser FQDN des Hosts nicht zurückgibt, oder wenn der FQDN falsch ist, fügen Sie einen reverse-DNS-Eintrag für Ihre [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf Linux-Host auf einen DNS-Server.

## <a name="check-your-krb5-configuration-is-correct"></a>Überprüfen Sie, dass Ihre krb5-Konfiguration richtig ist.

Überprüfen Sie Ihre `/etc/krb5.conf` ordnungsgemäß konfiguriert ist. Für die meisten Anbieter für Drittanbieter-AD erfolgt dies automatisch. Vergewissern Sie sich jedoch `/etc/krb5.conf` für die folgenden Werte ein, um zukünftige Probleme zu vermeiden:

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

In diesem Artikel wir erläutert, wie Sie konfigurieren eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf Linux-Host-Computer mit AD-Authentifizierung bei AD-Anbieter von Drittanbietern verwenden. Um die Konfiguration von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Linux, um AD-Konten zu unterstützen, befolgen Sie die Anweisungen unter [verwenden Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md).

> [!div class="nextstepaction"]
> [Verwenden Sie Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md)

> [!NOTE]
>
> Können Sie im Abschnitt "Join SQLServer-Host mit AD-Domäne" in überspringen [verwenden Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md) , wie Sie dies nur in diesem Lernprogramm durchgeführt haben.
