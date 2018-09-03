---
title: 'ReencryptSecureInformation-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.suite: pro-bi
ms.topic: conceptual
apiname:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5492420f484892b172de6cdefde484469b1e7054
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43278631"
---
# <a name="configurationsetting-method---reencryptsecureinformation"></a>ConfigurationSetting Method – ReencryptSecureInformation (ConfigurationSetting-Methode: ReencryptSecureInformation)
  Generiert einen neuen Verschlüsselungsschlüssel und verschlüsselt alle sicheren Informationen im Katalog erneut mit diesem neuen Schlüssel  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub ReencryptSecureInformation(ByRef HRESULT as Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ReencryptSecureInformation (out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parameter  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
 *ExtendedErrors[]*  
 [out] Ein Zeichenfolgenarray, das zusätzliche Fehler enthält, die durch den Aufruf zurückgegeben werden  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Remarks  
 Die ReencryptSecureInformation-Methode ermöglicht es dem Administrator, den vorhandenen Verschlüsselungsschlüssel durch einen neuen Schlüssel zu ersetzen.  
  
 Bei einem Aufruf dieser Methode generiert der Berichtsserver einen neuen Verschlüsselungsschlüssel und durchläuft den gesamten verschlüsselten Inhalt, um ihn erneut mit diesem neuen Verschlüsselungsschlüssel zu verschlüsseln.  
  
 Übermittlungserweiterungen können gesicherte Informationen in den Strukturen ihrer Übermittlungseinstellungen speichern. Beim Aufruf von ReencryptSecureInformation lädt der Berichtsserver jedes Abonnement und die entsprechende Übermittlungserweiterung, um die in den zugehörigen Einstellungen gespeicherten Informationen erneut zu verschlüsseln.  
  
 Wenn diese Methode auf einem Computer in einer Bereitstellung für horizontales Skalieren ausgeführt wird, muss jeder Computer in der Bereitstellung für horizontales Skalieren neu initialisiert werden.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [MSReportServer_ConfigurationSetting-Member](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
