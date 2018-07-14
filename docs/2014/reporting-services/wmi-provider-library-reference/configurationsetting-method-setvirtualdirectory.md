---
title: 'SetVirtualDirectory-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
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
- SetVirtualDirectory method
ms.assetid: 1a25cb1d-38d5-401a-970b-87b642a780e4
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8918cb7e3f5386a0e8a777f4689c9d07dbb430f5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185852"
---
# <a name="setvirtualdirectory-method-wmi-msreportserverconfigurationsetting"></a>SetVirtualDirectory-Methode (WMI: MSReportServer_ConfigurationSetting)
  Legt den Namen des virtuellen Verzeichnisses für eine angegebene Anwendung fest.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub SetVirtualDirectory(ByVal Application As String, _  
    ByVal VirtualDirectory As String, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetVirtualDirectory(string Application, string VirtualDirectory,   
       int Lcid,out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *Application*  
 Der für das virtuelle Verzeichnis festzulegende Name der Anwendung.  
  
 *VirtualDirectory*  
 Der Name des virtuellen Verzeichnisses  
  
 *lcid*  
 Die Gebietsschema-ID für das virtuelle Verzeichnis  
  
 *Fehler*  
 [out] Die Beschreibung des Fehlers, der aufgetreten ist  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Fehlercode gibt an, dass der Aufruf nicht erfolgreich war.  
  
## <a name="remarks"></a>Hinweise  
 Eine Anwendung kann nur einen Namen für ein virtuelles Verzeichnis für alle URL-Reservierungen verwenden.  
  
 VirtualDirectory muss den Namenskonventionen für virtuelle Verzeichnisse entsprechen. VirtualDirectory darf keine leere Zeichenfolge sein.  
  
 Aktualisiert den Wert des \Configuration\URLReservations\Application\VirtualDirectory-Elements. Ist erfolgreich, auch wenn noch keine URL-Reservierungen erstellt wurden.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
