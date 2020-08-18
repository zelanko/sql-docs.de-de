---
description: Ascendants (MDX)
title: Vorgänger (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eb485e2785facba4a47647f8a51548e0140b3efb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491466"
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)


  Gibt die Menge der vorausgehenden Elemente zu einem angegebenen Element zurück, einschließlich des Elements selbst.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Vorgänger** Funktion gibt alle Vorgänger eines Members vom Element selbst bis zum Anfang der Hierarchie des Members zurück. genauer gesagt führt er eine nach der Bestellung ausgeführten Überquerung der Hierarchie für das angegebene Element aus und gibt dann alle aufsteigenden Member zurück, die mit dem Element verknüpft sind, einschließlich selbst in einer Menge. Dies steht im Gegensatz zur [Vorgänger](../mdx/ancestor-mdx.md) Funktion, die einen bestimmten aufsteigenden Member oder Vorgänger auf einer bestimmten Ebene zurückgibt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Anzahl der Bestellungen des Wiederverkäufers für das `[Sales Territory].[Northwest]` -Element und alle Vorgänger dieses Members aus dem **Adventure Works** -Cube zurückgegeben. Die **Vorgänger Funktion erstellt die Menge** , die den `[Sales Territory].[Northwest]` Member und seine Vorgänger für die ROWS-Achse einschließt.  
  
```  
SELECT  
   Measures.[Reseller Order Count] ON COLUMNS,  
   Order(  
      Ascendants(  
         [Sales Territory].[Northwest]  
      ),  
      DESC  
   ) ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
