---
title: Überwachen von Verfügbarkeitsgruppen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 1d5e3291-0d0a-45a1-88e5-1fc242d17210
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8080c3d0825104019f1e3156d39348b5676d8159
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257446"
---
# <a name="monitoring-of-availability-groups-sql-server"></a>Überwachen von Verfügbarkeitsgruppen (SQL Server)
  Zum Überwachen der Eigenschaften und des Status einer AlwaysOn-Verfügbarkeitsgruppe können Sie die folgenden Tools verwenden.  
  
|Tool|Kurze Beschreibung|Links|  
|----------|-----------------------|-----------|  
|Systemcenter-Überwachungspaket für SQL Server|Das Überwachungspaket für SQL Server (SQLMP) ist die empfohlene Lösung, mit der IT-Administratoren Verfügbarkeitsgruppen sowie Verfügbarkeitsreplikate und Verfügbarkeitsdatenbanken überwachen. Die auf [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] abgestimmten Überwachungsfunktionen umfassen:<br /><br /> Automatische Erkennung von Verfügbarkeitsgruppen, Verfügbarkeitsreplikaten und Verfügbarkeitsdatenbank unter Hunderten von Computern. Dies ermöglicht Ihnen die einfache Nachverfolgung des [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Inventars.<br /><br /> Umfassende Warnungs- und Tickererstellungsfunktionen durch den System Center Operations Manager (SCOM). Diese Funktionen liefern detaillierte Informationen zur schnelleren Behebung eines Problems.<br /><br /> Eine benutzerdefinierte Erweiterung der AlwaysOn-Systemüberwachung unter Verwendung der richtlinienbasierten Verwaltung.<br /><br /> Integritätsrollups von Verfügbarkeitsdatenbanken auf Verfügbarkeitsreplikate.<br /><br /> Benutzerdefinierte Aufgaben zur Verwaltung von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] über die System Center Operations Manager-Konsole.|Hier können Sie das Überwachungspaket (SQLServerMP.msi) und das *SQL Server Management Pack-Handbuch für System Center Operations Manager* (SQLServerMPGuide.doc) herunterladen:<br /><br /> [Systemcenter-Überwachungspaket für SQL Server](http://www.microsoft.com/download/details.aspx?displaylang=en&id=10631)|  
|[!INCLUDE[tsql](../../../includes/tsql-md.md)]|[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Katalog und dynamische Verwaltungssichten stellen zahlreiche Informationen zu den Verfügbarkeitsgruppen und deren Replikaten, Datenbanken, Listenern und zur WSFC-Clusterumgebung bereit.|[Überwachen von Verfügbarkeitsgruppen &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|Der Bereich **Details zum Objekt-Explorer** zeigt grundlegende Informationen zu den Verfügbarkeitsgruppen an, die auf der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gehostet werden, mit der eine Verbindung besteht.<br /><br /> Tipp: Verwenden Sie diesen Bereich, um mehrere Verfügbarkeitsgruppen, Replikate oder Datenbanken auszuwählen und routinemäßige administrative Aufgaben auf den ausgewählten Objekten auszuführen, beispielsweise das Entfernen von mehreren Verfügbarkeitsreplikaten oder Datenbanken aus einer Verfügbarkeitsgruppe.|[Verwenden der Details zum Objekt-Explorer zum Überwachen von Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|**Eigenschaftendialogfelder** ermöglichen es, die Eigenschaften von Verfügbarkeitsgruppen, Replikaten oder Listenern anzuzeigen und, in einigen Fällen, deren Werte zu ändern.|[Anzeigen von Verfügbarkeitsgruppeneigenschaften &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md)<br /><br /> [Anzeigen von Verfügbarkeitsreplikateigenschaften &#40;SQL Server&#41;](view-availability-replica-properties-sql-server.md)<br /><br /> [Anzeigen von Eigenschaften des Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](view-availability-group-listener-properties-sql-server.md)|  
|Systemmonitor|Das Leistungsobjekt **SQL Server:Verfügbarkeitsreplikat** enthält Leistungsindikatoren, die Informationen zu Verfügbarkeitsreplikaten bereitstellen.|[SQL Server, Verfügbarkeitsreplikat](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)|  
|Systemmonitor|Das Leistungsobjekt **SQL Server:Datenbankreplikat** beinhaltet Leistungsindikatoren, die Informationen zu den sekundären Verfügbarkeitsdatenbanken eines bestimmten sekundären Replikats bereitstellen.<br /><br /> Das **SQLServer:Databases** -Objekt in SQL Server enthält u. a. Leistungsindikatoren zum Überwachen von Transaktionsprotokollaktivitäten. Die folgenden Indikatoren sind besonders für die Überwachung der Transaktionsprotokollaktivität von Verfügbarkeitsdatenbanken relevant: **Schreibdauer für Protokollleerungen (ms)**, **Protokollleerungen/Sekunde**, **Protokollpool-Cachefehlversuche/Sekunde**, **Protokollpool-Lesevorgänge auf dem Datenträger/Sekunde**und **Protokollpoolanforderungen/Sekunde**.|[SQL Server, Datenbankreplikat](../../../relational-databases/performance-monitor/sql-server-database-replica.md) und [SQL Server, Datenbank-Objekt](../../../relational-databases/performance-monitor/sql-server-databases-object.md)|  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   **Blogs:**  
  
     [Das AlwaysOn-Zustandsmodell Teil 1 – Zustandsmodellarchitektur](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/09/overview-of-the-alwayson-manageability-health-model.aspx)  
  
     [Das AlwaysOn-Zustandsmodell Teil 2 – Erweitern des Zustandsmodells](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx)  
  
     [Überwachen von AlwaysOn-Zustands mit PowerShell – Teil 1: Übersicht über grundlegende Cmdlets](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-1.aspx)  
  
     [Überwachen von AlwaysOn-Zustands mit PowerShell – Teil 2: Verwendung erweiterter Cmdlets](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-2.aspx)  
  
     [Überwachen von AlwaysOn-Zustands mit PowerShell – Teil 3: eine einfache Überwachungsanwendung](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/monitoring-alwayson-health-with-powershell-part-3.aspx)  
  
     [Überwachen von AlwaysOn-Zustands mit PowerShell – Teil 4: Integration in SQL Server-Agent](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/the-always-on-health-model-part-4.aspx)  
  
     [SQL Server AlwaysOn-Teamblogs: Der offizielle SQL Server AlwaysOn-Teamblog](http://blogs.msdn.com/b/sqlalwayson/)  
  
     
  [CSS SQL Server-Technikblogs](http://blogs.msdn.com/b/psssql/)  
  
-   **Whitepaper:**  
  
     [Microsoft-Whitepapers für SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepapers des SQL Server-Kundenberatungsteams](http://sqlcat.com/)  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten AlwaysOn-Verfügbarkeitsgruppen &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql)   
 [AlwaysOn-Verfügbarkeitsgruppen dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions)   
 [Flexible Failoverrichtlinie für automatisches Failover einer Verfügbarkeitsgruppe (SQL Server)](flexible-automatic-failover-policy-availability-group.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Automatische Seitenreparatur &#40;für Verfügbarkeitsgruppen und Datenbankspiegelung&#41;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
