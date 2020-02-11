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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **Members (String)** -Funktion gibt einen einzelnen Member zurück, dessen Name angegeben ist. In der Regel verwenden Sie die **Members (String)** -Funktion mit externen Funktionen und stellen der Member **(String)** -Funktion eine Zeichenfolge zur Verfügung, die einen Member identifiziert, und die **Members (String)** -Funktion gibt den Wert für dieses angegebene Element zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die-Member **(String)** -Funktion verwendet, um die angegebene Zeichenfolge in einen gültigen Member zu konvertieren, und anschließend wird das Standardmeasure für das in der Zeichenfolge angegebene Element zurückgegeben. Die angegebene Zeichenfolge ist in einfache Anführungszeichen eingeschlossen. Das Standardmeasure entspricht dem Reseller Sales Amount-Measure.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
