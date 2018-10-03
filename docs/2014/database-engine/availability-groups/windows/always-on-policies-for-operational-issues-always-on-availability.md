---
title: Always On-Richtlinien für Betriebsprobleme mit Always On-Verfügbarkeitsgruppen (SQLServer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], troubleshooting
- Availability Groups [SQL Server], policies
ms.assetid: afa5289c-641a-4c03-8749-44862384ec5f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e1e4c878004f3cdcc492637d338e8ff6c8d92937
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104171"
---
# <a name="always-on-policies-for-operational-issues-with-always-on-availability-groups-sql-server"></a>Always On-Richtlinien für Betriebsprobleme mit Always On-Verfügbarkeitsgruppen (SQL Server)
  Das [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]-Zustandsmodell wertet eine Reihe vordefinierter Richtlinien der richtlinienbasierten Verwaltung aus. Sie können Thesen verwenden, um den Zustand einer Verfügbarkeitsgruppe sowie deren Verfügbarkeitsreplikate und Datenbanken in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]anzuzeigen.  
  
 
  
##  <a name="TermsAndDefinitions"></a> Begriffe und Definitionen  
 Vordefinierte AlwaysOn-Richtlinien  
 Ein Satz integrierter Richtlinien, die es Datenbankadministratoren ermöglichen, eine Verfügbarkeitsgruppe und die zugehörigen Verfügbarkeitsreplikate und -datenbanken auf Konformität mit den Zuständen zu prüfen, die durch die AlwaysOn-Richtlinien definiert werden.  
  
 [AlwaysOn-Verfügbarkeitsgruppen](always-on-availability-groups-sql-server.md) eine hohe Verfügbarkeit und notfallwiederherstellung – Lösung, die Alternative zur datenbankspiegelung auf Unternehmensebene bietet.  
  
 Verfügbarkeitsgruppe  
 Ein Container für jeden diskreten Satz von Benutzerdatenbanken (auch *Verfügbarkeitsdatenbanken*genannt), für die zusammen ein Failover ausgeführt wird.  
  
 Verfügbarkeitsreplikat  
 Eine Instanziierung einer Verfügbarkeitsgruppe, die von einer bestimmten Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gehostet wird und eine lokale Kopie jeder Verfügbarkeitsdatenbank beibehält, die zur Verfügbarkeitsgruppe gehört. Zwei Typen von Verfügbarkeitsreplikaten sind vorhanden: ein einzelnes *primäres Replikat* und ein bis vier *sekundäre Replikate*. Die Serverinstanzen, die die Verfügbarkeitsreplikate für eine angegebene Verfügbarkeitsgruppe hosten, müssen sich auf verschiedenen Konten eines einzelnen WSFC-Clusters (Windows Server-Failoverclustering) befinden.  
  
 Verfügbarkeitsdatenbank  
 Eine Datenbank, die zu einer Verfügbarkeitsgruppe gehört. Für jede Verfügbarkeitsdatenbank verwaltet die Verfügbarkeitsgruppe eine einzelne Lese-/Schreibkopie (die *primäre Datenbank*) und eine bis vier schreibgeschützte Kopien (*sekundäre Datenbanken*).  
  
 AlwaysOn-Dashboard  
 Ein [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] -Dashboard, das eine Übersicht über die Integrität einer Verfügbarkeitsgruppe bereitstellt. Weitere Informationen hierzu finden Sie unter [AlwaysOn-Dashboard](#Dashboard)weiter unten in diesem Thema.  
  
##  <a name="AlwaysOnPBM"></a> Vordefinierte Richtlinien und Probleme  
 In der folgenden Tabelle sind die vordefinierten Richtlinien zusammengefasst.  
  
|Richtlinienname|Problem|Kategorie**<sup>*</sup>**|Facet|  
|-----------------|-----------|------------------------------|-----------|  
|WSFC-Clusterstatus|[WSFC cluster service is offline](wsfc-cluster-service-is-offline.md).|Kritisch|SQL Server-Instanz|  
|Onlinezustand der Verfügbarkeitsgruppe|[Availability group is offline](availability-group-is-offline.md).|Kritisch|Verfügbarkeitsgruppe|  
|Bereitschaft der Verfügbarkeitsgruppe für automatisches Failover|[Availability group is not ready for automatic failover](availability-group-is-not-ready-for-automatic-failover.md).|Kritisch|Verfügbarkeitsgruppe|  
|Datensynchronisierungsstatus der Verfügbarkeitsreplikate|[Some availability replicas are not synchronizing data](some-availability-replicas-are-not-synchronizing-data.md).|Warnung|Verfügbarkeitsgruppe|  
|Datensynchronisierungsstatus synchroner Replikate|[Some synchronous replicas are not synchronized](some-synchronous-replicas-are-not-synchronized.md).|Warnung|Verfügbarkeitsgruppe|  
|Verfügbarkeitsreplikat-Rollenstatus|[Some availability replicas do not have a healthy role](some-availability-replicas-do-not-have-a-healthy-role.md).|Warnung|Verfügbarkeitsgruppe|  
|Verbindungsstatus von Verfügbarkeitsreplikaten|[Some availability replicas are disconnected](some-availability-replicas-are-disconnected.md).|Warnung|Verfügbarkeitsgruppe|  
|Verfügbarkeitsreplikat-Rollenstatus|[Availability replica does not have a healthy role](availability-replica-does-not-have-a-healthy-role.md).|Kritisch|Verfügbarkeitsreplikat|  
|Verfügbarkeitsreplikat-Verbindungsstatus|[Availability replica is disconnected](availability-replica-is-disconnected.md).|Kritisch|Verfügbarkeitsreplikat|  
|Joinzustand des Verfügbarkeitsreplikats|[Verfügbarkeitsreplikat ist nicht verknüpft](availability-replica-is-not-joined.md).|Warnung|Verfügbarkeitsreplikat|  
|Datensynchronisierungsstatus des Verfügbarkeitsreplikats|[Data synchronization state of some availability database is not healthy](data-synchronization-state-of-some-availability-database-is-not-healthy.md).|Warnung|Verfügbarkeitsreplikat|  
|Verfügbarkeitsdatenbank im angehaltenen Zustand|[Availability database is suspended](availability-database-is-suspended.md).|Warnung|Verfügbarkeitsdatenbank|  
|Joinzustand der Verfügbarkeitsdatenbank|[Secondary database is not joined](secondary-database-is-not-joined.md).|Warnung|Verfügbarkeitsdatenbank|  
|Datensynchronisierungsstatus der Verfügbarkeitsdatenbank|[Data synchronization state of availability database is not healthy](data-synchronization-state-of-availability-database-is-not-healthy.md).|Warnung|Verfügbarkeitsdatenbank|  
  
> [!IMPORTANT]  
>  **<sup>*</sup>**  Für AlwaysOn-Richtlinien werden die Kategorienamen als IDs verwendet. Durch die Änderung des Namens einer AlwaysOn-Kategorie wird die Funktion zur Integritätsüberprüfung unterbrochen. Ändern Sie die Namen von AlwaysOn-Kategorien daher nicht.  
  
##  <a name="Dashboard"></a> AlwaysOn-Dashboard  
 Das AlwaysOn-Dashboard bietet eine Übersicht über die Integrität einer Verfügbarkeitsgruppe. Das AlwaysOn-Dashboard umfasst die folgenden Funktionen:  
  
-   Ermöglicht Ihnen, Details zu einer angegebenen Verfügbarkeitsgruppe, zu deren Verfügbarkeitsreplikaten und Datenbanken leicht anzuzeigen.  
  
-   Zeigt visuelle Indikatoren für wichtige Zustände an, um Datenbankadministratoren zu helfen, schnelle Entscheidungen zum Betriebsablauf zu treffen.  
  
-   Stellt Startpunkte für Problembehandlungsszenarien bereit.  
  
-   Für ein gegebenes Betriebsproblem wird das Dialogfeld **Ergebnis der Richtlinienauswertung** mit Informationen zu bestimmten AlwaysOn-Integritätsrichtlinienverletzungen und Links zur Problemlösungshilfe gefüllt.  
  
-   Stellt einen Systemintegritäts-Viewer für erweiterte Ereignisse bereit, um vorherige Ereignisse für AlwaysOn-spezifische Probleme anzuzeigen.  
  
-   Wenn die Ausführung eines Failovers für die Verfügbarkeitsgruppe eine mögliche Problembehebung ist, wird ein Startpunkt für die Links[Assistent für das Failover von Verfügbarkeitsgruppen](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)bereitgestellt. Dieser Assistent führt den Datenbankadministrator durch den manuellen Failoverprozess.  
  
##  <a name="ExtendHealthModel"></a> Erweitern des Always On-Zustandsmodells  
 Die Erweiterung des [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Zustandsmodells bezieht sich darauf, dass Sie eigene benutzerdefinierte Richtlinien erstellen und diese je nach überwachtem Objekttyp bestimmten Kategorien zuweisen können.  Nachdem Sie einige Einstellungen geändert haben, wertet das AlwaysOn-Dashboard automatisch eigene benutzerdefinierte Richtlinien sowie vordefinierte AlwaysOn-Richtlinien aus.  
  
 Eine benutzerdefinierte Richtlinie kann beliebige der verfügbaren PBM-Facets verwenden, einschließlich der von vordefinierten AlwaysOn-Richtlinien verwendeten Facets (siehe [Vordefinierte Richtlinien und Probleme](#AlwaysOnPBM)weiter oben in diesem Thema). Das serverfacet stellt die folgenden Eigenschaften für die Überwachung [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] Integrität: (`IsHadrEnabled` und `HadrManagerStatus`). Das Serverfacet stellt auch Eigenschaften der folgenden Richtlinien zum Überwachen der WSFC-Clusterkonfiguration bereit: `ClusterQuorumType` und `ClusterQuorumState`.  
  
 Weitere Informationen finden Sie unter [Das AlwaysOn-Zustandsmodell Teil 2 – Erweitern des Zustandsmodells](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx) (ein SQL Server AlwaysOn-Teamblog).  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Verwenden von AlwaysOn-Richtlinien zum Anzeigen des Zustands einer verfügbarkeitsgruppe &#40;SQLServer&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
-   [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [WSFC-Notfallwiederherstellung durch erzwungenes Quorum &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
-   [Erzwingen des Starts eines Clusters ohne Quorum](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [Ausführen eines erzwungenen manuellen Failovers einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Problembehandlung bei einem fehlerhaften Dateihinzufügungsvorgängen Vorgang &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Das AlwaysOn-Zustandsmodell Teil 1 – Zustandsmodellarchitektur](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx)  
  
-   [Das AlwaysOn-Zustandsmodell Teil 2 – Erweitern des Zustandsmodells](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx)  
  
-   [Microsoft SQL Server AlwaysOn-Lösungshandbuch für hohe Verfügbarkeit und Notfallwiederherstellung](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a>Siehe auch  
 [AlwaysOn-Verfügbarkeitsgruppen (SQLServer)](always-on-availability-groups-sql-server.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwaltung einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md)   
 [Überwachen von Verfügbarkeitsgruppen &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)  
  
  
