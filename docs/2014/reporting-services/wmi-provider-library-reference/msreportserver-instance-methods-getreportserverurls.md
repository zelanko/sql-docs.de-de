---
title: 'GetReportServerUrls-Methode (WMI: MSReportServer_Instance) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 148e0ece44e97bd4c559bbed9cc95aa97092dffb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171050"
---
# <a name="getreportserverurls-method-wmi-msreportserverinstance"></a>GetReportServerUrls-Methode (WMI: MSReportServer_Instance)
  Gibt eine Liste von URLs zurück, über die Benutzer auf den Berichtsserver und den Berichts-Manager zugreifen können  
  
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
 Ein Array, das die installierten Anwendungen enthält. Werte sind entweder `ReportServerWebService` oder `ReportManager`.  
  
 *URLs[]*  
 Ein Array, das die erfolgreich registrierten URLs enthält  
  
 *Länge*  
 Ein Integer-Wert, der die Länge der zurückgegebenen Arrays enthält.  
  
 *HRESULT*  
 Ein Wert, der Erfolg oder einen Fehlercode angibt  
  
## <a name="return-values"></a>Rückgabewerte  
  
## <a name="remarks"></a>Hinweise  
 Von WMI-Verwaltungsobjekten verfügbar gemachte Methoden werden durch die InvokeMethod-Funktion aufgerufen. Weitere Informationen finden Sie in "Ausführen von Methoden für Verwaltungsobjekte" in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework WMI-Dokumentation.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
