---
title: Drop Member-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4e8e38a3ff3f40f44c911a277f99ab9b629c7c87
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038192"
---
# <a name="mdx-data-definition---drop-member"></a>MDX-Datendefinition – DROP MEMBER


  Entfernt ein berechnetes Element.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP MEMBER   
   CURRENTCUBE | Cube_Name  
      .Member_Name   
               [,CURRENTCUBE | Cube_Name.Member_Name ...n]  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Name*  
 Ein gültiger Zeichenfolgenausdruck, der einen Cubenamen bereitstellt.  
  
 *Member_Identifier*  
 Ein gültiger Zeichen folgen Ausdruck, der einen Elementnamen oder Element Schlüssel bereitstellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create Member-Anweisung &#40;MDX-&#41;](../mdx/mdx-data-definition-create-member.md)   
 [MDX-Daten Definitions Anweisungen &#40;MDX-&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
