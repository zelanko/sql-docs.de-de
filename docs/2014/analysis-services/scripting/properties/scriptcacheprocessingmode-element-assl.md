---
title: ScriptCacheProcessingMode-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ScriptCacheProcessingMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ScriptCacheProcessingMode
helpviewer_keywords:
- ScriptCacheProcessingMode element
ms.assetid: 95c0723c-69a4-43e7-b743-f712180a7681
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7d74499d0678f920fe9f09b9cdc2d8626045a380
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221340"
---
# <a name="scriptcacheprocessingmode-element-assl"></a>ScriptCacheProcessingMode-Element (ASSL)
  Gibt an, ob der Server den Skriptcache während oder nach der Verarbeitung erstellen soll.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Cube>  
   ...  
      <ScriptCacheProcessingMode>...</ScriptCacheProcessingMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Reguläre*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Cube](../objects/cube-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Reguläre*|Der Server erstellt den Skriptcache während der Verarbeitung.|  
|*Lazy*|Der Server erstellt den Skriptcache nach der Verarbeitung.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `ScriptCacheProcessingMode` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ScriptCacheProcessingMode>.  
  
 Das Element, das dem übergeordneten entspricht `ScriptCacheProcessingMode` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Cube>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
