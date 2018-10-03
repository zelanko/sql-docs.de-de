---
title: Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler | Microsoft-Dokumentation
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 4aebb8febbf181a54ed32f31096c408c04c1dae3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621988"
---
# <a name="using-the-detail-property-to-handle-specific-errors"></a>Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler
  Zur weiteren Klassifizierung von Ausnahmen gibt [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] zusätzliche Fehlerinformationen in der **InnerText**-Eigenschaft der untergeordneten Elemente in der **Detail**-Eigenschaft der SOAP-Ausnahme zurück. Da die **Detail**-Eigenschaft ein **XmlNode**-Objekt ist, können Sie mit folgendem Code auf den inneren Text des untergeordneten **Message**-Elements zugreifen.  
  
 Eine Liste aller verfügbaren untergeordneten Elemente, die in der **Detail**-Eigenschaft enthalten sind, finden Sie unter [Detail-Eigenschaft](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md). Weitere Informationen finden Sie unter „Detail-Eigenschaft“ in der Dokumentation zum [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   ' The exception is a SOAP exception, so use  
   ' the Detail property's Message element.  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   // The exception is a SOAP exception, so use  
   // the Detail property's Message element.  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   If ex.Detail("ErrorCode").InnerXml = "rsInvalidItemName" Then  
   End If ' Perform an action based on the specific error code  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   if (ex.Detail["ErrorCode"].InnerXml == "rsInvalidItemName")  
   {  
      // Perform an action based on the specific error code  
   }  
}  
```  
  
 Folgende Codezeile gibt den spezifischen Fehlercode wieder, der in der SOAP-Ausnahme zur Konsole zurückgegeben wird. Sie können den Fehlercode auch auswerten und bestimmte Aktionen ausführen.  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Introducing Exception Handling in Reporting Services (Einführung in die Ausnahmebehandlung in Reporting Services)](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [SoapException-Klasse von Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [SoapException Errors Table (Tabelle für SoapException-Fehler)](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/soapexception-errors-table.md)  
  
  
