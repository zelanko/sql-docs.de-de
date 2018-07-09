---
title: AggregationType-Element (ASSL) | Microsoft-Dokumentation
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
- AggregationType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationType element
ms.assetid: c1393bc6-d715-4397-8bc5-82abdb275330
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f7c95f9566f483ec7a047ceedd074237f9ff5f7e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183217"
---
# <a name="aggregationtype-element-assl"></a>AggregationType-Element (ASSL)
  Definiert den Typ von Aggregation, die gespeichert werden, indem die [Partition](../objects/partition-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AggregationInstance>  
   ...  
   <AggregationType>...</AggregationType>  
   ...  
</AggregationInstance>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[AggregationInstance](../objects/aggregationinstance-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*IndexedView*|Die Aggregation wird in einer indizierten Sicht gespeichert.|  
|*Tabelle*|Die Aggregation wird in einer Tabelle gespeichert.|  
|*UserDefined*|Die Aggregation ist benutzerdefiniert.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `AggregationType` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
