---
description: '&lt;&gt; (Ungleich) MDX'
title: '&lt;&gt; (Ungleich) (MDX) | Microsoft-Dokumentation'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8c2651c7d542ac0a8707c20e8b32f4ba33ac7b54
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471792"
---
# <a name="ltgt-not-equal-to-mdx"></a>&lt;&gt; (Ungleich) MDX


  Führt eine Vergleichsoperation aus, die bestimmt, ob der Wert eines MDX-Ausdrucks (Multidimensional Expressions) ungleich dem Wert eines anderen MDX-Ausdrucks ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
MDX_Expression <> MDX_Expression  
```  
  
#### <a name="parameters"></a>Parameter  
 *MDX_Expression*  
 Ein gültiger MDX-Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der auf den folgenden Bedingungen basiert:  
  
-   **true** , wenn beide Parameter nicht NULL sind und der erste Parameter nicht gleich dem zweiten Parameter ist.  
  
-   **false** , wenn beide Parameter nicht NULL sind und der erste Parameter gleich dem zweiten Parameter ist.  
  
-   NULL, wenn mindestens einer der Parameter zu einem NULL-Wert ausgewertet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
