---
description: Verwenden von Elementausdrücken
title: Verwenden von Element Ausdrücken | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e833d8d579841a3fc15aad89612a1d25b71fd0f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494825"
---
# <a name="using-member-expressions"></a>Verwenden von Elementausdrücken


  Ein Elementausdruck enthält einen Elementbezeichner, eine Elementfunktion oder einen Ausdruck, der in ein Element konvertiert werden kann.  
  
 Elementbezeichner können viele verschiedene Formate haben. Die einfachste Form eines Elementbezeichners besteht aus dem Namen des Elements. Beispiel:  
  
```  
SELECT Amount ON 0  
FROM [Adventure Works]  
  
```  
  
 Falls es jedoch mehrere Elemente des gleichen Namens in unterschiedlichen Hierarchien gibt, gibt es keine Möglichkeit, zu bestimmen, welches Element die Abfrage zurückgibt. Zum Beispiel fordert die folgende Abfrage Daten für ein Element mit dem Namen [CY 2004] an. Die Abfrage wird erfolgreich ausgeführt, jedoch gibt es im Adventure Works-Cube mindestens sechs Elemente mit diesem Namen:  
  
```  
SELECT [CY 2004] ON 0  
FROM [Adventure Works]  
  
```  
  
 Deshalb ist die zuverlässigste Form von Elementbezeichnern der eindeutige Name des Elements, um ein spezifisches Element in einem Cube sicher zu identifizieren. Analyses Services kann auf unterschiedliche Weise eindeutige Namen generieren, ein eindeutiger Name setzt sich jedoch immer aus mindestens zwei Bezeichnern zusammen: dem Dimensionsnamen sowie dem Elementnamen oder dem Elementschlüssel. Ein eindeutiger Name hat folgendes Format:  
  
```  
  
Dimension_Name  
.[Hierarchy_Name.] [[{Member_Name | &Member_Key}.]... ] {Member_Name | &Member_Key}  
  
```  
  
 Im Folgenden sind einige Beispiele für eindeutige Elementnamen aus dem Adventure Works-Cube aufgelistet:  
  
```  
[Measures].[Amount]  
[Date].[Calendar Year].&[2004]  
[Date].[Calendar].[Calendar Quarter].&[2004]&[1]  
[Employee].[Employees].&[112]  
[Product].[Product Categories].[All Products]  
  
```  
  
 Es gibt viele MDX-Funktionen, die Elemente zurückgeben. Eine vollständige Liste finden Sie unter [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
> [!NOTE]  
>  Weitere Informationen zu Elementnamen und Element Schlüsseln finden Sie unter [Arbeiten mit Membern, Tupeln und Mengen &#40;MDX-&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;MDX-&#41;](../mdx/expressions-mdx.md)  
  
  
