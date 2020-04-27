---
title: Webdienst für Berichtsserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b577fd9a78dbb5f12af79e190709065931ec463a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62520560"
---
# <a name="report-server-web-service"></a>Report Server-Webdienst
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet Zugriff auf die vollständige Funktionalität des Berichts Servers über den Report Server-Webdienst. Der Berichtsserver-Webdienst stellt einen XML-Webdienst mit einer SOAP-API dar. Er verwendet SOAP über HTTP und agiert als Kommunikationsschnittstelle zwischen den Clientprogrammen und dem Berichtsserver. Der Webdienst versieht zwei Endpunkte (einen für die Berichtsausführung und einen für die Berichtsverwaltung) mit Methoden, anhand derer die Funktionen des Berichtsservers zugänglich gemacht werden und die Ihnen die Erstellung benutzerdefinierter Tools für jeden Teil des gesamten Berichtslebenszyklus ermöglichen.  
  
 Es gibt drei Hauptmöglichkeiten, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Anwendungen auf Grundlage des Webdiensts zu entwickeln. Sie können:  
  
-   Entwickeln Sie Anwendungen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mit und [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] dem SDK. Weitere Informationen zur Verwendung von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] zur Erstellung von Webdienstanwendungen finden Sie unter [Building Applications Using the Web Service and the .NET Framework (Erstellen von Anwendungen mit dem Webdienst und .NET Framework)](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
-   Entwickeln Sie Anwendungen mit dem **RS**-Hilfsprogramm (RS.exe) und der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Skriptumgebung. Mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]- und [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]-Skripts können alle Vorgänge des Berichtsserver-Webdiensts ausgeführt werden. Weitere Informationen zur Skripterstellung in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] finden Sie unter [Skripterstellung mit dem Hilfsprogramm rs.exe und dem Webdienst](../tools/script-with-the-rs-exe-utility-and-the-web-service.md).  
  
-   Entwickeln Sie Anwendungen mithilfe von SOAP-aktivierten Entwicklungstools. Weitere Informationen finden Sie unter [The Role of SOAP in Reporting Services (Die Rolle von SOAP in Reporting Services)](../report-server-web-service/the-role-of-soap-in-reporting-services.md).  
  
## <a name="programming-diagram"></a>Programmierdiagramm  
 ![Entwicklungsoptionen für den Berichtsserver-Webdienst](../../../2014/reporting-services/media/reportserviceswebserviceprog-01.gif "Entwicklungsoptionen für den Berichtsserver-Webdienst")  
Reporting Services, verfügbare Webdienstentwicklungsoptionen  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Webdienstmethoden für Berichtsserver](../report-server-web-service/methods/report-server-web-service-methods.md)  
 Beschreibt die Funktionen und Methoden jedes Berichtsserver-Webdiensts.  
  
 [Die Rolle von SOAP in Reporting Services](../report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 Bietet eine Übersicht über SOAP und erläutert die Verwendung in den Berichtsserver-Webdiensten.  
  
 [Accessing the SOAP API](../report-server-web-service/accessing-the-soap-api.md)  
 Beschreibt die Webdienstbeschreibungssprache (WSDL) und stellt URLs bereit, mit denen auf eine Reporting Services-WSDL-Datei zugegriffen werden kann.  
  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 Enthält Informationen über die Entwicklung von Anwendungen und Webdiensten, die die Reporting Services-SOAP-API aufrufen.  
  
 [Skripterstellung mit dem Hilfsprogramm rs.exe und dem Webdienst](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 Enthält eine Übersicht über die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Skriptumgebung.  
  
 [Technische Referenz (SSRS)](../../../2014/reporting-services/technical-reference-ssrs.md)  
 Enthält Referenzmaterial, das speziell für die Methoden des Berichtsserver-Webdiensts und die entsprechenden komplexen Typen bestimmt ist.  
  
## <a name="user-requirements-for-web-service-development"></a>Benutzeranforderungen für Webdienstentwicklung  
 Um Anwendungen mithilfe des Berichtserver-Webdiensts zu entwickeln, benötigen Sie:  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 5.5 oder eine spätere Version auf Ihrem Computer, einen Internetanschluss und Zugriff auf den Berichtsserver.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] oder das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK, das auf einem Computer installiert ist, wenn Sie [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Anwendungen mithilfe [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]von entwickeln und bereitstellen möchten.  
  
-   Ein detailliertes Verständnis der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Features und Funktionen.  
  
-   Sehr gute Kenntnisse von SOAP und [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)].  
  
-   Entwicklung in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]einer-kompatiblen Sprache wie [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]oder, wenn Sie planen, [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] als Entwicklungsplattform zu verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Report Server Web Service (Report Server-Webdienst)](../report-server-web-service/report-server-web-service.md)  
  
  
