---
title: 'CreateSSLCertificateBinding-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- CreateSSLCertificateBinding
ms.assetid: 407d50e4-0a55-43cb-8ddf-2d82714071b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f16b86b1343d83c44819427b8ba6c43726798e93
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66098541"
---
# <a name="createsslcertificatebinding-method-wmi-msreportserverconfigurationsetting"></a>CreateSSLCertificateBinding-Methode (WMI: MSReportServer_ConfigurationSetting)
  Erstellt eine SSL-Zertifikatsbindung  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub CreateSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void CreateSSLCertificateBinding(string application,   
    string certificateHash, string IPAddress, int Port,   
    int lcid, out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *Application*  
 Der Name der Anwendung, für die die Zertifikatsbindung erstellt werden soll  
  
 *CertificateHash*  
 Der Hash für das Zertifikat  
  
 *IPAddress*  
 Die IP-Adresse für die Anwendung  
  
 *Port*  
 Der SSL-Port, der der Bindung zugeordnet ist.  
  
 *Lcid*  
 Das Gebietsschema, das für die zurückgegebenen Fehlermeldungen verwendet werden soll  
  
 *Fehler*  
 [out] Die Beschreibung der Fehler, die aufgetreten sind  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Fehlercode gibt an, dass der Aufruf nicht erfolgreich war.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode fügt rsreportserver.config eine Bindung für die Anwendung hinzu. Wenn HTTP.SYS noch keine Bindung enthält, wird diese dort erstellt.  
  
 Vor dem Erstellen der Bindung untersucht der Methodenaufruf die URL-Reservierungen für die angegebene Anwendung, um zu überprüfen, ob die SSL-Zertifikatsbindung gültig ist.  
  
 Die folgenden Bedingungen werden überprüft und können Ursache für Fehler sein:  
  
1.  Das Zertifikat ist nicht vorhanden.  
  
2.  Die angegebene IPAddress entspricht keiner IPAddress dieses Computers.  
  
3.  Die angegebene IP-Adresse ist eine DHCP-IP-Adresse (ändert sich in regelmäßigen Abständen). Verwenden Sie stattdessen die Platzhalter-IP-Adresse (0.0.0.0).  
  
4.  Die angegebene IP-Adresse entspricht weder der IP-Adresse für URL-Reservierungen noch ist eine Platzhalter- oder Hostnamen-URL-Reservierung vorhanden.  
  
5.  Eine URL-Reservierung, die einen Hostnamen angibt, ist vorhanden, der Hostname stimmt jedoch nicht mit dem Zertifikathostnamen überein.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting-Member](msreportserver-configurationsetting-members.md)  
  
  
