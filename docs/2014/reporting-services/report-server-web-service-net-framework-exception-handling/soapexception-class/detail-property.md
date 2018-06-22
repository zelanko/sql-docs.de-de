---
title: Detail-Eigenschaft | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
caps.latest.revision: 32
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: fa7a39ee74bcdd9399c6e06eff9ee6df4688653a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049122"
---
# <a name="detail-property"></a>Detail-Eigenschaft
  Die **Detail**-Eigenschaft der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException**-Klasse verfügt über folgende XML-Struktur:  
  
## <a name="elements"></a>Elemente  
 **Detail**  
 Das Element der obersten Ebene, das alle anderen Fehlerdetailelemente enthält.  
  
 **ErrorCode**  
 Der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-spezifische Fehlercode.  
  
 **HttpStatus**  
 Der HTTP-Statuscode.  
  
 **MessageBox**  
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
  
 **MessageBox**  
 Ein untergeordnetes Element von **MoreInformation**. Die Fehlermeldung einer verschachtelten Ausnahme. Dieses Element enthält XML-Attribute für **ErrorCode** und **HelpLink**.  
  
 **Warnungen**  
 Eine XML-Zeichenfolge, die die von der Berichtsverarbeitung zurückgegebenen Warnungen enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [Introducing Exception Handling in Reporting Services (Einführung in die Ausnahmebehandlung in Reporting Services)](../introducing-exception-handling-in-reporting-services.md)   
 [SoapException-Klasse von Reporting Services](reporting-services-soapexception-class.md)   
 [Using the Detail Property to Handle Specific Errors (Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler)](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  