---
title: ReadSourceData-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8c341162a62eb74dc0b07863959e0e5318daf0a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166512"
---
# <a name="readsourcedata-element-assl"></a>ReadSourceData-Element (ASSL)
  Bestimmt, wie eindeutige Namen für Hierarchien, die in enthaltenen generiert werden, die [CubePermission](../objects/cubepermission-element-assl.md).  
  
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
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Keine*|Es ist kein Zugriff auf Daten erlaubt, die auf Berechnungsdurchlauf 0 verfügbar sind.|  
|*Zulässig*|Der Zugriff auf Daten, die auf Berechnungsdurchlauf 0 verfügbar sind, ist erlaubt.|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das dem übergeordneten entspricht `ReadSourceData` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.CubePermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Cube-Element &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Dimension-Element &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
