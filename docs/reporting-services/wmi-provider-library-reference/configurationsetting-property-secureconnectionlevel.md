---
title: 'SecureConnectionLevel-Eigenschaft (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- SecureConnectionLevel
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SecureConnectionLevel property
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 59c833c86c632c0f5a0838a98f31d89f4f0df5fb
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81635872"
---
# <a name="configurationsetting-property---secureconnectionlevel"></a>ConfigurationSetting-Eigenschaft: SecureConnectionLevel
  Gibt die in der Datei RSReportServer.config angegebene sichere Verbindungsebene zurück. Schreibgeschützt.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## <a name="property-values"></a>Eigenschaftswerte  
 Ein **Integer** -Wert, der die sichere Verbindungsebene darstellt. Die Rückgabewerte geben an, dass TLS entweder konfiguriert ist oder nicht. Ein Wert größer oder gleich 1 gibt an, dass TLS aktiviert ist. Der Wert 0 gibt an, dass TLS deaktiviert ist.  
  
## <a name="example-code"></a>Beispielcode  
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Bemerkungen

In SQL Server 2008 R2 wird SecureConnectionLevel zu einer ON/OFF-Option. Weitere Informationen finden Sie unter [ConfigurationSetting-Methode: SetSecureConnectionLevel](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setsecureconnectionlevel.md).

## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
