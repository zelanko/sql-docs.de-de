---
title: Verwenden einer DNS-Weiterleitung
description: Verwenden Sie eine DNS-Weiterleitung zum Auflösen von DNS-Namen, die keine Appliance sind, in Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 3d1d0d9428138da615fad7ff5745c758d9fcd3b8
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399434"
---
# <a name="use-a-dns-forwarder-to-resolve-non-appliance-dns-names-in-analytics-platform-system"></a>Verwenden einer DNS-Weiterleitung zum Auflösen von DNS-Namen, die keine Appliance sind, in Analytics Platform System
Eine DNS-Weiterleitung kann auf den Active Directory Domain Services Knoten (**_Appliance\_Domain_-ad01** und ** _Appliance\_Domain_-ad02**) Ihrer Analytics Platform System Appliance konfiguriert werden, damit Skripts und Softwareanwendungen auf externe Server zugreifen können.  
  
## <a name="ResolveDNS"></a>Verwenden einer DNS-Weiterleitung  
Die Analytics Platform System Appliance ist so konfiguriert, dass das Auflösen von DNS-Namen von Servern, die nicht in der Appliance sind, verhindert wird. Einige Prozesse, z. b. Windows Software Update Services (WSUS), müssen auf Server außerhalb des Geräts zugreifen. Zur Unterstützung dieses Verwendungs Szenarios kann der Analytics Platform System-DNS so konfiguriert werden, dass eine externe namens Weiterleitung unterstützt wird, mit der Analyseplattform-System Hosts und-Virtual Machines (VMS) externe DNS-Server zum Auflösen von Namen außerhalb des Geräts verwenden können. Die benutzerdefinierte Konfiguration von DNS-Suffixen wird nicht unterstützt. Dies bedeutet, dass Sie vollständig qualifizierte Domänen Namen verwenden müssen, um einen nicht-Appliance-Servernamen aufzulösen.  
  
**So erstellen Sie eine DNS-Weiterleitung mit der DNS-GUI**  
  
1.  Melden Sie sich am Knoten ** _Appliance\_Domäne_-ad01** an.  
  
2.  Öffnen Sie den DNS-Manager (**dnsmgmt. msc**).  
  
3.  Klicken Sie mit der rechten Maustaste auf den Namen des Servers, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Deaktivieren Sie auf der Registerkarte **erweitert** die Option **Rekursion deaktivieren (auch Weiterleitungen deaktiviert)** , und klicken Sie **dann auf über**nehmen.)  
  
5.  Klicken Sie **auf die Register** Karte Weiterleitungen und dann auf **Bearbeiten**.  
  
6.  Geben Sie die IP-Adresse für den externen DNS-Server ein, der die Namensauflösung bereitstellt. Die virtuellen Computer und Server (Hosts) im Gerät stellen mithilfe von voll qualifizierten Domänen Namen eine Verbindung mit externen Servern her.  
  
7.  Wiederholen Sie die Schritte 1-6 auf dem Knoten " ** _Appliance\_Domäne_ad02** ".  
  
**So erstellen Sie eine DNS-Weiterleitung mithilfe von Windows PowerShell**  
  
1.  Melden Sie sich am Knoten ** _Appliance\_Domäne_-ad01**an.  
  
2.  Führen Sie das folgende Windows PowerShell-Skript über den Knoten " ** _Appliance\_Domäne_-ad01** " aus. Ersetzen Sie vor dem Ausführen des Windows PowerShell-Skripts die IP-Adressen durch die IP-Adressen Ihrer nicht-Appliance-DNS-Server.  
  
    ```  
    $DNS=Get-WmiObject -class "MicrosoftDNS_Server"  -Namespace "root\microsoftdns"  
    $DNS.Forwarders = ("xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx")  
    $DNS.put()  
    ```  
  
3.  Führen Sie den gleichen Befehl auf dem Knoten " ** _Appliance\_Domäne_-ad02** " aus.  
  
## <a name="configuring-dns-resolution-for-wsus"></a>Konfigurieren der DNS-Auflösung für WSUS  
SQL Server PDW 2012 bietet integrierte Funktionen für Wartung und Patchen. SQL Server PDW verwendet Microsoft Update und andere Microsoft-Wartungs Technologien. Zum Aktivieren von Updates muss das Gerät entweder eine Verbindung mit einem WSUS-Unternehmens Repository oder dem öffentlichen WSUS-Repository von Microsoft herstellen können.  
  
Für Kunden, die sich für die Konfiguration der Appliance für die Suche nach Updates im öffentlichen WSUS-Repository von Microsoft entscheiden, werden die richtigen Konfigurationsdetails auf der Appliance in den folgenden Anweisungen festgelegt.  
  
> [!NOTE]  
> Der Kundennetzwerk Administrator muss die IP-Adresse für einen DNS-Server des Unternehmens angeben, der Namen unter **Microsoft.com**auflösen kann.  
  
1.  Melden Sie sich mithilfe von Remote Desktop bei der VMM<fabric domain>-VM (-VMM) mit dem Fabric-Domänen Administrator Konto an.  
  
2.  Öffnen Sie die Systemsteuerung, klicken Sie auf **Netzwerk und Internet**, und klicken Sie dann auf **Netzwerk-und Freigabe Center**.  
  
3.  Klicken Sie in der Liste Verbindung auf **vmgthernet**, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Wählen Sie **Internetprotokoll Version 4 (TCP/IPv4)** aus, und klicken Sie dann auf **Eigenschaften**.  
  
5.  Fügen Sie im Feld **Alternativer DNS-Server** die IP-Adresse hinzu, die vom Kundennetzwerk Administrator bereitgestellt wird.  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
