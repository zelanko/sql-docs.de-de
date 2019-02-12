---
title: Verwenden der IDeliveryReportServerInformation-Schnittstelle für Übermittlungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d211842a43af771e953fd74a15403ba9321f2860
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56028001"
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a>Verwenden der IDeliveryReportServerInformation-Schnittstelle für Übermittlungserweiterungen
  Die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>-Schnittstelle macht mehrere Eigenschaften verfügbar, die Sie verwenden können, um Informationen über einen Berichtsserver abzurufen. Sie können diese Informationen verwenden, um Benachrichtigungen und Berichte zu übermitteln. Beim Implementieren der Übermittlungserweiterung implementieren Sie die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A>-Eigenschaft wie von der <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>-Schnittstelle gefordert. Die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A>-Eigenschaft gibt ein Objekt zurück, das die <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>-Schnittstelle implementiert. Von diesem Objekt können Sie eine Liste der Renderingerweiterungen abrufen, die derzeit vom Berichtsserver unterstützt werden.  
  
 Die folgenden `for` Schleife verwendet werden, um eine Liste der derzeit verfügbaren Renderingerweiterungen zu speichern, auf dem Berichtsserver in eine **ArrayList** Objekt.  
  
```vb  
Dim renderFormats As New ArrayList()  
Dim e As Microsoft.ReportingServices.Interfaces.Extension  
For Each e In  ReportServerInformation.RenderingExtension  
   If e.Visible Then  
      renderFormats.Add(e.Name)  
   End If  
Next e  
```  
  
```csharp  
ArrayList renderFormats = new ArrayList();  
foreach (Microsoft.ReportingServices.Interfaces.Extension e in ReportServerInformation.RenderingExtension)  
{   
   if (e.Visible)  
   {  
      renderFormats.Add(e.Name);  
   }  
}  
```  
  
 Weitere Informationen zur <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>-Schnittstelle finden Sie unter [Verwenden der IDeliveryReportServerInformation-Schnittstelle für Übermittlungserweiterungen](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [Implementieren von Übermittlungserweiterungen](implementing-a-delivery-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
