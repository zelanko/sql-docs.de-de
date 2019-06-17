---
title: Gerät installieren und konfigurieren Sie-Analytics Platform System | Microsoft-Dokumentation
description: Führt Sie Analytics Platform System (APS) Appliance-Administratoren über die ersten Schritte zum Einrichten und erste Schritte mit Ihrer neuen Anwendung.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5b6aa75cdab85fce9ef308d3e853ddb0107c28ee
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63276349"
---
# <a name="appliance-installation-and-configuration-for-analytics-platform-system"></a>Appliance-Installation und Konfiguration für Analytics Platform System
Führt Sie Analytics Platform System (APS) Appliance-Administratoren über die ersten Schritte zum Einrichten und erste Schritte mit Ihrer neuen Anwendung.  
  
<!-- MISSING LINKS ## <a name="BeforeYouBegin"></a>Before You Begin  
Before you begin to install, configure, and use your new appliance, we recommend reviewing information about the appliance components. Review the following to familiarize yourself with the appliance:  
  
-   Review [Understanding the Appliance Nodes and Hardware (SQL Server PDW)](assetId:///f60f419f-d1e1-403d-8cf9-07e7ef6d6627) to be sure you understand the components included in your new appliance.  
  
-   Review [Connecting to SQL Server PDW (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808) to understand how and when appliance administrators will connect to each appliance node.  
-->

## <a name="InstallHardware"></a>1. Installieren Sie die Hardware  
Ihre neue Anwendung wird auf Paletten dem Dock am Ihrem Rechenzentrum übermittelt werden.  
  
> [!IMPORTANT]  
> In einigen Fällen wird Ihrem unabhängigen Hardwarehersteller Auspacken, Einbauen und schließen Sie die Einheit für die Sie in Ihrem Rechenzentrum. Falls Ja, diese Anweisungen nicht erforderlich sind, und Sie können zum Überspringen der [3. Konfigurieren Sie die Appliance](#ConfigureAppliance) Abschnitt weiter unten.  
  
Wenn Ihrem unabhängigen Hardwarehersteller nicht die Hardware-Installation ausgeführt wird, verwenden Sie die folgenden Schritte aus, um die Hardware zu installieren.  
  
|||  
|-|-|  
|**Task**|**Beschreibung**|  
|Bestätigen Sie die Dokumentation|Vergewissern Sie sich, dass Sie alle erforderlichen Dokumente und Informationen von Ihrem unabhängiger Hardwarehersteller (IHVS) erhalten haben. Finden Sie unter [Informationen zum Abrufen von Ihrem unabhängigen Hardwarehersteller &#40;Analytics-Plattformsystem&#41;](information-to-obtain-from-your-ihv.md).|  
|Installieren von hardware|Stellen Sie sicher, dass das Rechenzentrum die Appliance aufnehmen kann. Verschieben Sie die Komponenten der Appliance an das Rechenzentrum an. Die Netzwerkswitches, Stomverteilereinheiten, einsetzen und Verkabelung. Finden Sie unter [Hardwareinstallation &#40;Analytics-Plattformsystem&#41;](hardware-installation.md).|  
  
## <a name="PowerOnAppliance"></a>2. Schalten Sie das Gerät  
  
|||  
|-|-|  
|**Task**|**Beschreibung**|  
|Schalten Sie das Gerät|Schalten Sie jede Appliance Komponentenknoten in der erforderlichen Reihenfolge, warten nach Bedarf, um sicherzustellen, dass keine Fehler auftreten.|  
  
## <a name="ConfigureAppliance"></a>3. Konfigurieren Sie die Appliance  
  
|||  
|-|-|  
|**Task**|**Beschreibung**|  
|||  
|Konfigurieren Sie die Appliance mit SQL Server-PDW**Configuration Manager**|Verwenden Sie den Konfigurations-Manager, um Gerät-Kennwörter, Zeitzonen, Netzwerk-und Firewalleinstellungen, Sicherheitszertifikate, und Leistung und andere Einstellungen auf Ihrem Gerät festzulegen. Finden Sie unter [Anwendungskonfiguration &#40;Analytics-Plattformsystem&#41;](appliance-configuration.md).|  
  
> [!WARNING]  
> Änderungen an der Konfiguration sollte nur vorgenommen werden mithilfe der SQL Server PDW**Configuration Manager**. Änderungen, die nicht über verfügbar gemacht **Configuration Manager** werden nicht unterstützt. Die SQL Server-PDW-Appliance unterstützt z. B. nur die Spracheinstellung für Englisch (USA).  
  
## <a name="SoftwareServicing"></a>4. Richten Sie Softwarewartung  
  
|||  
|-|-|  
|**Task**|**Beschreibung**|  
|Anwenden von Updates für SQL Server PDW|(Optional) Sie müssen möglicherweise Anwenden von einem oder mehreren SQL Server PDW-Updates, um Ihre SQL Server-PDW-Software auf die neueste Version zu aktualisieren. Finden Sie unter [Anwenden von Hotfixes für Analytics Platform System &#40;Analytics-Plattformsystem&#41;](apply-analytics-platform-system-hotfixes.md).|  
|Konfigurieren von Windows Server Update Services|Konfigurieren Sie das Gerät aus, um Updates von Windows Server Update Services für die Unterstützung von Software zu erhalten. Finden Sie unter [herunter, und Microsoft Updates &#40;Analytics-Plattformsystem&#41;](download-and-apply-microsoft-updates.md).|  
  
## <a name="NextSteps"></a>Nächste Schritte  
Nachdem Sie alle vorherigen Schritte abgeschlossen haben, ist Ihr Gerät für die Verwendung bereit. Die folgenden Aufgaben können Sie oder andere Mitarbeiter an Ihrem Standort fortsetzen.  
  
|||  
|-|-|  
|**Task**|**Beschreibung**|  
|Installieren Sie SQL Server-PDW-Treiber und konfigurieren Sie der Konnektivität|Konfigurieren von lokalen Computern herstellen einer Verbindung mit SQL Server PDW mithilfe von SQL Server Data Tools, Sqlcmd, Business Intelligence-Software oder andere Tools. <!-- MISSING LINKS See [Client Tools (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808).-->|  
|Erstellen von Anmeldungen und Serverrollen und Zuweisen von Berechtigungen|Planen und Erstellen von Anmeldungen und Serverrollen, die Benutzer mit den entsprechenden Berechtigungen in SQL Server PDW Anmelden ermöglichen. <!-- MISSING LINKS See [PDW Permissions &#40;SQL Server PDW&#41;](../sqlpdw/pdw-permissions-sql-server-pdw.md).-->|  
|Konfigurieren Sie das Azure Data Management Gateway|Das Gateway ermöglicht Azure-Benutzer für den lokalen APS Datenzugriff durch Verfügbarmachen von APS-Daten als OData Feeds sichern. Das Gateway ist bereits auf dem steuerknoten installiert. Bitten Sie Microsoft, um Unterstützung bei der Konfiguration.|  
|Monitor-Abfragen und Benutzern|Verwenden Sie die Verwaltungskonsole und andere Ressourcen zum Überwachen der Abfragen und Benutzern. Finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)<!-- MISSING LINKS and [User Sessions &#40;SQL Server PDW&#41;](../sqlpdw/user-sessions-sql-server-pdw.md)-->.|  
|Laden von Daten in SQL Server PDW|Laden von Daten in Ihre Anwendung. <!-- MISSING LINKS See [Load &#40;SQL Server PDW&#41;](../sqlpdw/load-sql-server-pdw.md).-->|  
|Erstellen eines Wiederherstellungsplans|Planen, wie Sie Ihre Daten vor Hardwareausfällen zu schützen, oder Daten überschrieben. Erstellen eines Plans verwenden regelmäßige Sicherungen und Pläne im Falle von datenbeschädigungen oder-Verlusten wiederherstellen. <!-- MISSING LINKS See [Create a Disaster Recovery Plan &#40;SQL Server PDW&#41;](../sqlpdw/create-a-disaster-recovery-plan-sql-server-pdw.md).-->|  
|Überwachen der appliance|Überwachen der Appliance-Zustand, Integrität und Leistung mithilfe von Systemsichten, Protokolle und die Admin-Konsole an. Korrigieren oder Probleme zu melden. Finden Sie unter [Integritätsstatus des Monitors Appliance &#40;Analytics-Plattformsystem&#41;](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md).|  
