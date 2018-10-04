---
title: EventID-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- EventID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EventID
helpviewer_keywords:
- EventID element
ms.assetid: a6b2ee50-1753-496c-af5c-206d63f2542b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d8f1f785d365b1899185297d903c81871fc3df41
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218886"
---
# <a name="eventid-element-assl"></a>EventID-Element (ASSL)
  Eindeutig identifiziert eine [Ereignis](../objects/event-element-assl.md) -Element, das als Teil des aufgezeichnet werden eine [Ablaufverfolgung](../objects/trace-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Event>  
  
      <EventID>...</EventID>  
  
</Event>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Ereignis](../objects/event-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das dem übergeordneten entspricht `EventID` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.TraceEvent>.  
  
## <a name="see-also"></a>Siehe auch  
 [Events-Element &#40;ASSL&#41;](../collections/events-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
