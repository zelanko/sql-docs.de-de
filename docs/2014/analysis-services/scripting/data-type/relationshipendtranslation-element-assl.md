---
title: RelationshipEndTranslation-Element (ASSL) | Microsoft Docs
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
ms.assetid: 04e09370-fdfe-4051-9998-4a6859ce8c54
caps.latest.revision: 4
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bb93b3cdaf3eda1b8be15679b0736e626a802cf3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049800"
---
# <a name="relationshipendtranslation-element-assl"></a>RelationshipEndTranslation-Element (ASSL)
  Definiert einen Grunddatentyp, der für ein [RelationshipEnd](relationshipend-data-type-assl.md) -Element eine lokalisierte Übersetzung darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<RelationshipEndTranslation>  
   <Language>...</Language>  
   <Caption>...</Caption>  
   <CollectionCaption>...</Caption>  
   <Description>...</Description>  
   <DisplayFolder>...</DisplayFolder>  
   <Annotations>...</Annotations>  
</RelationshipEndTranslation>  
```  
  
## <a name="data-type-characteristics"></a>Datentypmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Basisdatentypen|InclusionThresholdSetting|  
|Abgeleitete Datentypen|[AttributeTranslation](translation-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Translations (Übersetzungen)](../collections/translations-element-assl.md)|  
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [Beschriftung](../properties/caption-element-assl.md), [CollectionCaption](../properties/caption-element-assl.md), [Beschreibung](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [Sprache](../properties/language-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  