---
title: Verfügbarkeitsreplikat hat keine fehlerfreie Rolle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp1rolehealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: ebb2c9f4-2097-4688-b4fb-8f0571047317
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c5d487965237395da68bbc8ba3134c8d372f90db
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62815597"
---
# <a name="availability-replica-does-not-have-a-healthy-role"></a>Verfügbarkeitsreplikat hat keine fehlerfreie Rolle
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|Verfügbarkeitsreplikat-Rollenstatus|  
|**Problem**|Das Verfügbarkeitsreplikat hat keine fehlerfreie Rolle.|  
|**Kategorie**|**Kritisch**|  
|**Facet**|Verfügbarkeitsreplikat|  
  
## <a name="description"></a>Description  
 Diese Richtlinie überprüft den Status der Verfügbarkeitsreplikatrolle. Die Richtlinie befindet sich in einem fehlerhaften Zustand, wenn die Rolle des Verfügbarkeitsreplikats weder primär noch sekundär ist. Die Richtlinie befindet sich andernfalls in einem ordnungsgemäßen Zustand.  
  
> [!NOTE]  
>  Für diese Version von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [Verfügbarkeitsreplikat hat keine fehlerfreie Rolle](https://go.microsoft.com/fwlink/p/?LinkId=220856) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 Die Rolle dieses Verfügbarkeitsreplikats ist fehlerhaft. Das Replikat hat nicht entweder die primäre oder sekundäre Rolle inne.  
  
## <a name="possible-solution-informationstilltocome"></a>Mögliche Lösung: Informationen_werden_noch_bereitgestellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
