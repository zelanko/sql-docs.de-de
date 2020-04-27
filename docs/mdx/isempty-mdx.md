---
title: IsEmpty (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8b31b884e0f86bf2aebe4859cd1c7a441669e813
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905988"
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
 Die **IsEmpty** -Funktion gibt **true** zurück, wenn der ausgewertete Ausdruck ein leerer Zellwert ist. Andernfalls gibt diese Funktion **false**zurück.  
  
> [!NOTE]  
>  Die Standardeigenschaft eines Elements ist sein Wert.  
  
 Die **IsEmpty** -Funktion ist die einzige Möglichkeit, zuverlässig auf eine leere Zelle zu testen, da der leere Zellwert in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]eine besondere Bedeutung hat.  
  
> [!IMPORTANT]  
>  Wenn bei der Auswertung des Value-Ausdrucks ein Fehler zurückgegeben wird, gibt die Funktion **false**zurück. Ein Wertausdruck kann z. B. einen Fehler zurückgeben, wenn ein Eigenschaftsverweis auf eine ungültige oder nicht vorhandene Eigenschaft verweist.  
  
 Weitere Informationen zu leeren Zellen finden Sie in der OLE DB-Dokumentation.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird TRUE zurückgegeben, wenn der Internetverkaufsbetrag für das aktuelle Element auf der Fiscal-Hierarchie der Date-Dimension eine leere Zelle zurückgibt:  
  
 `WITH MEMBER MEASURES.ISEMPTYDEMO AS`  
  
 `IsEmpty([Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.ISEMPTYDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit leeren Werten](../mdx/working-with-empty-values.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
