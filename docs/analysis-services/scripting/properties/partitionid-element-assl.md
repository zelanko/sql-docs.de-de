---
title: PartitionID-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b61d63e43131426846884a253d56851633322689
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="partitionid-element-assl"></a>PartitionID-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Ordnet eine [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md) Element mit einem übergeordneten Element, Bindung oder Out-of-Line-Bindung.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<PartitionBinding>  
   ...  
   <PartitionID>...</PartitionID>  
   ...  
</PartitionBinding>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[PartitionBinding](../../../analysis-services/scripting/data-type/partitionbinding-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu Bindungen und Out-of-Line-Bindungen, finden Sie unter [Datenquellen und-Bindungen &#40;mehrdimensionale SSAS-&#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
