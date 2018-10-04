---
title: SoapException-Klasse von Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: de33b2cdbc082e609e392d36aa53b8c5bbd2ce4f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48160492"
---
# <a name="reporting-services-soapexception-class"></a>Reporting Services-SoapException-Klasse
  Sie sollten bestimmte [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Fehler angeben, die erfahrungsgemäß auftreten können. In einer Anwendung, in der Sie den Benutzer auffordern, einen Ordner zu erstellen, kann es beispielsweise passieren, dass der Benutzer einen Ordner erstellen möchte, der bereits vorhanden ist. Als Entwickler können Sie nicht steuern, welchen Ordnernamen und welches Verzeichnis der Benutzer in der Anwendung angibt. Allerdings können Sie steuern, was passieren soll, wenn jemand ein Element erstellen möchte, das bereits vorhanden ist.  
  
 Um bestimmte Fehlerbedingungen leichter zu erfassen, klassifiziert [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] einen Fehlercode für die Ausnahme und gibt die Fehlerklassifizierung mithilfe der Eigenschaften aus der **SoapException**-Klasse zurück. Weitere Informationen finden Sie unter „SoapException-Klasse“ in der Dokumentation zum [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.  
  
 In der folgenden Tabelle sind die öffentlichen Eigenschaften der **SoapException**-Klasse aufgeführt.  
  
|Öffentliche Eigenschaft|Description|  
|---------------------|-----------------|  
|**Actor**|Der Code, der die Ausnahme verursacht hat. Der Wert ist die URL der Webdienstmethode.|  
|**Detail**|Anwendungsspezifische Fehlerinformationen. Der Wert wird vom Berichtsserver festgelegt und ist im XML-Format. Weitere Informationen finden Sie unter [Detail-Eigenschaft](detail-property.md) und [Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler](../best-practices/using-the-detail-property-to-handle-specific-errors.md).|  
|**HelpLink**|Eine URL oder eine URN zu einer zum Fehler gehörigen Hilfedatei. Der Wert wird normalerweise durch einen Webdienst festgelegt, und er richtet eine URL zu [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Hilfe und Support ein. Da [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] mehrere HelpLinks für auftretende Fehler unterstützt, richtet der Berichtsserver die HelpLink-Informationen als Teil der **Detail**-Eigenschaft ein. Weitere Informationen finden Sie unter [HelpLink-Element](helplink-element.md).|  
|**MessageBox**|Eine informative, lokalisierte Meldung, die den Fehler beschreibt. Dieser Text kann in der Benutzeroberfläche der Anwendung angezeigt werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Introducing Exception Handling in Reporting Services (Einführung in die Ausnahmebehandlung in Reporting Services)](../introducing-exception-handling-in-reporting-services.md)   
 [SoapException Errors Table (Tabelle für SoapException-Fehler)](soapexception-errors-table.md)  
  
  
