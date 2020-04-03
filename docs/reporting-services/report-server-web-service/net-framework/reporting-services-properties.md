---
title: Eigenschaften von Reporting Services | Microsoft-Dokumentation
description: Ein Berichtsserver definiert globale Systemeigenschaften und einzelne Elementeigenschaften. Anwendungen können den System- und Elementeigenschaften benutzerdefinierte Eigenschaften hinzufügen.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- properties [Reporting Services], about properties
- reports [Reporting Services], properties
- Report Server Web service, properties
- report properties [Reporting Services]
- XML Web service [Reporting Services], properties
- Web service [Reporting Services], properties
- properties [Reporting Services]
ms.assetid: 8c855194-4c20-4ecc-a328-5137d54b560c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7240bf3e987c5817489035d94879817f5f39569b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "79509711"
---
# <a name="reporting-services-properties"></a>Eigenschaften von Reporting Services
  Der Berichtsserver definiert eine Reihe von Systemeigenschaften, die global für den Berichtsserver gelten, und eine Reihe von Elementeigenschaften, die zu einem in der Berichtsserver-Datenbank gespeicherten Einzelelement gehören. Vom Berichtsserver definierte Eigenschaften können nicht gelöscht werden, und in einigen Fällen sind sie schreibgeschützt. In einer Anwendung können die System- und Elementeigenschaften erweitert werden, indem zusätzliche benutzerdefinierte Eigenschaften zu den System- und den Elementeigenschaften hinzugefügt werden.  
  
 Die folgenden Webdienstmethoden rufen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Eigenschaften ab und legen diese fest.  
  
|Methode|Aktion|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|Gibt die Werte von einer oder mehreren Eigenschaften eines Elements in der Berichtsserver-Datenbank zurück.|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|Gibt eine oder mehrere Systemeigenschaften zurück.|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|Legt eine oder mehrere Eigenschaften eines Elements in der Berichtsserver-Datenbank fest.|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|Legt eine oder mehrere Systemeigenschaften fest.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Eigenschaften der Berichtsserverelemente](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-item-properties.md)|Beschreibt die elementspezifischen Eigenschaften in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Berichtsserver-Systemeigenschaften](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)|Beschreibt die systemspezifischen Eigenschaften in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Berichtsserver-Webdienst](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Technische Referenz (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
