---
description: IsLeaf (MDX)
title: IsLeaf (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1b7dd1d76b417633ff50a77b3f2822e6f7cfd462
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471822"
---
# <a name="isleaf-mdx"></a>IsLeaf (MDX)


  Gibt zurück, ob ein angegebenes Element ein Blattelement ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IsLeaf(Member_Expression)   
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **IsLeaf** -Funktion gibt **true** zurück, wenn der angegebene Member ein Blatt Element ist. Andernfalls gibt die Funktion **false**zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird TRUE zurückgegeben, wenn [Date].[Fiscal].CurrentMember ein Blattelement ist:  
  
 `WITH MEMBER MEASURES.ISLEAFDEMO AS`  
  
 `IsLeaf([Date].[Fiscal].CURRENTMEMBER)`  
  
 `SELECT {MEASURES.ISLEAFDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
