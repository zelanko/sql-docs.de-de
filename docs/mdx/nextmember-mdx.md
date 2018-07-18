---
title: NextMember (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4535b837d81db10f41f1445a7051678ce4fdd688
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742179"
---
# <a name="nextmember-mdx"></a>NextMember (MDX)


  Gibt das nächste Element in der Ebene zurück, die ein angegebenes Element enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression.NextMember   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **NextMember** Funktion gibt das nächste Element in der gleichen Ebene befinden, mit dem angegebenen Element zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das August 2001-Element als das auf das July 2001-Element folgende Element zurückgegeben.  
  
```  
SELECT [Date].[Calendar].[Month].[July 2001].NextMember ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
