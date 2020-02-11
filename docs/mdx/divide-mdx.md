---
title: Divide (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6184aa9d932355cd935a9131848ec27895faea5f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68049297"
---
# <a name="divide-mdx"></a>Dividieren (MDX)


  Führt eine Division aus und gibt ein alternatives Ergebnis oder BLANK() bei Division durch 0 zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>Argumente  
 *numerator*  
 Die zu dividierende Dividende oder Zahl.  
  
 *denominator*  
 Der Divisor oder die Zahl, durch die dividiert werden soll.  
  
 *alternateresult*  
 (Optional) Der Rückgabewert, wenn die Division durch null zu einem Fehler führt. Der Standardwert ist BLANK(), wenn nichts angegeben ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Das alternative Ergebnis für eine Division durch 0 muss eine Konstante sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
