---
title: Unorder (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9fe8d86b322aaf753f1ce45be2332095e2b85af9
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581332"
---
# <a name="unorder-mdx"></a>Unorder (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Entfernt eine erzwungene Reihenfolge von einer angegebenen Menge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Unorder(Set_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Unorder** -Funktion entfernt jede Sortierung, die auf den Tupeln in der Menge durch eine andere Funktion oder Anweisung, wie z. B. die [Reihenfolge](../mdx/order-mdx.md) Funktion. Die Reihenfolge der Tupel in der Menge zurückgegebenes der **Unorder** Funktion unbestimmt ist.  
  
 Die **Unorder** Funktion dient als Hinweis für [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] zur abfrageoptimierung bei der mengenverarbeitung. Wenn die Reihenfolge der Tupel in einer Menge für eine Berechnung oder Abfrage unwichtig ist, mithilfe der **Unorder** -Funktion einen Leistungsvorteil in solchen Fällen bieten kann. Z. B. die [NonEmpty (MDX)](../mdx/nonempty-mdx.md) Funktion möglicherweise eine bessere Leistung bei der für diese Funktion bereitgestellte Satz ungeordnet ist, als If ist [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Reihenfolge beibehalten muss, obwohl mit [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], der Abfrageprozessor versucht, die automatisch für viele Funktionen, wie z. B. verarbeitetes **Summe** und **aggregieren**. Der Leistungsvorteil mit **Unorder** wahrscheinlich nur bei sehr großen Mengen, die aus Millionen von Tupeln bestehen, bemerkbar.  
  
## <a name="example"></a>Beispiel  
 Der folgende Pseudocode veranschaulicht die Syntax für diese Funktion.  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
