---
title: 'DeleteEncryptedInformation-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DeleteEncryptedInformation method
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8596860d7da0f41844c9dfcef341ec595609e1e1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620153"
---
# <a name="configurationsetting-method---deleteencryptedinformation"></a>ConfigurationSetting-Methode: DeleteEncryptedInformation
  Löscht die verschlüsselten Informationen aus der Berichtsserver-Datenbank  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parameter  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
 *ExtendedErrors[]*  
 [out] Ein Zeichenfolgenarray, das zusätzliche Fehler enthält, die durch den Aufruf zurückgegeben werden  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Remarks  
 Wenn diese Methode aufgerufen wird, werden die folgenden Daten gelöscht:  
  
-   Datenquellinformationen, die verschlüsselt werden, einschließlich des Benutzernamens und des Kennworts  
  
-   Abonnementdaten, die mithilfe der Schnittstellen der Übermittlungserweiterung verschlüsselt werden  
  
-   Alle Informationen aus der Schlüsseltabelle der Berichtsserver-Datenbank  
  
 Nach dem Aufruf dieser Methode muss der Benutzer jeden Computer initialisieren, auf dem die Berichtsserver-Datenbank verwendet wird.  
  
 Der Aufruf der „DeleteEncryptedInformation“-Methode hat keinen Einfluss auf die Berichtsserver-Konfigurationsdatei.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [MSReportServer_ConfigurationSetting-Member](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
