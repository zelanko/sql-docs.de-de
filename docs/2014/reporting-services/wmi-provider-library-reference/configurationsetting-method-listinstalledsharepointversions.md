---
title: ListInstalledSharePointVersions-Methode (WMI) | Microsoft-Dokumentation
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
- ListInstalledSharePointVersions method
ms.assetid: 8f0a5e9f-23f1-41e5-9a90-dfec19ef1df7
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 41c68f8c0a440aec22079f308cd501c7204b1f41
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157631"
---
# <a name="listinstalledsharepointversions-method-wmi"></a>ListInstalledSharePointVersions-Methode (WMI)
  Gibt einen Satz von Token zurück, die die Versionen von Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]oder [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] darstellen, die auf dem gleichen Computer wie der Berichtsserver installiert sind.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub ListInstalledSharePointVersions(ByRef VersionTokens() _  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] VersionTokens,   
    out Int32 Length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *VersionTokens[]*  
 [out] Ein Array, das die Token enthält, welche die Version eines SharePoint-Produkts oder der SharePoint-Technologie darstellen, die mit dem installierten Berichtsserver kompatibel ist  
  
 *Länge*  
 [out] Die Länge des Arrays von Versionstoken  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Jedes Token, das zurückgegeben wird, stellt eine Version von [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] oder [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] dar, die mit dem derzeit installierten Berichtsserver kompatibel ist. Wenn eine bestimmte Version von SharePoint kompatibel mit früheren Versionen von SharePoint ist, werden Token für jede kompatible Version von SharePoint zurückgegeben.  
  
 Die folgende Tabelle enthält die SharePoint-Token, die zurückgegeben werden.  
  
|**Versionstoken**|**Beschreibung**|  
|------------------------|---------------------|  
|WSS_V2_Compatible|Es ist eine [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]-, [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]-, [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]-, [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]- oder [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] -Installation vorhanden, die mit [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 2.0 kompatibel ist.|  
|WSS_V3_Compatible|Es ist eine [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]-, [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]-, [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]-, [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]- oder [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] -Installation vorhanden, die mit [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0 kompatibel ist.|  
|WSS_V4_Compatible|Es ist eine [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] - oder [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] -Installation vorhanden, die mit Office 14 kompatibel ist.|  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
