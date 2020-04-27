---
title: Detail-Eigenschaft | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 27d9d7ab4cd29c6eb0ea7ae1c6bddbe8c1b7ef06
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046006"
---
# <a name="detail-property"></a>Detail-Eigenschaft
  Die XML-Struktur der **Detail**-Eigenschaft der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException**-Klasse in  sieht wie folgt aus:  
  
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
 Die HelpLink-URL zu einer Website, unter der weitere Informationen zum Fehler zur Verfügung stehen. Weitere Informationen finden Sie unter [HelpLink-Element](helplink-element.md).  
  
 **LinkID**  
 Die dem Link zugewiesene ID.  
  
 **ProductName**  
 Der Name des Produkts. Der Standardwert ist **Microsoft SQL Server Reporting Services**.  
  
 **ProductVersion**  
 Die Version von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Die maximale Länge beträgt 15 Zeichen. Das Format der Versionsnummer sollte folgendermaßen sein: 8.00.0xxx.00.  
  
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
 [Einführung in die Ausnahmebehandlung in Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException-Klasse](reporting-services-soapexception-class.md)   
 [Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
