---
title: Reporting Services-Websitesammlung-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9475ee323222b800a9c4b9a86e737fdd161e7a60
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66102759"
---
# <a name="reporting-services-site-collection-features"></a>Funktion zur Reporting Services-Websitesammlung
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus umfasst drei SharePoint-Websitesammlung-Funktionen. Die Funktionen unterstützen Folgendes: die allgemeine Berichterstellungsumgebung des [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus, [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], eine Funktion des [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-Ins für [!INCLUDE[SPS2010](../includes/sps2010-md.md)] Enterprise Edition und Verwaltungsvorgänge für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in der SharePoint-Zentraladministration.  
  
## <a name="site-collection-features"></a>Websitesammlung-Funktionen  
 In der folgenden Tabelle sind die Websitesammlung-Funktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] beschrieben.  
  
|Funktion|Description|  
|-------------|-----------------|  
|**Funktion für die Berichtsserver-Zentraladministration**|Aktiviert Funktionen zum Verwalten der Integration in einen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver. Diese Funktion ist nur unter der Websitesammlung-Funktion der SharePoint-Zentraladministration installiert und wird auch nur darunter verwendet.<br /><br /> Die Berichtsserver-Integrationsfunktion wird für die Websitesammlung in der SharePoint-Zentraladministration automatisch aktiviert, nachdem Sie das [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] -Add-In für SharePoint-Produkte installiert haben. In einigen Situationen müssen Sie die Funktion manuell aktivieren. Um die Berichtsserverfunktion zu aktivieren, verwenden Sie die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Seiten auf der Seite Siteeinstellungen der SharePoint-Zentraladministration.<br /><br /> Durch die [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Version und höhere Versionen des Add-Ins für SharePoint-Produkte wird die Berichtsserver-Integrationsfunktion bei der Installation des Add-Ins für alle vorhandenen Websitesammlungen aktiviert. Darüber hinaus ist die Funktion für neue Websitesammlungen automatisch aktiv.|  
|**Funktion für die Berichtsserverintegration**|Ermöglicht die umfassende Berichterstellung mithilfe von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> Diese Funktion ist standardmäßig aktiv.|  
|**Power View-Integrationsfunktion**|Aktiviert das interaktive Durchsuchen von Daten und deren visuelle Präsentation für PowerPivot-Arbeitsmappen und tabellarische Analysis Services-Datenbanken.<br /><br /> Auf das Feature kann über die Kontextmenüs der folgenden Datenquellen zugegriffen werden:<br /><br /> RDLX<br /><br /> RSDS<br /><br /> BISM-Verbindungsdatei<br /><br /> <br /><br /> Wenn [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] nicht in den Kontextmenüs angezeigt wird, sollten Sie überprüfen, ob die **Power View-Integrationsfunktion** aktiviert ist.<br /><br /> Diese Funktion ist standardmäßig deaktiviert.|  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren der Berichtsserver- und Power View-Integrationsfunktionen in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Einstellungen und Funktionen für Reporting Services-Websites &#40;SharePoint-Modus&#41;](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [Aktivieren des Features zur Berichtsserver-Dateisynchronisierung in der SharePoint-Zentraladministration](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
  
