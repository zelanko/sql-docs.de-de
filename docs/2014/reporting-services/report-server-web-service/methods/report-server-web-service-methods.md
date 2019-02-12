---
title: Webdienstmethoden für Berichtsserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- XML Web service [Reporting Services], features
- Web service [Reporting Services], features
- Report Server Web service, features
- XML Web service [Reporting Services], methods
ms.assetid: ce5afa27-e90c-44a7-b204-098a065b3665
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 44a9c9eda59b5bfd69d8d22f81f470a4ab46c21c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014651"
---
# <a name="report-server-web-service-methods"></a>Webdienstmethoden für Berichtsserver
  Der Berichtsserver-Webdienst umfasst mehrere Kategorien von Methoden, die auf Komponentenfunktionen basieren. Diese Methoden werden über mehrere Webdienst-Endpunkte (drei für die Berichtsverwaltung und einer für die Berichtsausführung) bereitgestellt, die als Mitglieder der Klassen <xref:ReportService2010.ReportingService2010> und <xref:ReportExecution2005.ReportExecutionService> verfügbar gemacht werden. Diese Klassen können über ein Proxyklassentool wie „wsdl.exe“ generiert werden, das im [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK enthalten ist. Weitere Informationen zu Berichtsserver-Webdiensten und [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] finden Sie unter [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
## <a name="endpoints-and-methods"></a>Endpunkte und Methoden  
 In der folgenden Tabelle sind die Endpunkte des Berichtsserver-Webdiensts und die vom <xref:ReportService2010.ReportingService2010>-Endpunkt bereitgestellten Methodenkategorien aufgeführt. Informationen zu den in den anderen Endpunkten verfügbaren Methoden finden Sie unter [Technische Referenz (SSRS)](../../technical-reference-ssrs.md).  
  
|Thema|Description|  
|-----------|-----------------|  
|[Report Server Web Service Endpoints (Report Server-Webdienst-Endpunkte)](report-server-web-service-endpoints.md)|Beschreibt die Verwaltungs- und Ausführungsendpunkte des Berichtsserver-Webdiensts.|  
|[Report Server Namespace Management Methods (Methoden zur Berichtsserver-Namespaceverwaltung)](report-server-namespace-management-methods.md)|Beschreibt Methoden, mit denen Sie die Berichtsserver-Datenbank verwalten können. Insbesondere können Sie Ordner und Ressourcen verwalten und Elementeigenschaften festlegen.|  
|[Authorization Methods (Autorisierungsmethoden)](authorization-methods.md)|Beschreibt Methoden, mit denen Sie Aufgaben, Rollen und Richtlinien verwalten können.|  
|[Data Sources and Connection Methods (Datenquellen- und Verbindungsmethoden)](data-sources-and-connection-methods.md)|Beschreibt Methoden, mit denen Sie Datenquellenverbindungen und Anmeldeinformationen für Berichte festlegen und verwalten können.|  
|[Report Parameters Methods (Melden von Parametermethoden)](report-parameters-methods.md)|Beschreibt Methoden, mit denen Sie Parameter für Berichte festlegen und abrufen können.|  
|[Modellmethoden](../report-server-web-service.md)|Beschreibt Methoden, mit denen Sie Modelle verwalten können.|  
|[Rendering and Execution Methods (Rendering- und Execution-Methode)](rendering-and-execution-methods.md)|Beschreibt Methoden, mit denen Sie die Berichtsausführung sowie das Rendern und Zwischenspeichern verwalten können.|  
|[Report History Methods (Berichtsverlaufsmethoden)](report-history-methods.md)|Beschreibt Methoden, mit denen Sie Berichtsverlaufs-Momentaufnahmen erstellen und verwalten können.|  
|[Scheduling Methods (Zeitplanmethoden)](scheduling-methods.md)|Beschreibt Methoden, mit denen Sie freigegebene Zeitpläne und Cacheaktualisierungspläne, die auf dem Berichtsserver verwendet werden, erstellen und verwalten können.|  
|[Subscription and Delivery Methods (Abonnement und Übermittlungsmethoden)](subscription-and-delivery-methods.md)|Beschreibt Methoden, mit denen Sie Abonnements und die Übermittlung von Berichten erstellen und verwalten können.|  
|[Linked Reports Methods (Methoden für verknüpfte Berichte)](linked-reports-methods.md)|Beschreibt Methoden, mit denen Sie verknüpfte Berichte erstellen und verwalten können.|  
  
## <a name="see-also"></a>Siehe auch  
 [Zugriff auf die SOAP-API](../accessing-the-soap-api.md)   
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Berichtsserver-Webdienst](../report-server-web-service.md)   
 [Technische Referenz (SSRS)](../../technical-reference-ssrs.md)  
  
  
