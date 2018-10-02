---
title: Reporting Services-Entwicklerdokumentation | Microsoft-Dokumentation
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 89a5bcc19baead2f0ba8413635fe330048963cfd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835498"
---
# <a name="reporting-services-developer-documentation"></a>Reporting Services-Entwicklerdokumentation
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] enthält mehrere Programmierschnittstellen, die Sie in Ihre eigenen Anwendungen einbauen können. Sie können die vorhandenen Funktionen und Funktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] verwenden, um benutzerdefinierte Berichts- und Verwaltungstools in Websites und Windows-Anwendungen zu erstellen, oder Sie können die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Plattform erweitern.  
  
 Das Erweitern der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Plattform umfasst die Erstellung neuer Komponenten und Ressourcen, die für den Datenzugriff, die Berichtsübermittlung und vieles mehr verwendet werden können. Sie können diese Komponenten und Ressourcen in den Unternehmen vermarkten, die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in ihrer Organisation verwenden.  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] enthält Programmierbeispiele und Lernprogramme, die Ihnen den Einstieg erleichtern. Weitere Informationen finden Sie unter [Reporting Services-Beispiele](https://msdn.microsoft.com/library/ms160954\(v=sql.110\).aspx) und [Developer's Guide: Tutorials (Reporting Services) (Entwicklerhandbuch: Tutorials (Reporting Services))](https://msdn.microsoft.com/library/aa337423\(v=sql.110\).aspx).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Integrating Reporting Services into Applications (Integration von Reporting Services in Anwendungen)](../reporting-services/application-integration/integrating-reporting-services-into-applications.md)  
 Gibt eine Übersicht darüber, wie die Berichterstellung mithilfe von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in benutzerdefinierte Anwendungen integriert werden kann. Beschreibt, wann der direkte URL-Zugriff und wann der Webdienst für den Zugriff auf den Berichtsserver verwendet werden sollte.  
  
 [Report Server Web Service for ASP.net and traditional applications (Berichtsserver-Webdienst für ASP.NET und herkömmliche Anwendungen)](../reporting-services/report-server-web-service/report-server-web-service.md)  
 Über den Berichtsserver-Webdienst erhalten Sie Zugriff auf die kompletten Funktionen des Berichtsservers. Der Webdienst verwendet SOAP über HTTP und wurde als Kommunikationsschnittstelle zwischen den Clientprogrammen und dem Berichtsserver konzipiert. Der Webdienst und seine Methoden stellen die Funktionen des Berichtsservers zur Verfügung und ermöglichen die Erstellung benutzerdefinierter Tools für jeden Teil des gesamten Berichtslebenszyklus, von der Verwaltung bis zur Ausführung.  
 
 [Develop with REST APIs for modern applications (Entwickeln mit REST-APIs für moderne Anwendungen)](developer/rest-api.md)</br>
 Die Reporting Services REST-APIs stellen programmgesteuerten Zugriff auf die Objekte im Reporting Services-Berichtsserverkatalog bereit. Mithilfe der REST-APIs können Sie zu einer Ordnerhierarchie navigieren, die Inhalte eines Ordners ermitteln oder eine Berichtsdefinition herunterladen. Außerdem können Sie Objekte erstellen, aktualisieren und löschen.

 [URL-Zugriff (SSRS)](../reporting-services/url-access-ssrs.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt einen vollständige Satz URL-basierter Anforderungen, über die Sie schnell und problemlos auf die Berichtsnavigation und -anzeige zugreifen können. Sie können diese Technologie zusammen mit dem Berichtsserver-Webdienst verwenden, um eine vollständige Berichtslösung in Ihre vorhandenen Geschäftsanwendungen zu integrieren. Der URL-Zugriff ist dann besonders sinnvoll, wenn Sie Berichte als Teil eines Internetportals integrieren oder wenn Sie Berichte über einen Webbrowser anzeigen.  
  
 [Reporting Services Extensions (Erweiterungen für Reporting Services)](../reporting-services/extensions/reporting-services-extensions.md)  
 Die modulare Architektur von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ermöglicht Erweiterungen. Eine verwaltete Code-API steht zur Verfügung, sodass Sie problemlos Erweiterungen entwickeln, installieren und verwalten können, die von vielen [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Komponenten benötigt werden. Sie können Assemblys erstellen, indem Sie [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verwenden und neue [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Funktionen für das Rendering, die Sicherheit, die Übermittlung und die Datenverarbeitung hinzufügen, um den wachsenden betrieblichen Anforderungen Ihres Unternehmens gerecht zu werden.  
  
 [Custom Report Items (Benutzerdefinierte Berichtselemente)](../reporting-services/custom-report-items/custom-report-items.md)  
 Beschreibt, wie Sie benutzerdefinierte Elemente erstellen, um Funktionen zu RDL hinzuzufügen, oder wie Sie vorhandene Steuerelemente erweitern.  
  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
 Beschreibt, wie benutzerdefinierte Assemblys mit Berichten verwendet werden, indem Codeverweise in die Berichtsdefinition aufgenommen werden.  
  
 [Access the Reporting Services WMI Provider (Zugreifen auf den Reporting Services-WMI-Anbieter)](../reporting-services/tools/access-the-reporting-services-wmi-provider.md)  
 Beschreibt, wie Sie den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-WMI-Anbieter zum Verwalten von Berichtsserverbereitstellungen verwenden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Reporting Services &#40;SSRS&#41;](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Berichtsdefinitionssprache (SSRS)](../reporting-services/reports/report-definition-language-ssrs.md)   
 [Technische Referenz (SSRS)](../reporting-services/technical-reference-ssrs.md)   
 [Sichere Entwicklung (Reporting Services)](../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
  
  
