---
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
ms.openlocfilehash: bc04865c9dcbdf16627c1ab4598610426e4a8d5a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65571951"
---
# <a name="msreportserverinstance-methods---getreportserverurls"></a>MSReportServer_Instance-Methoden: GetReportServerUrls
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
  
## <a name="remarks"></a>Remarks  
 Von WMI-Verwaltungsobjekten verfügbar gemachte Methoden werden durch die InvokeMethod-Funktion aufgerufen. Weitere Informationen finden Sie in "Ausführen von Methoden für Verwaltungsobjekte" in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI-Dokumentation.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting-Member](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
