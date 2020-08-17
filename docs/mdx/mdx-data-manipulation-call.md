---
description: MDX-Datenbearbeitung – CALL
title: Callcenter-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3a8f3b550e3fed3fe28e74896c3c4ff764db8810
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387039"
---
# <a name="mdx-data-manipulation---call"></a>MDX-Datenbearbeitung – CALL


  Führt eine gespeicherte Prozedur, die "void" zurückgibt, im aktuellen Bereich oder optional für einen angegebenen Cube aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CALL SP_Name   
   [ (SP_Argument   
      [, SP_Argument ,...n]  
      ) ]   
[ONCube_Expression]  
```  
  
## <a name="arguments"></a>Argumente  
 *SP_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen einer gespeicherten Prozedur bereitstellt.  
  
 *SP_Argument*  
 Ein gültiger Zeichenfolgenausdruck, der ein Argument für die aufgerufene gespeicherte Prozedur bereitstellt.  
  
 *Cube_Expression*  
 Ein gültiger Zeichenfolgen-Cube-Ausdruck, der den Namen des Cubes bereitstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Statement-** Anweisung führt eine angegebene registrierte gespeicherte Prozedur aus, die optional ein oder mehrere Argumente für die angegebene gespeicherte Prozedur einschließt. Die **callanweisung** dient nur zur Verwendung mit gespeicherten Prozeduren, die Voids zurückgeben. Die Anweisung kann nicht mit anderen Funktionen oder Operatoren in einem MDX-Ausdruck kombiniert werden. Registrierte gespeicherte Prozeduren, die Werte zurückgeben, können direkt in MDX-Ausdrücken aufgerufen und mit anderen MDX-Funktionen und -Operatoren kombiniert werden.  
  
 Wenn kein Cube angegeben wird, führt die Anweisung die gespeicherte Prozedur mit dem aktuellen Cube als Argument aus.  
  
> [!NOTE]  
>  Wenn die gespeicherte Prozedur nicht auf dem Client registriert ist, versucht die **-Anweisung, die gespeicherte** Prozedur von einer Instanz von aufzurufen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Daten Bearbeitungsanweisungen &#40;MDX-&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Verwenden von gespeicherten Prozeduren &#40;MDX&#41;](../mdx/using-stored-procedures-mdx.md)  
  
  
