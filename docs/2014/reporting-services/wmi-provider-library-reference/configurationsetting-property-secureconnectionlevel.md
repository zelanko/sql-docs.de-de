---
title: 'SecureConnectionLevel-Eigenschaft (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
api_name:
- SecureConnectionLevel
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SecureConnectionLevel property
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
caps.latest.revision: 19
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ae2fe910ea69330198158b661eb13f283746fe6b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166251"
---
# <a name="secureconnectionlevel-property-wmi-msreportserverconfigurationsetting"></a>SecureConnectionLevel-Eigenschaft (WMI: MSReportServer_ConfigurationSetting)
  Gibt die in der Datei RSReportServer.config angegebene sichere Verbindungsebene zurück. Schreibgeschützt.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## <a name="property-values"></a>Eigenschaftswerte  
 Ein `Integer` -Wert, der die sichere Verbindungsebene darstellt. Die Rückgabewerte geben an, dass SSL entweder konfiguriert ist oder nicht. Ein Wert größer oder gleich 1 gibt an, dass SSL aktiviert ist. Der Wert 0 gibt an, dass SSL deaktiviert wird.  
  
## <a name="example-code"></a>Beispielcode  
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
