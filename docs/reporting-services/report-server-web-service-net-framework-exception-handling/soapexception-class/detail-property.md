---
title: Detail-Eigenschaft | Microsoft-Dokumentation
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 087f7f6da8882f181c55a187438d4493ec5b1a9b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "62991555"
---
# <a name="detail-property"></a>Detail-Eigenschaft
  Die XML-Struktur der **Detail**-Eigenschaft der **SoapException**-Klasse in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] sieht wie folgt aus:  
  
## <a name="elements"></a>Elemente  
 **Detail**  
 Das Element der obersten Ebene, das alle anderen Fehlerdetailelemente enthält.  
  
 **ErrorCode**  
 Der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-spezifische Fehlercode.  
  
 **HttpStatus**  
 Der HTTP-Statuscode.  
  
 **Meldung**  
 Die Fehlermeldung und der Fehlercode, die vom Berichtsserver zugewiesen werden.  
  
 **HelpLink**  
 Die HelpLink-URL zu einer Website, unter der weitere Informationen zum Fehler zur Verfügung stehen. Weitere Informationen finden Sie unter [HelpLink-Element](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md).  
  
 **LinkID**  
 Die dem Link zugewiesene ID.  
  
 **ProductName**  
 Der Name des Produkts. Der Standardwert ist **Microsoft SQL Server Reporting Services**.  
  
 **ProductVersion**  
 Die Version von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Die maximale Länge beträgt 15 Zeichen. Das Format der Versionsnummer sollte folgendermaßen aussehen: 8.00.0xxx.00.  
  
 **ProductLocaleId**  
 Die Gebietsschema- oder Sprach-ID der INTL DLL (z.B. 0x41A) der Anwendung.  
  
 **OperatingSystem**  
 Das Betriebssystem, auf dem [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] installiert ist. Gültige Werte sind: **0** für betriebssystemunabhängig, **1** für [!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)] und **16** für Windows XP.  
  
 **CountryLocaleId**  
 Die Gebietsschema- oder Sprach-ID des Betriebssystems. Der Wert für die französische Version von Windows kann z. B. "0x040c" sein.  
  
 **MoreInformation**  
 Eine XML-Zeichenfolge, die geschachtelte Ausnahmen enthält, die während der Ausführung der Methode aufgetreten sind.  
  
 **Quelle**  
 Ein untergeordnetes Element von **MoreInformation**. Die Ursache des Fehlers.  
  
 **Meldung**  
 Ein untergeordnetes Element von **MoreInformation**. Die Fehlermeldung einer verschachtelten Ausnahme. Dieses Element enthält XML-Attribute für **ErrorCode** und **HelpLink**.  
  
 **Warnungen**  
 Eine XML-Zeichenfolge, die die von der Berichtsverarbeitung zurückgegebenen Warnungen enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Introducing Exception Handling in Reporting Services (Einführung in die Ausnahmebehandlung in Reporting Services)](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [SoapException-Klasse von Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [Using the Detail Property to Handle Specific Errors (Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler)](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
