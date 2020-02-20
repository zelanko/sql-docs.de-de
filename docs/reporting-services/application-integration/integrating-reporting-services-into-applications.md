---
title: Integration in Anwendungen
description: Reporting Services ist eine offene und erweiterbare Berichtsplattform, die Entwicklern eine umfangreiche Reihe von APIs zur Entwicklung von Lösungen zur Verfügung stellt.
ms.custom: seo-lt-2019
ms.date: 05/14/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
author: maggiesMSFT
ms.author: maggies
monikerRange: = sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 889967d4a7731b25b2704b8695c6b8797d367430
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "74796954"
---
# <a name="integrating-reporting-services-into-applications"></a>Integration von Reporting Services in Anwendungen

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt eine offene und erweiterbare Berichtsplattform dar, die Entwicklern eine umfangreiche Reihe von APIs zur Entwicklung von Lösungen zur Verfügung stellt.

> [!NOTE]
> Ab SQL Server 2017 Reporting Services ist der Zugriff auf die REST-API für die Entwicklung von Lösungen verfügbar. Der Zugriff auf die SOAP-API ist veraltet. Weitere Informationen finden Sie unter [Develop with the REST APIs for Reporting Services (Entwickeln mit den REST-APIs für Reporting Services)](../developer/rest-api.md).
  
 Es gibt drei Möglichkeiten für die Integration von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in benutzerdefinierte Anwendungen: den Berichtsserver-Webdienst, auch [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-SOAP-API genannt, die Berichts-Viewer-Steuerelemente für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und den URL-Zugriff. Jede Option hat einen anderen Ansatz zur Integration von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in die Anwendungen.
  
## <a name="report-server-web-service"></a>Berichtsserver-Webdienst

 Der Berichtsserver-Webdienst stellt die primäre Schnittstelle zum Entwickeln für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dar. Unabhängig davon, ob Sie Code zur Verwaltung Ihres Berichtskatalogs oder Code zum Rendern von Berichten in einem unterstützten Format entwickeln, verfügt der Webdienst über alle notwendigen Methoden, um [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in Ihre Anwendungen zu integrieren. Ein Beispiel für eine solche Anwendung ist das Webportal, das in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthalten ist. Das Portal verwendet den Webdienst, um die Berichtsserver-Datenbank zu verwalten.  
  
## <a name="report-viewer-controls-for-visual-studio"></a>Report Viewer-Steuerelemente für Visual Studio

 Mit den für [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verfügbaren Report Viewer-Steuerelementen können Berichtanzeigen in Ihre Anwendungen integriert werden. Es gibt zwei Steuerelemente: eines für Windows Forms-Anwendungen und eines für WebForms-Anwendungen. Jedes Steuerelement verfügt über die Möglichkeit zur Anzeige von Berichten, die auf einem Berichtsserver bereitgestellt wurden, sowie zum Rendern von Berichten, die in einer Umgebung vorliegen, in der kein Berichtsserver installiert ist.  
  
## <a name="url-access"></a>URL-Zugriff  
 Der URL-Zugriff ist eine weitere Option zum Integrieren der Berichtanzeige in Ihre Anwendungen, wenn die Report Viewer-Steuerelemente nicht verfügbar sind. Darüber hinaus ist der URL-Zugriff hilfreich, wenn Links zu Berichten per E-Mail an Benutzer gesendet werden sollen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt

 [Integrating Reporting Services Using SOAP (Integrieren von Reporting Services mit SOAP)](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)  
 Beschreibt, wie Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsnavigation und -verwaltung mithilfe des Berichtsserver-Webdiensts in Ihre vorhandenen Geschäftsanwendungen integrieren.  
  
 [Integrieren von Reporting Services mit den Report Viewer-Steuerelementen](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 Beschreibt, wie Sie die Berichtanzeige mithilfe der Report Viewer-Steuerelemente in Ihre vorhandenen Anwendungen integrieren.  
  
 [Integrating Reporting Services Using URL Access (Integrieren von Reporting Services mit URL-Zugriff)](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)  
 Beschreibt, wie Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsnavigation mithilfe des URL-Zugriffs in Ihre vorhandenen Geschäftsanwendungen integrieren.  
  
## <a name="next-steps"></a>Nächste Schritte

Für weitere Informationen zur Entscheidung, ob der URL-Zugriff oder die SOAP-API verwendet wird, finden Sie unter [Entscheidung zwischen URL-Zugriff und SOAP in Reporting Services](choosing-between-url-access-and-soap.md).

Weitere Informationen zur REST API für SQL Server 2017 Reporting Services finden Sie unter [Develop with the REST APIs for Reporting Services (Entwickeln mit den REST-APIs für Reporting Services)](../developer/rest-api.md).

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
