---
title: CubeHierarchy-Datentyp (ASSL) | Microsoft Docs
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
- CubeHierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeHierarchy
helpviewer_keywords:
- CubeHierarchy data type
ms.assetid: cd633409-0c14-4dd9-97cc-3d30e25df24f
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 48176b4096b7fa7ba8e1847750410be0f65da552
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147769"
---
# <a name="cubehierarchy-data-type-assl"></a>CubeHierarchy-Datentyp (ASSL)
  Definiert einen Grunddatentyp, der Informationen darstellt, zu einer [Hierarchie](../objects/hierarchy-element-assl.md) Element in eine [Cube](../objects/cube-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```  
<CubeHierarchy>   <HierarchyID>...</HierarchyID>   <Name>...</Name>   <OptimizedState>...</OptimizedState>   <Visible>...</Visible>   <Enabled>...</Enabled>   <Annotations>...</Annotations></CubeHierarchy>  
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
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [aktiviert](../properties/enabled-element-assl.md), [HierarchyID](../properties/id-element-assl.md), [Namen](../properties/name-element-assl.md), [OptimizedState](../properties/state-element-assl.md), [sichtbar](../properties/visible-element-assl.md)|  
|Abgeleitete Elemente|[Hierarchie](../objects/hierarchy-element-assl.md) ([Hierarchien](../collections/hierarchies-element-assl.md) Auflistung von [CubeDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Hinweise  
 Dieser Datentyp unterliegt in keinem Bereitstellungsmodus Einschränkungen und kann in jedem dieser Modi verwendet werden: 0 - Mehrdimensional und Data Mining, 1 - SharePoint und 2 - Tabellarisch.  
  
 In [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)], *aktiviert* Eigenschaft kann nicht festgelegt werden, um `False` für *CubeHierarchy*.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.CubeHierarchy>.  
  
## <a name="see-also"></a>Siehe auch  
 [Discover-Methode &#40;XMLA&#41;](../../xmla/xml-elements-methods-discover.md)   
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  