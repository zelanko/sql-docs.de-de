---
title: Source-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f0c18df53f7e53d044c5a5fe1ef3f59d9c4f7dd7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="source-element-xmla"></a>Source-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Stellt eine Quellpartition dar, die während eines [MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md) -Befehls zusammengeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Sources>  
   <Source>  
      <DatabaseID>...</DatabaseID>  
      <CubeID>...</CubeID>  
      <MeasureGroupID>...</MeasureGroupID>  
      <PartitionID>...</PartitionID>  
   </Source>  
</Sources>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|1-n: Erforderliches Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Datenquellen](../../../analysis-services/xmla/xml-elements-properties/sources-element-xmla.md)|  
|Untergeordnete Elemente|[CubeID](../../../analysis-services/xmla/xml-elements-properties/cubeid-element-xmla.md), [DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md), [MeasureGroupID](../../../analysis-services/xmla/xml-elements-properties/measuregroupid-element-xmla.md), [PartitionID](../../../analysis-services/xmla/xml-elements-properties/partitionid-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das **Source** -Element ist ein Objektverweis auf eine einzelne Partition, die mit einer Zielpartition zusammengeführt wird, die vom **Target** -Element des übergeordneten **MergePartitions** -Elements angegeben wird.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden alle vier Partitionen der `Internet Sales` -Measuregruppe mit der `Internet_Sales_2004` -Zielpartition kombiniert. Das Beispiel verweist auf den **Adventure Works** -Cube der [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] -Beispiel- [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenbank.  
  
```  
<MergePartitions xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
     <Source>        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>        <CubeID>Adventure Works</CubeID>        <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>        <PartitionID>Internet_Sales_2001</PartitionID>     </Source>     <Source>        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>        <CubeID>Adventure Works</CubeID>      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>      <PartitionID>Internet_Sales_2002</PartitionID>    </Source>    <Source>      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>      <PartitionID>Internet_Sales_2003</PartitionID>    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Target-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)   
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
