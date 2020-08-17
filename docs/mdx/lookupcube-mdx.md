---
description: LookupCube (MDX)
title: LookupCube (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d00f7cf0d657d2424b461ad95bc7f534cd2c33e8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341475"
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
  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
 *String_Expression*  
 Ein gültiger Zeichenfolgenausdruck, bei dem es sich in der Regel um einen gültigen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, der eine Zeichenfolge zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein numerischer Ausdruck angegeben wird, wertet die **LookupCube** -Funktion den angegebenen numerischen Ausdruck im angegebenen Cube aus und gibt den resultierenden numerischen Wert zurück.  
  
 Wenn ein Zeichen folgen Ausdruck angegeben wird, wertet die **LookupCube** -Funktion den angegebenen Zeichen folgen Ausdruck im angegebenen Cube aus und gibt den resultierenden Zeichen folgen Wert zurück.  
  
 Die **LookupCube** -Funktion funktioniert für Cubes in derselben Datenbank wie der Quellcube, in dem die MDX-Abfrage ausgeführt wird, die die **LookupCube** -Funktion enthält.  
  
> [!IMPORTANT]  
>  Sie müssen alle notwendigen aktuellen Elemente in dem numerischen oder Zeichenfolgenausdruck angeben, da der Kontext der aktuellen Abfrage nicht für den abgefragten Cube übernommen wird.  
  
 Jede Berechnung mit der **LookupCube** -Funktion beeinträchtigt wahrscheinlich die Leistung. Überlegen Sie sich, die Lösung umzugestalten anstatt diese Funktion zu verwenden, damit alle Daten, die Sie benötigen, in einem Cube vorhanden sind.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage veranschaulicht die Verwendung von LookupCube:  
  
 `WITH MEMBER MEASURES.LOOKUPCUBEDEMO AS`  
  
 `LOOKUPCUBE("Adventure Works", "[Measures].[In" + "ternet Sales Amount]")`  
  
 `SELECT MEASURES.LOOKUPCUBEDEMO  ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
