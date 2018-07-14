---
title: 'ListIPAddresses-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ListIPAddresses method
ms.assetid: 7e7cf182-fba0-4604-a474-098461e23e9d
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 048d654b94d537aa5e6209d0012105ddaef127cb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166171"
---
# <a name="listipaddresses-method-wmi-msreportserverconfigurationsetting"></a>ListIPAddresses-Methode (WMI: MSReportServer_ConfigurationSetting)
  Listet die IP-Adressen für den Berichtsservercomputer auf.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub ListIPAddresses (ByRef IPAddress() as String, _  
    ByRef IPVersion()as String, ByRef IsDhcpEnabled () as Boolean, _   
    ByRef Length as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListIPAddresses (out string[] IPAddress,   
    out string[] IPVersion, out bool[] isDhcpEnabled, out int length,   
    out int HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *IPAddress[]*  
 [out] Die Liste der IP-Adressen für den Computer  
  
 *IPVersion[]*  
 [out] Die Version für die IP-Adressen  
  
 *IsDhcpEnabled[]*  
 [out] Gibt an, ob die IP-Adressen DHCP-aktiviert sind  
  
 *Länge*  
 [out] Die Länge des von der Methode zurückgegebenen Arrays  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Fehlercode gibt an, dass der Aufruf nicht erfolgreich war.  
  
## <a name="remarks"></a>Hinweise  
 *IPVersion* -Zeichenfolgen sind V4 und V6.  
  
 Wenn *IsDhcpEnabled* ist `True`, *IP-Adresse* ist dynamisch. Eine Verwendung für SSL-Bindungen wird nicht empfohlen.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
