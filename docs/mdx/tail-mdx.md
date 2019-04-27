---
title: Tail (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4563ec53f3ed12081e91b5010ae00a71b6c2feb3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62677336"
---
# <a name="tail-mdx"></a>Tail (MDX)


  Gibt eine Teilmenge vom Ende einer Menge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Tail(Set_Expression [ ,Count ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Count*  
 Ein gültiger numerischer Ausdruck, der die Anzahl der Tupel angibt, die zurückgegeben werden sollen.  
  
## <a name="remarks"></a>Hinweise  
 Die **Tail** Funktion gibt die angegebene Anzahl von Tupeln vom Ende der angegebenen Menge zurück. Die Reihenfolge der Elemente wird beibehalten. Der Standardwert von *Anzahl* ist 1. Wenn die angegebene Anzahl der Tupel kleiner als 1 ist, gibt die Funktion die leere Menge zurück. Wenn die angegebene Anzahl der Tupel größer ist als die Anzahl der Tupel in der Menge, gibt die Funktion die ursprüngliche Menge zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Reseller Sales-Measure für die fünf bestverkauften Produktunterkategorien unabhängig von der Hierarchie basierend auf Reseller Gross Profit zurückgegeben. Die **Tail** Funktion wird verwendet, um nur die letzten fünf Mengen aus dem Ergebnis zurückzugeben, nachdem das Ergebnis in umgekehrter Reihenfolge sortiert wird mithilfe der **Reihenfolge** Funktion.  
  
```  
SELECT Tail  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BASC  
      )  
   ,5  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
