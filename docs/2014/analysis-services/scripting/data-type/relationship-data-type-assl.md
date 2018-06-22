---
title: Beziehungsdatentyp (ASSL) | Microsoft Docs
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
ms.assetid: 73d7c48d-d8e0-4119-849d-b5f912d449e4
caps.latest.revision: 4
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 81421605828b064644f0b9a0cfae2a7ed1b301a8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149149"
---
# <a name="relationship-data-type-assl"></a>Beziehungsdatentyp (ASSL)
  Definiert einen Grunddatentyp, der eine Beziehung in einer Dimension darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Relationship>  
   <ID>...</ID>  
   <Visible>...</Visible>  
   <FromRelationshipEnd>...</FromRelationshipEnd>  
   <ToRelationshipEnd>...</ToRelationshipEnd>  
</Relationship>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|InclusionThresholdSetting|  
|Untergeordnete Elemente|[ID](../properties/id-element-assl.md), [Sichtbar](../properties/visible-element-assl.md), [FromRelationshipEnd](relationshipend-data-type-assl.md), [ToRelationshipEnd](relationshipend-data-type-assl.md)|  
|Abgeleitete Elemente||  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.Relationship>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  