---
title: CollectionCaption-Element (ASSL) | Microsoft Docs
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
ms.assetid: 33929373-11df-4f89-8d2e-d63923c44f53
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bba7c2ab2cffb2287b1eff84c5e9fc9f385119cb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149981"
---
# <a name="collectioncaption-element-assl"></a>CollectionCaption-Element (ASSL)
  Enthält den Pluralnamen für das übergeordnete Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<RelationshipEndTranslation>  
   <CollectionCaption>...</CollectionCaption>  
</RelationshipEndTranslation>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[RelationshipEndTranslation](../objects/translation-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das das übergeordnete Element des entspricht `CollectionCaption` im Objekt Analysis Management Objects (AMO) Modell t: Microsoft.AnalysisServices.relationshipendtranslation ist.  
  
  