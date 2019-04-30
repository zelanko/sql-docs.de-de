---
title: Diese (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 77db403ee016283a565a6bc86d2f6857de0eff45
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63259027"
---
# <a name="this-mdx"></a>This (MDX)


  Gibt den aktuellen Teilcube zum Verwenden mit Zuweisungen im MDX-Berechnungsskript (Multidimensional Expressions) zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
This   
```  
  
## <a name="remarks"></a>Hinweise  
 Die **dies** Funktion kann Teilcubeausdrucks verwendet werden, um den aktuellen Teilcube im aktuellen Gültigkeitsbereich innerhalb des MDX-Berechnungsskripts bereitzustellen. Die **dies** Funktion muss auf der linken Seite einer Zuweisung verwendet werden.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Berechnungen](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
