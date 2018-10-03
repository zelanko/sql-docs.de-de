---
title: IgnoreUnrelatedDimensions-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- IgnoreUnrelatedDimensions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- IgnoreUnrelatedDimensions
helpviewer_keywords:
- IgnoreUnrelatedDimensions element
ms.assetid: c7d7a1cd-a8e0-4ae7-9464-a1d2a55a86ab
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 400a1ef9f55d5696e2bbaeabbdd4a109c7a13587
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099340"
---
# <a name="ignoreunrelateddimensions-element-assl"></a>IgnoreUnrelatedDimensions-Element (ASSL)
  Bestimmt, ob nicht verknüpfte Dimensionen auf ihre höchste Ebene gezwungen werden, wenn Elemente von Dimensionen, die nicht mit der Measuregruppe verknüpft sind, in eine Abfrage eingeschlossen werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MeasureGroup>  
   ...  
   <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|Wahr|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MeasureGroup-Objekt](../objects/group-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Wenn `IgnoreUnrelatedDimensions` `true` ist, werden nicht verknüpfte Dimensionen auf ihre höchste Ebene gezwungen; wenn der Wert `false` ist, werden die Dimensionen nicht auf ihre oberste Ebene gezwungen. Diese Eigenschaft ähnelt, die MDX (Multidimensional Expressions) [ValidMeasure](/sql/mdx/validmeasure-mdx) Funktion.  
  
 Das Element, das dem übergeordneten entspricht `IgnoreUnrelatedDimensions` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
