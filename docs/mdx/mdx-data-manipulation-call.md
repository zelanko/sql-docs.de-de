---
title: CALL-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: de74590ac4c43a9141c0ab2092babf41ffd23ba5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106300"
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
 *"Sp_name"*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen einer gespeicherten Prozedur bereitstellt.  
  
 *SP_Argument*  
 Ein gültiger Zeichenfolgenausdruck, der ein Argument für die aufgerufene gespeicherte Prozedur bereitstellt.  
  
 *Cube_Expression*  
 Ein gültiger Zeichenfolgen-Cube-Ausdruck, der den Namen des Cubes bereitstellt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Aufrufen** -Anweisung führt eine angegebene registrierte gespeicherte Prozedur, optional einschließlich von ein oder mehrere Argumente für die angegebene gespeicherte Prozedur. Die **Aufrufen** -Anweisung ist nur mit gespeicherten Prozeduren, die ' void ' zurückgeben. Die Anweisung kann nicht mit anderen Funktionen oder Operatoren in einem MDX-Ausdruck kombiniert werden. Registrierte gespeicherte Prozeduren, die Werte zurückgeben, können direkt in MDX-Ausdrücken aufgerufen und mit anderen MDX-Funktionen und -Operatoren kombiniert werden.  
  
 Wenn kein Cube angegeben wird, führt die Anweisung die gespeicherte Prozedur mit dem aktuellen Cube als Argument aus.  
  
> [!NOTE]  
>  Wenn die gespeicherte Prozedur nicht auf dem Client registriert ist die **Aufrufen** Anweisung versucht, auf die gespeicherte Prozedur von einer Instanz von Aufrufen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Datenbearbeitungsanweisungen &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Verwenden von gespeicherten Prozeduren &#40;MDX&#41;](../mdx/using-stored-procedures-mdx.md)  
  
  
