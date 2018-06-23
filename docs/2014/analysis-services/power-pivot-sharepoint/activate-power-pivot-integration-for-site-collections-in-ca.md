---
title: Aktivieren der PowerPivot-Funktionsintegration für Websitesammlungen in der Zentraladministration | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 00e8f0336c075c14feb8c4e3b4a8b43e0ebdaf9e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149992"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a>Aktivieren der PowerPivot-Funktionsintegration für Websitesammlungen in der Zentraladministration
  Die Integration der PowerPivot-Funktion für bestimmte Websitesammlungen muss aktiviert werden, wenn Sie die Installationsoption Vorhandene Farm zur Installation von SQL Server PowerPivot für SharePoint verwendet haben. Wenn Sie PowerPivot für SharePoint mit der Option "Neuer Server" installiert haben, können Sie diese Aufgabe überspringen, da SQL Server-Setup bereits die Funktion zur PowerPivot-Integration für die Stammwebsitesammlung aktiviert hat, als die Bereitstellung konfiguriert wurde.  
  
 Die Funktionsaktivierung auf der Ebene der Websitesammlung ist erforderlich, um Ihren Websites Anwendungsseiten und Vorlagen zur Verfügung zu stellen,  einschließlich Konfigurationsseiten für geplante Datenaktualisierungen und Anwendungsseiten für PowerPivot-Katalog- und Datenfeed-Bibliotheken.  
  
 Sie müssen die PowerPivot-Integration für jede Websitesammlung aktivieren, die die PowerPivot-Abfrageverarbeitung unterstützt.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Sie müssen Administrator einer Websitesammlung sein.  
  
## <a name="activate-powerpivot-features"></a>Aktivieren der PowerPivot-Funktionen  
  
1.  Klicken Sie auf einer SharePoint-Website auf **Websiteaktionen**.  
  
     Standardmäßig wird auf SharePoint-Webanwendungen über Port 80 zugegriffen. Dies bedeutet, dass Sie häufig eine SharePoint-Website zugreifen können, indem Sie http:// eingeben\<Computername > um die Stammwebsitesammlung zu öffnen.  
  
2.  Klicken Sie auf **Siteeinstellungen**.  
  
3.  Klicken Sie unter Websitesammlungsverwaltung auf **Websitesammlungsfeatures**.  
  
4.  Führen Sie einen Bildlauf nach unten bis dort **PowerPivot-Integration für Webseitensammlungen**.  
  
5.  Klicken Sie auf **Aktivieren**.  
  
6.  Wiederholen Sie den Schritt für zusätzliche Websitesammlungen, indem Sie jede Website öffnen und auf **Websiteaktionen**klicken.  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot-Serververwaltung und-Konfiguration in der Zentraladministration](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Anfängliche Konfiguration &#40;PowerPivot für SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [PowerPivot für SharePoint 2010-Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  