---
title: Installieren und Konfigurieren von Geräten
description: Führt die ersten Schritte für die Einrichtung und den Einstieg in die Verwendung ihrer neuen Appliance durch.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 9f96d953dbd427bfb6cf94470c0ee80ade3aed48
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401447"
---
# <a name="appliance-installation-and-configuration-for-analytics-platform-system"></a>Geräteinstallation und-Konfiguration für Analytics Platform System
Führt die ersten Schritte für die Einrichtung und den Einstieg in die Verwendung ihrer neuen Appliance durch.  
  
<!-- MISSING LINKS ## <a name="BeforeYouBegin"></a>Before You Begin  
Before you begin to install, configure, and use your new appliance, we recommend reviewing information about the appliance components. Review the following to familiarize yourself with the appliance:  
  
-   Review [Understanding the Appliance Nodes and Hardware (SQL Server PDW)](assetId:///f60f419f-d1e1-403d-8cf9-07e7ef6d6627) to be sure you understand the components included in your new appliance.  
  
-   Review [Connecting to SQL Server PDW (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808) to understand how and when appliance administrators will connect to each appliance node.  
-->

## <a name="InstallHardware"></a>1. Installieren der Hardware  
Ihr neues Gerät wird in Ihrem Rechenzentrum auf Paletten an das Dock übermittelt.  
  
> [!IMPORTANT]  
> In einigen Fällen werden Sie in Ihrem Rechenzentrum von IHV entpackt, Rack und eine Verbindung mit dem Gerät hergestellt. Wenn dies der Fall ist, sind diese Anweisungen nicht erforderlich, und Sie können mit 3 fortfahren [. Konfigurieren Sie den](#ConfigureAppliance) Abschnitt "Appliance" weiter unten.  
  
Wenn Ihre IHV die Hardware Installation nicht ausführt, führen Sie die folgenden Schritte aus, um die Hardware zu installieren.  
  
|||  
|-|-|  
|**Aufgabe**|**Beschreibung**|  
|Dokumentation bestätigen|Vergewissern Sie sich, dass Sie alle erforderlichen Dokumente und Informationen von Ihrem unabhängigen Hardwarehersteller (IHV) erhalten haben. Weitere Informationen finden Sie unter [Informationen zum Abrufen von ihrer IHV &#40;Analytics-Platt Form System&#41;](information-to-obtain-from-your-ihv.md).|  
|Installieren von Hardware|Vergewissern Sie sich, dass das Rechenzentrum die Appliance aufnehmen kann. Verschieben Sie die Gerätekomponenten in das Rechenzentrum. Gestell der Netzwerk Switches, PDUs und Verkabelung. Weitere Informationen finden Sie unter [Hardware Installation &#40;Analytics Platform System&#41;](hardware-installation.md).|  
  
## <a name="PowerOnAppliance"></a>2. Einschalten des Geräts  
  
|||  
|-|-|  
|**Aufgabe**|**Beschreibung**|  
|Einschalten des Geräts|Schalten Sie die einzelnen applivenkomponentenknoten in der erforderlichen Reihenfolge ein, und warten Sie, bis Sie sicher sind, dass keine Fehler auftreten.|  
  
## <a name="ConfigureAppliance"></a>3. Konfigurieren der Appliance  
  
|||  
|-|-|  
|**Aufgabe**|**Beschreibung**|  
|||  
|Konfigurieren Sie die Appliance mithilfe der SQL Server PDW**Configuration Manager**|Verwenden Sie die Configuration Manager, um Geräte Kennwörter, Zeitzonen, Netzwerk-und Firewalleinstellungen, Sicherheitszertifikate sowie die Leistung und andere Einstellungen auf Ihrem Gerät festzulegen. Weitere Informationen finden Sie unter [Appliance Configuration &#40;Analytics Platform System&#41;](appliance-configuration.md).|  
  
> [!WARNING]  
> Konfigurationsänderungen sollten nur mithilfe der SQL Server PDW**Configuration Manager**vorgenommen werden. Nicht durch **Configuration Manager** verfügbar gemachte Änderungen werden nicht unterstützt. Beispielsweise unterstützt die SQL Server PDW Appliance nur die Spracheinstellung Deutsch (USA).  
  
## <a name="SoftwareServicing"></a>4. Einrichten der Software Wartung  
  
|||  
|-|-|  
|**Aufgabe**|**Beschreibung**|  
|Anwenden von SQL Server PDW Updates|Optionale Möglicherweise müssen Sie eine oder mehrere SQL Server PDW Updates anwenden, um Ihre SQL Server PDW Software auf die neueste Version zu aktualisieren. Weitere Informationen finden Sie unter [Apply Analytics Platform System Hotfixes &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md).|  
|Konfigurieren von Windows Server Update Services|Konfigurieren Sie das Gerät für den Empfang von Updates von Windows Server Update Services zur Unterstützung von Software. Weitere [Informationen finden Sie unter herunterladen und Anwenden von Microsoft Updates &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md).|  
  
## <a name="NextSteps"></a>Nächste Schritte  
Nachdem Sie alle vorherigen Schritte abgeschlossen haben, ist Ihr Gerät einsatzbereit. Sie oder andere Mitarbeiter an Ihrem Standort können mit den folgenden Aufgaben fortfahren.  
  
|||  
|-|-|  
|**Aufgabe**|**Beschreibung**|  
|Installieren von SQL Server PDW Treibern und Konfigurieren der Konnektivität|Konfigurieren Sie lokale Computer für die Verbindung mit SQL Server PDW mithilfe von SQL Server Data Tools, sqlcmd, Business Intelligence Software oder anderen Tools. <!-- MISSING LINKS See [Client Tools (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808).-->|  
|Erstellen von Anmeldungen und Server Rollen und Zuweisen von Berechtigungen|Planen und erstellen Sie Anmeldungen und Server Rollen, die es Benutzern ermöglichen, sich mit den entsprechenden Berechtigungen bei SQL Server PDW anzumelden. <!-- MISSING LINKS See [PDW Permissions &#40;SQL Server PDW&#41;](../sqlpdw/pdw-permissions-sql-server-pdw.md).-->|  
|Konfigurieren des Azure Datenverwaltung-Gateways|Das Gateway ermöglicht Azure-Benutzern den Zugriff auf lokale APS-Daten, indem APS-Daten als sichere odata-Feeds verfügbar gemacht werden. Das Gateway ist bereits auf dem Steuer Knoten installiert. Bitten Sie Microsoft um Unterstützung bei der Konfiguration.|  
|Überwachen von Abfragen und Geräte Benutzern|Verwenden Sie die Verwaltungskonsole und andere Ressourcen, um die Abfragen und Gerätebenutzer zu überwachen. Weitere Informationen finden [Sie unter Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)<!-- MISSING LINKS and [User Sessions &#40;SQL Server PDW&#41;](../sqlpdw/user-sessions-sql-server-pdw.md)-->.|  
|Laden von Daten in SQL Server PDW|Laden Sie Daten in Ihre Appliance. <!-- MISSING LINKS See [Load &#40;SQL Server PDW&#41;](../sqlpdw/load-sql-server-pdw.md).-->|  
|Erstellen eines Plans für die Notfall Wiederherstellung|Planen Sie, wie Sie Ihre Daten vor Hardwarefehlern oder über schreibungen von Daten schützen. Erstellen Sie einen Plan mithilfe regulärer Sicherungen und Wiederherstellungs Pläne im Falle von Daten Beschädigung oder-Verlust. <!-- MISSING LINKS See [Create a Disaster Recovery Plan &#40;SQL Server PDW&#41;](../sqlpdw/create-a-disaster-recovery-plan-sql-server-pdw.md).-->|  
|Überwachen der Appliance|Überwachen Sie den Status, die Integrität und die Leistung von Geräten mithilfe von System Sichten, Protokollen und der Verwaltungskonsole. Korrigieren oder melden Sie etwaige Probleme. Weitere Informationen finden Sie unter [Monitor Appliance Health State &#40;Analytics Platform System&#41;](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md).|  
