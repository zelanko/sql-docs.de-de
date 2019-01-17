---
title: Verfügbarkeitsreplikat hat keine fehlerfreie Rolle für eine Verfügbarkeitsgruppe
description: Identifizieren Sie mögliche Ursachen dafür, warum ein Replikat keine fehlerfreie Rolle innerhalb einer Always On-Verfügbarkeitsgruppe hat.
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.arp1rolehealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: ebb2c9f4-2097-4688-b4fb-8f0571047317
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9d072fc8664163e5b2a0a175a90cb0c13fe3495e
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53204269"
---
# <a name="availability-replica-does-not-have-a-healthy-role-for-an-always-on-availability-group"></a>Verfügbarkeitsreplikat hat keine fehlerfreie Rolle für eine Always On-Verfügbarkeitsgruppe
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|Verfügbarkeitsreplikat-Rollenstatus|  
|**Problem**|Das Verfügbarkeitsreplikat hat keine fehlerfreie Rolle.|  
|**Kategorie**|**Kritisch**|  
|**Facet**|Verfügbarkeitsreplikat|  
  
## <a name="description"></a>und Beschreibung  
 Diese Richtlinie überprüft den Status der Verfügbarkeitsreplikatrolle. Die Richtlinie befindet sich in einem fehlerhaften Zustand, wenn die Rolle des Verfügbarkeitsreplikats weder primär noch sekundär ist. Die Richtlinie befindet sich andernfalls in einem ordnungsgemäßen Zustand.  
  
> [!NOTE]  
>  Für diese Version von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [Verfügbarkeitsreplikat hat keine fehlerfreie Rolle](https://go.microsoft.com/fwlink/p/?LinkId=220856) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 Die Rolle dieses Verfügbarkeitsreplikats ist fehlerhaft. Das Replikat hat nicht entweder die primäre oder sekundäre Rolle inne.  
  
## <a name="possible-solution-informationstilltocome"></a>Mögliche Lösung: Informationen_werden_noch_bereitgestellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
