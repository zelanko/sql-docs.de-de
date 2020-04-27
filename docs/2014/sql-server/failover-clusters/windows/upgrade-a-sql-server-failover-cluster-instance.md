---
title: Aktualisieren eines SQL Server-Failoverclusters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a7a8d5f04808582bd56c106adce0df2c1f66aa77
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62913696"
---
# <a name="upgrade-a-sql-server-failover-cluster"></a>Aktualisieren eines SQL Server-Failoverclusters
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt ein separates Upgrade von [!INCLUDE[ssDE](../../../includes/ssde-md.md)] und [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] auf allen Failoverclusterknoten unter [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] und [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 Informationen zur Unterstützung:  
  
-   Das Upgrade kann sowohl über die Benutzeroberfläche als auch an der Eingabeaufforderung ausgeführt werden. Weitere Informationen finden Sie unter [Aktualisieren einer SQL Server-Failoverclusterinstanz &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) und [Installieren von SQL Server 2014 von der Eingabeaufforderung](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
-   Upgrade von [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] : Sie können ein Upgrade über die Eingabeaufforderung auf jedem Failoverclusterknoten ausführen oder über die Setup Benutzeroberfläche ein Upgrade für die einzelnen Cluster Knoten ausführen. Wenn die Volltextsuche und Replikationsfunktionen auf der zu aktualisierenden Instanz nicht vorhanden sind, werden sie automatisch und obligatorisch installiert.  
  
-   Installation der Service Packs: Sie müssen die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service Packs und Patches für [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]-Failovercluster auf allen Knoten einzeln anwenden.  
  
-   Folgende Szenarios werden nicht unterstützt:  
  
    -   Sie können nicht von einer eigenständigen Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zu einem Failovercluster migrieren.  
  
    -   Fügen Sie einem Failovercluster Funktionen hinzu. Beispielsweise können Sie einem vorhandenen Nur- [!INCLUDE[ssDE](../../../includes/ssde-md.md)] -Failovercluster nicht [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]hinzufügen.  
  
    -   Sie können Failoverclusterknoten nicht zu einer eigenständigen Instanz herabstufen.  
  
-   Weitere Informationen finden Sie unter [ Always On-Failoverclusterinstanzen (SQL Server)](always-on-failover-cluster-instances-sql-server.md).  
  
## <a name="upgrading-a-ssnoversion-multi-subnet-failover-cluster"></a>Aktualisieren eines [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Multisubnetz-Failoverclusters  
 Ein nicht-multisubnetz [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster kann nicht direkt auf einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] multisubnetz-Failovercluster aktualisiert werden. Weitere Informationen finden Sie unter [Aktualisieren einer SQL Server-Failoverclusterinstanz &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützte Versions-und Editions Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Aktualisieren einer SQL Server-Failoverclusterinstanz &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md)   
 [Installieren von SQL Server 2014 von der Eingabeaufforderung](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
  
