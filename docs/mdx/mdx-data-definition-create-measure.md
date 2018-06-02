---
title: CREATE MEASURE-Anweisung (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 98ca479c266d9e8c25b2e75d8b15da1cd76a46aa
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579352"
---
# <a name="mdx-data-definition---create-measure"></a>MDX-Datendefinition - MEASURE erstellen
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Erstellt ein Measure in einem tabellarischen Modell.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CREATE MEASURE Table_Name[Measure_Name] = DAX_Expression  
[; CREATE MEASURE ...n]  
  
```  
  
## <a name="arguments"></a>Argumente  
 *Tabellenname*  
 Ein gültiges Zeichenfolgenliteral, das den Namen der Tabelle bereitstellt, in dem das Measure erstellt wird.  
  
 *Measure_Name*  
 Ein gültiges Zeichenfolgenliteral, das einen Measurenamen bereitstellt.  
  
 *DAX_Expression*  
 Ein gültiger DAX-Ausdruck, der einen einzelnen skalaren Wert zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die *Measure_Name* muss in eckige Klammern eingeschlossen werden.  
  
 Die CREATE MEASURE-Anweisung kann nur innerhalb einer MDX-Skriptdefinition verwendet werden; finden Sie unter [MdxScript-Element &#40;ASSL&#41;](../analysis-services/scripting/objects/mdxscript-element-assl.md).  
  
 Sie können auch ein berechnetes Element definieren, das in einer einzelnen Abfrage verwendet wird. Wenn Sie ein berechnetes Element definieren möchten, das auf eine einzelne Abfrage beschränkt ist, verwenden Sie die WITH-Klausel in der SELECT-Anweisung. Weitere Informationen finden Sie unter [Erstellen von Measures in MDX](../analysis-services/multidimensional-models/mdx/mdx-building-measures.md).  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Datendefinitionsanweisungen &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
