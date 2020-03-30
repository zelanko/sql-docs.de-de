---
title: Integrieren mithilfe des Simple Object Access-Protokolls (SOAP)
description: Die SOAP-API der Reporting Services verfügt über mehrere Webdienst-Endpunkte zur Entwicklung von benutzerdefinierten Berichtslösungen.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.custom: seo-lt-2019
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application integration
- SOAP [Reporting Services]
- SOAP [Reporting Services], about report integration
- integrating reports [Reporting Services]
- Web service [Reporting Services], application integration
ms.assetid: 6bc17af5-883c-4bfa-87d9-48cd7056d145
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c19676b59b2de393f7d68a6660ec33db50c29e09
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "74796962"
---
# <a name="integrating-reporting-services-using-soap"></a>Integrieren von Reporting Services mit SOAP
  Die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-SOAP-API verfügt über mehrere Webdienst-Endpunkte zur Entwicklung von benutzerdefinierten Berichtslösungen. Die Endpunkte lassen sich derzeit in zwei Kategorien unterteilen: Verwaltung und Ausführung. Die Verwaltungsfunktionen werden durch die Endpunkte <xref:ReportService2005>, <xref:ReportService2006> und <xref:ReportService2010> verfügbar gemacht. Mit dem <xref:ReportService2005>-Endpunkt wird ein Berichtsserver verwaltet, der im einheitlichen Modus konfiguriert ist, und mit dem <xref:ReportService2006>-Endpunkt wird ein Berichtsserver verwaltet, der für den integrierten SharePoint-Modus konfiguriert ist. Der <xref:ReportService2010>-Endpunkt führt die Funktionen von <xref:ReportService2005> und <xref:ReportService2006> zusammen und kann einen Berichtsserver verwalten, der entweder für den einheitlichen Modus oder integrierten SharePoint-Modus konfiguriert ist.  
  
> [!NOTE]  
>  Der <xref:ReportService2005>-Endpunkt und der <xref:ReportService2006>-Endpunkt sind in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] als veraltet markiert. Der <xref:ReportService2010>-Endpunkt schließt die Funktionen beider Endpunkte ein und beinhaltet zusätzliche Verwaltungsfunktionen.  
  
 Die Ausführungsfunktion wird durch den <xref:ReportExecution2005>-Endpunkt verfügbar gemacht und wird verwendet, wenn der Berichtsserver im einheitlichen Modus oder im integrierten SharePoint-Modus konfiguriert ist. Folgende Themen zeigen, wie diese Endpunkte für die Entwicklung von Berichtslösungen in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-, SharePoint- und Webanwendungen verwendet werden können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verwenden der SOAP-API in einer Windows-Anwendung](../../reporting-services/application-integration/integrating-reporting-services-using-soap-windows-application.md)  
 Beschreibt, wie Sie die SOAP-API verwenden, um [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in eine Windows-Umgebung zu integrieren  
  
 [Verwenden der SOAP-API in einer Webanwendung](../../reporting-services/application-integration/integrating-reporting-services-using-soap-web-application.md)  
 Beschreibt, wie Sie die SOAP-API verwenden, um [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in eine Webumgebung zu integrieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration von Reporting Services in Anwendungen](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Berichtsserver-Webdienst](../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Building Applications Using the Web Service and the .NET Framework (Erstellen von Anwendungen mit dem Webdienst und .NET Framework)](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
