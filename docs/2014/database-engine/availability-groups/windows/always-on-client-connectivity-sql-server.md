---
title: Always On-Clientkonnektivität (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], client connectivity
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
caps.latest.revision: 19
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: 40025093ad9293b436893c41a9e3fa44f731ab01
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058769"
---
# <a name="always-on-client-connectivity-sql-server"></a>Always On-Clientkonnektivität (SQL Server)
  In diesem Thema werden Überlegungen zur Clientkonnektivität für AlwaysOn-Verfügbarkeitsgruppen beschrieben, einschließlich Voraussetzungen, Einschränkungen und Empfehlungen für Clientkonfigurationen und Einstellungen.  
  
 
  
##  <a name="ClientConnSupport"></a> Unterstützung für Clientkonnektivität  
 Der folgende Abschnitt enthält Informationen zur [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Unterstützung für Clientverbindungen.  
  
 **Treiberunterstützung**  
  
 In der folgenden Tabelle ist die Treiberunterstützung für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]zusammengefasst:  
  
|Treiber|Multisubnetz-Failover|Application Intent|Schreibgeschütztes Routing|Multisubnetz-Failover: Schnelleres Endpunktfailover in einzelnen Subnetzen|Multisubnetz-Failover: Auflösung benannter Instanzen für SQL-Clusterinstanzen|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|ja|ja|ja|ja|ja|  
|SQL Native Client 11.0 OLEDB|nein|ja|ja|nein|nein|  
|ADO.NET mit .NET Framework 4.0 mit konnektivitätspatch**<sup>*</sup>**|ja|ja|ja|ja|ja|  
|ADO.NET mit .NET Framework 3.5 SP1 mit konnektivitätspatch **<sup>**</sup>**|ja|ja|ja|ja|ja|  
|Microsoft JDBC-Treiber 4.0 für SQL Server|ja|ja|ja|ja|ja|  
  
 **<sup>*</sup>**  Download des konnektivitätspatches für ADO.NET mit .NET Framework 4.0: [ http://support.microsoft.com/kb/2600211 ](http://support.microsoft.com/kb/2600211).  
  
 **<sup>**</sup>** Laden Sie das konnektivitätspatch für ADO.NET mit .NET Framework 3.5 SP1: [ http://support.microsoft.com/kb/2654347 ](http://support.microsoft.com/kb/2654347).  
  
> [!IMPORTANT]  
>  Ein Client muss eine TCP-Verbindungszeichenfolge verwenden, um eine Verbindung mit einem Verfügbarkeitsgruppenlistener herzustellen.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellung und Konfiguration von Verfügbarkeitsgruppen &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  

  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Failoverclustering und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Verfügbarkeitsgruppenlistener, Clientkonnektivität und Anwendungsfailover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [Informationen zum Clientverbindungszugriff auf Verfügbarkeitsreplikate &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md)   
 [Microsoft SQL Server AlwaysOn-Lösungshandbuch für hohe Verfügbarkeit und Wiederherstellung im Notfall](http://go.microsoft.com/fwlink/?LinkId=227600)   
 [SQL Server AlwaysOn-Teamblog: Der offizielle SQL Server AlwaysOn-Teamblog](http://blogs.msdn.com/b/sqlalwayson/)   
 [Eine lange Verzögerung tritt auf, wenn Sie eine IPSec-Verbindung von einem Computer verbinden, auf dem Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7 oder Windows Server 2008 R2 ausgeführt wird](http://support.microsoft.com/kb/980915)   
 [Der Clusterdienst dauert ungefähr 30 Sekunden zum Failover von IPv6-IP-Adressen in Windows Server 2008 R2](http://support.microsoft.com/kb/2578113)   
 [Langsamer Failovervorgang, wenn kein Router zwischen dem Cluster und einem Anwendungsserver vorhanden ist](http://support.microsoft.com/kb/2582281)  
  
  