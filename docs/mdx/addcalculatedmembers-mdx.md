---
title: AddCalculatedMembers (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 982484b729b59a7106b6195e361110c1d4012653
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68017185"
---
# <a name="addcalculatedmembers-mdx"></a>AddCalculatedMembers (MDX)


  Gibt eine Menge zurück, die durch Hinzufügen berechneter Elemente zu einer angegebenen Menge erstellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
AddCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Standardmäßig schließt MDX berechnete Elemente beim Auflösen von Mengenfunktionen aus. Die **AddCalculatedMembers** Funktion untersucht den Mengenausdruck *Set_Expression,* und schließt berechnete Elemente, die gleichgeordnete Elemente der Elemente im Bereich dieser Menge enthalten sind. -Ausdruck.  
  
> [!NOTE]  
>  Die Funktion kann nur mit eindimensionalen Mengenausdrücken verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung dieser Funktion.  
  
```  
-- This query returns the calculated members for the cube  
-- by retrieving all members, and then excluding non-calculated members.  
SELECT   
   AddCalculatedMembers(  
      {[Measures].Members}  
      )-[Measures].Members ON COLUMNS  
FROM [Adventure Works]   
```  
  
 Das folgende Beispiel gibt die `Measures.[Unit Price]` -Element zusätzlich zu allen berechneten Elementen in der **Measures** -Dimension, aus der **Adventure Works** Cube.  
  
```  
SELECT  
   AddCalculatedMembers({Measures.[Unit Price]}) ON COLUMNS  
FROM   
   [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
