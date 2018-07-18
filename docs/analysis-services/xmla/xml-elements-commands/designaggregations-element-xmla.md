---
title: DesignAggregations-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b32a7ecaf7c8268b88d3fc417cc1e41e024bfd2f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34574132"
---
# <a name="designaggregations-element-xmla"></a>DesignAggregations-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Erstellt Aggregationen für einen Aggregationsentwurf auf einer Analysis Services-Instanz an.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <DesignAggregations>  
      <Object>...</Object>  
      <Time>...</Time>  
      <Steps>...</Steps>  
      <Optimization>...</Optimization>  
      <Storage>...</Storage>  
      <Materialize>...</Materialize>  
      <Queries>...</Queries>  
   </DesignAggregations>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[Materialisieren](../../../analysis-services/xmla/xml-elements-properties/materialize-element-xmla.md), [Objekt](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [Optimierung](../../../analysis-services/xmla/xml-elements-properties/optimization-element-xmla.md), [Abfragen](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md), [Schritte](../../../analysis-services/xmla/xml-elements-properties/steps-element-xmla.md), [Speicher](../../../analysis-services/xmla/xml-elements-properties/storage-element-xmla.md) , [Zeit](../../../analysis-services/xmla/xml-elements-properties/time-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Der **DesignAggregations** -Befehl wird verwendet, um Aggregationsdefinitionen zu generieren, die von einem Aggregationsentwurf gespeichert werden. Ein Aggregationsentwurf kann dann verwendet werden, um Aggregationen für eine Partition zu materialisieren, und kann zwischen Partitionen neu verwendet werden.  
  
## <a name="see-also"></a>Siehe auch
 [Befehle &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
