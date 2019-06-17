---
title: WSFC-Clusterdienst ist offline | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp1WSFCquorum.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: d502548d-ece6-4a42-9ded-2157d33e3d21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cfab5de4cd3d171d4d8b7515e65b0a9cd117ac16
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62812898"
---
# <a name="wsfc-cluster-service-is-offline"></a>WSFC-Clusterdienst ist offline
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|WSFC-Clusterstatus|  
|**Problem**|Der WSFC-Clusterdienst ist offline.|  
|**Kategorie**|**Kritisch**|  
|**Facet**|SQL Server-Instanz|  
  
## <a name="description"></a>Description  
 Diese Richtlinie überprüft den Status des Windows Server-Failoverclusters (WSFC). Die Richtlinie befindet sich in einem fehlerhaften Zustand und löst eine Warnung aus, wenn der WSFC-Cluster offline ist oder sich im erzwungenen Quorumstatus befindet. Alle innerhalb dieses Clusters gehosteten Verfügbarkeitsgruppen sind offline, oder eine Notfallwiederherstellungsaktion ist erforderlich.  
  
 Der Richtlinienstatus ist fehlerfrei, wenn der Clusterstatus das normale Quorum aufweist.  
  
> [!NOTE]  
>  Für diese Version von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [WSFC-Clusterdienst ist offline](https://go.microsoft.com/fwlink/p/?LinkId=220849) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 Dieses Problem kann von einem Clusterdienstfehler oder aufgrund des Verlusts des Quorums im Cluster verursacht werden.  
  
## <a name="possible-solution"></a>Mögliche Lösung  
 Verwenden Sie das Clusterverwaltungstool, um den Workflow für das erzwungene Quorum oder für die Notfallwiederherstellung auszuführen. Falls Sie das Problem nicht beheben können, indem Sie den Workflow für das erzwungene Quorum oder die Notfallwiederherstellung ausführen, sollten Sie Ihren Clusteradministrator um Unterstützung bei der Lösung dieses Problems bitten. Weitere Informationen finden Sie unter: [Erzwingen des Starts eines Clusters ohne Quorum](../../../sql-server/failover-clusters/windows/force-a-wsfc-cluster-to-start-without-a-quorum.md) in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
