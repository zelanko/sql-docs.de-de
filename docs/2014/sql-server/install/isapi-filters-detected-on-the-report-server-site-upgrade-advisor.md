---
title: Auf der Berichts Serversite wurden ISAPI-Filter erkannt (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- ISAPI filters
- report servers [Reporting Services], upgrade issues
ms.assetid: dd30560d-9e16-47c7-ba68-a9743a657e4e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bff1834ddf1b8f90787a47a8fd58a240d2b715d5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059229"
---
# <a name="isapi-filters-detected-on-the-report-server-site-upgrade-advisor"></a>Auf der Berichtsserversite wurden ISAPI-Filter erkannt (Upgrade Advisor)
  Upgrade Advisor hat mindestens einen ISAPI-Filter auf der Website gefunden, die die virtuellen Verzeichnisse des Berichtsservers und des Berichts-Managers hostet. ISAPI-Filter werden in nicht unterstützt [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Einheimischen.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Überprüfen Sie vor dem Upgrade, ob die ISAPI-Filter der Website von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Anwendungen verwendet werden. Wenn Sie den ISAPI-Filter nicht benötigen, können Sie den Berichtsserver aktualisieren. Setup erstellt die Standard-URLs ohne Unterstützung für den ISAPI-Filter, der in IIS ausgeführt wird. Wenn Sie den ISAPI-Filter benötigen, dürfen Sie das Upgrade erst durchführen, wenn Sie eine Alternative zum Hosten des ISAPI-Filters gefunden haben (indem Sie z. B. den ISA Server verwenden oder den ISAPI-Filter weiterhin in IIS hosten). Der Berichtsserver unterstützt in bestimmten Szenarios HttpModules von ASP.NET als Ersatz für ISAPI-Filter. Weitere Informationen finden Sie in der Dokumentation zu ASP.NET in MSDN.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Analysieren und verwenden Sie eine separate Lösung zum Hosten der ISAPI-Filter, die für die Bereitstellung erforderlich sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services Upgradeprobleme &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
