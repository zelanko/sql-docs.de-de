---
title: 'RSWindowsExtendedProtectionScenario-Eigenschaft (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 4e614c2f6cadf6633a5129a61e22cead353a5153
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56013221"
---
# <a name="rswindowsextendedprotectionscenario-property-wmi-msreportserverconfigurationsetting"></a>RSWindowsExtendedProtectionScenario-Eigenschaft (WMI: MSReportServer_ConfigurationSetting)
  Gibt einen Zeichenfolgenwert zurück, der das erweiterte Schutzszenario angibt, für das der Berichtsserver konfiguriert ist.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a>Hinweise  
 Gibt einen Zeichenfolgenwert zurück, der das erweiterte Schutzszenario angibt, für das der Berichtsserver konfiguriert ist. Wenn der Berichtsserver, mit dem der WMI-Anbieter verbunden wird, keinen erweiterten Schutz unterstützt, wird "" (leere Zeichenfolge) zurückgegeben.  
  
 In der folgenden Liste werden gültige Werte aufgeführt:  
  
 `"Any | Proxy | Direct"`  
  
## <a name="example-code"></a>Beispielcode  
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>Siehe auch  
 [RSWindowsExtendedProtectionLevel-Eigenschaft &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md)   
 [SetExtendedProtectionSettings-Methode (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setextendedprotectionsettings.md)   
 [Erweiterter Schutz für die Authentifizierung mit Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [RSReportServer-Konfigurationsdatei](../report-server/rsreportserver-config-configuration-file.md)  
  
  
