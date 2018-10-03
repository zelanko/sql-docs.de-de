---
title: AggregationType-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dad62254c9da3809ae33dcfb035de34fa52a89fc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059620"
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
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[AggregationInstance](../objects/aggregationinstance-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
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
  
  
