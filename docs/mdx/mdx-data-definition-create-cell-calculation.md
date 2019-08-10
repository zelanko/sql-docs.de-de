---
title: Create Cell Berechnung-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7ba563c848179e8cf3dc12f64d2b3c4233955159
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892164"
---
# <a name="mdx-data-definition---create-cell-calculation"></a>MDX-Datendefinition – CREATE CELL CALCULATION


  Erstellt eine Berechnung, die einen MDX-Ausdruck (Multidimensional Expressions) für eine angegebene Tupelmenge in einem Cube auswertet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
[WITH <CELL CALCULATION clause> Calculation_Name  
   [,WITH <CELL CALCULATION clause> Calculation_Name...n]  
CREATE CELL CALCULATION CURRENTCUBE | Cube_Name.Calculation_Name   
  
<CELL CALCULATION clause> ::=  
   FOR Set_Expression AS 'MDX_Expression'   
      [ [ CONDITION = 'Logical_Expression' ]   
    | [ DISABLED = { TRUE | FALSE } ]   
    | [ DESCRIPTION =String ]   
    | [ CALCULATION_PASS_NUMBER = Integer]   
    | [ CALCULATION_PASS_DEPTH = Integer]   
    | [ SOLVE_ORDER = Integer]   
    | [ Calculation_Name= Scalar_Expression ], ...n]  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Name*  
 Eine gültige Zeichenfolge, die einen Cubenamen bereitstellt.  
  
 *Calculation_Name*  
 Eine gültige Zeichenfolge, die den Namen einer Zellenberechnung bereitstellt.  
  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck, der eine Menge zurückgibt.  
  
 *String*  
 Ein gültiger Zeichenfolgenwert.  
  
 *MDX_Expression*  
 Ein gültiger MDX-Ausdruck.  
  
 *Logical_Expression*  
 Ein gültiger logischer MDX-Ausdruck.  
  
 *Integer*  
 Ein gültiger ganzzahliger Wert.  
  
 *Calculation_Name*  
 Eine gültige Zeichenfolge, die den Namen der Zellenberechnungseigenschaft bereitstellt.  
  
 *Scalar_Expression*  
 Ein gültiger skalarer MDX-Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Mithilfe berechneter Zellen kann die Clientanwendung einen Rollupwert für eine bestimmte Menge von Zellen angeben, statt für eine ganze Menge von Zellen, wie bei einer benutzerdefinierten Rollupformel oder einem berechneten Element. So kann beispielsweise angegeben werden, dass jede Zelle in der durch `{[Canada],[Time].[2000]}` definierten Menge einen Wert enthalten kann, der durch eine Formel definiert ist. Alle anderen Zellen, die nicht in dieser Menge enthalten sind, werden normal berechnet.  
  
> [!NOTE]  
>  Die Backus-Naur-Form (BNF) von `{*(<comment> | <whitespace> | <newline>)}` wird aus Gründen der Abwärtskompatibilität als `{*}` analysiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen berechneter Zellen im Bereich einer Sitzung](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-calculations-session-scoped-calculated-cells)   
 [Erstellen von Zellenberechnungen im Bereich einer Abfrage &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations)   
 [Aufbauen von Zellen Berechnungen in MDX &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations)   
 [Verwenden von Zelleneigenschaften &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties)   
 [FORMAT_STRING-Inhalt &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents)   
 [MDX für FORE_COLOR &#40;und BACK_COLOR-Inhalt&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents)   
 [MDX für MDX &#40;-Daten Definitions Anweisungen&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
