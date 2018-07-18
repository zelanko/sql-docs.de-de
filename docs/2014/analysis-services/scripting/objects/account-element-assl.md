---
title: Konto-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Account Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Account
helpviewer_keywords:
- Account element
ms.assetid: 0bb7d06c-0158-4ab2-b2b1-cb50ba24f7c0
caps.latest.revision: 41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d763b75cfb357554948565a59f5348d7fd3b725a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321170"
---
# <a name="account-element-assl"></a>Account-Element (ASSL)
  Enthält Details über einen Kontotyp innerhalb einer [Datenbank](database-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Accounts>  
   <Account>  
      <AccountType>...</AccountType>  
      <AggregationFunction>...</AggregationFunction>  
            <Aliases>...</Aliases>  
            <Annotations>...</Annotations>  
   </Account>  
</Accounts>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Konten](../collections/accounts-element-assl.md)|  
|Untergeordnete Elemente|[AccountType](../properties/accounttype-element-assl.md), [AggregationFunction](../properties/aggregationfunction-element-assl.md), [Aliase](../collections/aliases-element-assl.md), [Anmerkungen](../collections/annotations-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Dimensionen, deren [Typ](../properties/type-element-dimension-assl.md) -Elementgruppe ist *Konten* haben ein Attribut, das gibt an, den Kontotyp, wie "Income", "Expense und so weiter, dargestellt durch die Elemente in der Dimension. Der Kontotyp wird dann von verwendet [Measure](measure-element-assl.md) Elemente, deren [AggregationFunction](../properties/aggregatefunction-element-assl.md) Element nastaven NA hodnotu *ByAccount*, um zu bestimmen, die Aggregatfunktion verwendet wird, wenn Aggregieren der Elemente dieser Dimension. Die `Account` -Element stellt dar, einen einzelnen Kontotyp sowie die Aggregationsfunktion, die von solchen Measures verwendet werden soll.  
  
 Ein Kontotyp muss aufgelistet sein, wenn die Aggregatfunktion standardmäßig verwendet unterscheidet [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] für jeden Kontotyp.  
  
 Der Satz gültiger Kontotypen kann nicht geändert werden.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Siehe auch  
 [Database-Element &#40;ASSL&#41;](database-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
