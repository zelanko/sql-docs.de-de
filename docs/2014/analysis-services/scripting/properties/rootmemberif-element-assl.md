---
title: RootMemberIf-Element (ASSL) | Microsoft Docs
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
- RootMemberIf Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RootMemberIf
helpviewer_keywords:
- RootMemberIf element
ms.assetid: b695e271-c748-4abc-a09f-acb1014f768f
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5a923b08efc636d2635d60b00f85c42dc00a312e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056321"
---
# <a name="rootmemberif-element-assl"></a>RootMemberIf-Element (ASSL)
  Bestimmt, wie das Stammelement oder die Elemente eines übergeordneten Attributs identifiziert werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <RootMemberIf>...</RootMemberIf>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*ParentIsBlankSelfOrMissing*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Den Wert des der `RootMemberIf` Element wird nur von übergeordneten Attributen verwendet (also der Wert der die [Verwendung](usage-element-dimensionattribute-assl.md) Element des der `DimensionAttribute` auf übergeordnetes Element festgelegt ist *übergeordneten*) bestimmen den Stamm ( obersten Elemente) einer über-/ unterordnungshierarchie.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|Nur Elemente, die mindestens eine der für *ParentIsBlank*, *ParentIsSelf*oder *ParentIsMissing* geltenden Bedingungen erfüllen, werden als Stammelemente behandelt.|  
|*ParentIsBlank*|Nur Elemente mit Null, eine 0 (null) oder eine leere Zeichenfolge in den Schlüsselspalten, dargestellt durch die [KeyColumns](../collections/columns-element-assl.md) Auflistung von `DimensionAttribute` werden als Stammelemente behandelt.|  
|*ParentIsSelf*|Es werden nur Elemente als Stammelemente behandelt, die für sich selbst als übergeordnetes Element festgelegt wurden.|  
|*ParentIsMissing*|Es werden nur Elemente als Stammelemente behandelt, deren übergeordnete Elemente nicht gefunden werden.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `RootMemberIf` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.RootIfValue>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  