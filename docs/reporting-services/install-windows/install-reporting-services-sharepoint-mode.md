---
description: Installieren von Reporting Services 2016 im SharePoint-Modus
title: Installieren von Reporting Services 2016 im SharePoint-Modus | Microsoft-Dokumentation
ms.date: 12/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
author: maggiesMSFT
ms.author: maggies
monikerRange: '>=sql-server-2016 <=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: e9c615e709d31b9bd1632d77490ac84ad9081aa0
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91892110"
---
# <a name="install-reporting-services-2016-in-sharepoint-mode"></a>Installieren von Reporting Services 2016 im SharePoint-Modus

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

SQL Server Reporting Services in SharePoint ermöglicht die Berichterstellung und -anzeige in Dokumentbibliotheken, die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Abonnementübermittlung von Berichten per E-Mail, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], Datenwarnungen sowie Berichtsverwaltungsfunktionen, und das alles in einer Bereitstellung auf der Grundlage von [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint. Weitere Informationen zu Features im SharePoint-Modus finden Sie im Abschnitt „Funktionsunterstützung und Verhaltensunterschiede nach Servermodus“ unter [Reporting Services-Berichtsserver](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md).

> [!NOTE]
> Die Integration von Reporting Services in SharePoint ist nach SQL Server 2016 nicht mehr möglich.

Zwei [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Kernkomponenten müssen für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus installiert werden:  

|Installation|BESCHREIBUNG|  
|------------------|-----------------|  
|**Berichtsserver:** Im SharePoint-Modus installierter [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsserver|Der Berichtsserver ist für die Daten- und Berichtsverarbeitung, das Rendern von Berichten sowie für die Verarbeitung von Abonnements und Datenwarnungen zuständig. Der im SharePoint-Modus ausgeführte Berichtsserver ist als gemeinsamer SharePoint-Dienst konzipiert und wird in dieser Form installiert.<br /><br /> **So geht's:** Verwenden Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installationsmedien, um den Berichtsserver zu installieren.|  
|**Add-In** Im SharePoint-Modus installierter [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte, **rsSharePoint.msi**.|Durch das Add-In werden die Seiten und Funktionen der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Benutzeroberfläche auf einem SharePoint-Web-Front-End-Server installiert. Die Benutzeroberflächenfunktionen umfassen [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], Verwaltungsseiten in der SharePoint-Zentraladministration, innerhalb der SharePoint-Dokumentbibliotheken verwendete Funktionsseiten sowie Seiten für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Datenwarnungen.<br /><br /> **Vorgehensweise**  : Das Add-In kann entweder per Webdownload oder über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installationsmedien installiert werden. Weitere Informationen finden Sie unter [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).|  
  
## <a name="in-this-section"></a>In diesem Abschnitt

 [Supported Combinations of SharePoint and Reporting Services Server and Add-in (SQL Server 2016) (Unterstützte Kombinationen von SharePoint, Reporting Services-Server und -Add-In (SQL Server 2016))](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [Installieren des ersten Berichtsservers im SharePoint-Modus](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md)  
  
 [Installieren oder Deinstallieren des Reporting Services-Add-Ins für SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [Hinzufügen eines zusätzlichen Berichtsservers zu einer Farm &#40;Horizontales Skalieren für SSRS&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [Add an Additional Reporting Services Web Front-end to a Farm (Hinzufügen eines zusätzlichen Reporting Services-Web-Front-Ends zu einer Farm)](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Konfigurieren von E-Mail für eine Reporting Services-Dienstanwendung &#40;SharePoint 2013 und SharePoint 2016&#41;](./configure-e-mail-for-a-reporting-services-service-application.md)  
  
 [Provision Subscriptions and Alerts for SSRS Service Applications (Bereitstellen von Abonnements und Warnungen für SSRS-Dienstanwendungen)](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Übersicht über Claims to Windows Token Service &#40;c2WTS&#41; und Reporting Services](../../reporting-services/install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md)  

## <a name="next-steps"></a>Nächste Schritte

 [Datenwarnungsarchitektur und Workflow](../../reporting-services/reporting-services-data-alerts.md#AlertingWF)   
 [Data Alert Manager for Alerting Administrators (Datenwarnungs-Manager für Warnungsadministratoren)](../../reporting-services/data-alert-manager-for-alerting-administrators.md)  

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)