---
title: Parent (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 32922aebffd9704725e534742656b86348f5e1ee
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580642"
---
# <a name="parent-mdx"></a>Parent (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt das übergeordnete Element eines Elements zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression.Parent   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **übergeordneten** Funktion gibt das übergeordnete Element des angegebenen Elements zurück.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen wird das übergeordnete Element des July 1, 2001-Elements zurückgegeben. Im ersten Beispiel ist dieses Element im Kontext der Date-Attributhierarchie angegeben. Zurückgegeben wird das All Periods-Element.  
  
```  
SELECT [Date].[Date].[July 1, 2001].Parent ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel ist das July 1, 2001-Element im Kontext der Calendar-Hierarchie angegeben.  
  
```  
SELECT [Date].[Calendar].[July 1, 2001].Parent ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
