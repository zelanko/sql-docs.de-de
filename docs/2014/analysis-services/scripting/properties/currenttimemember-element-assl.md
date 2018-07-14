---
title: CurrentTimeMember-Element (ASSL) | Microsoft-Dokumentation
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
- CurrentTimeMember Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CurrentTimeMember
helpviewer_keywords:
- CurrentTimeMember element
ms.assetid: 2e73009c-9f2b-441c-bdf0-ca19b160da4f
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 804b68d36d75741869595232fd09cd67959caa70
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204100"
---
# <a name="currenttimemember-element-assl"></a>CurrentTimeMember-Element (ASSL)
  Definiert das aktuelle Element einer Dimension zugeordneten Zeit eine [Kpi](../objects/kpi-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Kpi>  
   ...  
   <CurrentTimeMember>...</CurrentTimeMember>  
   ...  
</AggregationDimension>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[KPI](../objects/kpi-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist eine MDX-Anweisung (Multidimensional Expressions), die zu einem einzigen Element in einer Zeitdimension ausgewertet wird, welche zum Abrufen des aktuellen Zeitraums beim Auswerten des Key Performance Indicator (KPI) dient.  
  
 Das Element, das dem übergeordneten entspricht `CurrentTimeMember` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Kpi>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
