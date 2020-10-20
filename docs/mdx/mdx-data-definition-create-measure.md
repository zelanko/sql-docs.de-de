---
description: MDX-Datendefinition – CREATE MEASURE
title: Create Measure-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d352a12a4567fc88d2d037862c4cab2f1cd20fe0
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92193962"
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
 Der *MEASURE_NAME*  muss in eckige Klammern eingeschlossen werden.  
  
 Die CREATE Measure-Anweisung kann nur in einer MDX-Skript Definition verwendet werden. Weitere Informationen finden Sie unter [MdxScript-Element &#40;ASSL&#41;](/analysis-services/assl/objects/mdxscript-element-assl?view=asallproducts-allversions).  
  
 Sie können auch ein berechnetes Element definieren, das in einer einzelnen Abfrage verwendet wird. Wenn Sie ein berechnetes Element definieren möchten, das auf eine einzelne Abfrage beschränkt ist, verwenden Sie die WITH-Klausel in der SELECT-Anweisung. Weitere Informationen finden Sie unter [Building Measures in MDX](/analysis-services/multidimensional-models/mdx/mdx-building-measures).  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Daten Definitions Anweisungen &#40;MDX-&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
