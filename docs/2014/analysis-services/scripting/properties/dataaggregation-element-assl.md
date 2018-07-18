---
title: DataAggregation-Element (ASSL) | Microsoft-Dokumentation
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
- DataAggregation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataAggregation element
ms.assetid: baf6d2c9-54f6-4a6d-95f7-e1e758be458d
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eca6c0e89bcc120334e179ad59c1dfce657ab057
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289586"
---
# <a name="dataaggregation-element-assl"></a>DataAggregation-Element (ASSL)
  Bestimmt, ob die Instanz persistente Daten oder zwischengespeicherte Daten für aggregieren kann die [MeasureGroup](../objects/group-element-assl.md).  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MeasureGroup>  
   ...  
   <DataAggregation>...</DataAggregation>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*DataAndCacheAggregatable*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MeasureGroup-Objekt](../objects/group-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Keine*|Aggregation wird nicht für diese Measuregruppe ausgeführt.|  
|*DataAggregatable*|Persistente Daten können für diese Measuregruppe nicht aggregiert werden.|  
|*CacheAggregatable*|Zwischengespeicherte Daten können für diese Measuregruppe aggregiert werden.|  
|*DataAndCacheAggregatable*|Sowohl persistente Daten als auch zwischengespeicherte Daten können für diese Measuregruppe aggregiert werden.|  
  
 Das Element, das dem übergeordneten entspricht `DataAggregation` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>Siehe auch  
 [Cube-Element &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Dimension-Element &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
