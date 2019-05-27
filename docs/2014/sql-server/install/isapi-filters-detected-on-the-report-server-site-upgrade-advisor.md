---
title: ISAPI-Filter erkannt wird, auf die Berichtsserver-Website (Upgrade Advisor) | Microsoft-Dokumentation
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
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 812fc3584f0d0742ea6065e4600da1f9a7755385
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66094156"
---
# <a name="isapi-filters-detected-on-the-report-server-site-upgrade-advisor"></a>Auf der Berichtsserversite wurden ISAPI-Filter erkannt (Upgrade Advisor)
  Upgrade Advisor hat mindestens einen ISAPI-Filter auf der Website gefunden, die die virtuellen Verzeichnisse des Berichtsservers und des Berichts-Managers hostet. ISAPI-Filter werden nicht unterstützt, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Überprüfen Sie vor dem Upgrade, ob die ISAPI-Filter der Website von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Anwendungen verwendet werden. Wenn Sie den ISAPI-Filter nicht benötigen, können Sie den Berichtsserver aktualisieren. Setup erstellt die Standard-URLs ohne Unterstützung für den ISAPI-Filter, der in IIS ausgeführt wird. Wenn Sie den ISAPI-Filter benötigen, dürfen Sie das Upgrade erst durchführen, wenn Sie eine Alternative zum Hosten des ISAPI-Filters gefunden haben (indem Sie z. B. den ISA Server verwenden oder den ISAPI-Filter weiterhin in IIS hosten). Der Berichtsserver unterstützt in bestimmten Szenarios HttpModules von ASP.NET als Ersatz für ISAPI-Filter. Weitere Informationen finden Sie in der Dokumentation zu ASP.NET in MSDN.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Analysieren und verwenden Sie eine separate Lösung zum Hosten der ISAPI-Filter, die für die Bereitstellung erforderlich sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
