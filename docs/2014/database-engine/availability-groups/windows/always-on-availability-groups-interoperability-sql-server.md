---
title: 'Always On-Verfügbarkeitsgruppen: Interoperabilität (SQL Server) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
caps.latest.revision: 18
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: e7a8ea0a461bb261b8a85769b0fe2048e6cc569c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159637"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a>Always On-Verfügbarkeitsgruppen: Interoperabilität (SQL Server)
  In diesem Thema wird die Interoperabilität von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] mit anderen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Funktionen in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]dokumentiert.  
  

  
##  <a name="Interop"></a> Funktionen, die mit AlwaysOn-Verfügbarkeitsgruppen Zusammenwirken  
 In der folgenden Tabelle sind [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Funktionen aufgeführt, die in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] mit [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]zusammenarbeiten. Ein Link in der Spalte **Weitere Informationen** weist darauf hin, dass zusätzliche Überlegungen zur Interoperabilität einer bestimmten Funktion vorhanden sind.  
  
|Funktion|Weitere Informationen|  
|-------------|----------------------|  
|Change Data Capture|[Replikation, Änderungsnachverfolgung, Change Data Capture und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|Änderungsnachverfolgung|[Replikation, Änderungsnachverfolgung, Change Data Capture und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](replicate-track-change-data-capture-always-on-availability.md)|  
|Eigenständige Datenbanken|[Eigenständige Datenbanken bei AlwaysOn-Verfügbarkeitsgruppen (SQLServer)](always-on-availability-groups-sql-server.md)|  
|Datenbankverschlüsselung|[Verschlüsselte Datenbanken bei AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|Datenbank-Momentaufnahmen|[Datenbankmomentaufnahmen bei AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|FILESTREAM und FileTable|[FILESTREAM und FileTable bei AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|Volltextsuche|Hinweis: Volltextindizes werden mit sekundären AlwaysOn-Datenbanken synchronisiert.|  
|Protokollversand|[Voraussetzungen für das Migrieren vom Protokollversand zu AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|Remote Blob Store (RBS)|[Remote Blob-Speicher &#40;RBS&#41; und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|Replikation[Konfigurieren der Replikation für AlwaysOn-Verfügbarkeitsgruppen (SQLServer)](configure-replication-for-always-on-availability-groups-sql-server.md)<br /><br /> [Warten einer AlwaysOn-Veröffentlichungsdatenbank &#40;SQLServer&#41;](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [Replikation, Änderungsnachverfolgung, Change Data Capture und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [Replikationsabonnenten und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|Analysis Services|[Analysis Services mit AlwaysOn-Verfügbarkeitsgruppen](analysis-services-with-always-on-availability-groups.md)|  
|Reporting Services|Verwenden Sie schreibgeschützte sekundäre Replikate als Berichtsdatenquelle, und reduzieren Sie die Last des primären Lese-/Schreibreplikats.<br /><br /> [Reporting Services mit AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|Service Broker|[Service Broker mit AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](service-broker-with-always-on-availability-groups-sql-server.md)|  
|SQL Server-Agent||  
  
##  <a name="NoInterop"></a> Funktionen, die nicht mit AlwaysOn-Verfügbarkeitsgruppen Zusammenwirken  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] funktioniert nicht in Verbindung mit folgenden Funktionen:  
  
-   Datenbankübergreifende Transaktionen/verteilte Transaktionen  
  
     Weitere Informationen dazu, warum solche Transaktionen nicht unterstützt werden, finden Sie unter [Datenbankübergreifende Transaktionen nicht unterstützt für Datenbankspiegelungs- oder AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).  
  
-   Datenbankspiegelung  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   **Blogs:**  
  
     [Migrationshandbuch: Migrieren zu SQL Server 2012-Failoverclustering und -Verfügbarkeitsgruppen von vorherigen Clustering- und Spiegelungsbereitstellungen](http://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [SQL Server AlwaysOn-Teamblogs: Der offizielle SQL Server AlwaysOn-Teamblog](http://blogs.msdn.com/b/sqlalwayson/)  
  
     
  [CSS SQL Server-Technikblogs](http://blogs.msdn.com/b/psssql/)  
  
-   **Whitepaper:**  
  
     [Migrationshandbuch: Migrieren zu AlwaysOn-Verfügbarkeitsgruppen von vorherigen Bereitstellungen, die Kombination von Datenbankspiegelung und Protokollversand](http://msdn.microsoft.com/library/jj635217)  
  
     [Microsoft SQL Server AlwaysOn-Lösungshandbuch für hohe Verfügbarkeit und Wiederherstellung im Notfall](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Microsoft-Whitepapers für SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepapers des SQL Server-Kundenberatungsteams](http://sqlcat.com/)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  