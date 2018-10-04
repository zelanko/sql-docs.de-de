---
title: ModelingFlag-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ModelingFlag Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ModelingFlag
helpviewer_keywords:
- ModelingFlag element
ms.assetid: c9af1b9a-506f-4cc1-acd7-e57698cb672c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8137da94a03e560fbed2c263e8e0a10b187fa569
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118130"
---
# <a name="modelingflag-element-assl"></a>ModelingFlag-Element (ASSL)
  Enthält ein Modellierungsflag für eine Spalte in einer Miningstruktur oder einem Miningmodell.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ModelingFlags>  
   <ModelingFlag xsi:type="MiningModelingFlag">...</ModelingFlag>  
</ModelingFlags>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[MiningModelingFlag](../data-type/miningmodelingflag-data-type-assl.md)|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[ModelingFlags](../collections/modelingflags-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Ein eng verwandtes Element im AMO-Objektmodell (Analysis Management Objects) ist <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>Siehe auch  
 [MiningModel-Element &#40;ASSL&#41;](miningmodel-element-assl.md)   
 [MiningStructure-Element &#40;ASSL&#41;](miningstructure-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
