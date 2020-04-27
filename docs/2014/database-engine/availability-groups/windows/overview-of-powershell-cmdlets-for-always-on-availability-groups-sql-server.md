---
title: Übersicht über PowerShell-Cmdlets für AlwaysOn-Verfügbarkeitsgruppen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], PowerShell cmdlets
- Availability Groups [SQL Server], about
- PowerShell [SQL Server], cmdlets
ms.assetid: b3fef0d5-b6d7-4386-a0f0-d06c165ad4de
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4996a1026b4c85b105efc09b8381913f7a47942a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62789457"
---
# <a name="overview-of-powershell-cmdlets-for-alwayson-availability-groups-sql-server"></a>Übersicht über PowerShell-Cmdlets für AlwaysOn-Verfügbarkeitsgruppen (SQL Server)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] PowerShell ist eine speziell für die Systemverwaltung entwickelte taskbasierte Befehlszeilenshell und Skriptsprache. [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] stellt in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] einen Satz von PowerShell-Cmdlets bereit, mit denen Sie Verfügbarkeitsgruppen, Verfügbarkeitsreplikate und Verfügbarkeitsdatenbanken bereitstellen, verwalten und überwachen können.  
  
> [!NOTE]  
>  Ein PowerShell-Cmdlet kann ausgeführt werden, indem eine Aktion erfolgreich initiiert wird. Dies zeigt nicht an, dass die vorgesehene Arbeit, z. B. das Failover einer Verfügbarkeitsgruppe, ausgeführt wurde. Wenn Sie Skripts für eine Aktionsfolge erstellen, müssen Sie möglicherweise den Status von Aktionen überprüfen und auf deren Ausführung warten.  
  
 Dieses Thema bietet eine Einführung in die Cmdlets für die folgenden Aufgaben:  
  
-   [Konfigurieren einer Serverinstanz für AlwaysOn-Verfügbarkeitsgruppen](#ConfiguringServerInstance)  
  
-   [Sichern und Wiederherstellen von Datenbanken und Transaktions Protokollen](#BnRcmdlets)  
  
-   [Erstellen und Verwalten von Verfügbarkeitsgruppen](#DeployManageAGs)  
  
-   [Erstellen und Verwalten von Verfügbarkeitsgruppenlistenern](#AGlisteners)  
  
-   [Erstellen und Verwalten eines Verfügbarkeits Replikats](#DeployManageARs)  
  
-   [Hinzufügen und Verwalten von Verfügbarkeitsdatenbanken](#DeployManageDbs)  
  
-   [Überwachen der Integrität von Verfügbarkeitsgruppen](#MonitorTblshtAGs)  
  
> [!NOTE]  
>  Eine Liste der Themen in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] der-Online Dokumentation, die beschreiben, wie Cmdlets zum [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] Ausführen von Aufgaben verwendet werden, finden Sie im Abschnitt "Verwandte Aufgaben" unter [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="configuring-a-server-instance-for-alwayson-availability-groups"></a><a name="ConfiguringServerInstance"></a>Konfigurieren einer Server Instanz für AlwaysOn-Verfügbarkeitsgruppen  
  
|Cmdlets|Beschreibung|Unterstützt auf|  
|-------------|-----------------|------------------|  
|`Disable-SqlAlwaysOn`|Deaktiviert die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Funktion auf einer Serverinstanz.|Die Serverinstanz, die vom Parameter `Path`, `InputObject` oder `Name` angegeben wird. (Muss eine Edition von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sein, die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]unterstützt.)|  
|`Enable-SqlAlwaysOn`|Aktiviert [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] auf einer Instanz von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , die die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Funktion unterstützt. Weitere Informationen zur-unter [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]Stützung für finden Sie unter [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).|Eine beliebige Edition von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]unterstützt.|  
|`New-SqlHadrEndPoint`|Erstellt einen neuen Datenbankspiegelungs-Endpunkt auf einer Serverinstanz. Dieser Endpunkt ist zur Datenverschiebung zwischen primären und sekundären Datenbanken erforderlich.|Eine beliebige Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|`Set-SqlHadrEndpoint`|Ändert die Eigenschaften eines vorhandenen Datenbankspiegelungs-Endpunkts, z. B. Namens-, Status- oder Authentifizierungseigenschaften.|Eine Serverinstanz, die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] unterstützt und keinen Datenbankspiegelungs-Endpunkt aufweist|  
  
##  <a name="backing-up-and-restoring-databases-and-transaction-logs"></a><a name="BnRcmdlets"></a>Sichern und Wiederherstellen von Datenbanken und Transaktions Protokollen  
  
|Cmdlets|Beschreibung|Unterstützt auf|  
|-------------|-----------------|------------------|  
|`Backup-SqlDatabase`|Erstellt eine Daten- oder Protokollsicherung.|Eine beliebige Onlinedatenbank (für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]eine Datenbank auf der Serverinstanz, die das primäre Replikat hostet)|  
|`Restore-SqlDatabase`|Stellt eine Sicherung wieder her.|Eine beliebige Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]eine Serverinstanz, die ein sekundäres Replikat hostet)<br /><br /> **&#42;&#42; wichtige &#42;&#42;** Beim Vorbereiten einer sekundären Datenbank müssen Sie den `-NoRecovery` -Parameter in jedem `Restore-SqlDatabase` Befehl verwenden.|  
  
 Informationen zur Verwendung dieser Cmdlets zum Vorbereiten einer sekundären Datenbank finden Sie unter [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
##  <a name="creating-and-managing-an-availability-group"></a><a name="DeployManageAGs"></a>Erstellen und Verwalten einer Verfügbarkeits Gruppe  
  
|Cmdlets|Beschreibung|Unterstützt auf|  
|-------------|-----------------|------------------|  
|`New-SqlAvailabilityGroup`|Erstellt eine neue Verfügbarkeitsgruppe.|Serverinstanz zum Hosten des primären Replikats|  
|`Remove-SqlAvailabilityGroup`|Löscht eine Verfügbarkeitsgruppe.|HADR-fähige Serverinstanz|  
|`Set-SqlAvailabilityGroup`|Legt die Eigenschaften einer Verfügbarkeitsgruppe fest; schaltet eine Verfügbarkeitsgruppe online/offline|Serverinstanz, die das primäre Replikat hostet|  
|`Switch-SqlAvailabilityGroup`|Initiiert einen der folgenden Failovertypen:<br /><br /> Ein erzwungenes Failover einer Verfügbarkeitsgruppe (mit möglichem Datenverlust).<br /><br /> Ein manuelles Failover einer Verfügbarkeitsgruppe.|Serverinstanz, die das sekundäre Zielreplikat hostet|  
  
##  <a name="creating-and-managing-an-availability-group-listener"></a><a name="AGlisteners"></a>Erstellen und Verwalten eines verfügbarkeitsgruppenlistener  
  
|Cmdlet|BESCHREIBUNG|Unterstützt auf|  
|------------|-----------------|------------------|  
|`New-SqlAvailabilityGroupListener`|Erstellt einen neuen Verfügbarkeitsgruppenlistener und fügt ihn einer vorhandenen Verfügbarkeitsgruppe hinzu.|Serverinstanz, die das primäre Replikat hostet|  
|`Set-SqlAvailabilityGroupListener`|Ändert die Porteinstellung eines vorhandenen Verfügbarkeitsgruppenlisteners.|Serverinstanz, die das primäre Replikat hostet|  
|`Add-SqlAvailabilityGroupListenerStaticIp`|Fügt der vorhandenen Konfiguration eines Verfügbarkeitsgruppenlisteners eine statische IP-Adresse hinzu. Die IP-Adresse kann eine IPv4-Adresse mit Subnetz oder eine IPv6-Adresse sein.|Serverinstanz, die das primäre Replikat hostet|  
  
##  <a name="creating-and-managing-an-availability-replica"></a><a name="DeployManageARs"></a>Erstellen und Verwalten eines Verfügbarkeits Replikats  
  
|Cmdlets|Beschreibung|Unterstützt auf|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityReplica**|Erstellt eine neue Verfügbarkeitsgruppe. Sie können mithilfe des `-AsTemplate`-Parameters ein Verfügbarkeitsreplikatobjekt im Arbeitsspeicher für jedes neue Verfügbarkeitsreplikat erstellen.|Serverinstanz, die das primäre Replikat hostet|  
|`Join-SqlAvailabilityGroup`|Verknüpft ein sekundäres Replikat mit der Verfügbarkeitsgruppe.|Serverinstanz, die ein sekundäres Replikat hostet|  
|**Remove-SqlAvailabilityReplica**|Lösch Sie ein Verfügbarkeitsreplikat.|Serverinstanz, die das primäre Replikat hostet|  
|`Set-SqlAvailabilityReplica`|Legt die Eigenschaften eines Verfügbarkeitsreplikats fest.|Serverinstanz, die das primäre Replikat hostet|  
  
##  <a name="adding-and-managing-an-availability-database"></a><a name="DeployManageDbs"></a>Hinzufügen und Verwalten einer Verfügbarkeits Datenbank  
  
|Cmdlets|Beschreibung|Unterstützt auf|  
|-------------|-----------------|------------------|  
|**Add-SqlAvailabilityDatabase**|Fügt auf dem primären Replikat einer Verfügbarkeitsgruppe eine Datenbank hinzu.<br /><br /> Verknüpft auf einem sekundären Replikat eine sekundäre Datenbank mit einer Verfügbarkeitsgruppe.|Eine beliebige Serverinstanz, die ein Verfügbarkeitsreplikat hostet (Verhalten unterscheidet sich für primäre und sekundäre Replikate)|  
|**Remove-SqlAvailabilityDatabase**|Entfernt auf dem primären Replikat die Datenbank aus der Verfügbarkeitsgruppe.<br /><br /> Entfernt auf einem sekundären Replikat die lokale sekundäre Datenbank aus dem lokalen sekundären Replikat.|Eine beliebige Serverinstanz, die ein Verfügbarkeitsreplikat hostet (Verhalten unterscheidet sich für primäre und sekundäre Replikate)|  
|`Resume-SqlAvailabilityDatabase`|Setzt die Datenverschiebung für eine angehaltene Verfügbarkeitsdatenbank fort.|Die Serverinstanz, auf der die Datenbank angehalten wurde.|  
|`Suspend-SqlAvailabilityDatabase`|Hält die Datenverschiebung für eine Verfügbarkeitsdatenbank an.|Eine beliebige Serverinstanz, die ein Verfügbarkeitsreplikat hostet.|  
  
##  <a name="monitoring-availability-group-health"></a><a name="MonitorTblshtAGs"></a>Überwachungs Verfügbarkeitsgruppenintegrität  
 Mit den folgenden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Cmdlets können Sie die Integrität einer Verfügbarkeitsgruppe und ihrer Replikate und Datenbanken überwachen.  
  
> [!IMPORTANT]  
>  Sie müssen über CONNECT-, VIEW SERVER STATE- und VIEW ANY DEFINITION-Berechtigungen verfügen, um diese Cmdlets auszuführen.  
  
|Cmdlet|BESCHREIBUNG|Unterstützt auf|  
|------------|-----------------|------------------|  
|`Test-SqlAvailabilityGroup`|Bewertet die Integrität einer Verfügbarkeitsgruppe durch die Auswertung der Richtlinien der richtlinienbasierten SQL Server-Verwaltung.|Eine beliebige Serverinstanz, die ein Verfügbarkeitsreplikat hostet.*|  
|`Test-SqlAvailabilityReplica`|Bewertet die Integrität von Verfügbarkeitsreplikaten durch die Auswertung der Richtlinien der richtlinienbasierten SQL Server-Verwaltung.|Eine beliebige Serverinstanz, die ein Verfügbarkeitsreplikat hostet.*|  
|`Test-SqlDatabaseReplicaState`|Bewertet die Integrität einer Verfügbarkeitsdatenbank für alle hinzugefügten Verfügbarkeitsreplikate durch die Auswertung der Richtlinien der richtlinienbasierten SQL Server-Verwaltung.|Eine beliebige Serverinstanz, die ein Verfügbarkeitsreplikat hostet.*|  
  
 *Verwenden Sie zum Anzeigen von Informationen zu allen Verfügbarkeitsreplikaten in einer Verfügbarkeitsgruppe die Serverinstanz, die das primäre Replikat hostet.  
  
 Weitere Informationen finden Sie unter [Verwenden von AlwaysOn-Richtlinien zum Anzeigen des Zustands einer Verfügbarkeits Gruppe &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
  
