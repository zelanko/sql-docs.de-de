---
title: Features der Reporting Services-Website Sammlung | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66102759"
---
# <a name="reporting-services-site-collection-features"></a>Funktion zur Reporting Services-Websitesammlung
  
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus umfasst drei SharePoint-Websitesammlung-Funktionen. Die Funktionen unterstützen Folgendes: die allgemeine Berichterstellungsumgebung des [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus, [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], eine Funktion des [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-Ins für [!INCLUDE[SPS2010](../includes/sps2010-md.md)] Enterprise Edition und Verwaltungsvorgänge für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in der SharePoint-Zentraladministration.  
  
## <a name="site-collection-features"></a>Websitesammlung-Funktionen  
 In der folgenden Tabelle sind die Websitesammlung-Funktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] beschrieben.  
  
|Funktion|BESCHREIBUNG|  
|-------------|-----------------|  
|**Funktion für die Berichts Server-zentral Administration**|Aktiviert Funktionen zum Verwalten der Integration in einen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsserver. Diese Funktion ist nur unter der Websitesammlung-Funktion der SharePoint-Zentraladministration installiert und wird auch nur darunter verwendet.<br /><br /> Die Berichts Server-Integrationsfunktion wird in der Website Sammlung der SharePoint-zentral Administration automatisch aktiviert [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] , nachdem Sie das-Add-in für SharePoint-Produkte installiert haben. In einigen Situationen müssen Sie die Funktion manuell aktivieren. Um die Berichtsserverfunktion zu aktivieren, verwenden Sie die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Seiten auf der Seite Siteeinstellungen der SharePoint-Zentraladministration.<br /><br /> Durch die [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Version und höhere Versionen des Add-Ins für SharePoint-Produkte wird die Berichtsserver-Integrationsfunktion bei der Installation des Add-Ins für alle vorhandenen Websitesammlungen aktiviert. Darüber hinaus ist die Funktion für neue Websitesammlungen automatisch aktiv.|  
|**Berichts Server-Integrationsfunktion**|Ermöglicht umfassende Berichterstellung [!INCLUDE[msCoName](../includes/msconame-md.md)] mithilfe von[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> Diese Funktion ist standardmäßig aktiv.|  
|**Power View-Integrations Feature**|Aktiviert das interaktive Durchsuchen von Daten und deren visuelle Präsentation für PowerPivot-Arbeitsmappen und tabellarische Analysis Services-Datenbanken.<br /><br /> Auf das Feature kann über die Kontextmenüs der folgenden Datenquellen zugegriffen werden:<br /><br /> RDLX<br /><br /> RSDS<br /><br /> BISM-Verbindungsdatei<br /><br /> <br /><br /> Wenn [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] nicht in den Kontextmenüs angezeigt wird, sollten Sie überprüfen, ob die **Power View-Integrationsfunktion** aktiviert ist.<br /><br /> Diese Funktion ist standardmäßig deaktiviert.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktivieren der Berichtsserver- und Power View-Integrationsfunktionen in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Reporting Services von Standorteinstellungen und Website Features&#40;SharePoint-Modus&#41;](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [Aktivieren der Berichts Server-Dateisynchronisierung Funktion in der SharePoint-zentral Administration](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
  
