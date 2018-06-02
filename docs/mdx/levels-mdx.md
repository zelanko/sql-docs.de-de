---
title: Ebenen (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2fba58261bb0ba8f91e8127b1d33b847accf0dc7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579512"
---
# <a name="levels-mdx"></a>Levels (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt die Ebene zurück, deren Position in einer Dimension oder Hierarchie durch einen numerischen Ausdruck angegeben ist oder deren Name durch einen Zeichenfolgenausdruck angegeben ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Numeric expression syntax  
Hierarchy_Expression.Levels( Level_Number )  
  
String expression syntax  
Hierarchy_Expression.Levels( Level_Name )  
```  
  
## <a name="arguments"></a>Argumente  
 *Hierarchy_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
 *Level_Number*  
 Ein gültiger numerischer Ausdruck, der eine Ebenennummer angibt.  
  
 *Ebenenname*  
 Ein gültiger Zeichenfolgenausdruck, der einen Ebenennamen angibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Ebenennummer angegeben wird, die **Ebenen** zurückgegeben, die auf der angegebenen nullbasierten Position zugeordnet.  
  
 Wenn ein Ebenenname angegeben wird, die **Ebenen** Funktion die angegebene Ebene zurück.  
  
> [!NOTE]  
>  Verwenden Sie die Syntaxvariante mit dem Zeichenfolgenausdruck für benutzerdefinierte Funktionen.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Beispiele veranschaulichen aller der **Ebenen** Syntaxen-Funktion.  
  
### <a name="numeric"></a>Numerisch  
 Im folgenden Beispiel wird die Country-Ebene zurückgegeben:  
  
```  
SELECT [Geography].[Geography].Levels(1) ON 0  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>Zeichenfolge  
 Im folgenden Beispiel wird die Country-Ebene zurückgegeben:  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
