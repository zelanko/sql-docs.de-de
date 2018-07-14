---
title: Slice-Element (ASSL) | Microsoft-Dokumentation
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
- Slice Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Slice
helpviewer_keywords:
- Slice element
ms.assetid: 2c8c4107-c641-4724-bfa5-0c47e0ec8888
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 299f84167ec64c4bdd795c56a608e76f61d348b0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178887"
---
# <a name="slice-element-assl"></a>Slice-Element (ASSL)
  Enthält einen Multidimensional Expressions (MDX)-Ausdruck, der den in einer Partition enthaltenen Slice definiert.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Partition>  
      ...  
   <Slice>...</Slice>  
   ...  
</Partition>  
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
|Übergeordnetes Element|[Partition](../objects/partition-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das `Slice`-Element enthält einen MDX-Tupelausdruck oder einen Mengenausdruck, der den Teil des Cubes identifiziert, für den die Partition Informationen speichert. Der MDX-Ausdruck ähnelt der [StrToSet](/sql/mdx/strtoset-mdx) MDX-Funktion mit dem Schlüsselwort CONSTRAINED, da der Ausdruck MDX oder benutzerdefinierten Funktionen enthalten kann.  
  
 Das Element, das dem übergeordneten entspricht `Slice` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
