---
title: Aktivieren der Synchronisierung Berichtsserverdateien in der SharePoint-Zentraladministration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 69d059807b7d48fe71cffb120c73fa9aa004a8bb
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018002"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>Aktivieren des Features zur Berichtsserver-Dateisynchronisierung in der SharePoint-Zentraladministration
  Das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Feature zur Berichtsserver-Dateisynchronisierung verwendet SharePoint-Ereignishandler, um den Berichtsserverkatalog mit Elementen in Dokumentbibliotheken zu synchronisieren. Diese Funktion ist nützlich, wenn Benutzer veröffentlichte Berichtselemente häufig direkt in die SharePoint-Dokumentbibliotheken hochladen. Wenn die Dateisynchronisierungsfunktion nicht aktiviert ist, werden Inhalte weiterhin synchronisiert. Dies erfolgt allerdings nicht so häufig.  
  
 Das Feature zur Dateisynchronisierung kann in der SharePoint-Websiteverwaltung aktiviert werden, nachdem Sie das [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]-Add-In für SharePoint-Produkte installiert haben.  
  
 Die Funktion kann für einzelne Websites manuell aktiviert und deaktiviert werden, jedoch nicht auf Ebene der Websitesammlung.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In für SharePoint muss installiert sein. Falls das Add-In nicht installiert ist, wird die Dateisynchronisierungsfunktion nicht in der Funktionsliste der Website angezeigt.  
  
 Um die Installation zu überprüfen, zeigen Sie die Liste der installierten Anwendungen in der [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows- **Systemsteuerung**an. Wenn das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Add-In installiert ist, folgen Sie den Anweisungen in diesem Thema, um das Feature zur Berichtsserver-Dateisynchronisierung zu aktivieren.  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>So aktivieren oder deaktivieren Sie das Feature zur Berichtsserver-Dateisynchronisierung auf einer Website  
  
1.  Klicken Sie auf der Hauptseite der Website auf das Menü **Websiteaktionen** , und klicken Sie dann auf **Siteeinstellungen**.  
  
2.  Klicken Sie im Bereich **Websiteaktionen** auf **Websitefunktionen verwalten**.  
  
3.  Suchen Sie **Berichtsserver-Dateisynchronisierung** in der Liste.  
  
4.  Klicken Sie auf **Aktivieren**.  
  
> [!NOTE]  
>  Gehen Sie auf die gleiche Weise vor, um das Feature zur Berichtsserver-Dateisynchronisierung zu deaktivieren. Klicken Sie jedoch auf **Deaktivieren**.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei Berichtsteilen &#40;Berichts-Generator und SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [Aktivieren der Berichtsserver- und Power View-Integrationsfunktionen in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Installieren oder Deinstallieren des Reporting Services Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Installieren oder Deinstallieren des Reporting Services Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
