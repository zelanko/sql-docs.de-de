---
title: Fehler (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6644318053321ae5189a70a2bd2c1f0e67d092fc
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740709"
---
# <a name="error-mdx"></a>Error (MDX)


  Löst einen Fehler aus. Optional wird eine angegebene Fehlermeldung ausgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Error( [ Error_Text ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Fehlertext*  
 Ein gültiger Zeichenfolgenausdruck, der die zurückzugebende Fehlermeldung enthält.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage zeigt, wie die **Fehler** Funktion in einem berechneten Measure:  
  
 `WITH MEMBER MEASURES.ERRORDEMO AS ERROR("THIS IS AN ERROR")`  
  
 `SELECT`  
  
 `MEASURES.ERRORDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
