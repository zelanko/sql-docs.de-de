---
title: SilenceOverrideInterval-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- SilenceOverrideInterval Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SilenceOverrideInterval
helpviewer_keywords:
- SilenceOverrideInterval element
ms.assetid: 0dcd2db4-9bc0-4460-b1dd-def0b38c4617
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5b52e5a7caa3f6bd72d4bf598392a03cf744cbd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120414"
---
# <a name="silenceoverrideinterval-element-assl"></a>SilenceOverrideInterval-Element (ASSL)
  Definiert, wie viel Zeit nach dem Empfang der ursprünglichen Benachrichtigung vergehen muss, bis das mehrdimensionale OLAP (MOLAP)-Imaging unbedingt beginnt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <SilenceOverrideInterval>...</SilenceOverrideInterval>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|duration|  
|Standardwert|P0s|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert des `SilenceOverrideInterval` überschreibt den Wert von `SilenceInterval` Wenn während des ruhezeitraums eine Benachrichtigung empfangen wird.  
  
 Das Element, das dem übergeordneten entspricht `SilenceOverrideInterval` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
