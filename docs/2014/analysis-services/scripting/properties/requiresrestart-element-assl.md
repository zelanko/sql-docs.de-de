---
title: RequiresRestart-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RequiresRestart Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RequiresRestart
helpviewer_keywords:
- RequiresRestart element
ms.assetid: 9e98f956-c41e-4e15-a7bd-e17c10ee6fc6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 752acb9d560ba62d74a3b5486c79279fb49fd2a8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120880"
---
# <a name="requiresrestart-element-assl"></a>RequiresRestart-Element (ASSL)
  Enthält einen schreibgeschützten Wert, der zugeordnete eine [ServerProperty](../objects/serverproperty-element-assl.md) -Element, das bestimmt, ob die Änderung des Werts der Servereigenschaft erfordert, dass die Instanz neu gestartet werden, damit die Änderung wirksam wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<ServerProperty>  
   ...  
   <RequiresRestart>...</RequiresRestart>  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[ServerProperty](../objects/serverproperty-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das dem übergeordneten entspricht `RequiresRestart` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Siehe auch  
 [ServerProperties-Element &#40;ASSL&#41;](../collections/serverproperties-element-assl.md)   
 [Server-Element &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
