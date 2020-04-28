---
title: Mitgliedestr (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9a33aede54557491dea50a557ed581929c5383e4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68001465"
---
# <a name="membertostr-mdx"></a>MemberToStr (MDX)


  Gibt eine Zeichenfolge im MDX-Format (Multidimensional Expressions) zurück, die einem angegebenen Element entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
MemberToStr(Member_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion gibt eine Zeichenfolge zurück, die den eindeutigen Namen eines Elements enthält. Sie wird normalerweise verwendet, um den UniqueName eines Elements an eine externe Funktion zu übergeben.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Zeichenfolge [Geography] zurückgegeben. [Geography]. [Land]. & [USA]:  
  
 `WITH MEMBER Measures.x AS MemberToStr`  
  
 `([Geography].[Geography].[Country].[United States])`  
  
 `SELECT Measures.x ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
