---
title: 'SetSecureConnectionLevel-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetSecureConnectionLevel method
ms.assetid: 0fac7d5e-2670-4657-9439-331e7d93babb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5318d25ed1e6113e65f6e41d40add3ff0203856c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "65580999"
---
# <a name="configurationsetting-method---setsecureconnectionlevel"></a>ConfigurationSetting-Methode: SetSecureConnectionLevel
  Legt die sichere Verbindungsebene des Berichtsservers fest  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub SetSecureConnectionLevel(Level as Integer, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Int32 Level,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *Level*  
 Ein ganzzahliger Wert, der eine sichere Verbindungsebene darstellt  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Bei einem Aufruf wird die SecureConnectionLevel-Eigenschaft des Berichtsservers auf den angegebenen Wert festgelegt. Der Wert 0 gibt an, dass SSL deaktiviert wird. Ein Wert größer oder gleich 1 gibt an, dass SSL aktiviert wird.  
  
-   Wenn der Wert festgelegt ist, wird das SecureConnectionLevel-Element in der Berichtsserver-Konfigurationsdatei geändert, und für das **URLRoot** -Element in der Konfigurationsdatei wird die Verwendung von „https://“ festgelegt, wenn das angegebene *Level* größer oder gleich 1 ist. Wenn das angegebene *Level* 0 ist, wird die Verwendung von „http://“ festgelegt.  
  
 In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]wird SecureConnectionLevel zu einer ON-/OFF-Option mit dem Standardwert 0. Bei einem beliebigen Wert größer oder gleich 1, der über eine API der SetSecureConnectionLevel-Methode übergeben wird, wird SSL als aktiviert erachtet und die SecureConnectionLevel-Konfigurationseigenschaft in der Datei „rsreportserver.config“ entsprechend festgelegt. Werte von 2 und 3 werden weiterhin aus Gründen der Abwärtskompatibilität zugelassen.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
