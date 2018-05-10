---
title: 'SetDatabaseLogonTimeout-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SetDatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetDatabaseLogonTimeout method
ms.assetid: b8773596-5b98-4355-a4ab-4412e1317c67
caps.latest.revision: 19
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 1372469803c7bb13200d53c7a2ace8fc51685f09
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="configurationsetting-method---setdatabaselogontimeout"></a>ConfigurationSetting-Methode: SetDatabaseLogonTimeout
  Gibt den Standardtimeoutwert für Verbindungen mit der Berichtsserver-Datenbank an  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub SetDatabaseLogonTimeout(LogonTimeout as Int32, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetDatabaseLogonTimeout(Int32 LogonTimeout,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *LogonTimeout*  
 Der Standardtimeoutwert (in Sekunden) für Verbindungen mit der Berichtsserver-Datenbank  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [MSReportServer_ConfigurationSetting-Member](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
