---
title: OnlineMode-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- OnlineMode Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- OnlineMode
helpviewer_keywords:
- OnlineMode element
ms.assetid: 0bbac4e2-002f-4be4-8dd6-ccd7034f5f93
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a7a4469a522b1364df645fc1dcb0362647397a89
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196840"
---
# <a name="onlinemode-element-assl"></a>OnlineMode-Element (ASSL)
  Gibt an, ob die Datenbank sofort nach dem Initiieren der Cache-Neuerstellung oder erst nach Abschluss der Cache-Neuerstellung wieder online geschaltet wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <OnlineMode>...</OnlineMode>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Sofortige*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Sofortige*|Datenbank wird sofort wieder online geschaltet, wenn die Neuerstellung des Caches initiiert wird.|  
|*OnCacheComplete*|Datenbank wird erst wieder online geschaltet, wenn die Neuerstellung des Caches abgeschlossen ist.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `OnlineMode` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>Siehe auch  
 [ProactiveCaching-Element &#40;ASSL&#41;](../objects/proactivecaching-element-assl.md)  
  
  
