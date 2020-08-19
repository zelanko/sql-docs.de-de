---
description: NameToSet (MDX)
title: NameToSet (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cd1de5e8c126d9457fda2c7c9545dedea26fd1f3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483753"
---
# <a name="nametoset-mdx"></a>NameToSet (MDX)


  Gibt eine Menge zurück, die das durch eine Zeichenfolge im MDX-Format (Multidimensional Expressions) angegebene Element enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
NameToSet(Member_Name)   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen eines Elements darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der angegebene Elementname vorhanden ist, gibt die **NameToSet** -Funktion eine Menge zurück, die diesen Member enthält. Andernfalls gibt die Funktion eine leere Menge zurück.  
  
> [!NOTE]  
>  Der angegebene Elementname muss zwingend ein Elementname sein. Ein Elementausdruck ist nicht zulässig. Informationen zum Verwenden eines Element Ausdrucks finden Sie unter " [&#40;MDX-&#41;](../mdx/strtoset-mdx.md)".  
  
## <a name="example"></a>Beispiel  
 Im Folgenden wird der Standardmeasurewert des angegebenen Elementnamens zurückgegeben.  
  
```  
SELECT NameToSet('[Date].[Calendar].[July 2001]') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
