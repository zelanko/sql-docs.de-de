---
title: Erstellen berechneter Zellen im Bereich einer Sitzung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- session-scoped calculated members [MDX]
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4388ef278c0762184859162dc55f656aae1c9a15
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66074429"
---
# <a name="creating-session-scoped-calculated-cells"></a>Erstellen berechneter Zellen im Bereich einer Sitzung
    
> [!IMPORTANT]  
>  Diese Syntax wurde als veraltet markiert. Sie sollten stattdessen MDX-Zuweisungen verwenden. Weitere Informationen zu Zuweisungen finden Sie unter [Grundlegendes MDX-Skript &#40;MDX&#41;](the-basic-mdx-script-mdx.md).  
  
 Wenn Sie berechnete Zellen erstellen möchten, die für alle Abfragen in derselben Sitzung verfügbar sind, verwenden Sie entweder die [CREATE CELL CALCULATION](/sql/mdx/mdx-data-definition-create-cell-calculation) -Anweisung oder die [ALTER CUBE](/sql/mdx/mdx-data-definition-alter-cube) -Anweisung. Beide Anweisungen führen zum selben Ergebnis.  
  
## <a name="create-cell-calculation-syntax"></a>Syntax von CREATE CELL CALCULATION  
  
> [!IMPORTANT]  
>  Diese Syntax wurde als veraltet markiert. Sie sollten stattdessen MDX-Zuweisungen verwenden. Weitere Informationen zu Zuweisungen finden Sie unter [Grundlegendes MDX-Skript &#40;MDX&#41;](the-basic-mdx-script-mdx.md).  
  
 Verwenden Sie folgende Syntax, wenn Sie mit der CREATE CELL CALCULATION-Anweisung eine berechnete Zelle im Bereich einer Sitzung definieren möchten:  
  
```  
CREATE CELL CALCULATION Cube_Expression.<CREATE CELL CALCULATION body clause>  
  
<CREATE CELL CALCULATION body clause> ::=CellCalc_Identifier FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
## <a name="alter-cube-syntax"></a>Syntax von ALTER CUBE  
  
> [!IMPORTANT]  
>  Diese Syntax wurde als veraltet markiert. Sie sollten stattdessen MDX-Zuweisungen verwenden. Weitere Informationen zu Zuweisungen finden Sie unter [Grundlegendes MDX-Skript &#40;MDX&#41;](the-basic-mdx-script-mdx.md).  
  
 Verwenden Sie folgende Syntax, wenn Sie mit der ALTER CUBE -Anweisung eine berechnete Zelle im Bereich einer Sitzung definieren möchten:  
  
```  
ALTER CUBE Cube_Identifier CREATE CELL CALCULATION  
FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
 Der `String_Expression` -Wert enthält eine Liste der orthogonalen, eindimensionalen MDX-Mengenausdrücke, von denen jeder aufgelöst zu einer der Mengenkategorien gehören muss, die in der folgenden Tabelle aufgelistet sind.  
  
|Category|BESCHREIBUNG|  
|--------------|-----------------|  
|Leere Menge|Ein MDX-Mengenausdruck, der zu einer leeren Menge aufgelöst wird. In diesem Fall ist der Gültigkeitsbereich der berechneten Zelle gleich dem gesamten Cube.|  
|Menge mit einem einzelnen Element|Ein MDX-Mengenausdruck, der zu einem einzelnen Element aufgelöst wird.|  
|Menge von Ebenenelementen|Ein MDX-Mengenausdruck, der zu den Elementen einer einzelnen Ebene aufgelöst wird. Ein Beispiel hierfür ist die *Level_Expression*.`Members` MDX-Funktion. Um berechnete Elemente einzuschließen, verwenden Sie die *Level_Expression*.`AllMembers` MDX-Funktion.<br /><br /> Weitere Informationen finden Sie unter [AllMembers &#40;MDX&#41;](/sql/mdx/allmembers-mdx).|  
|Menge nachfolgender Werte|Ein MDX-Mengenausdruck, der zu den nachfolgenden Werten eines angegebenen Elements aufgelöst wird. Ein Beispiel hierfür ist `Descendants`die MDX-Funktion (*Member_Expression*, *Level_Expression* *Desc_Flag*).<br /><br /> Weitere Informationen finden Sie unter [Descendants &#40;MDX&#41;](/sql/mdx/descendants-mdx).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Zellenberechnungen in MDX &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
