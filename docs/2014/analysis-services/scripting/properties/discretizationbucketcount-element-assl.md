---
title: DiscretizationBucketCount-Element (ASSL) | Microsoft-Dokumentation
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
- DiscretizationBucketCount Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DiscretizationBucketCount
helpviewer_keywords:
- DiscretizationBucketCount element
ms.assetid: 551a73ae-59e1-4079-a2d9-988df96b5e07
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0309610c503a229c698cc3d959eae10a5acbca06
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233730"
---
# <a name="discretizationbucketcount-element-assl"></a>DiscretizationBucketCount-Element (ASSL)
  Enthält die Anzahl der Buckets, in denen diskretisiert werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationBucketCount>...</DiscretizationBucketCount>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Integer|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert des `DiscretizationBucketCount`-Elements bestimmt, wie viele Gruppen oder "Buckets" erstellt werden, wenn Werte für `DimensionAttribute` oder `ScalarMiningStructureColumn` diskretisiert oder in einer spezifischen Menge an Gruppen angeordnet werden. Wenn das Element nicht angegeben wird, oder 0 (null) für den Wert des Elements angegeben ist [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] erstellt eine geeignete Anzahl von Gruppen in Abhängigkeit von der Diskretisierungsmethode. Weitere Informationen über die Diskretisierung finden Sie unter [Diskretisierungsmethoden &#40;Data Mining&#41;](../../data-mining/discretization-methods-data-mining.md).  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `DiscretizationBucketCount` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.DimensionAttribute> und <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Siehe auch  
 [DiscretizationMethod-Element &#40;ASSL&#41;](discretizationmethod-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
