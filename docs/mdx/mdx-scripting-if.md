---
description: IF-Anweisung (MDX)
title: IF-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 62b5a2e7d2ae04b7cd11bb08a3a65ddad903b6cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429732"
---
# <a name="mdx-scripting---if"></a>MDX-Skripts – IF


  Führt eine Anweisung aus, wenn die Bedingung erfüllt ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IF expression THEN assignment END IF  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein MDX-Ausdruck (Multidimensional Expressions), der zu einem booleschen Wert ausgewertet wird, der TRUE oder FALSE zurückgibt.  
  
 *Tätigkeit*  
 Ein MDX-Ausdruck, der entweder einem Teilcube oder einer berechneten Eigenschaft einen Wert zuweist.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die if-Anweisung für die Ablauf Steuerung, die im Gegensatz zur [IIf-&#40;MDX-&#41;](../mdx/iif-mdx.md) Funktion und der [Case-Anweisung &#40;MDX-&#41;](../mdx/case-statement-mdx.md) steht, die nur zum Zurückgeben von Werten oder Objekten verwendet werden können.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel ist der Gültigkeitsbereich auf die Country-Ebene der Customer Geography-Hierarchie in der Customer-Dimension beschränkt. Wenn das aktuelle Measure „Betrag der Internetsteuern“ ist, dann wird „Betrag der Internetsteuern“ auf 10 festgelegt:  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
