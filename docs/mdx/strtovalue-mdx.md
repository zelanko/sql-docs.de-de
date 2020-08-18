---
description: StrToValue (MDX)
title: "\"Strauch Wert\" (MDX) | Microsoft-Dokumentation"
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 200de3b42f522b77bae0b5037761a00da977176e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386746"
---
# <a name="strtovalue-mdx"></a>StrToValue (MDX)


  Gibt den numerischen Wert zurück, der durch eine Zeichenfolge im MDX-Format (Multidimensional Expressions) angegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
StrToValue(MDX_Expression [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argumente  
 *MDX_Expression*  
 Ein gültiger Zeichenfolgenausdruck, der direkt oder indirekt zu einer einzelnen Zelle aufgelöst wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Funktion "- **Wert** " gibt den numerischen Wert zurück, der durch den MDX-Ausdruck angegeben wird. Die Funktion " **Strauch Wert** " wird in der Regel mit benutzerdefinierten Funktionen verwendet, um einen MDX-Ausdruck aus einer externen Funktion an eine MDX-Anweisung zurückzugeben, die in eine einzelne Zelle aufgelöst werden kann.  
  
-   Wenn das CONSTRAINED-Flag verwendet wird, darf der MDX-Ausdruck nur einen Skalarwert enthalten. Das CONSTRAINED-Flag wird verwendet, um das Risiko von Injection-Angriffen über die angegebene Zeichenfolge zu minimieren. Wenn ein MDX-Ausdruck bereitgestellt wird, der nicht direkt zu einem Skalarwert aufgelöst werden kann, wird eine Fehlermeldung angezeigt, die besagt, dass die durch das CONSTRAINED-Flag in der STRTOVALUE-Funktion vorgegebenen Einschränkungen verletzt wurden.  
  
-   Wenn das CONSTRAINED-Flag nicht verwendet wird, kann der angegebene MDX-Ausdruck beliebig komplex sein, vorausgesetzt er wird zu einem gültigen MDX-Ausdruck (Multidimensional Expressions) aufgelöst, der eine einzelne Zelle zurückgibt.  
  
> [!NOTE]  
>  Das Zurückgeben des Ergebnisses eines MDX-Ausdrucks als numerischen Wert kann sinnvoll sein, wenn der Wert als Text gespeichert ist und Sie arithmetische Operationen für die zurückgegebenen Werte ausführen möchten.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Funktion "-Wert" mithilfe der Funktion "- **Wert** " als Wert zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS   
StrToValue   
   ([Product].[Product].CurrentMember.Properties ('Weight')  
   ,CONSTRAINED  
   )  
SELECT Measures.x ON 0  
,[Product].[Product].[Product].Members ON 1  
FROM [Adventure Works]  
WHERE [Product].[Product Categories].[Bikes]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
