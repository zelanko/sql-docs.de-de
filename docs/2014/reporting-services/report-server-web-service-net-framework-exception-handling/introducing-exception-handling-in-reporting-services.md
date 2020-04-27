---
title: Einführung der Ausnahmebehandlung in Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 091b1f40d293515617e369b750a5f18dfe12951b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63012323"
---
# <a name="introducing-exception-handling-in-reporting-services"></a>Einführung in die Ausnahmebehandlung in Reporting Services
  Wenn die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Anwendung die Anforderung an den Berichtsserver-Webdienst sendet, dass der Dienst die Verarbeitung nicht durchführen kann, gibt der Dienst eine SOAP-Ausnahme an den Client zurück. Die Behandlung von Ausnahmen, die vom Berichtsserver-Webdienst ausgelöst werden, stellt einen wichtigen Teil der Anwendungen dar, die Sie entwickeln, da Sie damit sinnvolle Informationen an die Benutzer zurückgeben können, wenn ein Fehler auftritt.  
  
 Dieser Abschnitt enthält spezielle Informationen zur Ausnahmebehandlung, damit ungültige Benutzereingaben verhindert und sinnvolle Fehlermeldungen an die Benutzer ausgegeben werden. Allgemeine Informationen zur Ausnahmebehandlung finden Sie unter "behandeln und Auslösen von Ausnahmen" in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] der SDK-Dokumentation.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Behandeln von Ausnahmen in Reporting Services](handling-exceptions-in-reporting-services.md)|Bietet eine Übersicht der Ausnahmen in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und die Rolle von SOAP, wenn Fehler von einem Webdienst zurückgegeben werden.|  
|[Bewährte Methoden für die Ausnahmebehandlung in Reporting Services](best-practices/best-practices-for-reporting-services-exception-handling.md)|Gibt Empfehlungen darüber, wie Ausnahmen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] behandelt werden sollten.|  
|[Reporting Services-SoapException-Klasse](soapexception-class/reporting-services-soapexception-class.md)|Beschreibt die **SoapException**-Klasse in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
