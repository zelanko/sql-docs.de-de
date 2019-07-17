---
title: NextMember (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b852564510c6b5918c781e0c75e84e3b30aecd44
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088362"
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
 Die **NextMember** Funktion gibt das nächste Element auf derselben Ebene, mit dem angegebenen Element zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das August 2001-Element als das auf das July 2001-Element folgende Element zurückgegeben.  
  
```  
SELECT [Date].[Calendar].[Month].[July 2001].NextMember ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
