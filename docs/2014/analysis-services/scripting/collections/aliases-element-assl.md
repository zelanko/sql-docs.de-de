---
title: Aliases-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Aliases Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Aliases
helpviewer_keywords:
- Aliases element
ms.assetid: 9de9e683-d30d-4d61-b32d-c5a946825742
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 677434b5ea6383e5905a703225edb5e56e3fb4e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267686"
---
# <a name="aliases-element-assl"></a>Aliases-Element (ASSL)
  Enthält die Auflistung der [Alias](../properties/alias-element-assl.md) Elemente, die zu einem [Konto](../objects/account-element-assl.md) Element  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Account>  
      ...  
   <Aliases>  
      <Alias>...</Alias>  
      </Aliases>  
      ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine (Auflistung)|  
|Standardwert|Keine (Auflistung)|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Konto](../objects/account-element-assl.md)|  
|Untergeordnete Elemente|[Alias](../properties/alias-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das dem übergeordneten entspricht `Aliases` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Siehe auch  
 [Konten Element &#40;ASSL&#41;](accounts-element-assl.md)   
 [Database-Element &#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
