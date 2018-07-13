---
title: Reporting Services-SharePoint-Modus-Installation (SharePoint 2010 und SharePoint 2013) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
caps.latest.revision: 30
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8800556239018222cd3ac63650a1a44c2a750227
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249670"
---
# <a name="reporting-services-sharepoint-mode-installation-sharepoint-2010-and-sharepoint-2013"></a>Reporting Services-Installation im SharePoint-Modus (SharePoint 2010 und SharePoint 2013)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus ist eine Sammlung von Serverkomponenten, die Erstellung von Berichten und Übermittlung, basierend auf bieten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint-Produkte.  
  
 Bei Ausführung von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus werden [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]- und Datenwarnungsfunktionen bereitgestellt. Weitere Informationen zu Funktionen im SharePoint-Modus finden Sie im Abschnitt „Funktionsunterstützung und Verhaltensunterschiede nach Servermodus“ in [Reporting Services-Berichtsserver](../reporting-services-report-server.md).  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus erfordert zwei grundlegende Installationen:  
  
|Installation|Description|  
|------------------|-----------------|  
|Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in für SharePoint-Produkte.|Durch das Add-In werden die Seiten und Funktionen der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Benutzeroberfläche auf einem SharePoint-Web-Front-End-Server installiert. Die Benutzeroberflächenfunktionen umfassen [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], Verwaltungsseiten in der SharePoint-Zentraladministration, innerhalb der SharePoint-Dokumentbibliotheken verwendete Funktionsseiten sowie Seiten für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenwarnungen.|  
|Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus installierten Berichtsserver|Der Berichtsserver ist für die Daten- und Berichtsverarbeitung, das Rendern von Berichten sowie für die Verarbeitung von Abonnements und Datenwarnungen zuständig. Der im SharePoint-Modus ausgeführte Berichtsserver ist als gemeinsamer SharePoint-Dienst konzipiert und wird in dieser Form installiert.|  
  
 Verwenden Sie zur Installation von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Installationsmedien.  
  
 Informationen zu erweiterten Bereitstellungsszenarien finden Sie unter [Bereitstellungsprüfliste: Reporting Services, Power View und PowerPivot für SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) und [Bereitstellungsprüfliste: Installieren von Reporting Services in eine vorhandene SharePoint-Farm](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Unterstützte Kombinationen von SharePoint- und Reporting Services-Server und-Add-in &#40;SQLServer 2014&#41;](supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [Installieren von SharePoint-Modus von Reporting Services für SharePoint 2013](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
 [Installieren des SharePoint-Modus von Reporting Services für SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 [Installieren oder Deinstallieren des Reporting Services Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [Wo die Reporting Services-add-in für SharePoint-Produkte zu finden.](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [Hinzufügen ein zusätzlichen Berichtsservers zu einer Farm &#40;SSRS Scale-Out&#41;](add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [Add an Additional Reporting Services Web Front-end to a Farm (Hinzufügen eines zusätzlichen Reporting Services-Web-Front-Ends zu einer Farm)](add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Konfigurieren von E-mail für eine Reporting-Dienstanwendung Services &#40;SharePoint 2010 und SharePoint 2013&#41;](configure-e-mail-for-a-reporting-services-service-application.md)  
  
 [Provision Subscriptions and Alerts for SSRS Service Applications (Bereitstellen von Abonnements und Warnungen für SSRS-Dienstanwendungen)](provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Claims to Windows Token Service &#40;C2WTS&#41; und Reporting Services](../../sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datenwarnungsarchitektur und Workflow](../reporting-services-data-alerts.md#AlertingWF)   
 [Data Alert Manager for Alerting Administrators (Datenwarnungs-Manager für Warnungsadministratoren)](../data-alert-manager-for-alerting-administrators.md)  
  
  
