---
title: Verfügbarkeitsgruppe nicht bereit für automatisches Failover | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp3autofailover.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 28261014-342c-442a-bd89-6d04b8d4e8b7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a9a7bdca770bccaac50da1ac6a7688eabd335e20
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62791864"
---
# <a name="availability-group-is-not-ready-for-automatic-failover"></a>Verfügbarkeitsgruppe nicht bereit für automatischen Failover
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|Bereitschaft der Verfügbarkeitsgruppe für automatisches Failover|  
|**Problem**|Die Verfügbarkeitsgruppe ist nicht für das automatische Failover bereit.|  
|**Kategorie**|**Critical** (Kritisch)|  
|**Facet**|Verfügbarkeitsgruppe|  
  
## <a name="description"></a>BESCHREIBUNG  
 Diese Richtlinie überprüft, ob die Verfügbarkeitsgruppe über mindestens ein sekundäres Replikat verfügt, das bereit für das Failover ist. Die Richtlinie befindet sich in einem fehlerhaften Zustand, und es wird eine Warnung ausgelöst, wenn für das primäre Replikat der automatische Failovermodus aktiviert ist, aber keines der sekundären Replikate in der Verfügbarkeitsgruppe für das Failover bereit ist.  
  
 Die Richtlinie befindet sich in einem ordnungsgemäßen Zustand, wenn mindestens ein sekundäres Replikat bereit für das automatische Failover ist.  
  
> [!NOTE]  
>  Für diese Version von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [Verfügbarkeitsgruppe nicht bereit für automatischen Failover](https://go.microsoft.com/fwlink/p/?LinkId=220851) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 Die Verfügbarkeitsgruppe ist nicht für das automatische Failover bereit. Das primäre Replikat wurde für das automatische Failover konfiguriert. Das sekundäre Replikat ist jedoch nicht für das automatische Failover bereit. Das sekundäre Replikat, das für automatisches Failover konfiguriert wurde, ist ggf. nicht verfügbar, oder dessen Datensynchronisierungsstatus lautet derzeit SYNCHRONIZED.  
  
## <a name="possible-solutions"></a>Mögliche Lösungen  
 Für dieses Problem gibt es die folgenden möglichen Lösungen:  
  
-   Stellen Sie sicher, dass mindestens ein sekundäres Replikat für automatisches Failover konfiguriert ist. Falls kein sekundäres Replikat für automatisches Failover konfiguriert ist, aktualisieren Sie die Konfiguration eines sekundären Replikats, sodass es als Ziel für das automatische Failover mit synchronem Commit dient.  
  
-   Überprüfen Sie anhand der Richtlinie, ob die Daten einen Synchronisierungsstatus aufweisen und ob das Ziel für das automatische Failover SYNCHRONIZED lautet. Beheben Sie dann das Problem des Verfügbarkeitsreplikats.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden Sie das AlwaysOn-Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
