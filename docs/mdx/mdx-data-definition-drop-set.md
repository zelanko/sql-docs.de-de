---
description: MDX-Datendefinition – DROP SET
title: Drop Set-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5c4ca356847d75150aa098b331bdf0f8c8368bb6
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92195605"
---
# <a name="mdx-data-definition---drop-set"></a>MDX-Datendefinition – DROP SET


  Entfernt eine benannte Menge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP [SESSION] SET   
   <Cube_Reference>.Set_Name   
               [,<Cube_Reference>.Set_Name ...n]  
  
<Cube_Reference> ::= {CURRENTCUBE | Cube_Name}  
  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen des Cubes bereitstellt.  
  
 *Set_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen der zu löschenden benannten Menge bereitstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Weitere Informationen zu benannten Mengen finden Sie unter [Erstellen von benannten Mengen in MDX &#40;MDX&#41;](/analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets).  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Daten Definitions Anweisungen &#40;MDX-&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
