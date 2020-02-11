---
title: Rswindowsextendecodschutzscenario-Eigenschaft (WMI-MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 60a61ca96aafe0e475d28023276c561f49c13cde
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66096982"
---
# <a name="rswindowsextendedprotectionscenario-property-wmi-msreportserver_configurationsetting"></a>RSWindowsExtendedProtectionScenario-Eigenschaft (WMI: MSReportServer_ConfigurationSetting)
  Gibt einen Zeichenfolgenwert zurück, der das erweiterte Schutzszenario angibt, für das der Berichtsserver konfiguriert ist.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Gibt einen Zeichenfolgenwert zurück, der das erweiterte Schutzszenario angibt, für das der Berichtsserver konfiguriert ist. Wenn der Berichtsserver, mit dem der WMI-Anbieter verbunden wird, keinen erweiterten Schutz unterstützt, wird "" (leere Zeichenfolge) zurückgegeben.  
  
 In der folgenden Liste werden gültige Werte aufgeführt:  
  
 `"Any | Proxy | Direct"`  
  
## <a name="example-code"></a>Beispielcode  
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [RSWindowsExtendedProtectionLevel-Eigenschaft &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md)   
 [SetExtendedProtectionSettings-Methode (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setextendedprotectionsettings.md)   
 [Erweiterter Schutz für die Authentifizierung mit Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)  
  
  
