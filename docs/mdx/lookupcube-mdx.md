---
title: LookupCube (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8f8338a542bf9e15816205930704c45a536a5629
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741719"
---
# <a name="lookupcube-mdx"></a>LookupCube (MDX)


  Gibt den Wert eines MDX-Ausdrucks (Multidimensional Expressions) zurück, der über einem anderen angegebenen Cube in derselben Datenbank ausgewertet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Numeric expression syntax  
LookupCube(Cube_Name, Numeric_Expression )  
  
String expression syntax  
LookupCube(Cube_Name, String_Expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen eines Cubes angibt.  
  
 *Numeric_expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
 *String_Expression*  
 Ein gültiger Zeichenfolgenausdruck, bei dem es sich in der Regel um einen gültigen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, der eine Zeichenfolge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein numerischer Ausdruck angegeben wird, die **LookupCube** Funktion wertet den angegebenen numerischen Ausdruck im angegebenen Cube, und gibt den sich ergebenden numerischen Wert zurück.  
  
 Wenn ein Zeichenfolgenausdruck angegeben wird, die **LookupCube** Funktion wertet den angegebenen Zeichenfolgenausdruck im angegebenen Cube, und gibt den sich ergebenden Zeichenfolgenwert zurück.  
  
 Die **LookupCube** -Funktion kann für Cubes innerhalb derselben Datenbank, da der Quellcube, auf denen die MDX-Abfrage, die enthält, die **LookupCube** Funktion ausgeführt wird.  
  
> [!IMPORTANT]  
>  Sie müssen alle notwendigen aktuellen Elemente in dem numerischen oder Zeichenfolgenausdruck angeben, da der Kontext der aktuellen Abfrage nicht für den abgefragten Cube übernommen wird.  
  
 Jeder Berechnung mithilfe der **LookupCube** Funktion unterscheidet sich wahrscheinlich unter schlechter Leistung darunter leiden. Überlegen Sie sich, die Lösung umzugestalten anstatt diese Funktion zu verwenden, damit alle Daten, die Sie benötigen, in einem Cube vorhanden sind.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage veranschaulicht die Verwendung von LookupCube:  
  
 `WITH MEMBER MEASURES.LOOKUPCUBEDEMO AS`  
  
 `LOOKUPCUBE("Adventure Works", "[Measures].[In" + "ternet Sales Amount]")`  
  
 `SELECT MEASURES.LOOKUPCUBEDEMO  ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
