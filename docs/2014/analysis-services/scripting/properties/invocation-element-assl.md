---
title: Invocation-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Invocation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Invocation
helpviewer_keywords:
- Invocation element
ms.assetid: f6bf64ad-ae57-4d46-bf92-1d07a65378bb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a67774a17518e44fa78c0caf639103bfb19de5e1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108950"
---
# <a name="invocation-element-assl"></a>Invocation-Element (ASSL)
  Gibt an, wie ein [Aktion](../objects/action-element-assl.md) aufgerufen werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action>  
   ...  
   <Invocation>...</Invocation>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Interaktive*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Aktion](../objects/action-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Aufruf einer Aktion hängt von der Clientanwendung ab. Die `Invocation` -Element empfiehlt einer Clientanwendung wie eine Aktion erfolgen soll, und gibt keine mit der Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] wie Sie eine Aktion aufzurufen.  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Interaktive*|Wird interaktiv vom Benutzer aufgerufen.|  
|*OnOpen*|Wird aufgerufen, wenn eine Clientanwendung das Objekt öffnet.|  
|*Batch*|Wird von einem Batchverarbeitungsbefehl aufgerufen.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `Invocation` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
