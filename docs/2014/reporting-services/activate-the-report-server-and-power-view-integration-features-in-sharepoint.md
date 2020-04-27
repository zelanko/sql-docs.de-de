---
title: Aktivieren des Berichts Servers und Power View von Integrationsfunktionen in SharePoint | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e30ae6ea0e7fa314748c4da265650273c0a7d56e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66110026"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Aktivieren der Berichtsserver- und Power View-Integrationsfunktionen in SharePoint
  Die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Website Sammlungs Funktionen werden in der Regel standardmäßig aktiviert, nachdem [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] Sie das-Add-in für SharePoint-Produkte installiert haben. In einigen Situationen müssen Sie die Funktionen manuell aktivieren.  
  
 Wenn Sie nach der Installation des SharePoint-Produkts das [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In für SharePoint 2010-Produkte installieren, werden die Berichtsserverintegrationsfunktion und die Power View-Integrationsfunktion nur für Stammwebsitesammlungen aktiviert. Für andere Websitesammlungen müssen Sie die Funktionen manuell aktivieren. Wenn Sie z. B. eine Websitesammlung von **http://[Mein Servername]/Websites/[Websitesammlungsname]** besitzen, müssen Sie die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Websitesammlungsfunktionen manuell aktivieren.  
  
 Wenn keine Stammwebsitesammlung vorhanden ist, wird vom [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Add-In ungefähr folgende Meldung protokolliert.  
  
 "SharePoint Web App 80 besitzt keine Stammwebsitesammlung"  
  
 Die Meldung befindet sich im Add-in-Installationsprotokoll mit dem Namen "RS_SP_ #. log", wobei "#" eine inkrementellen Zahl ist. Die Protokolldatei befindet sich im temporären Ordner des aktuellen Benutzers, z. b. c:\Users\\[Benutzername] \AppData\Local\Temp. Weitere Informationen zu Protokollierungs Optionen mit dem Add-in finden Sie unter [installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
 Inhalte dieses Themas:  
  
-   [So aktivieren Sie die Websitesammlungsfunktion für die Berichtsserver- und Power View-Integration:](#bkmk_features)  
  
-   [So aktivieren oder deaktivieren Sie die Websitesammlungsfunktion für die Berichtsserver-Zentraladministration:](#bkmk_centraladmin)  
  
##  <a name="to-activate-the-report-server-and-power-view-integration-site-collection-features"></a><a name="bkmk_features"></a>So aktivieren Sie die Website Sammlungs Funktionen des Berichts Servers und der Power View-Integration:  
  
1.  Öffnen Sie den Browser für die Website, auf der die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktionen aktiviert werden sollen.  
  
2.  Klicken Sie auf **Websiteaktionen**.  
  
3.  Klicken Sie auf **Siteeinstellungen**.  
  
4.  Klicken Sie in der Gruppe „Websitesammlungsverwaltung“ auf **Websitesammlungs-Features** .  
  
5.  Suchen Sie in der Liste **Berichtsserver-Integrationsfunktion** oder **Funktion zur Power View-Integration** .  
  
6.  Klicken Sie auf **Activate** (Aktivieren).  
  
 Verwenden Sie zum Deaktivieren der Funktionen die gleiche Prozedur, klicken Sie jedoch auf **Deaktivieren** statt auf **Aktivieren**.  
  
##  <a name="to-activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a><a name="bkmk_centraladmin"></a>So aktivieren oder deaktivieren Sie die Website Sammlungs Funktion für Reporting Services zentral Administration:  
  
1.  Öffnen Sie den Browser für die SharePoint-Zentraladministration.  
  
2.  Klicken Sie auf **Websiteaktionen**.  
  
3.  Klicken Sie auf **Siteeinstellungen**.  
  
4.  Klicken Sie in der Gruppe „Websitesammlungsverwaltung“ auf **Websitesammlungs-Features** .  
  
5.  Suchen Sie in der Liste die Funktion **Berichtsserver-Zentraladministration** .  
  
6.  Klicken Sie auf **Activate** (Aktivieren).  
  
 Verwenden Sie zum Deaktivieren der Funktion die gleiche Prozedur, klicken Sie jedoch auf **Deaktivieren** statt **Aktivieren**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nachdem die Funktion aktiviert wurde, können Sie die Serverintegration fortsetzen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
