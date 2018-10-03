---
title: 'SetExtendedProtectionSettings-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 81b0ea8c7142f33ef9fc91622d899e54f21fe756
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076212"
---
# <a name="setextendedprotectionsettings-method-wmi-msreportserverconfigurationsetting"></a>SetExtendedProtectionSettings-Methode (WMI: MSReportServer_ConfigurationSetting)
  Die SetExtendedProtectionSettings-Methode wird verwendet, um die RSWindowsExtendedProtectionLevel- und RSWindowsExtendedProtectionScenario-Eigenschaft in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationsdatei "RSReportServer.config" festzulegen.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *ExtendedProtectionLevel*  
 Legt "RSWindowsExtendedProtectionLevel" in der Datei "RSRreportserver.config" fest. Beim erforderlichen Wert wird die Groß-/Kleinschreibung nicht beachtet.  
  
 In der folgenden Liste werden gültige Werte aufgeführt:  
  
 `”Off | Allow | Require”`  
  
 *ExtendedProtectionScenario*  
 Legt "RSWindowsExtendedProtectionScenario" in der Datei "RSReportserver.config" fest. Beim erforderlichen Wert wird die Groß-/Kleinschreibung nicht beachtet.  
  
 In der folgenden Liste werden gültige Werte aufgeführt:  
  
 `”Any” | “Proxy” | “Direct”`  
  
## <a name="remarks"></a>Hinweise  
 Die RSWindowsExtendedProtectionLevel-Eigenschaft und die RSWindowsExtendedProtectionScenario-Eigenschaft sind gültig, wenn AuthenticationTypes in der Datei RSReportServer.config RSWindowNTLM, RSWindowsNegotiate oder RSWindowsKerberos einschließt. Das Festlegen dieser Eigenschaften wirkt sich darauf aus, wie sich Benutzer und Clientsoftware an einem Berichtsserver authentifizieren. Es empfiehlt sich die Lektüre der Dokumentation für erweiterten Schutz vor dem Festlegen von ExtendedProtectionLevel auf `Allow` oder `Require`.  
  
 Zum Festlegen von ExtendedProtectionLevel muss der Benutzer Mitglied der Gruppe "BUILTIN\Administrators" auf dem Berichtsserver sein.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [RSWindowsExtendedProtectionScenario-Eigenschaft &#40;WMI: MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md)   
 [RSWindowsExtendedProtectionLevel-Eigenschaft &#40;WMI: MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md)   
 [Erweiterter Schutz für die Authentifizierung mit Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [RSReportServer-Konfigurationsdatei](../report-server/rsreportserver-config-configuration-file.md)  
  
  
