---
title: 'SetWindowsServiceIdentity-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: aff708a3455c98ae0671b4970cd654d54f7dda36
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52399303"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserverconfigurationsetting"></a>SetWindowsServiceIdentity-Methode (WMI: MSReportServer_ConfigurationSetting)
  Lässt den Report Server-Windows-Dienst als einen angegebenen Windows-Benutzer ausführen und gibt diesem Konto die erforderlichen Dateisystemberechtigungen, damit der Berichtsserver ausgeführt werden kann  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *UseBuiltInAccount*  
 Gibt an, ob das angegebene Konto ein integriertes Windows-Konto ist  
  
 *Konto*  
 Das Windows-Konto, das verwendet werden soll, um den Windows-Dienst auszuführen (im Format "DOMAIN\alias")  
  
 *Kennwort*  
 Das Kennwort für das Konto  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die *UseBuiltInAccount* Parameter auf festgelegt ist `true` und der Berichtsserver ausgeführt wird, auf Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] oder Windows XP, den Wert des der *Name*, *Domäne*, und *Kennwort* Parameter werden ignoriert, und das lokale Systemkonto wird verwendet.  
  
 Wenn der *UseBuiltInAccount* Parametersatz zu `true` und der Berichtsserver unter Windows Server 2003 ausgeführt wird der *Domäne* und *Kennwort* Eigenschaften sind ignoriert, und das Namensfeld muss enthalten, "Builtin\system" oder "Builtin\System" oder "builtin\localservice enthalten".  
  
 Die SetWindowsServiceIdentity-Methode legt Dateiberechtigungen für Dateien und Ordner im Installationsverzeichnis des Berichtsservers fest.  
  
 Das angegebene Konto das *Konto* Parameter erfordert `LogonAsService` -Rechte in Windows. Die Methode gewährt dem angegebenen Konto dieses Recht.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting-Member](msreportserver-configurationsetting-members.md)  
  
  
