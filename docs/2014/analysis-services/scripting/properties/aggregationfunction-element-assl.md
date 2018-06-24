---
title: AggregationFunction-Element (ASSL) | Microsoft Docs
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
- AggregationFunction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationFunction
helpviewer_keywords:
- AggregationFunction element
ms.assetid: 40cfc7f9-1089-45f9-be90-a29770ed9682
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6c8b28c740e82d661c2664eac576f0e079fd3d46
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049988"
---
# <a name="aggregationfunction-element-assl"></a>AggregationFunction-Element (ASSL)
  Enthält die Aggregationsfunktion, die für den Kontotyp zu verwenden ist.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Account>  
   ...  
   <AggregationFunction>...</AggregationFunction>  
   ...  
</Account>  
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
|Übergeordnete Elemente|[Konto](../objects/account-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der folgenden Zeichenfolgen beschränkt:  
  
|value|Description|  
|-----------|-----------------|  
|*Sum*|Das Measure wird mit aggregiert die `Sum` Funktion.|  
|*Anzahl*|Das Measure wird mit aggregiert die `Count` Funktion.|  
|*Min*|Das Measure wird mit aggregiert die `Min` Funktion.|  
|*Max*|Das Measure wird mit aggregiert die `Max` Funktion.|  
|*DistinctCount*|Das Measure wird mit aggregiert die `DistinctCount` Funktion.|  
|*Keine*|Das Measure wird nicht aggregiert.|  
|*AverageOfChildren*|Das Measure wird durch Zurückgeben des Durchschnitts der untergeordneten Elemente aggregiert.|  
|*FirstChild*|Das Measure wird durch Zurückgeben des ersten untergeordneten Elements aggregiert.|  
|*LastChild*|Das Measure wird durch Zurückgeben des letzten untergeordneten Elements aggregiert.|  
|*FirstNonEmpty*|Das Measure wird durch Zurückgeben des ersten nicht leeren Elements aggregiert.|  
|*LastNonEmpty*|Das Measure wird durch Zurückgeben des letzten nicht leeren Elements aggregiert.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `AggregationFunction` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>Siehe auch  
 [Accounts-Element &#40;ASSL&#41;](../collections/accounts-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  