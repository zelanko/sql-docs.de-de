---
title: Konfiguration einer Serverinstanz für Always On-Verfügbarkeitsgruppen (SQLServer) | Microsoft-Dokumentation
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
ms.openlocfilehash: d8c9aa465237010ff48881a2df176de6d067da0c
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53374232"
---
# <a name="configuration-of-a-server-instance-for-always-on-availability-groups-sql-server"></a>Konfiguration einer Serverinstanz für Always On-Verfügbarkeitsgruppen (SQL Server)
  Dieses Thema enthält Informationen zu den Anforderungen für die Konfiguration einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zur Unterstützung von AlwaysOn-Verfügbarkeitsgruppen[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
> [!IMPORTANT]  
>  Wichtige Informationen zu erforderlichen [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]-Komponenten und Einschränkungen für WSFC-Knoten (Windows Server-Failoverclustering) und für Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] finden Sie unter [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
 
  
##  <a name="TermsAndDefinitions"></a> Begriffe und Definitionen  
  
 Eine Lösung für hohe Verfügbarkeit und Notfallwiederherstellung, die als Ersatz für die Datenbankspiegelung auf Unternehmensebene verwendet werden kann. Eine *Verfügbarkeitsgruppe* unterstützt eine Failoverumgebung für einen diskreten Satz von Benutzerdatenbanken (als *Verfügbarkeitsdatenbanken*bezeichnet), die zusammen ein Failover ausführen.  
  
 Verfügbarkeitsreplikat  
 Eine Instanziierung einer Verfügbarkeitsgruppe, die von einer bestimmten Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gehostet wird und eine lokale Kopie jeder Verfügbarkeitsdatenbank beibehält, die zur Verfügbarkeitsgruppe gehört. Zwei Typen von Verfügbarkeitsreplikaten sind vorhanden: ein einzelnes *primäres Replikat* und ein bis vier *sekundäre Replikate*. Die Serverinstanzen, die die Verfügbarkeitsreplikate für eine angegebene Verfügbarkeitsgruppe hosten, müssen sich auf verschiedenen Konten eines einzelnen WSFC-Clusters (Windows Server-Failoverclustering) befinden.  
  
 [Datenbank-Spiegelungsendpunkt](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
 Ein Endpunkt ist ein SQL Server-Objekt, mit dessen Hilfe SQL Server über das Netzwerk kommunizieren kann. Um an einer Datenbankspiegelung und/oder [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] teilnehmen zu können, ist für eine Serverinstanz ein spezieller, dedizierter Endpunkt erforderlich. Alle Spiegelungs- und Verfügbarkeitsgruppenverbindungen auf einer Serverinstanz verwenden denselben Datenbankspiegelungs-Endpunkt. Dieser Endpunkt ist ein auf einen bestimmten Zweck ausgerichteter Endpunkt, der ausschließlich dafür verwendet wird, diese Verbindungen von anderen Serverinstanzen zu empfangen.  
  
##  <a name="ConfigSI"></a> So konfigurieren Sie eine Serverinstanz zur Unterstützung von AlwaysOn-Verfügbarkeitsgruppen  
 Um [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]zu unterstützen, muss sich eine Serverinstanz in einem Knoten im WSFC-Failovercluster befinden, der die Verfügbarkeitsgruppe hostet. Sie muss [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -aktiviert sein und über einen Datenbankspiegelungs-Endpunkt verfügen.  
  
1.  Aktivieren Sie die Funktion AlwaysOn-Verfügbarkeitsgruppen auf jeder Serverinstanz, die an einer oder mehreren Verfügbarkeitsgruppen teilnehmen soll. Eine bestimmte Serverinstanz kann nur ein einzelnes Verfügbarkeitsreplikat für eine bestimmte Verfügbarkeitsgruppe hosten.  
  
2.  Stellen Sie sicher, dass die Serverinstanz einen Datenbankspiegelungs-Endpunkt besitzt.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So aktivieren Sie AlwaysOn-Verfügbarkeitsgruppen**  
  
-   [Aktivieren und Deaktivieren von Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **So bestimmen Sie, ob ein Datenbankspiegelungs-Endpunkt vorhanden ist**  
  
-   [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
 **So erstellen Sie einen Datenbankspiegelungs-Endpunkt**  
  
-   [Erstellen Sie eine Datenbank mit dem Datenbankspiegelungs-Endpunkts für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Erstellen eines Endpunkts der Datenbankspiegelung für Windows-Authentifizierung &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Ermöglichen des Verwendens von Zertifikaten für ausgehende Verbindungen für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   **Blogs:**  
  
     [AlwaysON - HADRON-Lernreihe: Nutzung des Arbeitsthreadpools für HADRON-fähige Datenbanken](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [SQL Server AlwaysOn-Teamblogs: Der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server-Technikblogs](https://blogs.msdn.com/b/psssql/)  
  
-   **Videos:**  
  
     [Microsoft SQL Server Codename "Denali" AlwaysOn-Reihe, Teil 1: Einführung in die nächste Generation von Lösungen mit Hochverfügbarkeit](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server Codename "Denali" AlwaysOn-Reihe, Teil 2: Erstellen einer Lösung für unternehmenskritische hohe Verfügbarkeit mit AlwaysOn](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Whitepaper:**  
  
     [Microsoft SQL Server AlwaysOn-Lösungshandbuch für hohe Verfügbarkeit und Notfallwiederherstellung](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Microsoft-Whitepapers für SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepapers des SQL Server-Kundenberatungsteams](http://sqlcat.com/)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [AlwaysOn-Verfügbarkeitsgruppen: Interoperabilität (SQLServer)](always-on-availability-groups-interoperability-sql-server.md)   
 [Failoverclustering und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Windows Server-Failoverclustering &#40;WSFC&#41; mit SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [AlwaysOn-Failoverclusterinstanzen](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)  
  
  
