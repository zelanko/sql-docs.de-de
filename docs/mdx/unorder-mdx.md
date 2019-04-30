---
title: Unorder (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3b5e360c8f15eafba2b4565ca41a557c9e1ceda9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63297916"
---
# <a name="unorder-mdx"></a>Unorder (MDX)


  Entfernt eine erzwungene Reihenfolge von einer angegebenen Menge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Unorder(Set_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Unorder** -Funktion entfernt jede Sortierung, die auf den Tupeln in der Gruppe durch eine andere Funktion oder Anweisung, wie z. B. die [Reihenfolge](../mdx/order-mdx.md) Funktion. Die Reihenfolge der Tupel in der Gruppe, die zurückgegeben werden, indem die **Unorder** Funktion ist unbestimmt.  
  
 Die **Unorder** Funktion wird als Hinweis für für die abfrageoptimierung bei der mengenverarbeitung verwendet. Wenn die Reihenfolge der Tupel in einer Gruppe für eine Berechnung oder Abfrage unwichtig ist, verwenden die **Unorder** Funktion kann einen Leistungsvorteil in solchen Fällen bereitstellen. Z. B. die [NonEmpty (MDX)](../mdx/nonempty-mdx.md) Funktion möglicherweise bieten eine bessere Leistung bei der für diese Funktion bereitgestellte Satz ungeordnet ist, als If wird [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Reihenfolge beibehalten muss, obwohl mit [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], der Abfrageprozessor versucht, ausführen Diese Funktion automatisch für viele Funktionen, z. B. **Summe** und **aggregieren**. Der Leistungsvorteil durch Verwendung von **Unorder** vermutlich nur bei sehr großen Mengen, die aus Millionen von Tupeln bestehen, bemerkbar sein.  
  
## <a name="example"></a>Beispiel  
 Der folgende Pseudocode veranschaulicht die Syntax für diese Funktion.  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
