---
title: Verfügbarkeitsreplikat wird getrennt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp2connected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 1a2162d3-54fb-4356-b349-effbdc15a5a4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 51004cf91b039ccdd83eda91425b3aea0764d237
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937069"
---
# <a name="availability-replica-is-disconnected"></a>Verfügbarkeitsreplikat wird getrennt
    
## <a name="introduction"></a>Einführung  
  
|||  
|-|-|  
|**Richtlinienname**|Verfügbarkeitsreplikat-Verbindungsstatus|  
|**Problem**|Das Verfügbarkeitsreplikat wird getrennt.|  
|**Kategorie**|**Critical** (Kritisch)|  
|**Facet**|Verfügbarkeitsreplikat|  
  
## <a name="description"></a>Beschreibung  
 Diese Richtlinie überprüft den Verbindungsstatus zwischen Verfügbarkeitsreplikaten. Die Richtlinie befindet sich in einem fehlerhaften Zustand, wenn der Verbindungsstatus des Verfügbarkeitsreplikats DISCONNECTED lautet. Die Richtlinie befindet sich andernfalls in einem ordnungsgemäßen Zustand.  
  
> [!NOTE]  
>   Für diese Version von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]finden Sie Informationen zu möglichen Ursachen und Lösungen im TechNet Wiki unter [Verfügbarkeitsreplikat wird getrennt](https://go.microsoft.com/fwlink/p/?LinkId=220857) .  
  
## <a name="possible-causes"></a>Mögliche Ursachen  
 Das sekundäre Replikat ist nicht mit dem primären Replikat verbunden. Der Verbindungsstatus lautet DISCONNECTED. Dieses Problem kann folgende Ursachen haben:  
  
-   Für den Verbindungsport besteht ein Konflikt mit einer anderen Anwendung.  
  
-   Der Verschlüsselungstyp oder der Algorithmus stimmt nicht überein.  
  
-   Der Verbindungsendpunkt wurde gelöscht oder nicht gestartet.  
  
-   Die Verbindung des Transports wurde getrennt.  
  
## <a name="possible-solutions"></a>Mögliche Lösungen  
 Für dieses Problem gibt es die folgenden möglichen Lösungen:  
  
-   Überprüfen Sie die Datenbankspiegelungs-Endpunktkonfiguration für die Instanzen des primären und sekundären Replikats, und aktualisieren Sie die nicht übereinstimmende Konfiguration.  
  
-   Überprüfen Sie, ob für den Port ein Konflikt besteht, und ändern Sie ggf. die Portnummer.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verwenden des AlwaysOn-Dashboards &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
