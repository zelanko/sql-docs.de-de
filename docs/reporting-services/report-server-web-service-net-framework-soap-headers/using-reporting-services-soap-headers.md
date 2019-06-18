---
title: Verwenden von Reporting Services SOAP-Headern | Microsoft-Dokumentation
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-soap-headers
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 99a4ac18003defd2a6b3cffdd4bc1d2955c44816
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63026011"
---
# <a name="using-reporting-services-soap-headers"></a>Verwenden von Reporting Services SOAP-Headern
  Die Kommunikation mit einer Webdienstmethode über SOAP erfolgt nach einem Standardformat. Teil dieses Formats bilden die Daten, die in einem XML-Dokument verschlüsselt sind. Das XML-Dokument besteht aus einem **Envelope**-Stammelement, das sich wiederum aus einem erforderlichen **Textkörper**-Element und einem optionalen **Header**-Element zusammensetzt. Das **Textelement** enthält die für die Meldung spezifischen Daten. Das optionale **Header**-Element kann zusätzliche Informationen umfassen, die sich nicht direkt auf die spezifische Meldung beziehen. Die untergeordneten Elemente des **Header**-Elements werden SOAP-Header genannt.  
  
 Obwohl die SOAP-Header Daten enthalten können, die sich auf die Meldung beziehen, beinhalten sie in der Regel von der Infrastruktur des Webservers verarbeitete Informationen.  
  
 Die Berichtsserver-Webdienste definieren mehrere Klassen für die Verwendung im SOAP-Header: <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader> und <xref:ReportExecution2005.ExecutionHeader>.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|und Beschreibung|  
|-----------|-----------------|  
|[Batching Methods (Methoden der Batchverarbeitung) ](../../reporting-services/report-server-web-service-net-framework-soap-headers/batching-methods.md)|Beschreibt, wie mehrere Vorgänge mithilfe von <xref:ReportService2005.BatchHeader> in einer Batchtransaktion verarbeitet werden können.|  
|[Identifying Execution State (Identifizieren des Ausführungsstatus)](../../reporting-services/report-server-web-service-net-framework-soap-headers/identifying-execution-state.md)|Beschreibt, wie der Sitzungsstatus in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mit **SessionHeader** (Sitzungsheader) verwaltet werden kann.|  
|[Setting the Item Namespace for the GetProperties Method (Festlegen des Elementnamespaces für die GetProperties-Methode)](../../reporting-services/report-server-web-service-net-framework-soap-headers/setting-the-item-namespace-for-the-getproperties-method.md)|Beschreibt, wie Eigenschaften anhand des Pfads oder der ID des Elements mit der <xref:ReportService2010.ReportingService2010.GetProperties%2A>-Methode und dem <xref:ReportService2010.ItemNamespaceHeader>-SOAP-Header abgerufen werden können.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Technische Referenz (SSRS)](../../reporting-services/technical-reference-ssrs.md)  
  
  
