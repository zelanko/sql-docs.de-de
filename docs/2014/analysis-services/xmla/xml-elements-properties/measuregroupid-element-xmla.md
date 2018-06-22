---
title: MeasureGroupID-Element (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MeasureGroupID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#MeasureGroupID
- http://schemas.microsoft.com/analysisservices/2003/engine#MeasureGroupID
- microsoft.xml.analysis.measuregroupid
helpviewer_keywords:
- MeasureGroupID element
ms.assetid: ff55777e-54ea-42b9-a084-2e12e0a10988
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: ee7a4c63f1ab71ad7f15e69a6288793378de5316
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047887"
---
# <a name="measuregroupid-element-xmla"></a>MeasureGroupID-Element (XMLA)
  Identifiziert eine Measuregruppe innerhalb eines übergeordneten Elements, das einen Objektverweis enthält.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Object> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <MeasureGroupID>...</MeasureGroupID>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|[Quelle](source-element-xmla.md), [Ziel](../xml-elements-properties/target-element-xmla.md) = 1-1: Erforderliches Element, das nur einmal vorkommt.|  
|Cardinality|Alle anderen = 0-1: Optionales Element, das nur einmal vorkommen kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Object](object-element-xmla.md), [ParentObject](parentobject-element-xmla.md), [Source](source-element-xmla.md), [Target](../xml-elements-properties/target-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  