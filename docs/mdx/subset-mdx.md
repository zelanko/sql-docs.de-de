---
description: Subset (MDX)
title: Teilmenge (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d0b7e79ebf0415011665ae63e7b9699200e374b1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386726"
---
# <a name="subset-mdx"></a>Subset (MDX)


  Gibt eine Teilmenge von Tupeln aus einer angegebenen Menge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Subset(Set_Expression, Start [ ,Count ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Starten*  
 Ein gültiger numerischer Ausdruck, der die Position des ersten zurückzugebenden Tupels angibt.  
  
 *Count*  
 Ein gültiger numerischer Ausdruck, der die Anzahl der Tupel angibt, die zurückgegeben werden sollen.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Teilmenge** -Funktion gibt aus der angegebenen Menge eine Teilmenge zurück, die die angegebene Anzahl von Tupeln enthält, beginnend an der angegebenen Anfangsposition. Die Startposition basiert auf einem nullbasierten Index, d. h., null (0) entspricht dem ersten Tupel in der Menge, 1 entspricht dem zweiten Tupel usw.  
  
 Wenn *count* nicht angegeben wird, gibt die Funktion alle Tupel vom *Anfang* bis zum Ende der Menge zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Reseller Sales-Measure für die fünf bestverkauften Produktunterkategorien unabhängig von der Hierarchie basierend auf Reseller Gross Profit zurückgegeben. Die **Subset** -Funktion wird verwendet, um nur die ersten fünf Sätze im Ergebnis zurückzugeben, nachdem das Ergebnis mithilfe der **Order** -Funktion sortiert wurde.  
  
```  
SELECT Subset  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BDESC  
      )  
   ,0  
   ,5  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
