---
title: 'IsSharePointIntegrated-Eigenschaft (WMI: MSReportServer_Instance) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 95e7bade956c791feceddc32f2a0423c331fe77f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66097112"
---
# <a name="issharepointintegrated-property-wmi-msreportserver_instance"></a>IsSharePointIntegrated-Eigenschaft (WMI: MSReportServer_Instance)
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
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:**[!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mitglieder MSReportServer_Instance](msreportserver-instance-members.md)   
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](msreportserver-configurationsetting-class.md)  
  
  
