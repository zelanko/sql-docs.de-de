---
title: IncrementalProcessingNotification-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 22f3975b8f2c09a45f0d82857ced58424c4a9b74
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="incrementalprocessingnotification-element-assl"></a>IncrementalProcessingNotification-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält Informationen für die [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) Element über eine Abfrage zum Ermitteln des Fortschritts der inkrementellen Verarbeitung ausgeführt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<IncrementalProcessingNotifications>  
   <IncrementalProcessingNotification xsi:type="IncrementalProcessingNotification">...</IncrementalProcessingNotification>  
</IncrementalProcessingNotifications>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|[IncrementalProcessingNotification](../../../analysis-services/scripting/data-type/incrementalprocessingnotification-data-type-assl.md)|  
|Standardwert|Keine|  
|Kardinalität|1-n: Erforderliches Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[IncrementalProcessingNotifications](../../../analysis-services/scripting/collections/incrementalprocessingnotifications-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>.  
  
## <a name="see-also"></a>Siehe auch  
 [ProactiveCachingQueryBinding-Datentyp & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)   
 [ProactiveCaching-Element &#40;ASSL&#41;](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)   
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
