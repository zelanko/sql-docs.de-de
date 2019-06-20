---
title: DROP MEMBER-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 78d5d27853922d7e7524d93ae2b8157e57166968
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248298"
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
 Ein gültiger Zeichenfolgenausdruck, der einen Elementnamen oder Elementschlüssel bereitstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE MEMBER-Anweisung &#40;MDX&#41;](../mdx/mdx-data-definition-create-member.md)   
 [MDX-Datendefinitionsanweisungen &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
