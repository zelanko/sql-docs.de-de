---
title: Veraltete Erweiterungen wurden auf dem Berichtsservercomputer installiert (Upgrade Advisor) erkannt. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 40d245a2-0631-470e-81b3-1feb47e028cb
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6188ddab466ccbb27e121e5500a9af68ecbd71fb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48184760"
---
# <a name="obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor"></a>Veraltete Erweiterungen wurden auf dem Berichtsservercomputer erkannt (Upgrade Advisor)
  Upgrade Advisor hat eine oder mehrere Renderingerweiterungen erkannt, die in der aktuellen Version nicht mehr verfügbar sind.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**: [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im einheitlichen Modus &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Der Berichtsserver ist für die Verwendung einer oder mehrerer Erweiterungen konfiguriert, die in dieser Version nicht mehr unterstützt werden. Nicht mehr unterstützte Erweiterungen sind:  
  
-   HTML-OWC-Renderingerweiterung  
  
-   HTML 3.2-Renderingerweiterung  
  
 Das Upgrade kann fortgesetzt werden, jedoch wird die nicht unterstützte Funktionalität auf dem aktualisierten Berichtsserver nicht mehr verfügbar sein.  
  
 Wenn Sie diese Erweiterungen benötigen, aktualisieren Sie erst, wenn Sie eine alternative Lösung für diese Anforderungen gefunden haben. Möglicherweise müssen Sie eine benutzerdefinierte Renderingerweiterung beziehen oder erstellen, die die gleiche oder eine ähnliche Funktionalität bereitstellt.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Prüfen Sie das aktuelle Featureset, das in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthalten ist, um zu ermitteln, ob die unterstützte Funktionalität Ihre Anforderungen erfüllt.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
