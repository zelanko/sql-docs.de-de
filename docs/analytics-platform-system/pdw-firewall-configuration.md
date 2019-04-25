---
title: PDW-Firewallkonfiguration - Analytics Platform System | Microsoft-Dokumentation
description: Auf der Seite Firewall der SQL Server PDW-Konfigurations-Manager können Sie Firewallregeln, die zulassen oder verhindern den Zugriff auf bestimmte Ports auf dem Gerät Analytics Platform System aktivieren oder deaktivieren.
aauthor: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3195007b4346c6010b416fae833643f3a80136fb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62639530"
---
# <a name="parallel-data-warehouse-firewall-configuration-in-analytics-platform-system"></a>Parallel Data Warehouse-Firewall-Konfiguration in Analytics Platform System
Die **Firewall** von SQL Server PDW-Konfigurations-Manager können Sie Ihre Firewallregeln, die zulassen oder verhindern den Zugriff auf bestimmte Ports auf dem Gerät Analytics Platform System aktivieren oder deaktivieren.  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>Verwalten von Ports und firewall-Regeln für applianceknoten  
  
1.  Starten Sie den Konfigurations-Manager. Weitere Informationen finden Sie unter [Starten des Konfigurations-Managers &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Erweitern Sie im linken Bereich des Konfigurations-Managers **Parallel Data Warehouse-Topologie**, und klicken Sie dann auf **Firewall**.  
  
3.  Suchen Sie nach der Regel Port oder eine Firewall, aktualisieren Sie in der Liste, und klicken Sie dann aktivieren oder deaktivieren das Kontrollkästchen neben diesem Element. Nur SQL Server PDW-Admin konfigurierbare Optionen werden in dieser Liste, einschließlich öffnen und Schließen von Ports in der extern angezeigte Knoten angezeigt.  
  
4.  Klicken Sie auf **übernehmen** zum Speichern der Änderungen.  
  
![DWConfig Appliance PDW Firewall](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>Externe Ports  
Die folgenden Ports werden für Clientverbindungen stammen, die außerhalb von PDW geöffnet.  
  
|Zweck|Port #|Knoten|  
|-----------|-----------|---------|  
|SQL-Client-Zugriff für PDW (TDS)|17001|CTL|  
|Ladeprogramm-Clientzugriff (Dwloader und SSIS)|8001|CTL|  
|Remotedesktopzugriff|3389|CTL, CMP|  
|SSIS BinaryLoaderDataChannel|16551|CTL|  
|dwloader BinaryLoaderDataChannel|16551|CMP|  
|SSL verschlüsselte Verbindungen (für die interne Kommunikation, um die Verwaltungskonsole zugreifen)|443|Alle Knoten|  
|SQL Server PDW Load Ablaufsteuerung - Windows-Anmeldeinformationen|8002|CTL|  
|_Kerberos|88|AD01 und AD02,|  
|_ldap|389|AD01 und AD02|  
  
## <a name="internal-ports"></a>Interne Ports  
Die folgenden Ports werden für die interne Kommunikation von PDW verwendet, aber nicht für Verbindungen von außerhalb der PDW-Anwendung geöffnet werden.  
  
|Zweck|Port #|Knoten|  
|-----------|-----------|---------|  
|DMS-Steuerungskanal Datenverkehr|16450|CTL, CMP|  
|DMS-Datenkanal-Datenverkehr|16550|CTL, CMP|  
|Interne Diagnose|16650|CTL, CMP|  
|Failoverstatus (DMS)|15000|CTL, CMP|  
|Failoverstatus (-Engine)|15001|CMP|  
|Bereich für dynamische (kurzlebige) Ports|20000-65535|CTL, CMP|  
|Bereiche (TDS) für SQL Server-port|1433, 1500-1508|CTL, CMP|  
  
> [!NOTE]  
> Erstellen von externen Tabellen oder externen Datenquellen verwendet standardmäßig den TCP-Port 8020. Diese Anweisungen können konfiguriert werden, um andere Ports verwenden. Der Standardport für Hortonworks JOB_TRACKER_LOCATION ist 50300. Die Integration mit anderen Systemen und -Tools unter Umständen zusätzliche Ports.  
  
<!-- MISSING LINKS ## See Also  
[HDInsight Firewall Configuration &#40;Analytics Platform System&#41;](hdinsight-firewall-configuration.md)  -->  
  
