---
title: IncrementalProcessingNotification-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- IncrementalProcessingNotification Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- IncrementalProcessingNotification element
ms.assetid: bfc9b0a4-4043-4aaf-82d9-67e7f1d1eb81
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 639d58928b27e965a707602c0ea124c9078e5b47
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120740"
---
# <a name="incrementalprocessingnotification-element-assl"></a>IncrementalProcessingNotification-Element (ASSL)
  Enthält Informationen für die [ProactiveCaching](proactivecaching-element-assl.md) Element über eine Abfrage zum Ermitteln des Fortschritts der inkrementellen Verarbeitung ausgeführt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<IncrementalProcessingNotifications>  
   <IncrementalProcessingNotification xsi:type="IncrementalProcessingNotification">...</IncrementalProcessingNotification>  
</IncrementalProcessingNotifications>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[IncrementalProcessingNotification](../data-type/incrementalprocessingnotification-data-type-assl.md)|  
|Standardwert|None|  
|Cardinality|1-n: Erforderliches Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[IncrementalProcessingNotifications](../collections/incrementalprocessingnotifications-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>.  
  
## <a name="see-also"></a>Siehe auch  
 [ProactiveCachingQueryBinding-Datentyp &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [ProactiveCaching-Element &#40;ASSL&#41;](proactivecaching-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
