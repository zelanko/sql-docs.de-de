---
title: Die Rolle von SOAP in Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- SOAP [Reporting Services], role in Reporting Services
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: f229c3ef-f2ca-448f-98f1-b8df350b9992
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 02328b46cb9741a26d3e6b9b2d320ab28a879d55
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56038059"
---
# <a name="the-role-of-soap-in-reporting-services"></a>Die Rolle von SOAP in Reporting Services
  Der Berichtsserver-Webdienst verwendet SOAP-Messaging (Simple Object Access Protocol), um textbasierte Befehle über ein Netzwerk zu senden. Bei diesen Befehlen handelt es sich um XML-Text, der mit HTTP über das World Wide Web gesendet wird. Wenn SOAP als Kommunikationsprotokoll verwendet wird, erlaubt der Report Server-Webdienst Anwendungen und Komponenten den Datenaustausch mit dem Berichtsserver über eine offene und weit verbreitete Infrastruktur. Der SOAP-Standard wird unter www.w3.org/TR/SOAP definiert.  
  
 Jede Clientanwendung kann als SOAP-Client dienen, wenn sie SOAP erkennt und SOAP-Anforderungen senden kann. Der Berichts-Manager ist ein solcher SOAP-Client. Er bietet eine Schnittstelle zur Berichtsserver-Datenbank, in der alle Berichte und alle mit dem Bericht verbundenen Inhalte gespeichert werden. Endbenutzer können mit der Anwendung Berichte und Ordner im Berichtsserver-Namespace durchsuchen und verwalten. Der Berichts-Manager basiert auf der Infrastruktur des Report Server-Webdiensts.  
  
 Ein Berichtsserver fungiert als ein SOAP-Server, ein Dienst, der SOAP erkennt und Anforderungen von SOAP-Clients akzeptieren sowie entsprechende Antworten zurückgeben kann. Der Server behandelt die Anforderungen und sendet codierte Antworten an den Client zurück.  
  
 SOAP-Nachrichten in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] können verschiedene Formate haben. Dies hängt von der Art der Anforderung ab, die vom Client gesendet wird. Das folgende Beispiel zeigt eine einfache Anforderung vom SOAP-Client, ein Element aus der Berichtsserver-Datenbank zu entfernen.  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItem xmlns="https://www.microsoft.com/sql/ReportingServer">  
            <item>/Samples/Report1</item>  
        </DeleteItem>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 SOAP selbst erfordert, dass Nachrichten in ein `Envelope`-Element gestellt werden, wobei sich der Großteil der Nachricht in einem `Body`-Element befindet. In diesem Beispiel enthält der Nachrichtentext einen Aufruf an die <xref:ReportService2010.ReportingService2010.DeleteItem%2A>-Methode, die einen Zeichenfolgenparameter akzeptiert, welcher den Pfad des zu löschenden Elements darstellt. Sie können eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Clientproxyklasse erstellen, die alle SOAP-Vorgänge in Methoden kapselt. Die folgende [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)]-Methode stellt das oben gezeigte SOAP-Beispiel dar.  
  
```  
public void DeleteItem(string item);  
```  
  
 Die Antwort vom Server könnte folgendermaßen aussehen:  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItemResponse xmlns="https://www.microsoft.com/sql/ReportingServer" />  
    </soap:Body>  
</soap:Envelope>  
```  
  
 Da die <xref:ReportService2010.ReportingService2010.DeleteItem%2A>-Methode über keinen Rückgabewert verfügt, wird eine leere Antwort zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Zugriff auf die SOAP-API](accessing-the-soap-api.md)   
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md)   
 [Reporting Services-Berichtsserver](../reporting-services-report-server.md)   
 [Report Server Web Service (Report Server-Webdienst)](report-server-web-service.md)  
  
  
