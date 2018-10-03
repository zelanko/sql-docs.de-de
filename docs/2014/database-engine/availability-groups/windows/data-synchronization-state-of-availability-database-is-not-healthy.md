---
title: Datensynchronisierungsstatus der Verfügbarkeitsdatenbank ist nicht fehlerfrei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1aa901fe3230a76af3127af41630b075414d77a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096874"
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy"></a>Datensynchronisierungsstatus der Verfügbarkeitsdatenbank ist nicht fehlerfrei
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|Datensynchronisierungsstatus der Verfügbarkeitsdatenbank|  
|**Problem**|Der Datensynchronisierungsstatus der Verfügbarkeitsdatenbank ist nicht fehlerfrei.|  
|**Kategorie**|**Warnung**|  
|**Facet**|Verfügbarkeitsdatenbank|  
  
## <a name="description"></a>Description  
 Diese Richtlinie führt ein Rollup des Datensynchronisierungsstatus aller Verfügbarkeitsdatenbanken (auch bekannt als "Datenbankreplikate") im Verfügbarkeitsreplikat aus. Die Richtlinie befindet sich in einem fehlerhaften Zustand, wenn ein beliebiges Datenbankreplikat nicht den erwarteten Datensynchronisierungsstatus aufweist. Die Richtlinie befindet sich andernfalls in einem ordnungsgemäßen Zustand.  
  
> [!NOTE]  
>  Für dieses Release von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [Datensynchronisierungsstatus einer Verfügbarkeitsdatenbank ist nicht fehlerfrei](http://go.microsoft.com/fwlink/p/?LinkId=220858) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 Der Datensynchronisierungsstatus dieser Verfügbarkeitsdatenbank ist fehlerhaft. Auf einem Verfügbarkeitsreplikat für asynchrone Commits sollte sich jede Verfügbarkeitsdatenbank im Status SYNCHRONIZING befinden. Auf einem Replikat für synchrone Commits muss sich jede Verfügbarkeitsdatenbank im Status SYNCHRONIZED befinden.  
  
## <a name="possible-solution"></a>Mögliche Lösung  
 Verwenden Sie die Datenbankreplikatrichtlinie zum Suchen nach dem Datenbankreplikat mit einem fehlerhaften Datensynchronisierungsstatus, und beheben Sie das Problem für das Datenbankreplikat.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
