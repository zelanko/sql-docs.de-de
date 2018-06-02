---
title: SetToStr (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b1a6cd7d87e0eb582c06a402a98a2294996ac12c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581582"
---
# <a name="settostr-mdx"></a>SetToStr (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt eine Zeichenfolge im MDX-Format (Multidimensional Expressions) zurück, die einer angegebenen Menge entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SetToStr(Set_Expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird zum Übertragen der Zeichenfolgendarstellung einer Menge an eine externe Funktion zur Analyse verwendet. Die Zeichenfolge, die zurückgegeben wird, wird in geschweifte Klammern eingeschlossen {}, wobei jedes Element in der Gruppe, die durch ein Komma getrennt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine Zeichenfolge zurückgegeben, die alle Elemente der Geography.Country-Attributhierarchie enthält.  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
