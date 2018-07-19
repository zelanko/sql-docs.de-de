---
title: Caption-Element (ASSL) | Microsoft-Dokumentation
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
- Caption Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Caption
helpviewer_keywords:
- Caption element
ms.assetid: ed2be851-0ddc-4fa5-8aee-b2acb2e6d25e
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 283e7f84373d5f36431ba1b706b4d27e23cb876f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167701"
---
# <a name="caption-element-assl"></a>Caption-Element (ASSL)
  Enthält die Beschriftung für das zugeordnete übergeordnete Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action> <!-- or Translation -->  
   ...  
  <Caption>...</Caption>  
   ...  
</Action>  
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
|Übergeordnetes Element|[Aktion](../objects/action-element-assl.md), [Übersetzung](../objects/translation-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente, die den übergeordneten Elementen von entsprechen `Caption` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.Action> und <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
