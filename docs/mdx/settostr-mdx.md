---
title: Setto Str (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3965c3cc8ea2a2f2de292ca0c75e49c957e04f02
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036967"
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
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion wird zum Übertragen der Zeichenfolgendarstellung einer Menge an eine externe Funktion zur Analyse verwendet. Die zurückgegebene Zeichenfolge wird in geschweiften {}Klammern eingeschlossen, wobei jedes Element im Satz durch ein Komma getrennt ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine Zeichenfolge zurückgegeben, die alle Elemente der Geography.Country-Attributhierarchie enthält.  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
