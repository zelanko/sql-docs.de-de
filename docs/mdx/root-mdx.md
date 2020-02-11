---
title: Root (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: be687d5cbfd4fdbb706ef5c10778a4f3e3f93197
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037040"
---
# <a name="root-mdx"></a>Root (MDX)


  Gibt ein Tupel zurück, das aus **allen** Membern aus jeder Attribut Hierarchie innerhalb des aktuellen Bereichs in einem Cube, einer Dimension oder einem Tupel besteht. Weitere Informationen zum Gültigkeitsbereich finden Sie unter [SCOPE-Anweisung &#40;MDX-&#41;](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Wenn eine Attribut Hierarchie nicht über einen **all** -Member verfügt, enthält das Tupel das Standardelement für diese Hierarchie.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Cube syntax  
Root ()  
Dimension syntax  
Root( Dimension_Name )  
Tuple syntax  
Root( Tuple_Expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *Dimension_Name*  
 Ein gültiger Zeichenfolgenausdruck, der einen Dimensionsnamen angibt.  
  
 *Tuple_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Tupel zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn weder ein Dimensions Name noch ein Tupelausdruck angegeben wird, gibt die **root** -Funktion ein Tupel zurück, das das **alle** -Element (oder das Standardelement, wenn das **all** -Element nicht vorhanden ist) aus jeder Attribut Hierarchie im Cube enthält. Die Reihenfolge der Elemente im Tupel basiert auf der Reihenfolge, in der die Attributhierarchien innerhalb des Cubes definiert sind.  
  
 Wenn ein Dimensions Name angegeben wird, gibt die **root** -Funktion ein Tupel zurück, das das **alle** -Element (oder das Standardelement, wenn das **all** -Element nicht vorhanden ist) aus jeder Attribut Hierarchie in der angegebenen Dimension basierend auf dem Kontext des aktuellen Elements enthält. Die Reihenfolge der Elemente im Tupel basiert auf der Reihenfolge, in der die Attributhierarchien innerhalb der Dimension definiert sind.  
  
> [!NOTE]  
>  Wenn ein Hierarchie Name angegeben wird, wählt die **Tupelfunktion** den Dimensions Namen aus dem angegebenen Hierarchienamen aus.  
  
 Wenn ein Tupelausdruck angegeben wird, gibt die **root** -Funktion ein Tupel zurück, das die Schnittmenge des angegebenen Tupels und **alle** Elemente aller anderen Dimensions Attribute enthält, die nicht explizit im angegebenen Tupel enthalten sind.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das Tupel zurückgegeben, das das **alle** -Element enthält (oder der Standardwert, wenn das **all** -Element nicht vorhanden ist) aus jeder Hierarchie im Adventure Works-Cube.  
  
```  
SELECT Root()ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird das Tupel zurückgegeben, das das **alle** -Element enthält (oder der Standardwert, wenn das **all** -Element nicht vorhanden ist) aus jeder Hierarchie in der Date-Dimension im Adventure Works-Cube und dem Wert für das angegebene Element der Measures-Dimension, die sich mit diesen Standardelementen überschneidet.  
  
```  
SELECT Root([Date]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
 Im folgenden Beispiel wird das Tupel mit dem angegebenen tupelmember (1. Juli 2001 zusammen mit dem **all** -Element (oder dem Standardwert, wenn das **alle** -Element nicht vorhanden ist) aus jeder nicht angegebenen Hierarchie im Adventure Works-Cube der Date-Dimension und dem Wert für das angegebene Element der Measures-Dimension, das mit diesen Membern interziert, zurückgegeben.  
  
```  
SELECT Root([Date].[July 1, 2001]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
