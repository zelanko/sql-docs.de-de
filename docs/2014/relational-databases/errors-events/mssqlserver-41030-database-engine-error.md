---
title: MSSQLSERVER_41030 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7f3514eea0d71d55332b4bfbdd4d3ee5fa08c702
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408860"
---
# <a name="mssqlserver41030"></a>MSSQLSERVER_41030
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41030|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|OPEN_CLUSTER_SUB_KEY|  
|Meldungstext|Fehler beim Öffnen des WSFC (Windows Server Failover Clustering)-Registrierungsunterschlüssels '%.*ls' (Fehlercode %d).  Der übergeordnete Schlüssel ist der Clusterstammschlüssel.  Der WSFC-Dienst wird möglicherweise nicht ausgeführt, der Zugriff auf den Dienst ist möglicherweise im aktuellen Zustand nicht möglich, oder die angegebenen Argumente sind ungültig. Wurde die entsprechende Verfügbarkeitsgruppe gelöscht, wird dieser Fehler erwartet. Informationen zu diesem Fehlercode finden Sie in der Dokumentation für die Windows-Entwicklung im Abschnitt zu Systemfehlercodes.|  
  
## <a name="explanation"></a>Erklärung  
 Wenn ein WSFC-Cluster zerstört wird, werden alle auf [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] bezogenen Registrierungsschlüssel entfernt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Nach dem Neuerstellen eines WSFC-Clusters deaktivieren und aktivieren Sie dann AlwaysOn auf jedem Clusterknoten erneut, auf dem eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz für AlwaysOn aktiviert wird. Sie können für diese Aufgabe den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren und Deaktivieren von AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)   
 [Windows Server-Failoverclustering &#40;WSFC&#41; mit SQL Server](../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
