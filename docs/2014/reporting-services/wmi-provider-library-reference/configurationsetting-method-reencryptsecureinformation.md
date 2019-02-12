---
title: 'ReencryptSecureInformation-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: b02e6f8bbaa25b3141d602107fa44ca526c9eb31
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56022051"
---
# <a name="reencryptsecureinformation-method-wmi-msreportserverconfigurationsetting"></a>ReencryptSecureInformation-Methode (WMI: MSReportServer_ConfigurationSetting)
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
  
## <a name="remarks"></a>Hinweise  
 Die ReencryptSecureInformation-Methode ermöglicht es dem Administrator, den vorhandenen Verschlüsselungsschlüssel durch einen neuen Schlüssel zu ersetzen.  
  
 Bei einem Aufruf dieser Methode generiert der Berichtsserver einen neuen Verschlüsselungsschlüssel und durchläuft den gesamten verschlüsselten Inhalt, um ihn erneut mit diesem neuen Verschlüsselungsschlüssel zu verschlüsseln.  
  
 Übermittlungserweiterungen können gesicherte Informationen in den Strukturen ihrer Übermittlungseinstellungen speichern. Beim Aufruf von ReencryptSecureInformation lädt der Berichtsserver jedes Abonnement und die entsprechende Übermittlungserweiterung, um die in den zugehörigen Einstellungen gespeicherten Informationen erneut zu verschlüsseln.  
  
 Wenn diese Methode auf einem Computer in einer Bereitstellung für horizontales Skalieren ausgeführt wird, muss jeder Computer in der Bereitstellung für horizontales Skalieren neu initialisiert werden.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting-Member](msreportserver-configurationsetting-members.md)  
  
  
