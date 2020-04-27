---
title: Verfügbarkeitsgruppe ist offline | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp2online.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 093c5208-bf7a-49f4-a546-72b48197cadf
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 35d8f9cdda7c3b85c77d290f9c793640705438e9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62815423"
---
# <a name="availability-group-is-offline"></a>Verfügbarkeitsgruppe ist offline
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|Onlinezustand der Verfügbarkeitsgruppe|  
|**Problem**|Die Verfügbarkeitsgruppe ist offline.|  
|**Kategorie**|**Critical** (Kritisch)|  
|**Facet**|Verfügbarkeitsgruppe|  
  
## <a name="description"></a>Beschreibung  
 Diese Richtlinie überprüft den Online- oder Offlinestatus der Verfügbarkeitsgruppe. Die Richtlinie befindet sich in einem fehlerhaften Zustand, und eine Warnung wird ausgelöst, wenn die Clusterressource der Verfügbarkeitsgruppe offline ist oder wenn die Verfügbarkeitsgruppe nicht über ein primäres Replikat verfügt.  
  
 Der Zustand der Richtlinie ist fehlerfrei, wenn die Clusterressource der Verfügbarkeitsgruppe online ist und die Verfügbarkeitsgruppe über ein primäres Replikat verfügt.  
  
> [!NOTE]  
>   Für diese Version von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [Verfügbarkeitsgruppe ist offline](https://go.microsoft.com/fwlink/p/?LinkId=220850) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 Dieses Problem kann von einem Fehler in der Serverinstanz verursacht werden, die das primäre Replikat hostet, oder dadurch, dass die Windows Server-Failovercluster (WSFC)-Verfügbarkeitsgruppenressource offline geht. Im Folgenden sind mögliche Ursachen für den Offlinezustand der Verfügbarkeitsgruppe aufgeführt:  
  
-   Die Verfügbarkeitsgruppe ist nicht für den automatischen Failovermodus konfiguriert. Das primäre Replikat ist nicht mehr verfügbar, und alle Replikate in der Verfügbarkeitsgruppe nehmen den Status RESOLVING an.  
  
    -   Der Instanzdienst des primären Replikats ist ausgefallen oder reagiert nicht.  
  
    -   Für die Verfügbarkeitsgruppe besteht ein Problem bei der Verbindung zum Cluster.  
  
-   Die Verfügbarkeitsgruppe wurde mit automatischem Failovermodus konfiguriert und nicht erfolgreich abgeschlossen.  
  
    -   Während des automatischen Failovers tritt für die primäre Bereitschaftsüberprüfung auf dem Zielreplikat ein Fehler auf, und es ist kein Replikat verfügbar, das zum neuen primären Replikat werden kann.  
  
-   Die Verfügbarkeitsgruppenressource im Cluster ist offline.  
  
    -   In einer abhängigen Clusterressource tritt ein schwerwiegendes Problem auf, und die Ressource wird in den Offlinezustand versetzt. Die Verfügbarkeitsgruppenressource ist ebenfalls offline, bis die abhängige Ressource online geschaltet wird.  
  
    -   Durch ein schwerwiegendes Problem im Cluster wird die Verfügbarkeitsgruppenressource deaktiviert.  
  
-   Für die Verfügbarkeitsgruppe wird ein automatisches, manuelles oder erzwungenes Failover durchgeführt.  
  
## <a name="possible-solutions"></a>Mögliche Lösungen  
 Für dieses Problem gibt es die folgenden möglichen Lösungen:  
  
-   Wenn die SQL Server-Instanz des primären Replikats ausgefallen ist, starten Sie den Server neu, und überprüfen Sie dann, ob die Verfügbarkeitsgruppe wieder einen ordnungsgemäßen Zustand erreicht.  
  
-   Falls anscheinend für das automatische Failover ein Fehler aufgetreten ist, überprüfen Sie, ob die Datenbanken auf dem Replikat mit dem zuvor bekannten primären Replikat synchronisiert werden, und führen Sie dann das Failover auf das primäre Replikat durch. Falls die Datenbanken nicht synchronisiert werden, wählen Sie ein Replikat mit einem minimalen Datenverlust aus und stellen dann den Failovermodus wieder her.  
  
-   Falls die Ressource im Cluster offline ist, während die Instanzen von SQL Server anscheinend fehlerfrei sind, verwenden Sie den Failovercluster-Manager, um den Clusterzustand oder andere Clusterprobleme auf dem Server zu überprüfen. Sie können mit dem Failovercluster-Manager auch versuchen, die Verfügbarkeitsgruppenressource wieder in den Onlinezustand zu versetzen.  
  
-   Falls gerade ein Failover durchgeführt wird, warten Sie, bis das Failover abgeschlossen ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
