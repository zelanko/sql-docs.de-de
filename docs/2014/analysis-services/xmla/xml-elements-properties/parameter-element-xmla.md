---
title: Parameter-Element (XMLA) | Microsoft-Dokumentation
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
- Parameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Parameter
- microsoft.xml.analysis.parameter
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameter
helpviewer_keywords:
- Parameter element
ms.assetid: fe31ac3d-a3e8-4f60-a81a-c43271ddbed4
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 07af3cb2626fb0c6407ce07e0521e665f0d5d556
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245622"
---
# <a name="parameter-element-xmla"></a>Parameter-Element (XMLA)
  Enthält den Namen und Wert eines Parameters, der von der [Execute](../xml-elements-methods-execute.md) -Methode verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Parameters>  
...  
   <Parameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </Parameter>  
...  
</Parameters>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Parameter](parameters-element-xmla.md)|  
|Untergeordnete Elemente|[Name](name-element-parameter-xmla.md), [Value](value-element-parameter-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Einige XMLA-Befehle (XML for Analysis) wie der [Process](../xml-elements-commands/process-element-xmla.md) -Befehl können weitere Informationen erfordern. Die `Parameter` -Element bietet einen Mechanismus zum Bereitstellen zusätzlicher Informationen, einschließlich segmentierter Informationen, XMLA-Befehl.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
