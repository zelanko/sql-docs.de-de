---
title: Reporting Services-Websitesammlung-Funktionen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
caps.latest.revision: 5
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 88dd168355249d5b1f2dfd645ad7f42505597cde
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057105"
---
# <a name="reporting-services-site-collection-features"></a>Funktion zur Reporting Services-Websitesammlung
  Der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus umfasst drei SharePoint-Websitesammlung-Funktionen. Die Funktionen unterstützen die allgemeine [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus, reporting-Umgebung [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], ein Feature von der [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in für [!INCLUDE[SPS2010](../includes/sps2010-md.md)] Enterprise Edition und Verwaltungsvorgänge für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in SharePoint-Zentraladministration.  
  
## <a name="site-collection-features"></a>Websitesammlung-Funktionen  
 In der folgenden Tabelle sind die Websitesammlung-Funktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] beschrieben.  
  
|Funktion|Description|  
|-------------|-----------------|  
|**Funktion für die Berichtsserver-Zentraladministration**|Aktiviert Funktionen zum Verwalten der Integration in einen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver. Diese Funktion ist nur unter der Websitesammlung-Funktion der SharePoint-Zentraladministration installiert und wird auch nur darunter verwendet.<br /><br /> Der Berichtsserver-Integrationsfunktion wird in der Auflistung der Website SharePoint-Zentraladministration automatisch aktiviert, nach der Installation der [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Add-in für SharePoint-Produkte. In einigen Situationen müssen Sie die Funktion manuell aktivieren. Um die Berichtsserverfunktion zu aktivieren, verwenden Sie die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Seiten auf der Seite Siteeinstellungen der SharePoint-Zentraladministration.<br /><br /> Die [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Version und später des Add-Ins für SharePoint-Produkte werden aktivieren die Berichtsserver-Integrationsfunktion für alle vorhandenen Websitesammlungen, wenn das Add-In installiert ist. Darüber hinaus ist die Funktion für neue Websitesammlungen automatisch aktiv.|  
|**Funktion für die Berichtsserverintegration**|Ermöglicht umfassende berichterstellung mithilfe von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> Diese Funktion ist standardmäßig aktiv.|  
|**Power View-Integrationsfunktion**|Aktiviert das interaktive Durchsuchen von Daten und deren visuelle Präsentation für PowerPivot-Arbeitsmappen und tabellarische Analysis Services-Datenbanken.<br /><br /> Auf das Feature kann über die Kontextmenüs der folgenden Datenquellen zugegriffen werden:<br /><br /> RDLX<br /><br /> RSDS<br /><br /> BISM-Verbindungsdatei<br /><br /> <br /><br /> Wenn [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] nicht in den Kontextmenüs angezeigt wird, sollten Sie überprüfen, ob die **Power View-Integrationsfunktion** aktiviert ist.<br /><br /> Diese Funktion ist standardmäßig deaktiviert.|  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren Sie das Report Server and Power View-Integrationsfunktionen in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Reporting Services-Site-Einstellungen und Funktionen&#40;SharePoint-Modus&#41;](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [Aktivieren der Funktion zur Synchronisierung der Berichtsserverdateien in der SharePoint-Zentraladministration](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
  