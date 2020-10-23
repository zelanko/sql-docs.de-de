---
description: 'GetReportServerUrls-Methode (WMI: MSReportServer_Instance)'
title: 'GetReportServerUrls-Methode (WMI: MSReportServer_Instance) | Microsoft-Dokumentation'
ms.date: 06/09/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e3b3e0f7e521cd2a105a3cf093c0a179bd7306d7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "92257523"
---
# <a name="msreportserver_instance-methods---getreportserverurls"></a>MSReportServer_Instance-Methoden: GetReportServerUrls
  Gibt eine Liste von URLs zurück, über die Benutzer auf den Berichtsserver und den [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]zugreifen können.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *ApplicationName[]*  
 Ein Array, das die installierten Anwendungen enthält. Werte sind entweder **ReportServerWebService** oder **ReportServerWebApp**.  
  
 *URLs[]*  
 Ein Array, das die erfolgreich registrierten URLs enthält  
  
 *Länge*  
 Ein Integer-Wert, der die Länge der zurückgegebenen Arrays enthält.  
  
 *HRESULT*  
 Ein Wert, der Erfolg oder einen Fehlercode angibt  
  
## <a name="return-values"></a>Rückgabewerte  
  
## <a name="remarks"></a>Hinweise  
 Von WMI-Verwaltungsobjekten verfügbar gemachte Methoden werden durch die InvokeMethod-Funktion aufgerufen. Weitere Informationen finden Sie in "Ausführen von Methoden für Verwaltungsobjekte" in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI-Dokumentation.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
