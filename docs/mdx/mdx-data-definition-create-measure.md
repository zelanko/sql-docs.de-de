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
ms.openlocfilehash: 02c6d29bbebcc794e72f4ca960e3d9259de7205b
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892146"
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
  
## <a name="remarks"></a>Hinweise  
 *MEASURE_NAME* muss in eckige Klammern eingeschlossen werden.  
  
 Die CREATE Measure-Anweisung kann nur in einer MDX-Skript Definition verwendet werden. siehe [MdxScript- &#40;Element ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/mdxscript-element-assl).  
  
 Sie können auch ein berechnetes Element definieren, das in einer einzelnen Abfrage verwendet wird. Wenn Sie ein berechnetes Element definieren möchten, das auf eine einzelne Abfrage beschränkt ist, verwenden Sie die WITH-Klausel in der SELECT-Anweisung. Weitere Informationen finden Sie unter [Building Measures in MDX](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-building-measures).  
  
## <a name="see-also"></a>Siehe auch  
 [MDX für MDX &#40;-Daten Definitions Anweisungen&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
