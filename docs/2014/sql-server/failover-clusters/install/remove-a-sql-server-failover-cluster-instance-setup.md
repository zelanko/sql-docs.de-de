---
title: Entfernen einer SQL Server-Failoverclusterinstanz (Setup) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], removing failover clustered instance
- failover clustering [SQL Server], removing failover clustered instance
- uninstalling failover clustered instances
- removing failover clustered instances
ms.assetid: bf63353b-69cf-4c5c-98ea-7b151e36537f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 07b57b7ebea8a2bf5eaf381c09d7eb29dd6a4cd4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63017029"
---
# <a name="remove-a-sql-server-failover-cluster-instance-setup"></a>Entfernen einer SQL Server-Failoverclusterinstanz (Setup)
  Verwenden Sie diese Prozedur, um eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failoverclusterinstanz zu deinstallieren.  
  
> [!IMPORTANT]  
>  Um einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster zu aktualisieren oder zu entfernen, müssen Sie ein lokaler Administrator mit der Berechtigung zum Anmelden als Dienst auf allen Knoten des Failoverclusters sein.  
  
 **Vorbereitungen**  
  
 Berücksichtigen Sie die folgenden wichtigen Punkte, bevor Sie einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster deinstallieren:  
  
-   Wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client versehentlich deinstalliert wurde, können die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressourcen nicht gestartet werden. Um [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zu installieren, führen Sie das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Setupprogramm aus, um die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Voraussetzungen zu installieren.  
  
-   Wenn Sie einen Failovercluster deinstallieren, der über mehr als eine SQL IP-Clusterressource verfügt, müssen Sie die zusätzlichen SQL IP-Ressourcen mithilfe der Clusterverwaltung entfernen.  
  
 Weitere Informationen zur eingabeaufforderungssyntax finden Sie unter [Installieren von SQL Server 2014 über die Eingabeaufforderung](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
### <a name="to-uninstall-a-includessnoversionincludesssnoversion-mdmd-failover-cluster"></a>So deinstallieren Sie einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster  
  
1.  Zur Deinstallation eines [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster verwenden Sie die vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Setup bereitgestellte Funktion Knoten entfernen, um jeden Knoten einzeln zu entfernen. Weitere Informationen finden Sie unter [Hinzufügen oder Entfernen von Knoten in einem SQL Server-Failovercluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
