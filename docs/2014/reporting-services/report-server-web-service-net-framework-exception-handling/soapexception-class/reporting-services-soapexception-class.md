---
title: SoapException-Klasse von Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f6efdfac89014116957990ef2db21cf52e76a4f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046032"
---
# <a name="reporting-services-soapexception-class"></a>Reporting Services-SoapException-Klasse
  Sie sollten bestimmte [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Fehler angeben, die erfahrungsgemäß auftreten können. In einer Anwendung, in der Sie den Benutzer auffordern, einen Ordner zu erstellen, kann es beispielsweise passieren, dass der Benutzer einen Ordner erstellen möchte, der bereits vorhanden ist. Als Entwickler können Sie nicht steuern, welchen Ordnernamen und welches Verzeichnis der Benutzer in der Anwendung angibt. Allerdings können Sie steuern, was passieren soll, wenn jemand ein Element erstellen möchte, das bereits vorhanden ist.  
  
 Um bestimmte Fehlerbedingungen leichter zu erfassen, klassifiziert [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] einen Fehlercode für die Ausnahme und gibt die Fehlerklassifizierung mithilfe der Eigenschaften aus der **SoapException**-Klasse zurück. Weitere Informationen finden Sie unter "SoapException Class" in der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK-Dokumentation.  
  
 In der folgenden Tabelle sind die öffentlichen Eigenschaften der **SoapException**-Klasse aufgeführt.  
  
|Öffentliche Eigenschaft|BESCHREIBUNG|  
|---------------------|-----------------|  
|**Teurs**|Der Code, der die Ausnahme verursacht hat. Der Wert ist die URL der Webdienstmethode.|  
|**Einzelnen**|Anwendungsspezifische Fehlerinformationen. Der Wert wird vom Berichtsserver festgelegt und ist im XML-Format. Weitere Informationen finden Sie unter [Detail-Eigenschaft](detail-property.md) und [Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler](../best-practices/using-the-detail-property-to-handle-specific-errors.md).|  
|**HelpLink**|Eine URL oder eine URN zu einer zum Fehler gehörigen Hilfedatei. Der Wert wird normalerweise durch einen Webdienst festgelegt, und er richtet eine URL zu [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Hilfe und Support ein. Da [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] mehrere HelpLinks für auftretende Fehler unterstützt, richtet der Berichtsserver die HelpLink-Informationen als Teil der **Detail**-Eigenschaft ein. Weitere Informationen finden Sie unter [HelpLink-Element](helplink-element.md).|  
|**Meldung**|Eine informative, lokalisierte Meldung, die den Fehler beschreibt. Dieser Text kann in der Benutzeroberfläche der Anwendung angezeigt werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Introducing Exception Handling in Reporting Services (Einführung in die Ausnahmebehandlung in Reporting Services)](../introducing-exception-handling-in-reporting-services.md)   
 [Tabelle für SoapException-Fehler](soapexception-errors-table.md)  
  
  
