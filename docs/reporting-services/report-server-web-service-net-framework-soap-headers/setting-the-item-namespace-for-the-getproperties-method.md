---
description: Festlegen des Elementnamespaces für die GetProperties-Methode
title: Festlegen des Elementnamespaces für die GetProperties-Methode | Microsoft-Dokumentation
Description: In diesem Artikel wird beschrieben, wie Eigenschaften anhand des Pfads oder einer Element-ID mit der Methode „GetProperties“und dem SOAP-Header „ItemNamespaceHeader“ abgerufen werden können.
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-soap-headers
ms.topic: reference
helpviewer_keywords:
- item properties [Reporting Services]
- ItemNamespaceHeader SOAP header
- GetProperties method
ms.assetid: b0a08639-3101-40a2-abe2-3a41753826d1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fc0d61726a885b6a2422a4fe048121e65b8642f8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423244"
---
# <a name="setting-the-item-namespace-for-the-getproperties-method"></a>Festlegen des Elementnamespaces für die GetProperties-Methode
  Sie können den <xref:ReportService2010.ItemNamespaceHeader>SOAP-Header[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwenden, um die Elementeigenschaften über zwei verschiedene Elementbezeichner abzurufen: über den vollständigen Pfad des Elements oder die ID des Elements.  
  
 Wenn Sie die <xref:ReportService2010.ReportingService2010.GetProperties%2A>-Methode abrufen, übergeben Sie normalerweise den vollständigen Pfad des Elements, dessen Eigenschaften Sie abrufen möchten, als Argument. Mithilfe von <xref:ReportService2010.ItemNamespaceHeader> können Sie den SOAP-Header für den Methodenaufruf so einstellen, dass Sie <xref:ReportService2010.ReportingService2010.GetProperties%2A> verwenden können, indem Sie die ID des Elements als Bezeichner übergeben.  
  
 Im folgenden Codebeispiel werden die Werte für die Elementeigenschaften auf Grundlage der ID des Elements abgerufen.  
  
> [!NOTE]  
>  Sie müssen standardmäßig keinen Wert für <xref:ReportService2010.ItemNamespaceHeader> festlegen, wenn Sie den vollständigen Pfadnamen als Elementbezeichner an die <xref:ReportService2010.ReportingService2010.GetProperties%2A>-Methode übergeben.  
  
```vb  
Imports System  
Imports System.Collections  
  
Class Sample  
   Sub Main()  
      Dim rs As New ReportingService2010()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      rs.Url = "https://<Server Name>/reportserver/ReportService2010.asmx"  
  
      Dim items() As CatalogItem  
  
      Try  
         ' Need the ID property of items. Normally, you would already have   
         ' this stored somewhere.  
         items = rs.ListChildren("/AdventureWorks Sample Reports", False)  
  
         ' Set the item namespace header to be GUID-based  
         rs.ItemNamespaceHeaderValue = New ItemNamespaceHeader()  
         rs.ItemNamespaceHeaderValue.ItemNamespace = ItemNamespaceEnum.GUIDBased  
  
         ' Call GetProperties with item ID.  
         If Not (items Is Nothing) Then  
            Dim item As CatalogItem  
            For Each item In  items  
               Dim properties As [Property]() = rs.GetProperties(item.ID, Nothing)  
               Dim property As [Property]  
               For Each property In  properties  
                  Console.WriteLine(([property].Name + ": " + [property].Value))  
               Next property  
               Console.WriteLine()  
            Next item  
         End If  
  
      Catch e As Exception  
         Console.WriteLine((e.Message + ": " + e.StackTrace))  
      End Try  
   End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.Collections;  
  
class Sample  
{  
   static void Main()  
   {  
   ReportingService2010 rs = new ReportingService2010();  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      rs.Url = "https://<Server Name>/reportserver/ReportService2010.asmx";  
  
      CatalogItem[] items;  
  
      try  
      {  
         // Need the ID property of items. Normally, you would already have   
         // this stored somewhere.  
         items = rs.ListChildren("/AdventureWorks Sample Reports", false);  
  
         // Set the item namespace header to be GUID-based  
         rs.ItemNamespaceHeaderValue = new ItemNamespaceHeader();  
         rs.ItemNamespaceHeaderValue.ItemNamespace = ItemNamespaceEnum.GUIDBased;  
  
         // Call GetProperties with item ID.  
         if (items != null)  
         {  
            foreach( CatalogItem item in items)  
            {  
               Property[] properties = rs.GetProperties(item.ID, null);  
               foreach (Property property in properties)  
               {  
                  Console.WriteLine(property.Name + ": " + property.Value);  
               }  
               Console.WriteLine();  
            }  
         }  
      }  
  
      catch (Exception e)  
      {  
         Console.WriteLine(e.Message);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Technische Referenz (SSRS)](../../reporting-services/technical-reference-ssrs.md)   
 [Verwenden von Reporting Services SOAP-Headern](../../reporting-services/report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)  
  
  
