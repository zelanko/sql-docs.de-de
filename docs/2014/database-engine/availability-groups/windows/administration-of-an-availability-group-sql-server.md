---
title: Verwaltung einer Verfügbarkeitsgruppe (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], managing
ms.assetid: 0b7542fa-235e-413d-81bf-3eff9ee07480
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e8d826201f44bb666050f5229b4824b5c2198dc0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75228998"
---
# <a name="administration-of-an-availability-group-sql-server"></a>Verwaltung einer Verfügbarkeitsgruppe (SQL Server)
  Die Verwaltung einer vorhandenen AlwaysOn-Verfügbarkeitsgruppe in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] schließt folgende Tasks ein:  
  
-   Ändern der Eigenschaften eines vorhandenen Verfügbarkeitsreplikats, z. B. Ändern des Clientverbindungszugriffs (zum Konfigurieren lesbarer sekundärer Replikate), des Failovermodus, Verfügbarkeitsmodus oder der Timeouteinstellung für die Sitzung  
  
-   Hinzufügen oder Entfernen sekundärer Replikate  
  
-   Hinzufügen oder Entfernen einer Datenbank  
  
-   Anhalten oder Fortsetzen einer Datenbank  
  
-   Ausführen eines geplanten manuellen Failovers ( *manuelles Failover*) oder eines erzwungenen manuellen Failovers ( *erzwungenes Failover*)  
  
-   Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners  
  
-   Verwalten [lesbarer sekundärer Replikate](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) für eine angegebene Verfügbarkeitsgruppe. Dies umfasst die Konfiguration eines oder mehrerer Replikate für den schreibgeschütztem Zugriff unter der sekundären Rolle sowie die Konfiguration von schreibgeschütztem Routing.  
  
-   Verwalten von [Sicherungen auf sekundären Replikaten](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) für eine angegebene Verfügbarkeitsgruppe. Dies umfasst die Konfiguration des bevorzugten Orts für die Ausführung von Sicherungsaufträgen und die anschließende Skripterstellung für Sicherungsaufträge, um die Sicherungseinstellung zu implementieren. Sie müssen Sicherungsauftragsskripts für jede Datenbank in der Verfügbarkeitsgruppe auf jeder Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erstellen, die ein Verfügbarkeitsreplikat hostet.  
  
-   Löschen einer Verfügbarkeitsgruppe  
  
-   Kreuzclustermigration von AlwaysOn-Verfügbarkeitsgruppen für Betriebssystemupgrade  
  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So konfigurieren Sie eine vorhandene Verfügbarkeitsgruppe**  
  
-   [Hinzufügen eines sekundären Replikats zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Entfernen einer sekundären Replikats aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
-   [Entfernen einer sekundären Datenbank aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Entfernen einer primären Datenbank aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [Konfigurieren Sie die flexible Failoverrichtlinie zum Steuern der Bedingungen für automatisches Failover &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](configure-flexible-automatic-failover-policy.md)  
  
 **So verwalten Sie eine Verfügbarkeits Gruppe**  
  
-   [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Ausführen eines geplanten manuellen Failovers einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Ausführen eines erzwungenen manuellen Failovers einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Entfernen einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md)  
  
 **Verwalten eines Verfügbarkeits Replikats**  
  
-   [Hinzufügen eines sekundären Replikats zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Entfernen einer sekundären Replikats aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Ändern des Verfügbarkeitsmodus eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Ändern des Failovermodus eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Konfigurieren des schreibgeschützten Zugriffs auf ein Verfügbarkeitsreplikat &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Konfigurieren des schreibgeschützten Routing für eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Ändern des Sitzungstimeouts für ein Verfügbarkeitsreplikat &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **So verwalten Sie eine Verfügbarkeitsdatenbank**  
  
-   [Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
-   [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Entfernen einer primären Datenbank aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [Entfernen einer sekundären Datenbank aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Anhalten einer Verfügbarkeitsdatenbank &#40;SQL Server&#41;](suspend-an-availability-database-sql-server.md)  
  
-   [Fortsetzen einer Verfügbarkeitsdatenbank &#40;SQL Server&#41;](resume-an-availability-database-sql-server.md)  
  
 **So überwachen Sie eine Verfügbarkeits Gruppe**  
  
-   [Überwachen von Verfügbarkeitsgruppen &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)  
  
 **So unterstützen Sie das Migrieren von Verfügbarkeits Gruppen zu einem neuen wsfc-Cluster (Kreuz Cluster Migration)**  
  
-   [Ändern des HADR-Clusterkontexts der Serverinstanz &#40;SQL Server&#41;](change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
-   [Offlineschalten einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../take-an-availability-group-offline-sql-server.md)  
  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   **Blogs:**  
  
     [SQL Server AlwaysOn-Teamblogs: Der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server-Technikblogs](https://blogs.msdn.com/b/psssql/)  
  
-   **Videos:**  
  
     [Microsoft SQL Server Codename "Denali" AlwaysOn-Reihe, Teil 1: Einführung in die nächste Generation von Lösungen mit hoher Verfügbarkeit](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server Codename "Denali" AlwaysOn-Reihe, Teil 2: Erstellen einer unternehmenswichtigen Lösung für hohe Verfügbarkeit mit AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Whitepaper:**  
  
     [Microsoft-Whitepaper für SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepapers des SQL Server-Kundenberatungsteams](http://sqlcat.com/)  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Konfiguration einer Server Instanz für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md)  
 [Erstellung und Konfiguration von Verfügbarkeitsgruppen &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Aktive sekundäre Replikate: lesbare sekundäre Replikate &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)   
 [Aktive sekundäre Replikate: Sicherung auf sekundären Replikaten &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
 [Verfügbarkeitsgruppenlistener, Clientkonnektivität und Anwendungsfailover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [AlwaysOn-Richtlinien für Betriebsprobleme mit AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)   
 [Überwachen von Verfügbarkeitsgruppen (SQL Server)](monitoring-of-availability-groups-sql-server.md)   
 [AlwaysOn-Verfügbarkeitsgruppen: Interoperabilität &#40;SQL Server&#41;](always-on-availability-groups-interoperability-sql-server.md)   
 [Übersicht über Transact-SQL-Anweisungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](transact-sql-statements-for-always-on-availability-groups.md)   
 [Übersicht über PowerShell-Cmdlets für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
