---
title: RelationshipEndTranslation-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 04e09370-fdfe-4051-9998-4a6859ce8c54
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0e36c3f114f70c17022e4fe0c11494f5e9c38748
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131520"
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
|Basisdatentypen|None|  
|Abgeleitete Datentypen|[AttributeTranslation](translation-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Datentypbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Translations (Übersetzungen)](../collections/translations-element-assl.md)|  
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [Beschriftung](../properties/caption-element-assl.md), [CollectionCaption](../properties/caption-element-assl.md), [Beschreibung](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [Sprache](../properties/language-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Datentypen &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
