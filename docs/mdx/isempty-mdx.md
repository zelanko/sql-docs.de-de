---
title: IsEmpty (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ab2f65bbc15aecec93294225435d3d2d38fff062
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578712"
---
# <a name="isempty-mdx"></a>IsEmpty (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
 Die **IsEmpty** Funktion ist die einzige Möglichkeit, zuverlässig für eine leere Zelle zu testen, da der leere Zellwert besondere Bedeutung, im hat [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
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
  
  
