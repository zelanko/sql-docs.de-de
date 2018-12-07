---
title: RSWindowsExtendedProtectionScenario-Eigenschaft | Microsoft-Dokumentation
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 78c3a7693ea17899afde6dec1173d79cddec9954
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52407707"
---
# <a name="rswindowsextendedprotectionscenario-property"></a>RSWindowsExtendedProtectionScenario-Eigenschaft
  Gibt einen Zeichenfolgenwert zurück, der das erweiterte Schutzszenario angibt, für das der Berichtsserver konfiguriert ist.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a>Remarks  
 Gibt einen Zeichenfolgenwert zurück, der das erweiterte Schutzszenario angibt, für das der Berichtsserver konfiguriert ist. Wenn der Berichtsserver, mit dem der WMI-Anbieter verbunden wird, keinen erweiterten Schutz unterstützt, wird "" (leere Zeichenfolge) zurückgegeben.  
  
 In der folgenden Liste werden gültige Werte aufgeführt:  
  
 `"Any | Proxy | Direct"`  
  
## <a name="example-code"></a>Beispielcode  
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [RSWindowsExtendedProtectionLevel-Eigenschaft &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionlevel-property.md)   
 [SetExtendedProtectionSettings-Methode (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md)   
 [Erweiterter Schutz für die Authentifizierung mit Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [RSReportServer.config-Konfigurationsdatei](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
