---
title: Verwenden der IDeliveryReportServerInformation-Schnittstelle für Übermittlungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a94b6da8536ee0269a448b8a446fc0da3f3f576
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63164043"
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
  
  
