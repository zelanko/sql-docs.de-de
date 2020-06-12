---
title: Aktivieren der Power Pivot-Funktions Integration für Website Sammlungen in der zentral Administration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
author: minewiskan
ms.author: owend
ms.openlocfilehash: b479564984727e47432754d0a660e6aa979244b3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547632"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a>Aktivieren der PowerPivot-Funktionsintegration für Websitesammlungen in der Zentraladministration
  Die Integration der PowerPivot-Funktion für bestimmte Websitesammlungen muss aktiviert werden, wenn Sie die Installationsoption Vorhandene Farm zur Installation von SQL Server PowerPivot für SharePoint verwendet haben. Wenn Sie PowerPivot für SharePoint mit der Option "Neuer Server" installiert haben, können Sie diese Aufgabe überspringen, da SQL Server-Setup bereits die Funktion zur PowerPivot-Integration für die Stammwebsitesammlung aktiviert hat, als die Bereitstellung konfiguriert wurde.  
  
 Die Funktionsaktivierung auf der Ebene der Websitesammlung ist erforderlich, um Ihren Websites Anwendungsseiten und Vorlagen zur Verfügung zu stellen,  einschließlich Konfigurationsseiten für geplante Datenaktualisierungen und Anwendungsseiten für PowerPivot-Katalog- und Datenfeed-Bibliotheken.  
  
 Sie müssen die PowerPivot-Integration für jede Websitesammlung aktivieren, die die PowerPivot-Abfrageverarbeitung unterstützt.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Sie müssen Administrator einer Websitesammlung sein.  
  
## <a name="activate-powerpivot-features"></a>Power Pivot-Funktionen aktivieren  
  
1.  Klicken Sie auf einer SharePoint-Website auf **Websiteaktionen**.  
  
     Standardmäßig wird auf SharePoint-Webanwendungen über Port 80 zugegriffen. Dies bedeutet, dass Sie häufig auf eine SharePoint-Website zugreifen können, indem Sie http://\<computer name> eingeben, um die Stammwebsitesammlung zu öffnen.  
  
2.  Klicken Sie auf **Siteeinstellungen**.  
  
3.  Klicken Sie unter Websitesammlungsverwaltung auf **Websitesammlungsfeatures**.  
  
4.  Scrollen Sie auf der Seite nach unten, bis Sie die **Funktion zur Power Pivot-Integration-Website Sammlung**  
  
5.  Klicken Sie auf **Activate** (Aktivieren).  
  
6.  Wiederholen Sie den Schritt für zusätzliche Websitesammlungen, indem Sie jede Website öffnen und auf **Websiteaktionen**klicken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Power Pivot-Server Verwaltung und-Konfiguration in der zentral Administration](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Anfängliche Konfiguration &#40;PowerPivot für SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [PowerPivot für SharePoint 2010-Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
