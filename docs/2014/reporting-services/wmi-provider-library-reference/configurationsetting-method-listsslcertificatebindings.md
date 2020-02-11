---
title: 'ListSSLCertificateBindings-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificateBindings method
ms.assetid: d12d280c-9b6f-47a8-bcd9-34cde31c8886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0a2a33d7aa992fd434b29fd519c805f57b2b46fc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098360"
---
# <a name="listsslcertificatebindings-method-wmi-msreportserver_configurationsetting"></a>ListSSLCertificateBindings-Methode (WMI: MSReportServer_ConfigurationSetting)
  Gibt eine Liste von auf dem Computer installierten SSL-Zertifikaten zurück  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub ListSSLCertificateBindings(ByVal LCID As Int32, ByRef Application() As String, _  
    ByRef CertificateHash() As String, ByRef IPAddresses() As String, ByRef Port() As Int32, _  
    ByRef Errors() As String, ByRef Length As Int32, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListSSLCertificateBindings(Int32 Lcid, out string[] Application,   
    out string[] CertificateHash,out string[] IPAddress,   
    out Int32[] Port, out string Errors,   
    out Int32 length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *LCID*  
 Das Gebietsschema, das für die zurückgegebenen Fehlermeldungen verwendet werden soll  
  
 *Anwendung []*  
 [out] Die Anwendungen, die Zertifikatsbindungen aufweisen  
  
 *Certifi-ehash []*  
 [out] Die Hashes für die Zertifikate  
  
 *IPAddress []*  
 [out] Die IP-Adresse für die Anwendungen  
  
 *Port []*  
 [out] Die in der Bindung in rsreportserver.config gespeicherte Portnummer.  
  
 *Fehler []*  
 [out] Die Beschreibungen für Fehler, die aufgetreten sind  
  
 *Länge*  
 [out] Die Länge des von der Methode zurückgegebenen Arrays  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
