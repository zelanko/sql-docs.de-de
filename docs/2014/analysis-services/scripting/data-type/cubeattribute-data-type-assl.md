---
title: CubeAttribute-Datentyp (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d64224c1b7489895ff0d9dca00a3841be0ed0bbc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203300"
---
# <a name="cubeattribute-data-type-assl"></a>CubeAttribute-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der ein Attribut mit verknüpften darstellt eine [Cube](../objects/cube-element-assl.md) Element.  
  
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
|Basisdatentypen|None|  
|Abgeleitete Datentypen|None|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|None|  
|Untergeordnete Elemente|[AggregationUsage](../properties/aggregationusage-element-assl.md), [Anmerkungen](../collections/annotations-element-assl.md), [AttributeHierarchyEnabled](../properties/enabled-element-assl.md), [AttributeHierarchyOptimizedState](../properties/state-element-assl.md), [ AttributeHierarchyVisible](../properties/visible-element-assl.md), [AttributeID](../properties/id-element-assl.md)|  
|Abgeleitete Elemente|[Attribut](../objects/attribute-element-assl.md) ([Attribute](../collections/attributes-element-assl.md) Auflistung von [CubeDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Die *AttributeHierarchyOptimizedState* Element wird nicht unterstützt, wenn der Dienst in der Konfiguration der DeploymentMode Eigenschaftswerte von 1 oder 2 (SharePoint- oder tabellarischer Modus zum Ausführen von PowerPivot- und tabellarischen modelldatenbanken) ausgeführt.  
  
 Ein Attribut kann nicht als Ebene einer Hierarchie hinzugefügt werden bei der Eigenschaft *AtttributeHierarchyEnabled*, auf "false" festgelegt ist und die Instanz im DeploymentMode 1 oder 2 (SharePoint- oder tabellarischer Servermodus) ausgeführt wird.  
  
 Attribute in der [CubeDimension](dimension-data-type-assl.md) -Element, das nicht explizit in enthalten sind die [Attribute](../collections/attributes-element-assl.md) Sammlung werden in der Auflistung mit den Standardwerten, die zugewiesen werden. Nachdem die Attribute der Auflistung hinzugefügt werden, können die Attribute zurückgegeben werden, indem die [Discover](../../xmla/xml-elements-methods-discover.md) Methode.  
  
 Die [AggregationUsage](../properties/aggregationusage-element-assl.md) Element Steuerelemente wie [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] automatisch Entwerfen von Aggregationen für das Attribut. Das `AggregationUsage`-Element schränkt keine Aggregationen ein, die manuell für den Cube erstellt werden.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.CubeAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
