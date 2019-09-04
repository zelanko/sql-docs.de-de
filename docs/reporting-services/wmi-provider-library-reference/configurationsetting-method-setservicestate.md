---
title: 'SetServiceState-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 83aa9fb906fc71b1dfb7fd3d036c119d9b4e41e2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65580989"
---
# <a name="configurationsetting-method---setservicestate"></a>ConfigurationSetting-Methode: SetServiceState
  Aktiviert und deaktiviert den Berichtsserver-Windows-Dienst und den Berichtsserver-Webdienst.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetServiceState(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *EnableWindowsService*  
 Ein **Boolean** -Wert, der den Status des Windows-Diensts angibt. Bei dem Wert **true** wird der Windows-Dienst des Berichtsservers gestartet. Bei dem Wert **false** wird der Windows-Dienst beendet.  
  
 *EnableWebService*  
 Ein **Boolean** -Wert, der den Status des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Webdiensts angibt. Bei dem Wert **true** wird der Webdienst des Berichtsservers gestartet. Bei dem Wert **false** wird der Webdienst beendet.  
  
 *EnableReportManager*  
 Ein **Boolean** -Wert, der den gewünschten Status des Berichts-Managers angibt.
 
 > [!NOTE] 
 > Diese Einstellung wurde ab dem Kumulativen Update 2 von SQL Server 2016 Reporting Services als veraltet gekennzeichnet. Das Webportal bleibt weiterhin aktiviert. Der Wert wird ignoriert.
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting-Member](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
