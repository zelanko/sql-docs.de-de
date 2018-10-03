---
title: NotificationTechnique-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NotificationTechnique Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- NotificationTechnique element
ms.assetid: 80c43de3-f147-4bf5-bb85-da9d182ce415
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8dc05b03286785e2d06d5595897a263a294ae97e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139488"
---
# <a name="notificationtechnique-element-assl"></a>NotificationTechnique-Element (ASSL)
  Gibt an, ob [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oder eine externe Clientanwendung die Benachrichtigungen verarbeitet.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ProactiveCachingBinding>  
   <NotificationTechnique>...</NotificationTechnique>  
</ProactiveCachingBinding>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Client*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ProactiveCachingBinding](../data-type/binding-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Client*|Externe Clientanwendung verarbeitet die Benachrichtigung.|  
|*Server*|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verarbeitet die Benachrichtigung.|  
  
 Das Element, das dem übergeordneten entspricht `NotificationTechnique` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ProactiveCachingBinding>.  
  
 Die Enumeration, die den zulässigen Werten für entspricht `NotificationTechnique` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.NotificationTechnique>.  
  
## <a name="see-also"></a>Siehe auch  
 [ProactiveCachingBinding-Datentyp &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)  
  
  
