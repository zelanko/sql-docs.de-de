---
title: CalendarLanguage-Element (ASSL) | Microsoft Docs
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
- CalendarLanguage Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CalendarLanguage
helpviewer_keywords:
- CalendarLanguage element
ms.assetid: e43a0f48-a583-418b-a0a4-d73a40035573
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d3be256a83ee4ee0d6b1c448699f50076e44e186
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160521"
---
# <a name="calendarlanguage-element-assl"></a>CalendarLanguage-Element (ASSL)
  Definiert die für verwendete Kalendersprache der [TimeBinding](../data-type/binding-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<TimeBinding>  
   ...  
   <CalendarLanguage>...</CalendarLanguage>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Integer|  
|Standardwert|`1033`|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Dies ist die Sprache, in der Dimensionselementnamen erstellt werden. Die Sprache von Beschriftungen sollte mit ganzzahlig-basierten LCID-Codes definiert werden. Zum Beispiel stellt den Standardwert die English-US LCID dar.  
  
 Das Element, das das übergeordnete Element des entspricht `CalendarLanguage` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.TimeBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  