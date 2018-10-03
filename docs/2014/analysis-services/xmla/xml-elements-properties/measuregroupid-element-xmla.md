---
title: MeasureGroupID-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 35f69c163fa2bf872ea777f5b79d8b7cce10ac76
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056450"
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
|Standardwert|None|  
|Cardinality|[Quelle](source-element-xmla.md), [Ziel](../xml-elements-properties/target-element-xmla.md) = 1-1: Erforderliches Element, das nur einmal vorkommt.|  
|Cardinality|Alle anderen = 0-1: Optionales Element, das nur einmal vorkommen kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Object](object-element-xmla.md), [ParentObject](parentobject-element-xmla.md), [Source](source-element-xmla.md), [Target](../xml-elements-properties/target-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
