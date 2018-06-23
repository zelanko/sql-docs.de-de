---
title: Groups-Element (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Groups Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Groups
helpviewer_keywords:
- Groups element
ms.assetid: 62196435-83a8-4a0a-8be1-7dfc986dc6c5
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cf89c9f0f5970bcc00d82cab42c0f759e5acb6c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057707"
---
# <a name="groups-element-assl"></a>Groups-Element (ASSL)
  Enthält die Auflistung der Gruppen von Elementen, die an ein Attribut gebunden sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Binding xsi:type="UserDefinedGroupBinding">  
   ...  
   <Groups>  
      <Group>...</Group>  
   </Groups>  
   ...  
</Binding>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Binden von](../data-type/binding-data-type-assl.md) des Typs [UserDefinedGroupBinding](../data-type/userdefinedgroupbinding-data-type-assl.md)|  
|Untergeordnete Elemente|[Gruppe](../objects/group-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.GroupCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen und-Bindungen &#40;SSAS – mehrdimensional&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  