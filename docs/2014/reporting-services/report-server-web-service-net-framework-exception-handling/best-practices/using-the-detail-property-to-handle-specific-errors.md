---
title: Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 39d820d82cc761afcc842dd4fe09bf5a7a4d60c9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56023461"
---
# <a name="using-the-detail-property-to-handle-specific-errors"></a>Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler
  Zur weiteren Klassifizierung von Ausnahmen gibt [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] zusätzliche Fehlerinformationen in der **InnerText**-Eigenschaft der untergeordneten Elemente in der **Detail**-Eigenschaft der SOAP-Ausnahme zurück. Da die **Detail**-Eigenschaft ein **XmlNode**-Objekt ist, können Sie mit folgendem Code auf den inneren Text des untergeordneten **Message**-Elements zugreifen.  
  
 Eine Liste aller verfügbaren untergeordneten Elemente, die in der **Detail**-Eigenschaft enthalten sind, finden Sie unter [Detail-Eigenschaft](../soapexception-class/detail-property.md). Weitere Informationen finden Sie unter „Detail-Eigenschaft“ in der Dokumentation zum [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Introducing Exception Handling in Reporting Services (Einführung in die Ausnahmebehandlung in Reporting Services)](../introducing-exception-handling-in-reporting-services.md)   
 [SoapException-Klasse von Reporting Services](../soapexception-class/reporting-services-soapexception-class.md)   
 [SoapException Errors Table (Tabelle für SoapException-Fehler)](../soapexception-class/soapexception-errors-table.md)  
  
  
