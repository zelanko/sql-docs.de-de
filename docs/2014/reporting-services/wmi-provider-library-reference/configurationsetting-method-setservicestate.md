---
title: 'SetServiceState-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
caps.latest.revision: 17
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 7fdcc309eca07c8fc29fa80934e6929054a59b44
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148527"
---
# <a name="setservicestate-method-wmi-msreportserverconfigurationsetting"></a>SetServiceState-Methode (WMI: MSReportServer_ConfigurationSetting)
  Aktiviert und deaktiviert den Berichtsserver-Windows-Dienst und den Berichtsserver-Webdienst.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *EnableWindowsService*  
 Ein `Boolean` Wert, der angibt, des Status des Windows-Diensts. Der Wert `true` startet den Berichtsserver-Windows-Dienst, der Wert `false` beendet den Windows-Dienst.  
  
 *EnableWebService*  
 Ein `Boolean`-Wert, der den Status des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Webdiensts angibt. Bei dem Wert `true` wird der Webdienst des Berichtsservers gestartet. Bei dem Wert `false` wird der Webdienst beendet.  
  
 *EnableReportManager*  
 Ein `Boolean` Wert, der angibt, des gewünschten Zustands des Berichts-Managers.  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  