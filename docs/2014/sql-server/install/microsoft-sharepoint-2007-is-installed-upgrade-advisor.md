---
title: Microsoft SharePoint 2007 ist installiert (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6f1da295-d9b7-4948-99d3-ebd3587337c6
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 82906615acb5c3c29ccaac0ecee72427e5fca2d2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37301682"
---
# <a name="microsoft-sharepoint-2007-is-installed-upgrade-advisor"></a>Microsoft SharePoint 2007 ist installiert (Upgrade Advisor)
  Der Upgrade Advisor hat eine Version eines SharePoint-Produkts bzw. einer SharePoint-Technologie erkannt, die nicht unterstützt wird.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] wird Sie nicht aktualisieren oder installieren SharePoint 2007. Das Upgrade wird blockiert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Um das Upgrade fortzusetzen, muss SharePoint 2007 entweder deinstalliert oder ein Upgrade von SharePoint 2007 auf ein SharePoint 2010-Produkt ausgeführt werden. Führen Sie den Upgrade Advisor nach dem Upgrade der SharePoint-Installation erneut aus, um zu bestätigen, dass keine weiteren Upgradeprobleme vorliegen.  
  
 Ein direktes Upgrade von SharePoint 2007 auf SharePoint 2013 kann nicht ausgeführt werden. Sie können jedoch ein so genanntes "Doppelhopszenario" mit Anfügen von Datenbanken durchführen, um ein Upgrade von Office SharePoint Server 2007 auf SharePoint Server 2010 und anschließend von SharePoint Server 2010 auf SharePoint Server 2013 auszuführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
