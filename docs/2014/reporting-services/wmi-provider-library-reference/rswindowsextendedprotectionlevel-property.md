---
title: 'RSWindowsExtendedProtectionLevel-Eigenschaft (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c3c4fdbf8642715a895e8c345ccd171c53ca3509
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63020128"
---
# <a name="rswindowsextendedprotectionlevel-property-wmi-msreportserverconfigurationsetting"></a>RSWindowsExtendedProtectionLevel-Eigenschaft (WMI MSReportServer_ConfigurationSetting)
  Gibt einen Zeichenfolgenwert zurück, der die Schutzebene angibt, für deren Unterstützung der Berichtsserver konfiguriert ist. Diese Eigenschaft ist schreibgeschützt.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## <a name="remarks"></a>Hinweise  
 Gibt einen Zeichenfolgenwert zurück, der die Schutzebene angibt, für deren Unterstützung der Berichtsserver konfiguriert ist. Wenn der Berichtsserver, mit dem der WMI-Anbieter verbunden wird, keinen erweiterten Schutz unterstützt, wird "" (leere Zeichenfolge) zurückgegeben. In der folgenden Liste werden gültige Werte aufgeführt:  
  
 `"Off" | "Allow" | "Require"`  
  
## <a name="example-code"></a>Beispielcode  
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>Siehe auch  
 [RSWindowsExtendedProtectionScenario-Eigenschaft &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md)   
 [SetExtendedProtectionSettings-Methode &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md)   
 [Erweiterter Schutz für die Authentifizierung mit Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [RSReportServer-Konfigurationsdatei](../report-server/rsreportserver-config-configuration-file.md)  
  
  
