---
title: Behandeln von Warnungen und Fällen, die keine Ausnahmen verursachen | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], warnings that don't cause
- warnings [Reporting Services]
ms.assetid: 475c0713-6265-44e7-9ebc-ebdd1b89e0af
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4c2c58a5edf42966ba828288c2aa8b84dbb49967
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046102"
---
# <a name="handling-warnings-and-cases-that-do-not-cause-exceptions"></a>Behandeln von Warnungen und Fällen, die keine Ausnahmen verursachen
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] löst keine Ausnahmen für Warnungen und bestimmte Fehler aus. Wenn Sie z. B. die Methode <xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> verwenden, um einen neuen Bericht auf dem Berichtsserver zu veröffentlichen, werden alle auftretenden Warnungen als Array der <xref:ReportService2010.Warning>-Objekte zurückgegeben. Diese Warnungen sollten so behandelt und angezeigt werden, dass eine entsprechende Maßnahme getroffen werden kann.  
  
```vb  
Try  
   rs.CreateCatalogItem(name, parentFolder, False, definition, Nothing, warnings)  
  
   If Not (warnings.Length = 0) Then  
      Dim warning As Warning  
      For Each warning In warnings  
         Console.WriteLine(warning.Message)  
      Next warning  
   Else  
      Console.WriteLine("Report {0} created successfully with no warnings", name)  
   End If  
  
Catch ex As SoapException  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.CreateCatalogItem("Report", name, parentFolder, false, definition, null, out warnings);  
  
   if (warnings.Length != 0)  
   {  
      foreach (Warning warning in warnings)  
      {  
         Console.WriteLine(warning.Message);  
      }  
   }  
   else  
      Console.WriteLine("Report {0} created successfully with no warnings", name);  
}  
  
catch (SoapException ex)  
{  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
 Eine andere Möglichkeit der Fehlerbehandlung liegt in der Auswertung der Rückgabewerte bestimmter Methoden. Beispiel: Mithilfe der Methode <xref:ReportService2010.ReportingService2010.FindItems%2A> können bestimmte Elemente in der Berichtsserver-Datenbank gesucht werden. Wenn keine Elemente gefunden werden, die den Suchkriterien entsprechen, wird ein NULL-Array von <xref:ReportService2010.CatalogItem>-Objekten zurückgegeben. Sie sollten dieses Array auswerten, nach `null` suchen und den Benutzer wissen lassen, dass keine Elemente gefunden wurden.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:ReportService2010.CatalogItem>   
 [Einführung in die Ausnahmebehandlung in Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services-SoapException-Klasse](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
