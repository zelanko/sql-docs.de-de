---
title: Konfiguration einer Server Instanz für Always on Verfügbarkeits Gruppen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], about
ms.assetid: fad8db32-593e-49d5-989c-39eb8399c416
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3dcd239c782f53ec11970e94f89e5acfac982785
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75228811"
---
# <a name="configuration-of-a-server-instance-for-always-on-availability-groups-sql-server"></a>Konfiguration einer Serverinstanz für Always On-Verfügbarkeitsgruppen (SQL Server)
  Dieses Thema enthält Informationen zu den Anforderungen für die Konfiguration einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zur Unterstützung von AlwaysOn-Verfügbarkeitsgruppen [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
> [!IMPORTANT]  
>  Wichtige Informationen zu erforderlichen [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]-Komponenten und Einschränkungen für WSFC-Knoten (Windows Server-Failoverclustering) und für Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] finden Sie unter [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
 
  
##  <a name="TermsAndDefinitions"></a>Begriffe und Definitionen  
  
 Eine Lösung für hohe Verfügbarkeit und Notfallwiederherstellung, die als Ersatz für die Datenbankspiegelung auf Unternehmensebene verwendet werden kann. Eine *Verfügbarkeits Gruppe* unterstützt eine Failoverumgebung für einen diskreten Satz von Benutzer Datenbanken (als *Verfügbarkeits Datenbanken*bezeichnet), für die ein Failover durchgeführt wird.  
  
 Verfügbarkeitsreplikat  
 Eine Instanziierung einer Verfügbarkeitsgruppe, die von einer bestimmten Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gehostet wird und eine lokale Kopie jeder Verfügbarkeitsdatenbank beibehält, die zur Verfügbarkeitsgruppe gehört. Zwei Typen von Verfügbarkeitsreplikaten sind vorhanden: ein einzelnes *primäres Replikat* und ein bis vier *sekundäre Replikate*. Die Serverinstanzen, die die Verfügbarkeitsreplikate für eine angegebene Verfügbarkeitsgruppe hosten, müssen sich auf verschiedenen Konten eines einzelnen WSFC-Clusters (Windows Server-Failoverclustering) befinden.  
  
 [Daten Bank Spiegelungs Endpunkt](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
 Ein Endpunkt ist ein SQL Server-Objekt, mit dessen Hilfe SQL Server über das Netzwerk kommunizieren kann. Um an einer Datenbankspiegelung und/oder [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] teilnehmen zu können, ist für eine Serverinstanz ein spezieller, dedizierter Endpunkt erforderlich. Alle Spiegelungs- und Verfügbarkeitsgruppenverbindungen auf einer Serverinstanz verwenden denselben Datenbankspiegelungs-Endpunkt. Dieser Endpunkt ist ein auf einen bestimmten Zweck ausgerichteter Endpunkt, der ausschließlich dafür verwendet wird, diese Verbindungen von anderen Serverinstanzen zu empfangen.  
  
##  <a name="ConfigSI"></a>So konfigurieren Sie eine Server Instanz zur Unterstützung von AlwaysOn-Verfügbarkeitsgruppen  
 Um [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]zu unterstützen, muss sich eine Serverinstanz in einem Knoten im WSFC-Failovercluster befinden, der die Verfügbarkeitsgruppe hostet. Sie muss [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -aktiviert sein und über einen Datenbankspiegelungs-Endpunkt verfügen.  
  
1.  Aktivieren Sie die Funktion AlwaysOn-Verfügbarkeitsgruppen auf jeder Serverinstanz, die an einer oder mehreren Verfügbarkeitsgruppen teilnehmen soll. Eine bestimmte Serverinstanz kann nur ein einzelnes Verfügbarkeitsreplikat für eine bestimmte Verfügbarkeitsgruppe hosten.  
  
2.  Stellen Sie sicher, dass die Serverinstanz einen Datenbankspiegelungs-Endpunkt besitzt.  
  
##  <a name="RelatedTasks"></a>Verwandte Aufgaben  
 **So aktivieren Sie AlwaysOn-Verfügbarkeitsgruppen**  
  
-   [Aktivieren und deaktivieren Sie AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **So bestimmen Sie, ob ein Datenbankspiegelungs-Endpunkt**  
  
-   [sys. database_mirroring_endpoints &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
 **So erstellen Sie einen Datenbankspiegelungs-Endpunkt**  
  
-   [Erstellen Sie einen Datenbankspiegelungs-Endpunkt für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Erstellen eines Datenbankspiegelungs-Endpunkts für die Windows-Authentifizierung &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Ermöglicht einem Datenbankspiegelungs-Endpunkt die Verwendung von Zertifikaten für ausgehende Verbindungen &#40;Transact-SQL-&#41;](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
##  <a name="RelatedContent"></a>Verwandte Inhalte  
  
-   **Gt**  
  
     [AlwaysON - HADRON-Lernreihe: Nutzung des Arbeitsthreadpools für HADRON-fähige Datenbanken](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [SQL Server AlwaysOn-Teamblogs: Der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blog zu CSS-SQL Server Technikern](https://blogs.msdn.com/b/psssql/)  
  
-   **Videos**  
  
     [Microsoft SQL Server Codename "Denali" AlwaysOn-Reihe, Teil 1: Einführung in die nächste Generation von Lösungen mit hoher Verfügbarkeit](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server Codename "Denali" AlwaysOn-Reihe, Teil 2: Erstellen einer unternehmenswichtigen Lösung für hohe Verfügbarkeit mit AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Whitepaper**  
  
     [Microsoft SQL Server AlwaysOn-Lösungshandbuch zu hoher Verfügbarkeit und Notfallwiederherstellung](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Microsoft-Whitepaper für SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepaper SQL Server Kundenberatungs Teams](http://sqlcat.com/)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [AlwaysOn-Verfügbarkeitsgruppen: Interoperabilität (SQL Server)](always-on-availability-groups-interoperability-sql-server.md)   
 [Failoverclustering und AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Windows Server-Failoverclustering &#40;wsfc-&#41; mit SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [AlwaysOn-Failoverclusterinstanzen](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)  
  
