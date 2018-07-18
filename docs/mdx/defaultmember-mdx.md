---
title: DefaultMember (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3a0c11acadcbdcadfd9398baff09db9292c87eb2
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740129"
---
# <a name="defaultmember-mdx"></a>DefaultMember (MDX)


  Gibt das Standardelement einer Hierarchie zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Hierarchy_Expression.DefaultMember  
```  
  
## <a name="arguments"></a>Argumente  
 *Hierarchy_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Das Standardelement eines Attributs wird zum Auswerten von Ausdrücken verwendet, wenn ein Attribut nicht in einer Abfrage enthalten ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die **DefaultMember** -Funktion in Verbindung mit der **Namen** -Funktion verwendet, um das Standardelement der Destination Currency-Dimension im Adventure Works-Cube zurückzugeben. Das Beispiel gibt **US-Dollar**. Die **Namen** Funktion dient zum Zurückgeben der Name des Measures anstelle der Standardeigenschaft des Measures, also **Wert**.  
  
```  
WITH MEMBER Measures.x AS   
   [Destination Currency].[Destination Currency].DefaultMember.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Definieren eines Standardelements](../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
