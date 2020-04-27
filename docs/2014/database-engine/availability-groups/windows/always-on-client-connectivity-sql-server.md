---
title: Always On-Clientkonnektivität (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], client connectivity
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d8a1b81d60ef691e02d4b69cc71fa961bbaddf18
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67793435"
---
# <a name="always-on-client-connectivity-sql-server"></a>Always On-Clientkonnektivität (SQL Server)
  In diesem Thema werden Überlegungen zur Clientkonnektivität für AlwaysOn-Verfügbarkeitsgruppen beschrieben, einschließlich Voraussetzungen, Einschränkungen und Empfehlungen für Clientkonfigurationen und Einstellungen.  
  
 
  
##  <a name="client-connectivity-support"></a><a name="ClientConnSupport"></a>Unterstützung für Client Konnektivität  
 Der folgende Abschnitt enthält Informationen zur [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Unterstützung für Clientverbindungen.  
  
 **Treiberunterstützung**  
  
 In der folgenden Tabelle ist die Treiberunterstützung für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]zusammengefasst:  
  
|Treiber|Multisubnetz-Failover|Application Intent|Schreibgeschütztes Routing|Multisubnetz-Failover: Schnelleres Endpunktfailover in einzelnen Subnetzen|Multisubnetz-Failover: Auflösung benannter Instanzen für SQL-Clusterinstanzen|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|Ja|Ja|Ja|Ja|Ja|  
|SQL Native Client 11.0 OLEDB|Nein |Ja|Ja|Nein|Nein|  
|ADO.net mit .NET Framework 4,0 mit konnektivitätspatch**<sup>*</sup>** |Ja|Ja|Ja|Ja|Ja|  
|ADO.net mit .NET Framework 3,5 SP1 mit konnektivitätspatch**<sup>**</sup>** |Ja|Ja|Ja|Ja|Ja|  
|Microsoft JDBC-Treiber 4.0 für SQL Server|Ja|Ja|Ja|Ja|Ja|  
  
 **<sup>*</sup>** Laden Sie den konnektivitätspatch für ADO .net [https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211)mit .NET Framework 4,0: herunter.  
  
 **<sup>**</sup>* * Laden Sie das konnektivitätspatch für ADO.net mit [https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347).NET Framework 3,5 SP1: herunter.  
  
> [!IMPORTANT]  
>  Ein Client muss eine TCP-Verbindungszeichenfolge verwenden, um eine Verbindung mit einem Verfügbarkeitsgruppenlistener herzustellen.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellung und Konfiguration von Verfügbarkeitsgruppen &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [Erstellen oder konfigurieren Sie einen verfügbarkeitsgruppenlistener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  

  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Failoverclustering und AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Verfügbarkeitsgruppenlistener, Client Konnektivität und Anwendungs Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [Informationen zum Clientverbindungszugriff auf Verfügbarkeitsreplikate &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md)   
 [Microsoft SQL Server AlwaysOn-Lösungs Handbuch zu hoher Verfügbarkeit und Notfall Wiederherstellung](https://go.microsoft.com/fwlink/?LinkId=227600)   
 [SQL Server AlwaysOn-Teamblog: der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)   
 [Eine lange Verzögerung tritt auf, wenn Sie eine IPSec-Verbindung von einem Computer wiederherstellen, auf dem Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7 oder Windows Server 2008 R2 ausgeführt wird.](https://support.microsoft.com/kb/980915)   
 [Der Clusterdienst benötigt ungefähr 30 Sekunden für ein Failover von IPv6-IP-Adressen in Windows Server 2008 R2.](https://support.microsoft.com/kb/2578113)   
 [Langsamer Failovervorgang, wenn kein Router zwischen dem Cluster und einem Anwendungsserver vorhanden ist](https://support.microsoft.com/kb/2582281)  
  
  
