---
title: Virtuelle Verzeichnisse sind nicht angegeben (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 7d32b560-49d6-4558-b5d6-9127067f82d6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cbadcd0f42f8d5ae81ea2a97625be96214df4ce2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227150"
---
# <a name="virtual-directories-are-unspecified-upgrade-advisor"></a>Virtuelle Verzeichnisse sind nicht angegeben (Upgrade Advisor)
  Upgrade Advisor hat keine Einstellungen für virtuelle Verzeichnisse des Report Server-Webdiensts oder des Berichts-Managers erkannt. Nach dem Abschluss des Upgrades müssen Sie URL-Reservierungen für den Berichtsserver konfigurieren, indem Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager verwenden.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Das Upgrade einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation beinhaltet das Reservieren neuer URLs für den Report Server-Webdienst und den Berichts-Manager. Der Upgrade Advisor hat für die zu aktualisierende Instanz keine virtuellen Verzeichnisse für den Berichtsserver oder den Berichts-Manager erkannt. Der Upgradeprozess verfügt somit nicht über ausreichende Informationen, um URL-Reservierungen für den aktualisierten Berichtsserver zu erstellen. Das Upgrade kann fortgesetzt werden, jedoch ist das virtuelle Verzeichnis des Berichtsservers oder Berichts-Managers erst nach der Upgradeinstallation definiert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Verwenden Sie nach Abschluss des Upgrades den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager, um die URLs für den Berichtsserver und den Berichts-Manager festzulegen. Verwenden Sie den IIS-Manager, um ggf. alle virtuellen Verzeichnisse zu entfernen, die Sie nicht mehr benötigen.  
  
 Weitere Informationen finden Sie unter [Konfigurieren einer URL &#40;SSRS-Konfigurations-Manager&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
