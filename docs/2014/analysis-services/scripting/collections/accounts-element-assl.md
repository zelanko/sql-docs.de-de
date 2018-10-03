---
title: -Element (ASSL)-Konten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Accounts Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Accounts
helpviewer_keywords:
- Accounts element
ms.assetid: 3ec62f58-c19b-4b15-b040-8941521a389b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d0dd0fabf7ebfc6ee020a533149b73e72f7a8a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126140"
---
# <a name="accounts-element-assl"></a>Accounts-Element (ASSL)
  Enthält die Auflistung der Kontotypen, die in definierten eine [Datenbank](../objects/database-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Database>  
   ...  
   <Accounts>  
      <Account>...</Account>  
   </Accounts>  
   ...  
</Database>  
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
|Übergeordnete Elemente|[Datenbank](../objects/database-element-assl.md)|  
|Untergeordnete Elemente|[Konto](../objects/account-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Dimensionen, deren [Typ](../properties/type-element-dimension-assl.md) Element nastaven NA hodnotu *Konten*, haben Sie ein Attribut, das den Kontotyp, wie "Income", "Expense gibt an, und so weiter von Elementen in der Dimension dargestellt wird. Der Kontotyp wird dann von verwendet [Measure](../objects/measure-element-assl.md) Elemente, deren [AggregationFunction](../properties/aggregatefunction-element-assl.md) Element nastaven NA hodnotu *ByAccount*, um zu bestimmen, die Aggregatfunktion verwendet wird, wenn Aggregieren der Elemente dieser Dimension. Das `Accounts`-Element enthält eine Auflistung von `Account`-Elementen, die Kontotypen und die zu verwendende Aggregatfunktion für die einzelnen Kontotypen darstellen.  
  
 Ein Kontotyp muss aufgelistet sein, wenn die Aggregatfunktion standardmäßig verwendet unterscheidet [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] für jeden Kontotyp.  
  
 Der Satz gültiger Kontotypen kann nicht geändert werden.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.AccountCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [AccountType-Element &#40;ASSL&#41;](../properties/accounttype-element-assl.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
