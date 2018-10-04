---
title: CaptionColumn-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CaptionColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CaptionColumn
helpviewer_keywords:
- CaptionColumn element
ms.assetid: bdb1b9b8-b5d5-4d91-81c7-8de8635bbb83
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bc8f782456b47f03ca8a7eab1bf9407020fda3f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108990"
---
# <a name="captioncolumn-element-assl"></a>CaptionColumn-Element (ASSL)
  Definiert die Spalte, die die Beschriftung für das Attribut bereitstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AttributeTranslation>  
   ...  
   <CaptionColumn xsi:type="DataItem">...</CaptionColumn>  
   ...  
</AttributeTranslation>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[DataItem-Objekt](../data-type/dataitem-data-type-assl.md)|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[AttributeTranslation](../data-type/translation-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu den `DataItem` Typ, einschließlich einer Tabelle von Analysis Services Scripting Language (ASSL)-Objekten und Eigenschaften der `DataItem` finden Sie unter [DataItem-Datentyp &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Das Element, das dem übergeordneten entspricht `CaptionColumn` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.AttributeTranslation>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
