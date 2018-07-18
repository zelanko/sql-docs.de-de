---
title: ID-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ID
helpviewer_keywords:
- ID element
ms.assetid: ea3ce0f4-9084-45d0-8150-73afb7005af2
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c323bd71865d0dd09bf724373ece03d83e7608ee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209940"
---
# <a name="id-element-assl"></a>ID-Element (ASSL)
  Enthält den eindeutigen Bezeichner (ID) des übergeordneten Elements.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action> <!-- or one of the elements listed in the Element Relationships table -->  
   ...  
   <ID>...</ID>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (bis zu 100 Zeichen)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Aktion](../objects/action-element-assl.md), [Aggregation](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [Assembly](../objects/assembly-element-assl.md), [Cube](../objects/cube-element-assl.md), [CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md), [CubeDimension](../data-type/dimension-data-type-assl.md), [Datenbank](../objects/database-element-assl.md), [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [Dimension ](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [Hierarchie](../objects/hierarchy-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [Ebene](../objects/level-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [Measure](../objects/measure-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MeasureGroupBinding](../data-type/binding-data-type-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [ MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [Partition](../objects/partition-element-assl.md), [Berechtigung](../data-type/permission-data-type-assl.md), [Perspektive](../objects/perspective-element-assl.md), [Rolle](../objects/role-element-assl.md), [Server](../objects/server-element-assl.md), [Ablaufverfolgung](../objects/trace-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Jedes Hauptobjekt in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verfügt über eine `ID` -Element als Eigenschaft. Der Wert des einem `ID` -Elements hat die folgenden Einschränkungen:  
  
-   Der Wert darf keine führenden oder nachgestellten Leerzeichen enthalten. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] entfernt implizit führende oder nachfolgende Leerzeichen aus dem Wert eines `ID`-Elements.  
  
-   Der Wert kann keine Steuerzeichen enthalten. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] entfernt implizit Steuerzeichen aus dem Wert eines `ID`-Elements.  
  
-   Die folgenden reservierten Werte können nicht verwendet werden:  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1 bis COM9 (COM1, COM2, COM3 usw.)  
  
    -   CON  
  
    -   LPT1 bis LPT9 (LPT1, LPT2, LPT3 usw.)  
  
    -   NUL  
  
    -   PRN  
  
 Die folgende Tabelle führt zusätzliche Zeichen, die im Wert verwendet werden, können keinem `ID` -Element, abhängig vom übergeordneten Element.  
  
|Übergeordnetes Element|Zeichen|  
|--------------------|----------------|  
|[Server](../objects/server-element-assl.md)|Der Wert muss den Regeln für [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Computernamen entsprechen. (IP-Adressen sind nicht gültig.)|  
|[DataSource](../objects/datasource-element-assl.md)|:/\\*&#124;?" () []{}<>|  
|[Ebene](../objects/level-element-assl.md), [Attribut-Element](../objects/attribute-element-assl.md)|.,;' `:/\\*&#124;?" & % $! += []{}<>|  
|Alle anderen übergeordneten Elemente|.,;' `:/\\*&#124;?" & % $! += () []{}<>|  
  
## <a name="see-also"></a>Siehe auch  
 [Namen von Element &#40;ASSL&#41;](name-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
