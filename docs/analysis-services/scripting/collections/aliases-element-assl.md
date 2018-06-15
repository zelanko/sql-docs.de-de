---
title: Aliases-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fb37f0a7393b6055621e9575aef3c20a50313ff9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032401"
---
# <a name="aliases-element-assl"></a>Aliases-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält die Auflistung der [Alias](../../../analysis-services/scripting/properties/alias-element-assl.md) Elemente, die zu einer [Konto](../../../analysis-services/scripting/objects/account-element-assl.md) Element  
  
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine (Auflistung)|  
|Standardwert|Keine (Auflistung)|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Konto](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|Untergeordnete Elemente|[Alias](../../../analysis-services/scripting/properties/alias-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das übergeordnete Element des entsprechende Element **Aliase** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Account>.  
  
## <a name="see-also"></a>Siehe auch  
 [Accounts-Element &#40;ASSL&#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [Database-Element &#40;ASSL&#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Schemaauflistungen & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
