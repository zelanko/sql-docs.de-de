---
title: HelpLink-Element | Microsoft-Dokumentation
description: Dieser Artikel informiert Sie über das Element „HelpLink“ der Eigenschaft „Detail“, einschließlich der Argumente der HelpLink-URL.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- HelpLink element
- SoapException class
ms.assetid: a4489103-a874-44c2-8f75-95cb238928ed
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5a03f514b2305676d93ada0119326c101595f9c3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "80215670"
---
# <a name="helplink-element"></a>HelpLink-Element
  Das **HelpLink** -Element der **Detail** -Eigenschaft ist eine URL-Zeichenfolge, die vom Berichtsserver generiert wird. Die URL steuert eine Webseite an, die von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Hilfe und Support verwaltet wird. Sie liefert zusätzliche Hilfestellungen und Artikel der Kowledge Base zu bestimmten Fehlern, die in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]auftreten. Die URL hat folgende Syntax:  
  
 **https://** www\.microsoft.com**/** products**/** ee**/** transform.aspx **?EvtSrc**=v_alue_**&EvtID**=_value_**&ProdName**=_value_**&ProdVer**=*value*  
  
 In der folgenden Tabelle sind die Argumente der **HelpLink** -URL aufgeführt.  
  
|Argument|Wert|  
|--------------|-----------|  
|**EvtSrc**|"Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings"|  
|**EvtID**|Der Fehlercode für den Berichtsserver, z. B. rsReservedItem.|  
|**ProdName**|"Microsoft SQL%20Server%20Reporting%20Services". Der Wert des Produktnamens ist URL-codiert.|  
|**ProdVer**|Die Versionsnummer von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Der Wert „8.00“ gibt [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] an.|  
  
 In folgendem Beispiel wird die **HelpLink** -URL erläutert, die für den Fehlercode **rsReservedItem**zurückgegeben wird. Dieser Fehler tritt auf, wenn ein Benutzer versucht, ein reserviertes Element in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]zu ändern oder zu löschen:  
  
```  
https://www.microsoft.com/products/ee/transform.aspx?  
EvtSrc=Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings  
&EvtID=rsReservedItem&ProdName=Microsoft%20SQL%20Server%20Reporting%20Services&ProdVer=8.00  
```  
  
 Sie können auf das **HelpLink** -Element im Code zugreifen, indem Sie die **SoapException** -Klasse verwenden.  
  
```vb  
Try  
   rs.DeleteItem("/Report1")  
  
Catch e As SoapException  
   Console.WriteLine(e.Detail("HelpLink").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.DeleteItem("/Report1");  
}  
  
catch (SoapException e)  
{  
   Console.WriteLine(e.Detail["HelpLink"].InnerXml);  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Introducing Exception Handling in Reporting Services (Einführung in die Ausnahmebehandlung in Reporting Services)](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [SoapException-Klasse von Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [Using the Detail Property to Handle Specific Errors (Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler)](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
