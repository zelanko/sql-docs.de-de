---
description: This (MDX)
title: This (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e00435741516fd1ed1942506084c26192b6d47da
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88413096"
---
# <a name="this-mdx"></a>This (MDX)


  Gibt den aktuellen Teilcube zum Verwenden mit Zuweisungen im MDX-Berechnungsskript (Multidimensional Expressions) zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
This   
```  
  
## <a name="remarks"></a>Bemerkungen  
 **Diese** Funktion kann anstelle eines Teilcubeausdrucks verwendet werden, um den aktuellen Teilcube innerhalb des aktuellen Gültigkeits Bereichs innerhalb des MDX-Berechnungs Skripts bereitzustellen. **Diese** Funktion muss auf der linken Seite einer Zuweisung verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Fragment eines MDX-Scripts veranschaulicht die Verwendung des This-Schlüsselworts mit SCOPE-Anweisungen, um Zuweisungen an Teilcubes vorzunehmen:  
  
 `Scope`  
  
 `(`  
  
 `[Date].[Fiscal Year].&[2005],`  
  
 `[Date].[Fiscal].[Fiscal Quarter].Members,`  
  
 `[Measures].[Sales Amount Quota]`  
  
 `) ;`  
  
 `This = ParallelPeriod`  
  
 `(`  
  
 `[Date].[Fiscal].[Fiscal Year], 1,`  
  
 `[Date].[Fiscal].CurrentMember`  
  
 `) * 1.35 ;`  
  
 `/*-- Allocate equally to months in FY 2002 -----------------------------*/`  
  
 `Scope`  
  
 `(`  
  
 `[Date].[Fiscal Year].&[2002],`  
  
 `[Date].[Fiscal].[Month].Members`  
  
 `) ;`  
  
 `This = [Date].[Fiscal].CurrentMember.Parent / 3 ;`  
  
 `End Scope ;`  
  
 `End Scope;`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Berechnungen](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/calculations)  
  
  
