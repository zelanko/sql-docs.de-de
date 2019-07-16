---
title: Dividieren (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6184aa9d932355cd935a9131848ec27895faea5f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68049297"
---
# <a name="divide-mdx"></a>Dividieren (MDX)


  Führt eine Division aus und gibt ein alternatives Ergebnis oder BLANK() bei Division durch 0 zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>Argumente  
 *Zähler*  
 Der Dividend oder Zahl dividiert werden soll.  
  
 *denominator*  
 Der Divisor oder Zahl, durch die dividiert werden soll.  
  
 *alternateresult*  
 (Optional) Der Rückgabewert, wenn die Division durch null zu einem Fehler führt. Der Standardwert ist BLANK(), wenn nichts angegeben ist.  
  
## <a name="remarks"></a>Hinweise  
 Das alternative Ergebnis für eine Division durch 0 muss eine Konstante sein.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
