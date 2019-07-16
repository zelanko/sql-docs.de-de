---
title: Ebenen (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 24e15602593f9116d499345ffca093f86ecfa135
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905646"
---
# <a name="levels-mdx"></a>Levels (MDX)


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
 Wenn eine Ebenennummer angegeben wird, die **Ebenen** Funktion gibt zurück, die auf der angegebenen nullbasierten Position zugeordnet.  
  
 Wenn ein Ebenenname angegeben wird, die **Ebenen** Funktion die angegebene Ebene zurück.  
  
> [!NOTE]  
>  Verwenden Sie die Syntaxvariante mit dem Zeichenfolgenausdruck für benutzerdefinierte Funktionen.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen veranschaulicht die **Ebenen** Syntaxen funktionieren.  
  
### <a name="numeric"></a>Numeric  
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
  
  
