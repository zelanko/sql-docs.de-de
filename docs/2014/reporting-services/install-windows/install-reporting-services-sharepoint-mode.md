---
title: Reporting Services Installation im SharePoint-Modus (SharePoint 2010 und SharePoint 2013) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef049b4ded6408e651d5ec2c3db99c10bf7c27b6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108765"
---
# <a name="reporting-services-sharepoint-mode-installation-sharepoint-2010-and-sharepoint-2013"></a>Reporting Services-Installation im SharePoint-Modus (SharePoint 2010 und SharePoint 2013)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]im SharePoint-Modus ist eine Auflistung von Serverkomponenten, die die Generierung und Übermittlung von Berichten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereit [!INCLUDE[msCoName](../../includes/msconame-md.md)] stellen, basierend auf-und SharePoint-Produkten.  
  
 Bei Ausführung von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus werden [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]- und Datenwarnungsfunktionen bereitgestellt. Weitere Informationen zu Funktionen im SharePoint-Modus finden Sie im Abschnitt "Funktions Unterstützung und Verhaltensunterschiede nach Server Modus" in [Reporting Services Berichts Servers](../reporting-services-report-server.md) .  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus erfordert zwei grundlegende Installationen:  
  
|Installation|Beschreibung|  
|------------------|-----------------|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-in für SharePoint-Produkte.|Durch das Add-In werden die Seiten und Funktionen der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Benutzeroberfläche auf einem SharePoint-Web-Front-End-Server installiert. Die Benutzeroberflächenfunktionen umfassen [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], Verwaltungsseiten in der SharePoint-Zentraladministration, innerhalb der SharePoint-Dokumentbibliotheken verwendete Funktionsseiten sowie Seiten für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenwarnungen.|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus installierte Berichts Server|Der Berichtsserver ist für die Daten- und Berichtsverarbeitung, das Rendern von Berichten sowie für die Verarbeitung von Abonnements und Datenwarnungen zuständig. Der im SharePoint-Modus ausgeführte Berichtsserver ist als gemeinsamer SharePoint-Dienst konzipiert und wird in dieser Form installiert.|  
  
 Verwenden Sie zur Installation von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Installationsmedien.  
  
 Anweisungen zu erweiterten Bereitstellungs Szenarien finden Sie unter Bereitstellungs Prüfliste [: Reporting Services, Power View und PowerPivot für SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) -und Bereitstellungs Prüfliste [: Installieren von Reporting Services in einer vorhandenen SharePoint-Farm](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Unterstützte Kombinationen von SharePoint-und Reporting Services Server-und Add-in-&#40;SQL Server 2014&#41;](supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [Installieren des SharePoint-Modus von Reporting Services für SharePoint 2013](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
 [Installieren Reporting Services SharePoint-Modus für SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 [Installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint &#40;SharePoint 2010 und SharePoint 2013&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [Hinzufügen eines zusätzlichen Berichtsservers zu einer Farm &#40;Horizontales Skalieren für SSRS&#41;](add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [Hinzufügen eines zusätzlichen Reporting Services-Web-Front-Ends zu einer Farm](add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Konfigurieren von E-Mail für eine Reporting Services-Dienstanwendung &#40;SharePoint 2010 und SharePoint 2013&#41;](configure-e-mail-for-a-reporting-services-service-application.md)  
  
 [Bereitstellen von Abonnements und Warnungen für SSRS-Dienstanwendungen](provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Claims to Windows Token Service &#40;C2WTS&#41; und Reporting Services](../../sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Architektur und Workflow für Daten Warnungen](../reporting-services-data-alerts.md#AlertingWF)   
 [Datenwarnungs-Manager für Warnungsadministratoren](../data-alert-manager-for-alerting-administrators.md)  
  
  
