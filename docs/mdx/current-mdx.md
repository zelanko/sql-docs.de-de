---
title: Aktuelle (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e30e2a7940223c7872151d96f05ff79ca919decf
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577692"
---
# <a name="current-mdx"></a>Current (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt das aktuelle Tupel in einer Menge während einer Iteration zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set_Expression.Current   
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Bei jedem Schritt einer Iteration ist das gerade bearbeitete Tupel das aktuelle Tupel. Die **aktuelle** Funktion gibt dieses Tupel zurück. Diese Funktion ist nur während einer Iteration über eine Menge gültig.  
  
 MDX-Funktionen, die einen Satz durchlaufen enthalten die [generieren](../mdx/generate-mdx.md) Funktion.  
  
> [!NOTE]  
>  Diese Funktion ist nur mit benannten Mengen ausführbar, d. h. beim Verwenden eines Mengen-Alias oder Definieren einer benannten Menge.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt, wie Sie die **aktuelle** -Funktion **generieren**:  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of all Calendar Years crossjoined with`  
  
 `//all Product Categories`  
  
 `SET MyTuples AS CROSSJOIN(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS,`  
  
 `[Product].[Category].[Category].MEMBERS)`  
  
 `//Iterates through each tuple in the set and returns the name of the Calendar`  
  
 `//Year in each tuple`  
  
 `MEMBER MEASURES.CURRENTDEMO AS`  
  
 `GENERATE(MyTuples, MyTuples.CURRENT.ITEM(0).NAME, ", ")`  
  
 `SELECT MEASURES.CURRENTDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
