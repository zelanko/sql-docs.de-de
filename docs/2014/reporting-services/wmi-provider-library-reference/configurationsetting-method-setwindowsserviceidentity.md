---
title: 'SetWindowsServiceIdentity-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
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
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d08e9900453fe259d727e202489d728e0dce47e0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66097875"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserver_configurationsetting"></a>SetWindowsServiceIdentity-Methode (WMI: MSReportServer_ConfigurationSetting)
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
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der *UseBuiltInAccount* - `true` Parameter auf festgelegt ist und der Berichts Server unter Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] oder Windows XP ausgeführt wird, werden der Wert der Parameter *Name*, *Domäne*und *Kennwort* ignoriert, und das lokale Systemkonto wird verwendet.  
  
 Wenn der *UseBuiltInAccount* -Parameter auf `true` festgelegt ist und der Berichts Server unter Windows Server 2003 ausgeführt wird, werden die *Domänen* -und Kenn *Wort* Eigenschaften ignoriert, und das Namensfeld muss entweder "Builtin\NetworkService", "Builtin\System" oder "Builtin\LocalService" enthalten.  
  
 Die SetWindowsServiceIdentity-Methode legt Dateiberechtigungen für Dateien und Ordner im Installationsverzeichnis des Berichtsservers fest.  
  
 Das im *Account* -Parameter angegebene Konto erfordert `LogonAsService` Rechte in Windows. Die Methode gewährt dem angegebenen Konto dieses Recht.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
