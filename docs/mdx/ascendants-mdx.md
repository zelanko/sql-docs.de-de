---
title: Vorgänger (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 16c6f812d1d7cae5a81a8e64fb425f4d33f4cb5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68017060"
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
 Im folgenden Beispiel wird die Anzahl der Bestellungen des wieder `[Sales Territory].[Northwest]` Verkäufers für das-Element und alle Vorgänger dieses Members aus dem **Adventure Works** -Cube zurückgegeben. Die **Vorgänger Funktion erstellt die Menge** , die den `[Sales Territory].[Northwest]` Member und seine Vorgänger für die ROWS-Achse einschließt.  
  
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
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
