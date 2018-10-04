---
title: DeniedSet-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DeniedSet Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DeniedSet
helpviewer_keywords:
- DeniedSet element
ms.assetid: 898deefb-822d-458b-96d8-880da287b687
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d946edf50041f2a754214b7d6c62d07621547a6c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48204450"
---
# <a name="deniedset-element-assl"></a>DeniedSet-Element (ASSL)
  Enthält einen Mengenausdruck, der die Liste von Berechtigungen definiert, die auf dem zugeordneten Attribut verweigert werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AttributePermission>  
      ...  
   <DeniedSet>...</DeniedSet>  
      ...  
</AttributePermission>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[AttributePermission](../objects/attributepermission-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das dem übergeordneten entspricht `DeniedSet` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.AttributePermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
