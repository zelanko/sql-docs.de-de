---
title: Integration von Reporting Services in Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- integrating reports [Reporting Services]
- custom applications [SSRS]
- Reporting Services, application integration
- application integration [Reporting Services]
- reports [Reporting Services], integrating
ms.assetid: 49eb539c-d89b-4291-839a-0ec1a65cd270
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9ad6d24495bb44a7bd1013dbc822eefe346f02d3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63126148"
---
# <a name="integrating-reporting-services-into-applications"></a>Integration von Reporting Services in Anwendungen
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt eine offene und erweiterbare Berichtsplattform dar, die Entwicklern eine umfangreiche Reihe von APIs zur Entwicklung von Lösungen zur Verfügung stellt.  
  
 Es gibt drei Möglichkeiten für die Integration von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in benutzerdefinierte Anwendungen: den Berichtsserver-Webdienst, auch als [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-SOAP-API bezeichnet, die ReportViewer-Steuerelemente für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] und den URL-Zugriff. Jede Option hat einen anderen Ansatz zur Integration von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in die Anwendungen.  
  
## <a name="report-server-web-service"></a>Report Server-Webdienst  
 Der Berichtsserver-Webdienst stellt die primäre Schnittstelle zum Entwickeln für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dar. Unabhängig davon, ob Sie Code zur Verwaltung Ihres Berichtskatalogs oder Code zum Rendern von Berichten in einem unterstützten Format entwickeln, verfügt der Webdienst über alle notwendigen Methoden, um [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in Ihre Anwendungen zu integrieren. Ein Beispiel für eine solche Anwendung ist der Berichts-Manager, der in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] enthalten ist. Er verwaltet die Berichtsserver-Datenbank mithilfe des Webdiensts.  
  
## <a name="reportviewer-controls-for-visual-studio"></a>ReportViewer-Steuerelemente für Visual Studio  
 Mit den in [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] enthaltenen ReportViewer-Steuerelementen können Berichtsanzeigen in Ihre Anwendungen integriert werden. Es gibt zwei Steuerelemente: eines für Windows Forms-Anwendungen und eines für WebForms-Anwendungen. Jedes Steuerelement verfügt über die Möglichkeit zur Anzeige von Berichten, die auf einem Berichtsserver bereitgestellt wurden, sowie zum Rendern von Berichten, die in einer Umgebung vorliegen, in der kein Berichtsserver installiert ist.  
  
## <a name="url-access"></a>URL-Zugriff  
 Der URL-Zugriff ist eine weitere Option für die Integration der Berichtsanzeige in Ihren Anwendungen, wenn die ReportViewer-Steuerelemente nicht zur Verfügung stehen. Darüber hinaus ist der URL-Zugriff hilfreich, wenn Links zu Berichten per E-Mail an Benutzer gesendet werden sollen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Integrating Reporting Services Using SOAP (Integrieren von Reporting Services mit SOAP)](../application-integration/integrating-reporting-services-using-soap.md)  
 Beschreibt, wie Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsnavigation und -verwaltung mithilfe des Berichtsserver-Webdiensts in Ihre vorhandenen Geschäftsanwendungen integrieren.  
  
 [Integrieren von Reporting Services mithilfe der ReportViewer-Steuerelemente](../application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 Beschreibt, wie Sie die Berichtsanzeige mithilfe der ReportViewer-Steuerelemente in Ihre vorhandenen Anwendungen integrieren.  
  
 [Integrating Reporting Services Using URL Access (Integrieren von Reporting Services mit URL-Zugriff)](../application-integration/integrating-reporting-services-using-url-access.md)  
 Beschreibt, wie Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsnavigation mithilfe des URL-Zugriffs in Ihre vorhandenen Geschäftsanwendungen integrieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Entscheidung zwischen URL-Zugriff und SOAP](../../../2014/reporting-services/application-integration/choosing-between-url-access-and-soap.md)   
 [Technische Referenz (SSRS)](../../../2014/reporting-services/technical-reference-ssrs.md)   
 [Report Server Web Service (Report Server-Webdienst)](../report-server-web-service/report-server-web-service.md)  
  
  
