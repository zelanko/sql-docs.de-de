---
title: Erstellen von Anwendungen mit dem Webdienst und .NET Framework | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application building
- .NET Framework [Reporting Services]
- XML Web service [Reporting Services], client creation
- reports [Reporting Services], building
- Web service [Reporting Services], application building
- Report Server Web service, client creation
- client configuration [Reporting Services]
- XML Web service [Reporting Services], application building
- Web service [Reporting Services], client creation
ms.assetid: 92a9678c-bc4f-4d7a-ba44-85989bfe27ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5136c67077ff90e7bbbd66ae72fed891267ba7a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62520344"
---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a>Erstellen von Anwendungen mit dem Webdienst und .NET Framework
  Mit können [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]Sie bekannte Programmierkonstrukte, wie z. b. Methoden, primitive Typen und benutzerdefinierte komplexe Typen, für die Arbeit mit Webdiensten verwenden. 
  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] enthält eine Infrastruktur und Tools, mit denen Sie Webdienstclients erstellen können, die jeden Webdienst von World Wide Web Consortium (W3C) aufrufen können, der den Standards entspricht.  
  
 Ein Berichtsserver-Webdienstclient ist jede Komponente oder Anwendung, die mit einem Berichtsserver über SOAP-Nachrichten (Simple Object Access Protocol) kommuniziert.  
  
 **Um einen Report Server-Webdienst Client mithilfe des .NET Framework zu erstellen, führen Sie die folgenden grundlegenden Schritte aus:**  
  
1.  Erstellen Sie eine Proxyklasse für den Webdienst.  
  
     Hierzu fügen Sie eine Proxyklasse oder einen Webverweis zu Ihrem Entwicklungsprojekt hinzu, verweisen auf die Proxyklasse im Clientcode und erstellen eine Instanz für diesen Proxy. Weitere Informationen finden Sie unter [Erstellen des Webdienstproxys](creating-the-web-service-proxy.md).  
  
2.  Authentifizieren Sie den Webdienstclient mit dem Berichtsserver.  
  
     Hierzu stellen Sie die <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A>-Eigenschaft des Dienstobjekts auf die Anmeldeinformationen eines authentifizierten Benutzers auf dem Berichtsserver ein. Weitere Informationen finden Sie unter [Webdienstauthentifizierung](web-service-authentication.md).  
  
3.  Rufen Sie die Methode der Proxyklasse auf, die dem Webdienstvorgang entspricht, den Sie aufrufen möchten.  
  
     Rufen Sie hierzu eine Webdienstmethode auf, und geben Sie die notwendigen Argumente an. Weitere Informationen zu den Webdienstmethoden finden Sie unter [Report Server Web Service Methods (Webdienstmethoden für Berichtsserver)](../methods/report-server-web-service-methods.md). Weitere Informationen über Aufrufe finden Sie unter [Calling Web Service Methods (Aufrufen von Webdienstmethoden)](calling-web-service-methods.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Erstellen des Webdienstproxys](creating-the-web-service-proxy.md)|Beschreibt die Möglichkeiten, dem Projekt mit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]eine Proxy Klasse hinzuzufügen.|  
|[Webdienstauthentifizierung](web-service-authentication.md)|Beschreibt, wie Aufrufe des Berichtsserver-Webdiensts authentifiziert werden.|  
|[Aufrufen von Webdienstmethoden](calling-web-service-methods.md)|Beschreibt, wie die SOAP-API verwendet wird, um Webdienst [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]Methoden in aufzurufen.|  
|[Festlegen der URL-Eigenschaft des Webdiensts](setting-the-url-property-of-the-web-service.md)|Erläutert, wie Sie den Webdienstproxy programmgesteuert auf eine neue Server-URL richten, nachdem Sie den Webverweis erstellt haben.|  
|[Bereitstellen von Argumenten für Webdienstmethoden](supplying-web-service-method-arguments.md)|Beschreibt, wie Sie eine Webdienstmethode aufrufen und Methodenargumente angeben.|  
|[Weglassen von Werten für optionale Webdienstobjekte](omitting-values-for-optional-web-service-objects.md)|Beschreibt, wie Werte für optionale Webdienstobjekte weggelassen werden.|  
|[Verwenden von sicheren Webdienstmethoden](using-secure-web-service-methods.md)|Beschreibt die **SecureConnectionLevel**-Einstellung und die Art und Weise, wie sie die Verwendung der Reporting Services-SOAP-API beeinflusst.|  
|[Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](passing-device-information-settings-to-rendering-extensions.md)|Beschreibt die Geräteinfoeinstellungen, die verwendet werden, um Berichte in andere Formate zu rendern.|  
|[Einstellungen der Reporting Services-Übermittlungserweiterungen](reporting-services-delivery-extension-settings.md)|Beschreibt die Einstellungen, die verwendet werden, um Berichte über Berichtsserver-E-Mail zu übermitteln.|  
|[Using Reporting Services SOAP Headers (Verwenden von Reporting Services SOAP-Headern)](../../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|Erklärt die Verwendung von SOAP-Headern in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Einführung in die Ausnahmebehandlung in Reporting Services](../../report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|Gibt Informationen über die Art, wie [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Fehler handhabt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsserver-Webdienst](../report-server-web-service.md)   
 [Technische Referenz (SSRS)](../../technical-reference-ssrs.md)  
  
  
