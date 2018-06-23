---
title: Columns-Element (ASSL) | Microsoft Docs
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
- Columns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- COLUMNS
helpviewer_keywords:
- Columns element
ms.assetid: 14011eed-6f10-4120-b256-d599d59bde80
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e635738dddc7eabda62f0c35df860db3d9a10b60
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059003"
---
# <a name="columns-element-assl"></a>Columns-Element (ASSL)
  Enthält die Auflistung der Spalten, die mit dem übergeordneten Element verknüpft sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action xsi:type="DrillThroughAction"> <!-- or one of the elements listed below in the Element Relationships table -->  
   <Columns>  
      <Column xsi:type="MeasureBinding">...</Column> <!-- parent: DrillThroughAction -->  
      <!-- or -->  
      <Column xsi:type="CubeAttributeBinding">...</Column> <!-- parent: DrillThroughAction -->  
      <!-- or -->  
      <Column xsi:type="EventColumn">...</Column> <!-- parent: Event -->  
      <!-- or -->  
      <Column xsi:type="MiningModelColumn">...</Column> <!-- parent: MiningModel or MiningModelColumn -->  
      <!-- or -->  
      <Column xsi:type="MiningStructureColumn">...</Column> <!-- parent: MiningStructure or TableMiningStructureColumn -->  
   </Columns>  
</DrillThroughAction>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
  
|Vorgänger oder übergeordnetes Element|Cardinality|  
|------------------------|-----------------|  
|[Ereignis](../objects/event-element-assl.md)|1-1: Erforderliches Element, das nur einmal auftritt.|  
|Alle sonstigen|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Aktion](../objects/action-element-assl.md) des Typs [DrillThroughAction](../data-type/action-data-type-assl.md), [Ereignis](../objects/event-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [ MiningStructure](../objects/miningstructure-element-assl.md), [TableMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
  
|Vorgänger oder übergeordnetes Element|Untergeordnete Elemente|  
|------------------------|--------------------|  
|[DrillThroughAction](../data-type/binding-data-type-assl.md) oder [MeasureBinding](../data-type/measurebinding-data-type-assl.md)|  
|[Ereignis](../data-type/eventcolumn-data-type-assl.md)|  
|[MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|[MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|  
|[MiningStructure](../objects/miningstructure-element-assl.md), [TableMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|[Miningstructurecolumn-Objekt](../data-type/miningstructurecolumn-data-type-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Für `DrillThroughAction` Elemente, die `Columns` Auflistung identifiziert die Spalten, enthalten Daten zurückgegeben, wenn die Aktion ausgeführt wird.  
  
 Für `TableMiningStructureColumn` Elemente, die `Columns` Sammlung kann Sie nur eine Ebene der Rekursion. Mit anderen Worten, jedes `TableMiningStructureColumn` -Element in dieser Auflistung darf nicht enthalten `TableMiningStructureColumn` Elemente in seiner `Columns` Auflistung.  
  
 Einige der entsprechenden Elemente im AMO-Objektmodell (Analysis Management Objects) sind <xref:Microsoft.AnalysisServices.TraceColumnCollection>, <xref:Microsoft.AnalysisServices.MiningModelColumnCollection> und <xref:Microsoft.AnalysisServices.MiningStructureColumnCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  