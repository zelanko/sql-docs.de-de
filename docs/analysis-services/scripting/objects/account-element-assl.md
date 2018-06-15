---
title: Konto-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e9cda9f82df4f1b7a6d445d7cb85e69c635833f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037261"
---
# <a name="account-element-assl"></a>Account-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält Details über einen Kontotyp innerhalb einer [Datenbank](../../../analysis-services/scripting/objects/database-element-assl.md) Element.  
  
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Konten](../../../analysis-services/scripting/collections/accounts-element-assl.md)|  
|Untergeordnete Elemente|[AccountType](../../../analysis-services/scripting/properties/accounttype-element-assl.md), [AggregationFunction](../../../analysis-services/scripting/properties/aggregationfunction-element-assl.md), [Aliase](../../../analysis-services/scripting/collections/aliases-element-assl.md), [Anmerkungen](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Dimensionen, deren [Typ](../../../analysis-services/scripting/properties/type-element-dimension-assl.md) -Elementgruppe ist *Konten,* können ein Attribut, das gibt des Kontotyp, wie "Income", "Expense und usw., dargestellt durch Elemente in der Dimension haben. Der Kontotyp wird dann von verwendet [Measure](../../../analysis-services/scripting/objects/measure-element-assl.md) Elemente, deren [AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md) -Elementgruppe ist *ByAccount*, um zu bestimmen, die Aggregatfunktion verwendet wird, wenn aggregieren Sie die Elemente dieser Dimension. Das **Account** -Element stellt einen einzelnen Kontotyp sowie die Aggregationsfunktion dar, die von solchen Measures verwendet werden sollte.  
  
 Ein Kontotyp muss aufgelistet sein, wenn die Aggregatfunktion verwendeten vom Standard abweicht [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] für jeden Kontotyp.  
  
 Der Satz gültiger Kontotypen kann nicht geändert werden.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Siehe auch  
 [Database-Element &#40;ASSL&#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
