---
title: CubeAttribute-Datentyp (ASSL) | Microsoft Docs
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
- CubeAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeAttribute
helpviewer_keywords:
- CubeAttribute data type
ms.assetid: 114ffb44-460b-4971-b31b-dd844e960b81
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dce594145db99d7edfa991c2e975f62e55d3ef34
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058384"
---
# <a name="cubeattribute-data-type-assl"></a>CubeAttribute-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der ein Attribut zugeordnet darstellt eine [Cube](../objects/cube-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CubeAttribute>  
   <AttributeID>...</AttributeID>  
   <AggregationUsage>...</AggregationUsage>  
   <AttributeHierarchyOptimizedState>...</AttributeHierarchyOptimizedState>  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   <Annotations>...</Annotations>  
</CubeAttribute>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[AggregationUsage](../properties/aggregationusage-element-assl.md), [Anmerkungen](../collections/annotations-element-assl.md), [AttributeHierarchyEnabled](../properties/enabled-element-assl.md), [AttributeHierarchyOptimizedState](../properties/state-element-assl.md), [ AttributeHierarchyVisible](../properties/visible-element-assl.md), [AttributeID](../properties/id-element-assl.md)|  
|Abgeleitete Elemente|[Attribut](../objects/attribute-element-assl.md) ([Attribute](../collections/attributes-element-assl.md) Auflistung von [CubeDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Die *AttributeHierarchyOptimizedState* Element wird nicht unterstützt, wenn der Dienst in der Konfiguration der DeploymentMode Eigenschaftswerte von 1 oder 2 (SharePoint- oder tabellarischer Modus zum Ausführen von PowerPivot- und tabellarischen modelldatenbanken) ausgeführt.  
  
 Ein Attribut kann nicht als Ebene einer Hierarchie hinzugefügt werden bei der Eigenschaft *AtttributeHierarchyEnabled*, auf "false" festgelegt ist und die Instanz im DeploymentMode 1 oder 2 (SharePoint- oder tabellarischer Servermodus) betrieben wird.  
  
 Attribute in der [CubeDimension](dimension-data-type-assl.md) Element, das nicht explizit in enthalten sind die [Attribute](../collections/attributes-element-assl.md) Auflistung werden in der Auflistung mit den Standardwerten, die ihnen zugewiesen. Nachdem die Attribute der Auflistung hinzugefügt werden, können die Attribute zurückgegeben werden, indem die [Discover](../../xmla/xml-elements-methods-discover.md) Methode.  
  
 Die [AggregationUsage](../properties/aggregationusage-element-assl.md) Element Steuerelemente wie [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] automatisch Aggregationen für das Attribut entwirft. Das `AggregationUsage`-Element schränkt keine Aggregationen ein, die manuell für den Cube erstellt werden.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.CubeAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  