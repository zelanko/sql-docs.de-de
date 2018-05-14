---
title: Partitionen-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2faa85cb0caa87e537fc66f3385e574559d00ce2
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="partitions-element-assl"></a>Partitions-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält die Auflistung der [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md) -Elemente, die von einem [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) -Element verwendet werden, oder die Auflistung der Partitionsbindungen, die ein Out-of-Line- [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md) -Element bilden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MeasureGroup> <!-- or MeasureGroupBinding -->  
   ...  
   <Partitions>  
      <Partition>...</Partition> <!-- parent: MeasureGroup -->  
      <!-- or -->  
      <Partition xsi:type="PartitionBinding">...</Partition> <!-- parent: MeasureGroupBinding -->  
   </Partitions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|  
|Untergeordnete Elemente|Siehe Tabelle unten.|  
  
|Vorgänger oder übergeordnetes Element|Untergeordnetes Element|  
|------------------------|-------------------|  
|[MeasureGroup-Objekt](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|[Partition](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[Partition](../../../analysis-services/scripting/objects/partition-element-assl.md) des Typs [PartitionBinding](../../../analysis-services/scripting/data-type/partitionbinding-data-type-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.PartitionCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Schemaauflistungen & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
