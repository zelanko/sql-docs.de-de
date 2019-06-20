---
title: SetToStr (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 57e74eb1c7db4aebdd01fde8fc48a425d7affa55
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149281"
---
# <a name="settostr-mdx"></a>SetToStr (MDX)


  Gibt eine Zeichenfolge im MDX-Format (Multidimensional Expressions) zurück, die einer angegebenen Menge entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SetToStr(Set_Expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird zum Übertragen der Zeichenfolgendarstellung einer Menge an eine externe Funktion zur Analyse verwendet. Die Zeichenfolge, die zurückgegeben wird, wird in geschweifte Klammern eingeschlossen {}, wobei die einzelnen Elemente in der Gruppe, die durch ein Komma getrennt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine Zeichenfolge zurückgegeben, die alle Elemente der Geography.Country-Attributhierarchie enthält.  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
