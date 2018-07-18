---
title: AggregateFunction-Element (ASSL) | Microsoft-Dokumentation
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
- AggregateFunction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregateFunction
helpviewer_keywords:
- AggregateFunction element
ms.assetid: 880b6bd0-d62a-4221-831c-39f748ee84f2
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bc2eccf4ca6e41ffba52424c4f45edb71c9c1c46
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261206"
---
# <a name="aggregatefunction-element-assl"></a>AggregateFunction-Element (ASSL)
  Definiert den Typ der Aggregatfunktion, die ein, die eine [Measure](../objects/measure-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Measure>  
   ...  
   <AggregateFunction>...</AggregateFunction>  
   ...  
</Measure>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Sum*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Measure](../objects/measure-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Sum*|Das Measure wird mit aggregiert die `Sum` Funktion.|  
|*Anzahl*|Das Measure wird mit aggregiert die `Count` Funktion.|  
|*Min*|Das Measure wird mit aggregiert die `Min` Funktion.|  
|*Max*|Das Measure wird mit aggregiert die `Max` Funktion.|  
|*DistinctCount*|Das Measure wird mit aggregiert die `DistinctCount` Funktion.|  
|*Keine*|Das Measure wird nicht aggregiert.|  
|*ByAccount*|Das Measure wird gemäß dem Konto aggregiert.|  
|*AverageOfChildren*|Das Measure wird durch Zurückgeben des Durchschnitts der untergeordneten Elemente aggregiert.|  
|*FirstChild*|Das Measure wird durch Zurückgeben des ersten untergeordneten Elements aggregiert.|  
|*LastChild*|Das Measure wird durch Zurückgeben des letzten untergeordneten Elements aggregiert.|  
|*FirstNonEmpty*|Das Measure wird durch Zurückgeben des ersten nicht leeren Elements aggregiert.|  
|*LastNonEmpty*|Das Measure wird durch Zurückgeben des letzten nicht leeren Elements aggregiert.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `AggregateFunction` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
