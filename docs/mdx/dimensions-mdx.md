---
title: Dimensionen (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b2703122b67debf0749abcd2ea01114fb6ecaa06
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740189"
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
  
 *Hierarchiename*  
 Ein gültiger Zeichenfolgenausdruck, der einen Hierarchienamen angibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Hierarchienummer angegeben wird, die **Dimensionen** Funktion gibt eine Hierarchie, deren nullbasierte Position innerhalb des Cubes ist angegebenen Hierarchienummer entspricht.  
  
 Wenn ein Hierarchiename angegeben wird, die **Dimensionen** Funktion die angegebene Hierarchie zurück. Normalerweise verwenden Sie diese Zeichenfolgenversion der **Dimensionen** -Funktion mit benutzerdefinierten Funktionen.  
  
> [!NOTE]  
>  Die **Measures** Dimension immer dargestellte `Dimensions(0)`.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele verwenden die **Dimensionen** -Funktion Name, der die Anzahl der Ebenen und der Anzahl von Elementen einer angegebenen Hierarchie, die mithilfe eines numerischen Ausdrucks und einem Zeichenfolgenausdruck zurück.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
