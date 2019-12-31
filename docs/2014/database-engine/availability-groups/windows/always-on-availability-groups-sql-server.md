---
title: Always On-Verfügbarkeitsgruppen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- secondary replicas, see Availability Groups [SQL Server]
- availability [SQL Server]
- AlwaysOn [SQL Server], see Availability Groups [SQL Server]
- Availability Groups [SQL Server]
ms.assetid: aa427606-8422-4656-b205-c9e665ddc8c1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2e040fb9c05683be9d737ea134710c03d36317cd
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75229013"
---
# <a name="always-on-availability-groups-sql-server"></a>Always On-Verfügbarkeitsgruppen (SQL Server)
  Die Funktion [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ist eine Lösung für hohe Verfügbarkeit und Notfallwiederherstellung, die eine Alternative zur Datenbankspiegelung auf Unternehmensebene bietet. 
  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]wurden in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] eingeführt und maximieren die Verfügbarkeit einer Gruppe von Benutzerdatenbanken für ein Unternehmen. Eine *Verfügbarkeits Gruppe* unterstützt eine Failoverumgebung für einen diskreten Satz von Benutzer Datenbanken (als *Verfügbarkeits Datenbanken*bezeichnet), für die ein Failover durchgeführt wird. Eine Verfügbarkeitsgruppe unterstützt einen Satz primärer Datenbanken mit Lese-/Schreibzugriff und einen bis acht Sätze entsprechender sekundärer Datenbanken. Optional können sekundäre Datenbanken für schreibgeschützten Zugriff und/oder einige Sicherungsvorgänge verfügbar gemacht werden.  
  
 Eine Verfügbarkeitsgruppe führt auf der Ebene eines Verfügbarkeitsreplikats ein Failover aus. Failover werden nicht durch Datenbankprobleme verursacht, z. B., wenn eine Datenbank aufgrund eines Verlusts einer Datendatei, des Löschens einer Datenbank oder der Beschädigung eines Transaktionsprotokolls, verdächtig wird.  
  
  
##  <a name="Benefits"></a>Davon  
 
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] stellen ein breites Spektrum von Optionen bereit, durch die die Datenbankverfügbarkeit verbessert und eine optimale Ressourcenverwendung ermöglicht werden. Die wichtigsten Komponenten sind:  
  
-   Unterstützt bis zu neun Verfügbarkeitsreplikate. Ein *Verfügbarkeitsreplikat* ist eine Instanziierung einer Verfügbarkeitsgruppe, die von einer bestimmten Instanz von SQL Server gehostet wird und eine lokale Kopie jeder Verfügbarkeitsdatenbank beibehält, die zur Verfügbarkeitsgruppe gehört. Jede Verfügbarkeitsgruppe unterstützt ein primäres Replikat und bis zu acht sekundäre Replikate. Weitere Informationen finden Sie unter [Übersicht über Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
    > [!IMPORTANT]  
    >  Jedes Verfügbarkeitsreplikat muss sich in einem anderen Knoten eines einzelnen WSFC-Clusters (Windows Server-Failoverclustering) befinden. Weitere Informationen zu Voraussetzungen, Einschränkungen und Empfehlungen für Verfügbarkeits Gruppen finden Sie unter [Voraussetzungen, Einschränkungen und Empfehlungen für Always on Verfügbarkeits Gruppen. SQL Server;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
-   Unterstützt die folgenden alternativen Verfügbarkeitsmodi:  
  
    -   *Asynchroner Commit-Modus*. Dieser Verfügbarkeitsmodus ist eine Lösung für die Notfallwiederherstellung, die gut funktioniert, wenn die Verfügbarkeitsreplikate über große Entfernungen verteilt sind.  
  
    -   *Synchroner Commit-Modus*. Bei diesem Verfügbarkeitsmodus haben hohe Verfügbarkeit und Datenschutz Vorrang vor Leistung, und dies hat eine höhere Transaktionslatenz zur Folge. Eine bestimmte Verfügbarkeitsgruppe kann bis zu drei Verfügbarkeitsreplikate mit synchronem Commit (einschließlich des aktuellen primären Replikats) unterstützen.  
  
     Weitere Informationen finden Sie unter [Verfügbarkeits Modi. Always on Verfügbarkeits Gruppen;](availability-modes-always-on-availability-groups.md).  
  
-   Unterstützt mehrere Failovermethoden für Verfügbarkeitsgruppen: automatisches Failover, geplantes manuelles Failover (im Allgemeinen "manuelles Failover" genannt) und erzwungenes manuelles Failover (im Allgemeinen "erzwungenes Failover" genannt). Weitere Informationen finden Sie unter [Failover und Failovermodi; Always on Verfügbarkeits Gruppen;](failover-and-failover-modes-always-on-availability-groups.md).  
  
-   Ermöglicht es Ihnen, ein angegebenes Verfügbarkeitsreplikat so zu konfigurieren, dass es entweder eines oder beide der folgenden Funktionen für aktive sekundäre Replikate unterstützt:  
  
    -   Lesezugriff, der es schreibgeschützten Verbindungen erlaubt, auf das Replikat zuzugreifen und dessen Datenbanken zu lesen, wenn es als sekundäres Replikat ausgeführt wird. Weitere Informationen finden Sie unter [aktive sekundäre Replikate: lesbare sekundäre Replikate; Always on Verfügbarkeits Gruppen](https://msdn.microsoft.com/library/ff878253.aspx)).  
  
    -   Das Ausführen von Sicherungsvorgängen für seine Datenbanken, wenn es als sekundäres Replikat ausgeführt wird. Weitere Informationen finden Sie unter [aktive sekundäre Replikate: Sicherung auf sekundären Replikaten](https://msdn.microsoft.com/library/ff878253.aspx)).  
  
     Durch die Verwendung aktiver sekundärer Replikate lassen sich durch die bessere Ressourcennutzung sekundärer Hardware die IT-Effizienz erhöhen und die Kosten reduzieren. Außerdem trägt das Auslagern reiner Lesevorgänge und Sicherungsaufträge auf sekundäre Replikate dazu bei, die Leistung auf dem primären Replikat zu verbessern.  
  
-   Unterstützt einen Verfügbarkeitsgruppenlistener für jede Verfügbarkeitsgruppe. Ein *Verfügbarkeitsgruppenlistener* ist ein Servername, mit dem Clients eine Verbindung herstellen können, um auf eine Datenbank in einem primären oder sekundären Replikat einer AlwaysOn-Verfügbarkeitsgruppe zuzugreifen. Verfügbarkeitsgruppenlistener leiten eingehende Verbindungen an das primäre Replikat oder ein schreibgeschütztes sekundäres Replikat weiter. Der Listener ermöglicht ein schnelles Anwendungsfailover, nachdem für eine Verfügbarkeitsgruppe ein Failover ausgeführt wurde. Weitere Informationen finden Sie unter [verfügbarkeitsgruppenlistener, Client Konnektivität und Anwendungs Failover. SQL Server;](../../listeners-client-connectivity-application-failover.md).  
  
-   Unterstützt eine flexible Failoverrichtlinie, um größere Kontrolle über das Failover von Verfügbarkeitsgruppen zu erlangen. Weitere Informationen finden Sie unter [Failover und Failovermodi; Always on Verfügbarkeits Gruppen;](failover-and-failover-modes-always-on-availability-groups.md).  
  
-   Unterstützt die automatische Seitenreparatur als Schutz vor Seitenbeschädigungen. Weitere Informationen finden Sie unter [Automatische Seiten Reparatur &#40;für Verfügbarkeits Gruppen und Daten Bank Spiegelung;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md).  
  
-   Unterstützt Verschlüsselung und Komprimierung, die einen sicheren, leistungsstarken Transport ermöglichen.  
  
-   Stellt einen integrierten Satz von Tools bereit, um die Bereitstellung und Verwaltung von Verfügbarkeitsgruppen zu erleichtern. Dazu gehören:  
  
    -   
  [!INCLUDE[tsql](../../../includes/tsql-md.md)] -DDL-Anweisungen zum Erstellen und Verwalten von Verfügbarkeitsgruppen. Weitere Informationen finden Sie unter [Übersicht über Transact-SQL-Anweisungen für Always on-Verfügbarkeits Gruppe; SQL Server;](transact-sql-statements-for-always-on-availability-groups.md).  
  
    -   
  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] -Tools:  
  
        -   Mit dem [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] wird eine Verfügbarkeitsgruppe erstellt und verwaltet. In einigen Umgebungen kann dieser Assistent auch die sekundären Datenbanken automatisch vorbereiten und die Datensynchronisierung für jede von ihnen starten. Weitere Informationen finden Sie unter [Verwenden des Dialog Felds "neue Verfügbarkeits Gruppe". SQL Server Management Studio;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md).  
  
        -   Der [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] fügt einer vorhandenen Verfügbarkeitsgruppe eine oder mehrere primäre Datenbanken hinzu. In einigen Umgebungen kann dieser Assistent auch die sekundären Datenbanken automatisch vorbereiten und die Datensynchronisierung für jede von ihnen starten. Weitere Informationen finden Sie unter [Verwenden des Assistenten zum Hinzufügen von Datenbanken zu Verfügbarkeitsgruppen (SQL Server)](availability-group-add-database-to-group-wizard.md).  
  
        -   Der [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] fügt einer vorhandenen Verfügbarkeitsgruppe ein oder mehrere sekundäre Replikate hinzu. In einigen Umgebungen kann dieser Assistent auch die sekundären Datenbanken automatisch vorbereiten und die Datensynchronisierung für jede von ihnen starten. Weitere Informationen finden Sie unter [Verwenden des Assistenten zum Hinzufügen von Replikaten zu Verfügbarkeits Gruppen. SQL Server Management Studio;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md).  
  
        -   Der [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)] initiiert ein manuelles Failover für eine Verfügbarkeitsgruppe. Abhängig von der Konfiguration und dem Zustand des sekundären Replikats, das Sie als Failoverziel angeben, kann der Assistent entweder ein geplantes oder ein erzwungenes manuelles Failover ausführen. Weitere Informationen finden Sie unter [Verwenden des Assistenten für das Failover von Verfügbarkeits Gruppen. SQL Server Management Studio;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).  
  
    -   Der [!INCLUDE[ssAoDash](../../../includes/ssaodash-md.md)] überwacht AlwaysOn-Verfügbarkeitsgruppen, Verfügbarkeitsreplikate und Verfügbarkeitsdatenbanken und wertet Ergebnisse für AlwaysOn-Richtlinien aus. Weitere Informationen finden Sie unter [Verwenden des AlwaysOn-Dashboards. SQL Server Management Studio;](use-the-always-on-dashboard-sql-server-management-studio.md).  
  
    -   Der Detailbereich im Objekt-Explorer zeigt grundlegende Informationen zu vorhandenen Verfügbarkeitsgruppen an. Weitere Informationen finden Sie unter [Verwenden der Objekt-Explorer Details zum Überwachen von Verfügbarkeits Gruppen. SQL Server Management Studio;](use-object-explorer-details-to-monitor-availability-groups.md).  
  
    -   PowerShell-Cmdlets. Weitere Informationen finden Sie unter [Übersicht über PowerShell-Cmdlets für Always on-Verfügbarkeits Gruppen. SQL-Dienst;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md).  
  
##  <a name="TermsAndDefinitions"></a>Begriffe und Definitionen  
 Verfügbarkeitsgruppe  
 Ein Container für eine Gruppe von Datenbanken ( *Verfügbarkeitsdatenbanken*), für die zusammen ein Failover ausgeführt wird.  
  
 Verfügbarkeitsdatenbank  
 Eine Datenbank, die zu einer Verfügbarkeitsgruppe gehört. Für jede Verfügbarkeitsdatenbank verwaltet die Verfügbarkeitsgruppe eine einzelne Lese-/Schreibkopie (die *primäre Datenbank*) und eine bis acht schreibgeschützte Kopien (*sekundäre Datenbanken*).  
  
 primäre Datenbank  
 Die Lese-/Schreibkopie einer Verfügbarkeitsdatenbank.  
  
 Sekundäre Datenbank  
 Eine schreibgeschützte Kopie einer Verfügbarkeitsdatenbank.  
  
 Verfügbarkeitsreplikat  
 Eine Instanziierung einer Verfügbarkeitsgruppe, die von einer bestimmten Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gehostet wird und eine lokale Kopie jeder Verfügbarkeitsdatenbank beibehält, die zur Verfügbarkeitsgruppe gehört. Zwei Typen von Verfügbarkeitsreplikaten sind vorhanden: ein einzelnes *primäres Replikat* und ein bis acht *sekundäre Replikate*.  
  
 primäres Replikat  
 Das Verfügbarkeitsreplikat, das die primären Datenbanken für Lese-/Schreibverbindungen von Clients verfügbar macht und darüber hinaus Transaktionsprotokoll-Datensätze für jede primäre Datenbank an jedes sekundäre Replikat sendet.  
  
 Sekundäres Replikat  
 Ein Verfügbarkeitsreplikat, das eine sekundäre Kopie jeder Verfügbarkeitsdatenbank beibehält und als potenzielles Failoverziel für die Verfügbarkeitsgruppe dient. Optional kann ein sekundäres Replikat schreibgeschützten Zugriff auf sekundäre Datenbanken und das Erstellen von Sicherungen für sekundäre Datenbanken unterstützen.  
  
 Verfügbarkeitsgruppenlistener  
 Ein Servername, mit dem Clients eine Verbindung herstellen können, um auf eine Datenbank in einem primären oder sekundären Replikat einer Always On-Verfügbarkeitsgruppe zuzugreifen. Verfügbarkeitsgruppenlistener leiten eingehende Verbindungen an das primäre Replikat oder ein schreibgeschütztes sekundäres Replikat weiter.  
  
> [!NOTE]  
>  Weitere Informationen finden Sie unter [Übersicht über AlwaysOn-Verfügbarkeitsgruppen. SQL-Dienst;](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="Interoperability"></a>Interoperabilität und Koexistenz mit anderen Datenbank-Engine Features  
 
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] können mit den folgenden Funktionen oder Komponenten von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verwendet werden:  
  
-   [Informationen zu Change Data Capture; SQL Server;](../../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
-   [Informationen zu Änderungsnachverfolgung; SQL-Dienst](../../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
-   [Eigenständige Datenbanken](../../../relational-databases/databases/contained-databases.md)  
  
-   [Datenbankverschlüsselung](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
-   [Datenbank-Momentaufnahmen](database-snapshots-with-always-on-availability-groups-sql-server.md)  
  
-   [FileStream](../../../relational-databases/blob/filestream-sql-server.md)  
  
-   [FileTable](../../../relational-databases/blob/filetables-sql-server.md)  
  
-   [Protokoll Versand](../../log-shipping/about-log-shipping-sql-server.md)  
  
-   [Remote BLOB-Speicher (RBS)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
-   [Reproduktions](../../install-windows/install-sql-server-replication.md)  
  
-   [Service Broker](../../configure-windows/sql-server-service-broker.md)  
  
-   [SQL Server-Agent](../../../ssms/agent/sql-server-agent.md)  
  
-   [Reporting Services](reporting-services-with-always-on-availability-groups-sql-server.md)  
  
> [!WARNING]  
>  Informationen zu Einschränkungen und Einschränkungen bei der Verwendung anderer Funktionen mit [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]finden Sie unter [Always on-Verfügbarkeits Gruppen: Interoperabilität; SQL Server;](always-on-availability-groups-interoperability-sql-server.md).  
  
##  <a name="RelatedTasks"></a>Verwandte Aufgaben  
  
-   [Ersten Einstieg in Always on Verfügbarkeits Gruppen SQL Server;](getting-started-with-always-on-availability-groups-sql-server.md)  
  
##  <a name="RelatedContent"></a>Verwandte Inhalte  
  
-   **Gt**  
  
     [SQL Server Always on Teamblogs: der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blog zu CSS-SQL Server Technikern](https://blogs.msdn.com/b/psssql/)  
  
-   **Videos**  
  
     [Microsoft SQL Server Codename "Denali" Always on Reihe, Teil 1: Einführung in die nächste Generation von Lösungen mit hoher Verfügbarkeit](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server mit dem Codenamen "Denali" Always on Reihe, Teil 2: Entwickeln einer Unternehmens wichtigen Lösung für hohe Verfügbarkeit mit AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Whitepaper**  
  
     [Microsoft SQL Server Always on Lösungs Handbuch für hohe Verfügbarkeit und Notfall Wiederherstellung](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über Always on Verfügbarkeits Gruppen SQL Server;](overview-of-always-on-availability-groups-sql-server.md)   
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Konfiguration einer Server Instanz für Always on Verfügbarkeits Gruppen; SQL Server;](always-on-availability-groups-sql-server.md)   
 [Erstellung und Konfiguration von Verfügbarkeits Gruppen SQL Server;](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Verwaltung einer Verfügbarkeits Gruppe; SQL Server;](administration-of-an-availability-group-sql-server.md)   
 [Überwachung von Verfügbarkeits Gruppen &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [Übersicht über Transact-SQL-Anweisungen für Always on-Verfügbarkeits Gruppen SQL Server;](transact-sql-statements-for-always-on-availability-groups.md)   
 [Übersicht über PowerShell-Cmdlets für AlwaysOn-Verfügbarkeitsgruppen; SQL Server;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
