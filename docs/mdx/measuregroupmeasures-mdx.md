---
title: MeasureGroupMeasures (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 55e00420ad3f941d50d9179dcd4a87d678cc28a0
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742039"
---
# <a name="measuregroupmeasures-mdx"></a>MeasureGroupMeasures (MDX)


  Gibt eine Menge der Measures zurück, die zur angegebenen Measuregruppe gehören.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
MEASUREGROUPMEASURES(MeasureGroupName)  
```  
  
## <a name="arguments"></a>Argumente  
 *MeasureGroupName*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen der Measuregruppe enthält, aus der die Menge der Measures abgerufen werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Die angegebene Zeichenfolge muss genau mit dem Namen der Measuregruppe übereinstimmen. Die Verwendung von eckigen Klammern für Measuregruppennamen, die Leerzeichen enthalten, ist nicht erforderlich.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden alle Measures in der Internet Sales-Measuregruppe im Adventure Works-Cube zurückgegeben.  
  
```  
SELECT MeasureGroupMeasures('Internet Sales') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
