---
title: Lastzeiträume (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6a9337e925da40f148bbe0d2c77fb1cf4f5f1a99
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905785"
---
# <a name="lastperiods-mdx"></a>LastPeriods (MDX)


  Gibt eine Menge von Elementen bis zu einem angegebenen Element, einschließlich des Elements, zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LastPeriods(Index [ ,Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Index*  
 Ein gültiger numerischer Ausdruck, der eine Anzahl von Zeiträumen angibt.  
  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die angegebene Anzahl von Zeiträumen positiv ist, gibt die **Last Zeiträume** -Funktion eine Menge von Membern zurück, die mit dem Element beginnen, das *Index* -1 aus dem angegebenen Element Ausdruck verzögert und mit dem angegebenen Element endet. Die Anzahl der von der Funktion zurückgegebenen Member ist gleich dem *Index*.  
  
 Wenn die angegebene Anzahl von Zeiträumen negativ ist, gibt die **Last Zeiträume** -Funktion eine Menge von Membern zurück, die mit dem angegebenen Element beginnen und mit dem Member endet, der (- *Index* -1) aus dem angegebenen Element führt. Die Anzahl der von der Funktion zurückgegebenen Member ist gleich dem absoluten Wert des *Indexes*.  
  
 Wenn die angegebene Anzahl von Zeiträumen 0 (null) ist, gibt die **Last Zeiträume** -Funktion die leere Menge zurück. Dies unterscheidet sich von der **lag** -Funktion, die den angegebenen Member zurückgibt, wenn 0 angegeben wird.  
  
 Wenn ein Member nicht angegeben wird, verwendet die Funktion " **lastzeiträume** " **time. CurrentMember**. Wenn keine Dimension als Time-Dimension markiert ist, wird die Funktion fehlerfrei analysiert und ausgeführt, erzeugt aber bei der Clientanwendung einen Zellenfehler.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Standardmeasurewert für das zweite, dritte und vierte Geschäftsquartal des Geschäftsjahres 2002 zurückgegeben.  
  
```  
SELECT LastPeriods(3,[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]) ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  Diese Beispiel kann auch mithilfe des Doppelpunkt-Operators (:) formuliert werden:  
>   
>  `[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]: [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2002]`  
  
 Im folgenden Beispiel wird der Standardmeasurewert für das erste Quartal im Geschäftsjahr 2002 zurückgegeben. Obwohl für die Anzahl der Zeiträume 3 angegeben wurde, kann nur der Wert für einen Zeitraum zurückgegeben werden, da es keine Zeiträume gibt, die vor dem angegebenen im Geschäftsjahr liegen.  
  
```  
SELECT LastPeriods  
   (3,[Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
