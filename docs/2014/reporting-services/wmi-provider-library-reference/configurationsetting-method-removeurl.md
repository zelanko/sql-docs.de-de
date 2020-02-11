---
title: 'RemoveURL-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveURL method
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdd38b66a62b3d839f89f078904f7a3a9cc82d66
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098170"
---
# <a name="removeurl-method-wmi-msreportserver_configurationsetting"></a>RemoveURL-Methode (WMI: MSReportServer_ConfigurationSetting)
  Entfernt eine für den Berichtsserver reservierte URL Wenn mehrere URLs entfernt werden müssen, muss dies einzeln durch mehrfache Aufrufe dieser API erfolgen.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *Anwendung*  
 Der Name der Anwendung, für die die Reservierung entfernt werden soll  
  
 *URLString*  
 Die URL für die Reservierung  
  
 *LCID*  
 Das Gebietsschema, das für die zurückgegebenen Fehlermeldungen verwendet werden soll  
  
 *Fehler*  
 [out] Die Beschreibung des Fehlers, der aufgetreten ist  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Fehlercode gibt an, dass der Aufruf nicht erfolgreich war.  
  
## <a name="remarks"></a>Bemerkungen  
 *UrlString* enthält nicht den Namen des virtuellen Verzeichnisses. die [SetVirtualDirectory-Methode &#40;WMI-MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) Methode wird zu diesem Zweck bereitgestellt.  
  
 Vor einem Aufruf der [ReserveURL](configurationsetting-method-reserveurl.md) -Methode müssen Sie einen Wert für die VirtualDirectory-Konfigurationseigenschaft des *Anwendungsparameters* angeben. Verwenden Sie die Methode [SetVirtualDirectory-Methode (WMI: MSReportServer_ConfigurationSetting)](configurationsetting-method-setvirtualdirectory.md), um die VirtualDirectory-Eigenschaft festzulegen.  
  
 Wenn durch [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ein SSL-Zertifikat bereitgestellt wurde und keine anderen URLs dieses benötigen, wird es entfernt.  
  
 Diese Methode verursacht einen "harten" Wiederverwendungsvorgang und ein Beenden aller Nichtkonfigurationsdomänen für Anwendungen. Die Anwendungsdomänen werden nach dem Abschluss des Vorgangs neu gestartet.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
