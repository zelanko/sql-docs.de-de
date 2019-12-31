---
title: PDW-Firewallkonfiguration
description: Auf der Seite Firewall der SQL Server PDW Configuration Manager können Sie Firewallregeln aktivieren bzw. deaktivieren, die den Zugriff auf bestimmte Ports auf der Analytics Platform System Appliance zulassen oder verhindern.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 4ed739ce12170aa6d0ab79b996de0075cd6723ee
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400885"
---
# <a name="parallel-data-warehouse-firewall-configuration-in-analytics-platform-system"></a>Parallele Data Warehouse Firewall-Konfiguration in Analytics Platform System

Auf der Seite **Firewall** der SQL Server PDW Configuration Manager können Sie Firewallregeln aktivieren bzw. deaktivieren, die den Zugriff auf bestimmte Ports auf der Analytics Platform System Appliance zulassen oder verhindern.  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>So verwalten Sie Ports und Firewallregeln für Anwendungs Knoten  
  
1.  Starten Sie die Configuration Manager. Weitere Informationen finden Sie unter [Start the Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Erweitern Sie im linken Bereich des Configuration Manager die Option **parallele Data Warehouse Topologie**, und klicken Sie dann auf **Firewall**.  
  
3.  Suchen Sie den zu Aktualisier Ende Port oder die Firewallregel in der Konfigurations Liste, und aktivieren oder deaktivieren Sie das Kontrollkästchen neben diesem Element. In dieser Liste werden nur SQL Server PDW vom Administrator konfigurierbare Optionen angezeigt, einschließlich öffnenden und schließenden Ports auf extern ausgerichteten Knoten.  
  
4.  Klicken **Sie auf über** nehmen, um die Änderungen zu speichern.  
  
![DWConfig-Anwendung, PDW-Firewall](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>Externe Ports  
Die folgenden Ports werden für Clientverbindungen geöffnet, die von außerhalb von PDW stammen.  
  
|Zweck|Port #|Nodes|  
|-----------|-----------|---------|  
|SQL-Client Zugriff für PDW (TDS)|17001|CTL|  
|Loader-Client Zugriff (dwloader #a0 SSIS)|8001|CTL|  
|Remotedesktopzugriff|3389|CTL, CMP|  
|SSIS-binaryloaderdatachannel|16551|CTL|  
|"dwloader binaryloaderdatachannel|16551|CMP|  
|SSL-verschlüsselte Verbindungen (für die interne Kommunikation für den Zugriff auf die Verwaltungskonsole)|443|Alle Knoten|  
|SQL Server PDW Auslastungs Ablauf Steuerung-Windows-Anmelde Informationen|8002|CTL|  
|_Kerberos|88|Ad01 und ad02,|  
|_ldap|389|Ad01 und ad02|  
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="internal-ports"></a>Interne Ports  
Die folgenden Ports werden von PDW für die interne Kommunikation verwendet, jedoch nicht für Verbindungen, die von außerhalb des PDW-Geräts stammen.  
  
|Zweck|Port #|Nodes|  
|-----------|-----------|---------|  
|DMS-Steuerungs Kanal-Datenverkehr|16450|CTL, CMP|  
|DMS-Datenkanal Datenverkehr|16550|CTL, CMP|  
|Interne Diagnose|16650|CTL, CMP|  
|Failoverstatus (DMS)|15000|CTL, CMP|  
|Failoverstatus (Engine)|15001|CMP|  
|Dynamischer (kurzlebiger) Port Bereich|20000-65535|CTL, CMP|  
|SQL Server Port Bereiche (TDS)|1433, 1500-1508|CTL, CMP|  
| &nbsp; | &nbsp; | &nbsp; |
  
> [!NOTE]  
> Beim Erstellen externer Tabellen oder externer Datenquellen wird standardmäßig der TCP-Port 8020 verwendet. Diese Anweisungen können stattdessen für die Verwendung anderer Ports konfiguriert werden. Der Standardport von hortonworks JOB_TRACKER_LOCATION ist 50300. Für die Integration in andere Systeme und Tools sind möglicherweise zusätzliche Ports erforderlich.  
  
<!-- MISSING LINKS ## See Also  
[HDInsight Firewall Configuration &#40;Analytics Platform System&#41;](hdinsight-firewall-configuration.md)
-->
  
