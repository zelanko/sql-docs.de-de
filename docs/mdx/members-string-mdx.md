---
title: Members (Zeichenfolge) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 302445cadc829de35eca28db2888aaa01673ca75
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741899"
---
# <a name="members-string-mdx"></a>Members (Zeichenfolge) (MDX)


  Gibt ein durch einen Zeichenfolgenausdruck angegebenes Element zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Members(Member_Name)   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Name*  
 Ein gültiger Zeichenfolgenausdruck, der einen Elementnamen angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Members (Zeichenfolge)** Funktion gibt ein einzelnes Element mit dem angegebenen Namen zurück. Normalerweise verwenden Sie die **Members (Zeichenfolge)** -Funktion mit externen Funktionen verwendet, auf die **Members (Zeichenfolge)** -Funktion eine Zeichenfolge, die ein Element kennzeichnet und den **Members (Zeichenfolge)** Funktion gibt den Wert für dieses Element angegeben.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die **Members (Zeichenfolge)** Funktion, um die angegebene Zeichenfolge in ein gültiges Element zu konvertieren, und klicken Sie dann das Standardmeasure für das in der Zeichenfolge angegebene Element zurückgegeben. Die angegebene Zeichenfolge ist in einfache Anführungszeichen eingeschlossen. Das Standardmeasure entspricht dem Reseller Sales Amount-Measure.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
