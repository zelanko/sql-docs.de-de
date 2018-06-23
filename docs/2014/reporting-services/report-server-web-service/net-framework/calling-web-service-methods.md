---
title: Webdienstmethoden aufrufen – Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
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
caps.latest.revision: 37
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: fce65cf5ed4e8342005e058aec793fa88e6aa182
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050254"
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
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Berichtsserver-Webdienst](../report-server-web-service.md)   
 [Technische Referenz (SSRS)](../../technical-reference-ssrs.md)  
  
  