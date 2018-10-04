---
title: Level-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Level Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LEVEL
helpviewer_keywords:
- Level element
ms.assetid: 66ee2c16-d6b8-4dd3-879f-1f2b6923bc43
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b057f53f04003755fecf4f297012559d48c6f09d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048246"
---
# <a name="level-element-assl"></a>Level-Element (ASSL)
  Definiert eine Ebene in einer [Hierarchie](hierarchy-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Levels>  
      <Level>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <SourceAttributeID>...</SourceAttributeID>  
      <HideMemberIf>...</HideMemberIf>  
      <Translations>...</Translations>  
      <Annotations>...</Annotations>  
   </Level>  
</Levels>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Levels](../collections/levels-element-assl.md)|  
|Untergeordnete Elemente|[Anmerkungen](../collections/annotations-element-assl.md), [Beschreibung](../properties/description-element-assl.md), [HideMemberIf](../properties/hidememberif-element-assl.md), [ID](../properties/id-element-assl.md), [Namen](../properties/name-element-assl.md), [SourceAttributeID](../properties/attributeid-element-assl.md), [Übersetzungen](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Bei diesem Datentyp gelten in keinem Bereitstellungsmodus Einschränkungen (1 - Mehrdimensional und Data Mining, 2 - SharePoint und 3 - Tabellarisch).  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.Level>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
