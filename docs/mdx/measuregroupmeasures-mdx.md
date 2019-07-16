---
title: MeasureGroupMeasures (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 45d7adc5e1f4e103790d9d067bc4876fb5b134d2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68033875"
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
  
  
