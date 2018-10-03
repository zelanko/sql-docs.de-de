---
title: Angeben von Geräteinformationseinstellungen in einer URL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 061fc6edeec6e3970ade638115b3d28389218a3f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067820"
---
# <a name="specify-device-information-settings-in-a-url"></a>Angeben von Geräteinformationseinstellungen in einer URL
  Geräteinformationseinstellungen sind Parameter, die an eine Renderingerweiterung übergeben werden. Wenn Sie einen Bericht mit den Methoden des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Berichtsserver-Webdiensts rendern, wird ein `DeviceInfo`-XML-Element als ein Eingabeparameter übergeben. Untergeordnete Elemente der `DeviceInfo` -Elements sind für die Geräteinformationseinstellungen anderer Renderingerweiterungen spezifisch. Sie können die Geräteinformationseinstellungen in einer URL angeben, indem Sie die *rc:tag=value* -Parameterzeichenfolge verwenden, wobei *tag* der Name des Elements für die Geräteinformationseinstellungen ist. Weitere Informationen zu Geräteinformationseinstellungen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], finden Sie unter [übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Format des angegebenen Berichts auf JPEG eingestellt, indem die Geräteinformationseinstellung *OutputFormat* der Bild-Renderingerweiterung verwendet wird (die Zeilenumbrüche wurden aus Gründen der Lesbarkeit eingefügt):  
  
```  
http://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a>Siehe auch  
 [URL-Zugriff &#40;SSRS&#41;](url-access-ssrs.md)   
 [URL Access Parameter Reference (URL-Zugriffsparameterverweis)](url-access-parameter-reference.md)  
  
  
