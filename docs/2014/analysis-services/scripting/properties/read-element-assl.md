---
title: Element (ASSL) lesen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Read Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Read element
ms.assetid: 2e2c1173-72ca-4e8a-a6cd-fd348ef96d78
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5d4d8b256e29f3f4e4998fdc029f0d9eb3e1a893
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321200"
---
# <a name="read-element-assl"></a>Read-Element (ASSL)
  Bestimmt, ob Daten oder Metadaten für gelesen werden, kann eine bestimmte [CubeDimensionPermission](../data-type/permission-data-type-assl.md) oder [Berechtigung](../data-type/permission-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CubeDimensionPermission> <!-- or Permission -->  
   ...  
   <Read>...</Read>  
   ...  
</CubeDimensionPermission>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Keine*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CubeDimensionPermission](../objects/cubepermission-element-assl.md), [Berechtigung](../data-type/permission-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Keine*|Das übergeordnete Objekt lässt keinen Zugriff auf Daten oder Metadaten zu.|  
|*Zulässig*|Das übergeordnete Objekt lässt Lesezugriff auf Daten und Metadaten zu.|  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente, die den übergeordneten Elementen von entsprechen `Read` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.CubeDimensionPermission> und <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Cube-Element &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Dimension-Element &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [CubePermission-Element &#40;ASSL&#41;](../objects/cubepermission-element-assl.md)   
 [Permission-Datentyp &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
