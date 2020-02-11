---
title: Dimensionen (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 84d5ab0caa22c6f35f3e7b790dbfb3348df8ceb1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67999966"
---
# <a name="dimensions-mdx"></a>Dimensionen (MDX)


  Gibt eine Hierarchie zurück, die durch einen numerischen Ausdruck oder einen Zeichenfolgenausdruck angegeben ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Numeric expression syntax  
Dimensions(Hierarchy_Number)  
  
String expression syntax  
Dimensions(Hierarchy_Name)  
```  
  
## <a name="arguments"></a>Argumente  
 *Hierarchy_Number*  
 Ein gültiger numerischer Ausdruck, der eine Hierarchienummer angibt.  
  
 *Hierarchy_Name*  
 Ein gültiger Zeichenfolgenausdruck, der einen Hierarchienamen angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Hierarchie Nummer angegeben wird, gibt die **Dimensions** Funktion eine Hierarchie zurück, deren null basierte Position innerhalb des Cubes die angegebene Hierarchie Nummer ist.  
  
 Wenn ein Hierarchie Name angegeben wird, gibt die **Dimensions** Funktion die angegebene Hierarchie zurück. In der Regel verwenden Sie diese Zeichen folgen Version der **Dimensions** Funktion mit benutzerdefinierten Funktionen.  
  
> [!NOTE]  
>  Die **Measures** -Dimension wird immer durch `Dimensions(0)`dargestellt.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen wird die **Dimensions** -Funktion verwendet, um den Namen, die Anzahl der Ebenen und die Anzahl der Elemente einer angegebenen Hierarchie zurückzugeben, wobei ein numerischer Ausdruck und ein Zeichen folgen Ausdruck verwendet werden.  
  
```  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Levels.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Members.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
