---
title: ProactiveCaching-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ProactiveCaching Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ProactiveCaching
helpviewer_keywords:
- ProactiveCaching element
ms.assetid: 85f9ed44-2ede-406f-b0ca-237ab2f49722
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1c873cc6885d4f3a40f0de9e2f34048aff193c72
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183235"
---
# <a name="proactivecaching-element-assl"></a>ProactiveCaching-Element (ASSL)
  Definiert die Einstellungen für die proaktive Zwischenspeicherung für das übergeordnete Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <ProactiveCaching>  
      <OnlineMode>...</OnlineMode>  
      <AggregationStorage>...</AggregationStorage>  
      <Source>...</Source>  
      <SilenceInterval>...</SilenceInterval>  
      <Latency>...</Latency>  
      <SilenceOverrideInterval>...</SilenceOverrideInterval>  
      <ForceRebuildInterval>...</ForceRebuildInterval>  
      <Enabled >...</Enabled>  
   </ProactiveCaching>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Cube](cube-element-assl.md), [Dimension](dimension-element-assl.md), [MeasureGroup](group-element-assl.md), [Partition](partition-element-assl.md)|  
|Untergeordnete Elemente|[AggregationStorage](../properties/aggregationstorage-element-assl.md), [aktiviert](../properties/enabled-element-assl.md), [ForceRebuildInterval](../properties/forcerebuildinterval-element-assl.md), [Latenz](../properties/latency-element-assl.md), [OnlineMode](../properties/onlinemode-element-assl.md), [ SilenceInterval](../properties/silenceinterval-element-assl.md), [SilenceOverrideInterval](../properties/silenceoverrideinterval-element-assl.md), [Quelle](../properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
