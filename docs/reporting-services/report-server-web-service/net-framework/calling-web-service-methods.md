---
title: Webdienstmethoden aufrufen – Microsoft-Dokumentation
description: In diesem Artikel wird das Aufrufen von Methoden einer Proxyklasse zum Durchführen von Berichterstellungsvorgängen auf dem Berichtsserver behandelt. Webdienstmethoden verfügen über öffentlichen Zugriff und erfordern entsprechende Argumente.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Web service [Reporting Services], calls
- calling Web service
- Report Server Web service, SOAP
- XML Web service [Reporting Services], calls
- Report Server Web service, calls
- XML Web service [Reporting Services], SOAP
- SOAP [Reporting Services], calls
ms.assetid: f6f0c6e3-8bb5-4c44-9d19-1872edc72746
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0e7347bfcb93d327bc6e56eb91c903bbc5e1f38f
ms.sourcegitcommit: d1f6da6f0f5e9630261cf733c64958938a3eb859
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2020
ms.locfileid: "79198325"
---
# <a name="calling-web-service-methods"></a>Aufrufen von Webdienstmethoden
  Wenn Sie eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Proxyklasse verwenden, um Webdienstvorgänge aufzurufen, verwenden Sie die Methoden dieser Klasse. Diese Methoden verhalten sich wie jede andere Methode einer Klasse in der [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Klassenbibliothek. Alle Webdienstmethoden verfügen über öffentlichen Zugriff, und es ist erforderlich, dass Sie die geeignete Anzahl von Argumenten und Argumenttypen angeben. Nachdem Sie eine Instanz der Proxyklasse im Projekt erstellt haben, können Sie die Methoden zum Ausführen von Berichterstellungsvorgängen über den Berichtsserver aufrufen. Im folgenden C#-Code wird die Verwendung der <xref:ReportService2010.ReportingService2010.ListChildren%2A>-Methode der <xref:ReportService2010.ReportingService2010>-Proxyklasse veranschaulicht. Der Code wird dazu verwendet, einen rekursiven Aufruf an den Webdienst auszuführen, der ein Array von <xref:ReportService2010.CatalogItem>-Objekten zurückgibt, das eine Liste aller Elemente in der Berichtsserver-Datenbank enthält:  
  
```vb  
Dim rs As New ReportingService2010()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
Dim items As CatalogItem() = rs.ListChildren("/", True)  
```  
  
```csharp  
ReportingService2010 rs = new ReportingService2010();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
CatalogItem[] items = rs.ListChildren("/", true);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Berichtsserver-Webdienst](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Technische Referenz (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
