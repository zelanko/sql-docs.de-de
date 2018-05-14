---
title: Lesen-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bfa72c2e279b6e4633706aa7afb0c9f68ccd1793
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="read-element-assl"></a>Read-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Bestimmt, ob Daten oder Metadaten für ein gegebenes [CubeDimensionPermission](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md) -Element oder [Permission](../../../analysis-services/scripting/data-type/permission-data-type-assl.md) -Element gelesen werden können.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CubeDimensionPermission> <!-- or Permission -->  
   ...  
   <Read>...</Read>  
   ...  
</CubeDimensionPermission>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*InclusionThresholdSetting*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CubeDimensionPermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md), [Permission](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*InclusionThresholdSetting*|Das übergeordnete Objekt lässt keinen Zugriff auf Daten oder Metadaten zu.|  
|*Zulässig*|Das übergeordnete Objekt lässt Lesezugriff auf Daten und Metadaten zu.|  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente, die den übergeordneten Elementen von entsprechen **lesen** im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.CubeDimensionPermission> und <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Cube-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Dimension-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [CubePermission-Element & #40; ASSL & #41;](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)   
 [Permission-Datentyp & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)   
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
