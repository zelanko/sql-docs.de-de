---
title: RSWindowsExtendedProtectionLevel-Eigenschaft | Microsoft-Dokumentation
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.suite: pro-bi
ms.topic: conceptual
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
author: markingmyname
ms.author: maghan
ms.openlocfilehash: fbab7b62b9ceb631fb0562097389b38d7ceac7da
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43282292"
---
# <a name="rswindowsextendedprotectionlevel-property"></a>RSWindowsExtendedProtectionLevel-Eigenschaft
  Gibt einen Zeichenfolgenwert zurück, der die Schutzebene angibt, für deren Unterstützung der Berichtsserver konfiguriert ist. Diese Eigenschaft ist schreibgeschützt.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## <a name="remarks"></a>Remarks  
 Gibt einen Zeichenfolgenwert zurück, der die Schutzebene angibt, für deren Unterstützung der Berichtsserver konfiguriert ist. Wenn der Berichtsserver, mit dem der WMI-Anbieter verbunden wird, keinen erweiterten Schutz unterstützt, wird “” (leere Zeichenfolge) zurückgegeben. In der folgenden Liste werden gültige Werte aufgeführt:  
  
 `“Off” | “Allow” | “Require”`  
  
## <a name="example-code"></a>Beispielcode  
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [RSWindowsExtendedProtectionScenario-Eigenschaft &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionscenario-property.md)   
 [SetExtendedProtectionSettings-Methode (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md)   
 [Erweiterter Schutz für die Authentifizierung mit Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [RsReportServer.config Configuration File (RSReportServer.config-Konfigurationsdatei)](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
