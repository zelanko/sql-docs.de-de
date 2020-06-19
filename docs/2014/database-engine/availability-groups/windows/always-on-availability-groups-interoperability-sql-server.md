---
title: 'Always On-Verfügbarkeitsgruppen: Interoperabilität (SQL Server) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 55e19c050d0dd5d0a07c12f88076c423ade3281a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937212"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a>Always On-Verfügbarkeitsgruppen: Interoperabilität (SQL Server)
  In diesem Thema wird die Interoperabilität von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] mit anderen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Funktionen in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]dokumentiert.  
  

  
##  <a name="features-that-interoperate-with-alwayson-availability-groups"></a><a name="Interop"></a>Funktionen, die mit AlwaysOn-Verfügbarkeitsgruppen zusammenarbeiten  
 In der folgenden Tabelle sind [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Funktionen aufgeführt, die in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] mit [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]zusammenarbeiten. Ein Link in der Spalte **Weitere Informationen** weist darauf hin, dass zusätzliche Überlegungen zur Interoperabilität einer bestimmten Funktion vorhanden sind.  
  
|Funktion|Weitere Informationen|  
|-------------|----------------------|  
|Erfassung geänderter Daten|[Replikation, Änderungsnachverfolgung, Change Data Capture und AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|Änderungsnachverfolgung|[Replikation, Änderungsnachverfolgung, Change Data Capture und AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|Eigenständige Datenbanken|[Eigenständige Datenbanken bei AlwaysOn-Verfügbarkeitsgruppen (SQL Server)](always-on-availability-groups-sql-server.md)|  
|Datenbankverschlüsselung|[Verschlüsselte Datenbanken mit AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|Datenbank-Momentaufnahmen|[Daten Bank Momentaufnahmen mit AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|FILESTREAM und FileTable|[FILESTREAM und FILETABLE mit AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|Volltextsuche|Hinweis: Volltextindizes werden mit sekundären AlwaysOn-Datenbanken synchronisiert.|  
|Protokollversand|[Voraussetzungen für das Migrieren vom Protokoll Versand zu AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|Remote Blob Store (RBS)|[Remote BLOB-Speicher &#40;RBS&#41; und AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|Replikation[Konfigurieren der Replikation für AlwaysOn-Verfügbarkeitsgruppen (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)<br /><br /> [Warten einer AlwaysOn-Veröffentlichungs Datenbank &#40;SQL Server&#41;](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [Replikation, Änderungsnachverfolgung, Change Data Capture und AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [Replikations Abonnenten und AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|Analysis Services|[Analysis Services mit AlwaysOn-Verfügbarkeitsgruppen](analysis-services-with-always-on-availability-groups.md)|  
|Reporting Services|Verwenden Sie schreibgeschützte sekundäre Replikate als Berichtsdatenquelle, und reduzieren Sie die Last des primären Lese-/Schreibreplikats.<br /><br /> [Reporting Services mit AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|Service Broker|[Service Broker mit AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](service-broker-with-always-on-availability-groups-sql-server.md)|  
|SQL Server-Agent||  
  
##  <a name="features-that-do-not-interoperate-with-alwayson-availability-groups"></a><a name="NoInterop"></a>Funktionen, die nicht mit AlwaysOn-Verfügbarkeitsgruppen zusammenarbeiten  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] funktioniert nicht in Verbindung mit folgenden Funktionen:  
  
-   Datenbankübergreifende Transaktionen/verteilte Transaktionen  
  
     Weitere Informationen dazu, warum solche Transaktionen nicht unterstützt werden, finden Sie unter [Datenbankübergreifende Transaktionen nicht unterstützt für Datenbankspiegelungs- oder AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).  
  
-   Datenbankspiegelung  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte  
  
-   **Blogs:**  
  
     [Migrationshandbuch: Migrieren zu SQL Server 2012-Failoverclustering und -Verfügbarkeitsgruppen von vorherigen Clustering- und Spiegelungsbereitstellungen](https://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [SQL Server AlwaysOn-Teamblogs: Der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server-Technikblogs](https://blogs.msdn.com/b/psssql/)  
  
-   **Whitepaper:**  
  
     [Migrationshandbuch: Migrieren zu AlwaysOn-Verfügbarkeitsgruppen von vorherigen Bereitstellungen, in denen Datenbankspiegelung und Protokollversand kombiniert sind](https://msdn.microsoft.com/library/jj635217)  
  
     [Microsoft SQL Server AlwaysOn-Lösungshandbuch zu hoher Verfügbarkeit und Notfallwiederherstellung](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Microsoft-Whitepapers für SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepapers des SQL Server-Kundenberatungsteams](http://sqlcat.com/)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
