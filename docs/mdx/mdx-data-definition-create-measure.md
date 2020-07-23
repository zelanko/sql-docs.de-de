---
title: Create Measure-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3bac5d7d067186e2b84277a5c0dc02cd31cba011
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86967381"
---
# <a name="mdx-data-definition---create-measure"></a>MDX-Datendefinition – CREATE MEASURE


  Erstellt ein Measure in einem tabellarischen Modell.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CREATE MEASURE Table_Name[Measure_Name] = DAX_Expression  
[; CREATE MEASURE ...n]  
  
```  
  
## <a name="arguments"></a>Argumente  
 *Table_Name*  
 Ein gültiges Zeichenfolgenliteral, das den Namen der Tabelle bereitstellt, in dem das Measure erstellt wird.  
  
 *Measure_Name*  
 Ein gültiges Zeichenfolgenliteral, das einen Measurenamen bereitstellt.  
  
 *DAX_Expression*  
 Ein gültiger DAX-Ausdruck, der einen einzelnen skalaren Wert zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Der *MEASURE_NAME* muss in eckige Klammern eingeschlossen werden.  
  
 Die CREATE Measure-Anweisung kann nur in einer MDX-Skript Definition verwendet werden. Weitere Informationen finden Sie unter [MdxScript-Element &#40;ASSL&#41;](https://docs.microsoft.com/analysis-services/assl/objects/mdxscript-element-assl?view=asallproducts-allversions).  
  
 Sie können auch ein berechnetes Element definieren, das in einer einzelnen Abfrage verwendet wird. Wenn Sie ein berechnetes Element definieren möchten, das auf eine einzelne Abfrage beschränkt ist, verwenden Sie die WITH-Klausel in der SELECT-Anweisung. Weitere Informationen finden Sie unter [Building Measures in MDX](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-building-measures).  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Daten Definitions Anweisungen &#40;MDX-&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
