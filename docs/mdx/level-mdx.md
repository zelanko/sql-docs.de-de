---
title: Ebene (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8406d02e167258901c3a6ce9ed3a1d7de935df54
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741749"
---
# <a name="level-mdx"></a>Level (MDX)


  Gibt die Ebene eines Elements zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression.Level  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger Multidimensional Expression (MDX), die ein Element zurückgibt.  
  
### <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die **Ebene** Funktion, um alle Monate im Adventure Works-Cube zurückzugeben.  
  
```  
SELECT[Date].[Fiscal].[Month].[February 2002].Level.Members ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die **Ebene** Funktion, um den Namen der Ebene für die-Purpose Bike Stand in der Model Name-Attributhierarchie im Adventure Works-Cube zurückzugeben.  
  
```  
WITH MEMBER Measures.x AS   
   [Product].[Model Name].[All-Purpose Bike Stand].Level.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
