---
title: CalendarEndDate-Element (ASSL) | Microsoft Docs
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
- CalendarEndDate Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CalendarEndDate
helpviewer_keywords:
- CalendarEndDate element
ms.assetid: abedd074-9a28-4169-85b5-49ea57f10fb6
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2702e10f6b772ff072212d1fc9ac3097b50e9308
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151446"
---
# <a name="calendarenddate-element-assl"></a>CalendarEndDate-Element (ASSL)
  Definiert das Enddatum des Kalenderzeitraums für ein [TimeBinding](../data-type/binding-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<TimeBinding>  
   ...  
   <CalendarEndDate>...</CalendarEndDate>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|datetime|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das `CalendarEndDate` muss nach dem `CalendarStartDate` liegen.  
  
 Das Element, das das übergeordnete Element des entspricht `CalendarEndDate` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.TimeBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  