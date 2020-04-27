---
title: Einige synchrone Replikate wurden nicht synchronisiert | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2423a011e75d346d196ebe5ebac2597ac30914a1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62788260"
---
# <a name="some-synchronous-replicas-are-not-synchronized"></a>Einige synchrone Replikate wurden nicht synchronisiert
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|Datensynchronisierungsstatus synchroner Replikate|  
|**Problem**|Einige synchrone Replikate wurden nicht synchronisiert.|  
|**Kategorie**|**Warning**|  
|**Facet**|Verfügbarkeitsgruppe|  
  
## <a name="description"></a>Beschreibung  
 Diese Richtlinie führt ein Rollup des Datensynchronisierungsstatus aller Verfügbarkeitsreplikate sowie eine Überprüfung auf Verfügbarkeitsreplikate durch, die sich nicht im erwarteten Synchronisierungsstatus befinden. Die Richtlinie befindet sich in einem fehlerhaften Zustand, wenn eines der asynchronen Replikate nicht den Status SYNCHRONIZING aufweist und eines der synchronen Replikate nicht den Status SYNCHRONIZED aufweist. Andernfalls befindet sich die Richtlinie in einem ordnungsgemäßen Zustand.  
  
> [!NOTE]  
>  Für diese Version von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [Einige synchrone Replikate wurden nicht synchronisiert](https://go.microsoft.com/fwlink/p/?LinkId=220853) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 In dieser Verfügbarkeitsgruppe wird derzeit mindestens ein synchrones Replikat nicht synchronisiert. Der Synchronisierungsstatus des Replikats lautet entweder SYNCHRONIZING oder NOT SYNCHRONIZING.  
  
## <a name="possible-solution"></a>Mögliche Lösung  
 Verwenden Sie den Verfügbarkeitsreplikat-Richtlinienstatus, um nach dem Verfügbarkeitsreplikat mit dem fehlerhaften Synchronisierungsstatus zu suchen, und beheben Sie das Problem für das Verfügbarkeitsreplikat.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
