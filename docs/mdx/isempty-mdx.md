---
title: IsEmpty (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dbed0eba3fec73d7134b1ce21275c28dbd387fcd
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740169"
---
# <a name="isempty-mdx"></a>IsEmpty (MDX)


  Gibt zurück, ob der ausgewertete Ausdruck dem leeren Zellenwert entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IsEmpty(Value_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Value_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der in der Regel die Zellenkoordinaten eines Elements oder Tupels zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **IsEmpty** -Funktion gibt **"true"** , wenn der ausgewertete Ausdruck einen leeren Zellenwert entspricht. Andernfalls, gibt diese Funktion **"false"**.  
  
> [!NOTE]  
>  Die Standardeigenschaft eines Elements ist sein Wert.  
  
 Die **IsEmpty** Funktion ist die einzige Möglichkeit, zuverlässig für eine leere Zelle zu testen, da der leere Zellwert besondere Bedeutung, im hat [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Wenn die Auswertung des wertausdrucks einen Fehler zurückgibt, wird die Funktion zurückgeben **"false"**. Ein Wertausdruck kann z. B. einen Fehler zurückgeben, wenn ein Eigenschaftsverweis auf eine ungültige oder nicht vorhandene Eigenschaft verweist.  
  
 Weitere Informationen zu leeren Zellen finden Sie in der OLE DB-Dokumentation.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird TRUE zurückgegeben, wenn der Internetverkaufsbetrag für das aktuelle Element auf der Fiscal-Hierarchie der Date-Dimension eine leere Zelle zurückgibt:  
  
 `WITH MEMBER MEASURES.ISEMPTYDEMO AS`  
  
 `IsEmpty([Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.ISEMPTYDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit leeren Werten](../mdx/working-with-empty-values.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
