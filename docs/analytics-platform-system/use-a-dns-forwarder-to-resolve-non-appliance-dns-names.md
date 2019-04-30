---
title: Verwenden Sie eine DNS-Weiterleitung in Analytics Platform System | Microsoft-Dokumentation"
description: Verwenden Sie eine DNS-Weiterleitung zum Auflösen von DNS-Namen in Analytics Platform System nicht zur Appliance gehört.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 6ce978d7b05382b1a02018f3d5022b0f8bfaf585
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63243789"
---
# <a name="use-a-dns-forwarder-to-resolve-non-appliance-dns-names-in-analytics-platform-system"></a>Verwenden Sie eine DNS-Weiterleitung für die nicht zur Appliance gehört DNS-namensauflösung in Analytics Platform System
Eine DNS-Weiterleitung konfiguriert werden kann, auf den Active Directory-Domänendienste-Knoten (**_Appliance\_Domäne_-AD01** und  **_Appliance\_ Domäne_-AD02**) Ihrer Analytics Platform System Appliance, die Skripts und Anwendungen Zugriff auf externe Server zulässt.  
  
## <a name="ResolveDNS"></a>Verwenden einer DNS-Weiterleitung  
Die Analytics Platform System Appliance ist konfiguriert, um zu verhindern, dass zum Auflösen von DNS-Namen von Servern, die nicht in der Appliance. Einige Prozesse, z. B. die Windows Software Update Services (WSUS), müssen auf Servern außerhalb der Appliance. Zur Unterstützung dieses Szenarios Verwendung der DNS Analytics Platform System kann konfiguriert werden, um eine Weiterleitung von externen Namen unterstützen, die Analytics Platform System-Hosts und virtuellen Computern (VMs), externe DNS-Servern zum Auflösen von Namen außerhalb der Anwendung verwendet werden kann. Benutzerdefinierte Konfiguration von DNS-Suffixe wird nicht unterstützt, was bedeutet, dass Sie vollständig qualifizierte Domänennamen verwenden müssen, um einen nicht zur Appliance gehört Servernamen zu beheben.  
  
**Erstellen Sie eine DNS-Weiterleitung mit der DNS-GUI**  
  
1.  Melden Sie sich an den  **_Appliance\_Domäne_-AD01** Knoten.  
  
2.  Öffnen Sie den DNS-Manager (**dnsmgmt.msc**).  
  
3.  Mit der rechten Maustaste in des Namens des Servers ein, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Auf der **erweitert** Registerkarte, deaktivieren Sie die **Rekursion (Weiterleitungen) deaktivieren** aus, und klicken Sie dann auf **übernehmen**.)  
  
5.  Klicken Sie auf die **Weiterleitungen** Registerkarte, und klicken Sie dann auf **bearbeiten**.  
  
6.  Geben Sie die IP-Adresse für den externen DNS-Server, der die namensauflösung bereitstellen. Die virtuellen Computer und Servern (Hosts) in das Gerät werden mit externen Servern herstellen, mithilfe des vollständig qualifizierten Domänennamen.  
  
7.  Wiederholen Sie die Schritte 1 bis 6 für die  **_Appliance\_Domäne_-AD02** Knoten  
  
**So erstellen Sie eine DNS-Weiterleitung mit Windows PowerShell**  
  
1.  Melden Sie sich an den  **_Appliance\_Domäne_-AD01**Knoten.  
  
2.  Führen Sie das folgende Windows PowerShell-Skript aus dem  **_Appliance\_Domäne_-AD01** Knoten. Ersetzen Sie vor dem Ausführen des Windows PowerShell-Skripts, IP-Adressen mit den IP-Adressen der DNS-Server nicht zur Appliance gehört.  
  
    ```  
    $DNS=Get-WmiObject -class "MicrosoftDNS_Server"  -Namespace "root\microsoftdns"  
    $DNS.Forwarders = ("xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx")  
    $DNS.put()  
    ```  
  
3.  Führen Sie den gleichen Befehl für die  **_Appliance\_Domäne_-AD02** Knoten.  
  
## <a name="configuring-dns-resolution-for-wsus"></a>Konfigurieren von DNS-Auflösung für WSUS  
SQL Server PDW 2012 bietet integrierte Wartung und Patchen von Funktionen. SQL Server PDW verwendet Microsoft Update und andere Microsoft-Technologien-Wartung. Zum Aktivieren von Updates muss das Gerät entweder in einem Unternehmen WSUS-Repository oder den öffentlichen Microsoft-WSUS-Repository verbinden können.  
  
Für Kunden, die die Appliance, Suchen nach Updates auf den öffentlichen Microsoft-WSUS-Repository konfigurieren, legen Sie die folgenden Anweisungen die entsprechenden Konfigurationsdetails auf dem Gerät.  
  
> [!NOTE]  
> Der Netzwerkadministrator Kunden muss die IP-Adresse angeben, für den Unternehmens-DNS-Server, die Namen von auflösen können **"Microsoft.com"**.  
  
1.  Mithilfe von Remotedesktop, melden Sie sich bei der VMM-VM (<fabric domain>- VMM) mit dem Fabric-Domänenadministratorkonto.  
  
2.  Öffnen Sie die Systemsteuerung, klicken Sie auf **Netzwerk und Internet**, und klicken Sie dann auf **Netzwerk- und Freigabecenter**.  
  
3.  Klicken Sie in der Verbindungsliste auf **VMSEthernet**, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Wählen Sie **Internet Protocol Version 4 (TCP/IPv4)**, und klicken Sie dann auf **Eigenschaften**.  
  
5.  In der **alternativer DNS-Server** hinzu, und die IP-Adresse, die vom Netzwerkadministrator Kunden bereitgestellt.  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
