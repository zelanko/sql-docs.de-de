---
title: 'InitializeReportServer-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- InitializeReportServer method
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5f6df892b16c7c384291e50640434ce9df15f662
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56029221"
---
# <a name="initializereportserver-method-wmi-msreportserverconfigurationsetting"></a>InitializeReportServer-Methode (WMI: MSReportServer_ConfigurationSetting)
  Initialisiert die angegebene Berichtsdienstinstanz  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parameter  
 *InstallationID*  
 Eine Zeichenfolge, mit der der Verschlüsselungsschlüssel verschlüsselt wird, bevor er zurückgegeben wird  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
 *ExtendedErrors[]*  
 [out] Ein Zeichenfolgenarray, das zusätzliche Fehler enthält, die durch den Aufruf zurückgegeben werden  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Wenn diese Methode aufgerufen wird, wird der Verschlüsselungsschlüssel, der auf die sicheren Informationen der Berichtsserverdatenbank zugreift, mit dem öffentlichen Schlüssel des Berichtsservers verschlüsselt, der von *InstallationID*angegeben wird.  
  
 Der angegebene öffentliche Schlüssel des Berichtsservers muss zuvor in die Berichtsserver-Datenbank geschrieben worden sein.  
  
 Die *InitializeReportServer* -Methode muss für einen Berichtsserver aufgerufen werden, der bereits Zugriff auf die sicheren Informationen hat, damit der Verschlüsselungsschlüssel entschlüsselt werden kann. Der resultierende verschlüsselte Verschlüsselungsschlüssel wird dann in der Berichtsserver-Datenbank gespeichert.  
  
 Wenn der Berichtsserver [IsInitialized](configurationsetting-property-isinitialized.md) -Eigenschaftensatz auf `true` die InitializeReportServer-Methode aufgerufen wird, gibt die Methode erfolgreich ohne zu versuchen, den Verschlüsselungsschlüssel zu verschlüsseln.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting-Member](msreportserver-configurationsetting-members.md)  
  
  
