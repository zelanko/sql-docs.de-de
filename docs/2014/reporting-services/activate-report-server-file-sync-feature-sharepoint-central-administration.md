---
title: Aktivieren der Berichts Server-Dateisynchronisierung Funktion in der SharePoint-zentral Administration | Microsoft-Dokumentation
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 03/06/2017
ms.openlocfilehash: 762cf7e67a9983c345b58d2afd1c47da93306bd0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67413149"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>Aktivieren des Features zur Berichtsserver-Dateisynchronisierung in der SharePoint-Zentraladministration

Das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Feature zur Berichtsserver-Dateisynchronisierung verwendet SharePoint-Ereignishandler, um den Berichtsserverkatalog mit Elementen in Dokumentbibliotheken zu synchronisieren. Diese Funktion ist nützlich, wenn Benutzer veröffentlichte Berichtselemente häufig direkt in die SharePoint-Dokumentbibliotheken hochladen. Wenn die Datei Synchronisierungs Funktion nicht aktiviert ist, werden die Inhalte weiterhin synchronisiert, aber nicht so häufig.  
  
Das Feature zur Dateisynchronisierung kann in der SharePoint-Websiteverwaltung aktiviert werden, nachdem Sie das [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]-Add-In für SharePoint-Produkte installiert haben.  
  
Die Funktion kann für einzelne Websites manuell aktiviert und deaktiviert werden, jedoch nicht auf Ebene der Websitesammlung.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In für SharePoint muss installiert sein. Wenn das Add-in nicht installiert ist, wird die Datei Synchronisierungs Funktion nicht in der Funktionsliste der Website angezeigt.  
  
 Um die Installation zu überprüfen, zeigen Sie die Liste der installierten Anwendungen in der [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows- **Systemsteuerung**an. Wenn das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Add-In installiert ist, folgen Sie den Anweisungen in diesem Thema, um das Feature zur Berichtsserver-Dateisynchronisierung zu aktivieren.  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>So aktivieren oder deaktivieren Sie das Feature zur Berichtsserver-Dateisynchronisierung auf einer Website  
  
1.  Klicken Sie auf der Hauptseite der Website auf das Menü **Website Aktionen** , und klicken Sie dann auf **Website Einstellungen**.  
  
2.  Klicken Sie in den **Website Aktionen**auf **Website Funktionen verwalten**.  
  
3.  Suchen Sie **Berichtsserver-Dateisynchronisierung** in der Liste.  
  
4.  Klicken Sie auf **Activate** (Aktivieren).  
  
> [!NOTE]  
>  Gehen Sie auf die gleiche Weise vor, um das Feature zur Berichtsserver-Dateisynchronisierung zu deaktivieren. Klicken Sie jedoch auf **Deaktivieren**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei Berichts teilen &#40;Berichts-Generator und SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [Aktivieren des Berichts Servers und Power View von Integrationsfunktionen in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
