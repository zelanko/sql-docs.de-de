---
title: 'IsSharePointIntegrated-Eigenschaft (WMI: MSReportServer_Instance) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c96d8e6bf204759f9096bd870c72887f9ef26f65
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257906"
---
# <a name="issharepointintegrated-property-wmi-msreportserverinstance"></a>IsSharePointIntegrated-Eigenschaft (WMI: MSReportServer_Instance)
  Gibt an, ob sich der Berichtsserver im integrierten SharePoint-Modus befindet Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] gibt diese Eigenschaft immer `False` zurück, da [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Instanzen im SharePoint-Modus freigegebene Dienste darstellen und nicht von WMI-Anbietern kontrolliert werden.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>Eigenschaftswerte  
 Ein `Boolean`-Wert, der angibt, ob sich der Berichtsserver im integrierten SharePoint-Modus befindet  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_Instance-Member](msreportserver-instance-members.md)   
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](msreportserver-configurationsetting-class.md)  
  
  
