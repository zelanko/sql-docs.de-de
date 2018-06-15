---
title: Accounts-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bf3d3b56e9cc2b299ddcdec1c0a506e0168f8741
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34030501"
---
# <a name="accounts-element-assl"></a>Accounts-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält die Auflistung der Kontotypen, die in definierten ein [Datenbank](../../../analysis-services/scripting/objects/database-element-assl.md) Element.  
  
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine (Auflistung)|  
|Standardwert|Keine (Auflistung)|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Datenbank](../../../analysis-services/scripting/objects/database-element-assl.md)|  
|Untergeordnete Elemente|[Konto](../../../analysis-services/scripting/objects/account-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Dimensionen, deren [Typ](../../../analysis-services/scripting/properties/type-element-dimension-assl.md) -Elementgruppe ist *Konten*, haben Sie ein Attribut, das den Kontotyp, wie "Income", "Expense gibt an, und so weiter von Elementen in der Dimension dargestellt. Der Kontotyp wird dann von verwendet [Measure](../../../analysis-services/scripting/objects/measure-element-assl.md) Elemente, deren [AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md) -Elementgruppe ist *ByAccount*, um zu bestimmen, die Aggregatfunktion verwendet wird, wenn aggregieren Sie die Elemente dieser Dimension. Das **Accounts** -Element enthält eine Auflistung von **Account** -Elementen, die Kontotypen und die zu verwendende Aggregatfunktion für die einzelnen Kontotypen darstellen.  
  
 Ein Kontotyp muss aufgelistet sein, wenn die Aggregatfunktion verwendeten vom Standard abweicht [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] für jeden Kontotyp.  
  
 Der Satz gültiger Kontotypen kann nicht geändert werden.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.AccountCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [AccountType-Element &#40;ASSL&#41;](../../../analysis-services/scripting/properties/accounttype-element-assl.md)   
 [Schemaauflistungen & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
