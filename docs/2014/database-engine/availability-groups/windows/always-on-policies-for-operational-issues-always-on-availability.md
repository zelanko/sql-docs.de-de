---
title: Always on von Richtlinien für Betriebsprobleme mit Always on Verfügbarkeits Gruppen (SQL Server) | Microsoft-Dokumentation
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
ms.openlocfilehash: 090ad6a9651a01532af528f5f78316eeadb9798d
ms.sourcegitcommit: 37a3e2c022c578fc3a54ebee66d9957ff7476922
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82922014"
---
# <a name="always-on-policies-for-operational-issues-with-always-on-availability-groups-sql-server"></a>Always On-Richtlinien für Betriebsprobleme mit Always On-Verfügbarkeitsgruppen (SQL Server)
  Das [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Zustandsmodell wertet eine Reihe vordefinierter Richtlinien der richtlinienbasierten Verwaltung aus. Sie können Thesen verwenden, um den Zustand einer Verfügbarkeitsgruppe sowie deren Verfügbarkeitsreplikate und Datenbanken in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]anzuzeigen.  
  
 
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a>Begriffe und Definitionen  
 Vordefinierte AlwaysOn-Richtlinien  
 Ein Satz integrierter Richtlinien, die es Datenbankadministratoren ermöglichen, eine Verfügbarkeitsgruppe und die zugehörigen Verfügbarkeitsreplikate und -datenbanken auf Konformität mit den Zuständen zu prüfen, die durch die AlwaysOn-Richtlinien definiert werden.  
  
 [AlwaysOn-Verfügbarkeitsgruppen](always-on-availability-groups-sql-server.md) Eine Lösung für hohe Verfügbarkeit und Notfall Wiederherstellung, die eine Alternative zur Daten Bank Spiegelung auf Unternehmensebene bereitstellt.  
  
 Verfügbarkeitsgruppe  
 Ein Container für jeden diskreten Satz von Benutzerdatenbanken (auch *Verfügbarkeitsdatenbanken*genannt), für die zusammen ein Failover ausgeführt wird.  
  
 Verfügbarkeitsreplikat  
 Eine Instanziierung einer Verfügbarkeitsgruppe, die von einer bestimmten Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gehostet wird und eine lokale Kopie jeder Verfügbarkeitsdatenbank beibehält, die zur Verfügbarkeitsgruppe gehört. Zwei Typen von Verfügbarkeitsreplikaten sind vorhanden: ein einzelnes *primäres Replikat* und ein bis vier *sekundäre Replikate*. Die Serverinstanzen, die die Verfügbarkeitsreplikate für eine angegebene Verfügbarkeitsgruppe hosten, müssen sich auf verschiedenen Konten eines einzelnen WSFC-Clusters (Windows Server-Failoverclustering) befinden.  
  
 Verfügbarkeitsdatenbank  
 Eine Datenbank, die zu einer Verfügbarkeitsgruppe gehört. Für jede Verfügbarkeitsdatenbank verwaltet die Verfügbarkeitsgruppe eine einzelne Lese-/Schreibkopie (die *primäre Datenbank*) und eine bis vier schreibgeschützte Kopien (*sekundäre Datenbanken*).  
  
 AlwaysOn-Dashboard  
 Ein [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] -Dashboard, das eine Übersicht über die Integrität einer Verfügbarkeitsgruppe bereitstellt. Weitere Informationen hierzu finden Sie unter [AlwaysOn-Dashboard](#Dashboard)weiter unten in diesem Thema.  
  
##  <a name="predefined-policies-and-issues"></a><a name="AlwaysOnPBM"></a>Vordefinierte Richtlinien und Probleme  
 In der folgenden Tabelle sind die vordefinierten Richtlinien zusammengefasst.  
  
|Richtlinienname|Problem|Kategorie**<sup>*</sup>**|Facet|  
|-----------------|-----------|------------------------------|-----------|  
|WSFC-Clusterstatus|[Wsfc-Cluster Dienst ist offline](wsfc-cluster-service-is-offline.md).|Kritisch|SQL Server-Instanz|  
|Onlinezustand der Verfügbarkeitsgruppe|[Verfügbarkeits Gruppe ist offline](availability-group-is-offline.md).|Kritisch|Verfügbarkeitsgruppe|  
|Bereitschaft der Verfügbarkeitsgruppe für automatisches Failover|Die [Verfügbarkeits Gruppe ist nicht für das automatische Failover bereit](availability-group-is-not-ready-for-automatic-failover.md).|Kritisch|Verfügbarkeitsgruppe|  
|Datensynchronisierungsstatus der Verfügbarkeitsreplikate|[Einige Verfügbarkeits Replikate synchronisieren keine Daten](some-availability-replicas-are-not-synchronizing-data.md).|Warnung|Verfügbarkeitsgruppe|  
|Datensynchronisierungsstatus synchroner Replikate|[Einige synchrone Replikate werden nicht synchronisiert](some-synchronous-replicas-are-not-synchronized.md).|Warnung|Verfügbarkeitsgruppe|  
|Verfügbarkeitsreplikat-Rollenstatus|[Einige Verfügbarkeits Replikate weisen keine](some-availability-replicas-do-not-have-a-healthy-role.md)fehlerfreie Rolle auf.|Warnung|Verfügbarkeitsgruppe|  
|Verbindungsstatus von Verfügbarkeitsreplikaten|[Einige Verfügbarkeits Replikate werden getrennt](some-availability-replicas-are-disconnected.md).|Warnung|Verfügbarkeitsgruppe|  
|Verfügbarkeitsreplikat-Rollenstatus|[Das Verfügbarkeits Replikat weist keine](availability-replica-does-not-have-a-healthy-role.md)fehlerfreie Rolle auf.|Kritisch|Verfügbarkeitsreplikat|  
|Verfügbarkeitsreplikat-Verbindungsstatus|[Verfügbarkeits Replikat ist getrennt](availability-replica-is-disconnected.md).|Kritisch|Verfügbarkeitsreplikat|  
|Joinzustand des Verfügbarkeitsreplikats|Das [Verfügbarkeits Replikat ist nicht](availability-replica-is-not-joined.md)verknüpft.|Warnung|Verfügbarkeitsreplikat|  
|Datensynchronisierungsstatus des Verfügbarkeitsreplikats|[Der Daten Synchronisierungs Status einer Verfügbarkeits Datenbank ist nicht](data-synchronization-state-of-some-availability-database-is-not-healthy.md)fehlerfrei.|Warnung|Verfügbarkeitsreplikat|  
|Verfügbarkeitsdatenbank im angehaltenen Zustand|Die [Verfügbarkeits Datenbank](availability-database-is-suspended.md)wurde angehalten.|Warnung|Verfügbarkeitsdatenbank|  
|Joinzustand der Verfügbarkeitsdatenbank|Die [sekundäre Datenbank ist nicht](secondary-database-is-not-joined.md)verknüpft.|Warnung|Verfügbarkeitsdatenbank|  
|Datensynchronisierungsstatus der Verfügbarkeitsdatenbank|[Der Daten Synchronisierungs Status der Verfügbarkeits Datenbank ist nicht](data-synchronization-state-of-availability-database-is-not-healthy.md)fehlerfrei.|Warnung|Verfügbarkeitsdatenbank|  
  
> [!IMPORTANT]  
>  **<sup>*</sup>** Für AlwaysOn-Richtlinien werden die Kategorien Amen als IDs verwendet. Durch die Änderung des Namens einer AlwaysOn-Kategorie wird die Funktion zur Integritätsüberprüfung unterbrochen. Ändern Sie die Namen von AlwaysOn-Kategorien daher nicht.  
  
##  <a name="alwayson-dashboard"></a><a name="Dashboard"></a>AlwaysOn-Dashboard  
 Das AlwaysOn-Dashboard bietet eine Übersicht über die Integrität einer Verfügbarkeitsgruppe. Das AlwaysOn-Dashboard umfasst die folgenden Funktionen:  
  
-   Ermöglicht Ihnen, Details zu einer angegebenen Verfügbarkeitsgruppe, zu deren Verfügbarkeitsreplikaten und Datenbanken leicht anzuzeigen.  
  
-   Zeigt visuelle Indikatoren für wichtige Zustände an, um Datenbankadministratoren zu helfen, schnelle Entscheidungen zum Betriebsablauf zu treffen.  
  
-   Stellt Startpunkte für Problembehandlungsszenarien bereit.  
  
-   Für ein gegebenes Betriebsproblem wird das Dialogfeld **Ergebnis der Richtlinienauswertung** mit Informationen zu bestimmten AlwaysOn-Integritätsrichtlinienverletzungen und Links zur Problemlösungshilfe gefüllt.  
  
-   Stellt einen Systemintegritäts-Viewer für erweiterte Ereignisse bereit, um vorherige Ereignisse für AlwaysOn-spezifische Probleme anzuzeigen.  
  
-   Wenn die Ausführung eines Failovers für die Verfügbarkeitsgruppe eine mögliche Problembehebung ist, wird ein Startpunkt für die Links[Assistent für das Failover von Verfügbarkeitsgruppen](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)bereitgestellt. Dieser Assistent führt den Datenbankadministrator durch den manuellen Failoverprozess.  
  
##  <a name="extending-the-alwayson-health-model"></a><a name="ExtendHealthModel"></a>Erweitern des AlwaysOn-Integritäts Modells  
 Die Erweiterung des [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Zustandsmodells bezieht sich darauf, dass Sie eigene benutzerdefinierte Richtlinien erstellen und diese je nach überwachtem Objekttyp bestimmten Kategorien zuweisen können.  Nachdem Sie einige Einstellungen geändert haben, wertet das AlwaysOn-Dashboard automatisch eigene benutzerdefinierte Richtlinien sowie vordefinierte AlwaysOn-Richtlinien aus.  
  
 Eine benutzerdefinierte Richtlinie kann beliebige der verfügbaren PBM-Facets verwenden, einschließlich der von vordefinierten AlwaysOn-Richtlinien verwendeten Facets (siehe [Vordefinierte Richtlinien und Probleme](#AlwaysOnPBM)weiter oben in diesem Thema). Das Serverfacet stellt die folgenden Eigenschaften zum Überwachen des [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]-Zustands bereit: (`IsHadrEnabled` und `HadrManagerStatus`). Das Serverfacet stellt auch Eigenschaften der folgenden Richtlinien zum Überwachen der WSFC-Clusterkonfiguration bereit: `ClusterQuorumType` und `ClusterQuorumState`.  
  
 Weitere Informationen finden Sie unter [Das AlwaysOn-Zustandsmodell Teil 2 – Erweitern des Zustandsmodells](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-2-extending-the-health-model) (ein SQL Server AlwaysOn-Teamblog).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Verwenden Sie AlwaysOn-Richtlinien, um die Integrität einer Verfügbarkeits Gruppe &#40;SQL Server anzuzeigen&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
-   [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [WSFC-Notfallwiederherstellung durch erzwungenes Quorum &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
-   [Erzwingen des Starts eines Clusters ohne Quorum](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [Führen Sie ein erzwungenes manuelles Failover einer Verfügbarkeits Gruppe &#40;SQL Server aus&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Problembehandlung bei einem fehlgeschlagenen Vorgang zum Hinzufügen einer Datei &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Das AlwaysOn-Zustandsmodell Teil 1 – Zustandsmodellarchitektur](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-1-basic-cmdlet-overview)  
  
-   [Das AlwaysOn-Zustandsmodell Teil 2 – Erweitern des Zustandsmodells](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-2-extending-the-health-model)  
  
-   [Microsoft SQL Server AlwaysOn-Lösungshandbuch zu hoher Verfügbarkeit und Notfallwiederherstellung](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a>Weitere Informationen  
 [AlwaysOn-Verfügbarkeitsgruppen (SQL Server)](always-on-availability-groups-sql-server.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwaltung einer Verfügbarkeits Gruppe &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md)   
 [Überwachen von Verfügbarkeitsgruppen (SQL Server)](monitoring-of-availability-groups-sql-server.md)  
  
  
