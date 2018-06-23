---
title: ReadSourceData-Element (ASSL) | Microsoft Docs
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
- ReadSourceData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ReadSourceData element
ms.assetid: 7da4665a-fba3-4aae-8dee-678dc14d3b05
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dcbb6ce5b9cda3b17b69558cd60f6030f9e097b1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148701"
---
# <a name="readsourcedata-element-assl"></a>ReadSourceData-Element (ASSL)
  Bestimmt, wie eindeutige Namen für die enthaltenen Hierarchien generiert werden, die [CubePermission](../objects/cubepermission-element-assl.md).  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CubePermission>  
   ...  
   <ReadSourceData>...</ReadSourceData>  
   ...  
</CubePermission>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Keine*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[CubePermission](../objects/cubepermission-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Keine*|Es ist kein Zugriff auf Daten erlaubt, die auf Berechnungsdurchlauf 0 verfügbar sind.|  
|*Zulässig*|Der Zugriff auf Daten, die auf Berechnungsdurchlauf 0 verfügbar sind, ist erlaubt.|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das das übergeordnete Element des entspricht `ReadSourceData` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.CubePermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Cube-Element &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Dimension-Element &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  