---
title: Members (Zeichenfolge) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 05df2d0a846af30d46e702c1d5489945d57c9115
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001493"
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
 Die **Members (Zeichenfolge)** Funktionsergebnis ist ein einzelnes Element, dessen Name angegeben ist. Normalerweise verwenden Sie die **Members (Zeichenfolge)** -Funktion mit externen Funktionen verwendet, auf die **Members (Zeichenfolge)** -Funktion eine Zeichenfolge, die ein Element identifiziert und die **Members (Zeichenfolge)**  Funktion gibt den Wert für dieses Element angegeben.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die **Members (Zeichenfolge)** -Funktion zum Konvertieren von der angegebenen Zeichenfolge in ein gültiges Element und gibt dann das Standardmeasure für das in der Zeichenfolge angegebene Element zurück. Die angegebene Zeichenfolge ist in einfache Anführungszeichen eingeschlossen. Das Standardmeasure entspricht dem Reseller Sales Amount-Measure.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
