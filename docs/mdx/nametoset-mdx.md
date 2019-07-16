---
title: NameToSet (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 77731495eb058da05f6c61be391591a40725e579
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088392"
---
# <a name="nametoset-mdx"></a>NameToSet (MDX)


  Gibt einen zurück, das das durch eine Multidimensional Expressions MDX-formatierte Zeichenfolge angegebene Element enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
NameToSet(Member_Name)   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen eines Elements darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der angegebene Elementname vorhanden ist, die **NameToSet** Funktion gibt eine Menge mit diesem Element zurück. Andernfalls gibt die Funktion eine leere Menge zurück.  
  
> [!NOTE]  
>  Der angegebene Elementname muss zwingend ein Elementname sein. Ein Elementausdruck ist nicht zulässig. Um einen Elementausdruck verwenden zu können, finden Sie unter [StrToSet &#40;MDX&#41;](../mdx/strtoset-mdx.md).  
  
## <a name="example"></a>Beispiel  
 Im Folgenden wird der Standardmeasurewert des angegebenen Elementnamens zurückgegeben.  
  
```  
SELECT NameToSet('[Date].[Calendar].[July 2001]') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
