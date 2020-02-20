---
title: Angeben von Geräteinformationseinstellungen in einer URL | Microsoft-Dokumentation
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 906a21de49d562d788f9a1384b31e080616c67c4
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "65578433"
---
# <a name="specify-device-information-settings-in-a-url"></a>Angeben von Geräteinformationseinstellungen in einer URL
  Geräteinformationseinstellungen sind Parameter, die an eine Renderingerweiterung übergeben werden. Wenn Sie einen Bericht mit den Methoden des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Berichtsserver-Webdiensts rendern, wird ein **DeviceInfo** -XML-Element als ein Eingabeparameter übergeben. Untergeordnete Elemente des **DeviceInfo** -Elements sind für die Geräteinformationseinstellungen anderer Renderingerweiterungen spezifisch. Sie können die Geräteinformationseinstellungen in einer URL angeben, indem Sie die *rc:tag=value* -Parameterzeichenfolge verwenden, wobei *tag* der Name des Elements für die Geräteinformationseinstellungen ist. Weitere Informationen zu den Geräteinformationseinstellungen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] finden Sie im Artikel [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Format des angegebenen Berichts auf JPEG eingestellt, indem die Geräteinformationseinstellung *OutputFormat* der Bild-Renderingerweiterung verwendet wird (die Zeilenumbrüche wurden aus Gründen der Lesbarkeit eingefügt):  
  
```  
https://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [URL-Zugriff &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [URL Access Parameter Reference (URL-Zugriffsparameterverweis)](../reporting-services/url-access-parameter-reference.md)  
  
  
