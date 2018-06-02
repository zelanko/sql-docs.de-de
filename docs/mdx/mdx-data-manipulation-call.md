---
title: CALL-Anweisung (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b8610a0ed7fc0c90fb3e8c684b33b466eb3858f9
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580102"
---
# <a name="mdx-data-manipulation---call"></a>Datenbearbeitung für MDX - AUFRUF
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Hinweise  
 Die **Aufrufen** -Anweisung führt eine angegebene registrierte gespeicherte Prozedur, einschließlich optional ein oder mehrere Argumente für die angegebene gespeicherte Prozedur. Die **Aufrufen** -Anweisung ist nur mit gespeicherten Prozeduren, die ' void ' zurückgeben. Die Anweisung kann nicht mit anderen Funktionen oder Operatoren in einem MDX-Ausdruck kombiniert werden. Registrierte gespeicherte Prozeduren, die Werte zurückgeben, können direkt in MDX-Ausdrücken aufgerufen und mit anderen MDX-Funktionen und -Operatoren kombiniert werden.  
  
 Wenn kein Cube angegeben wird, führt die Anweisung die gespeicherte Prozedur mit dem aktuellen Cube als Argument aus.  
  
> [!NOTE]  
>  Wenn die gespeicherte Prozedur nicht auf dem Client registriert ist die **Aufrufen** Anweisung versucht, auf die gespeicherte Prozedur von einer Instanz von Aufrufen [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Datenbearbeitungsanweisungen &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Verwenden von gespeicherten Prozeduren &#40;MDX&#41;](../mdx/using-stored-procedures-mdx.md)  
  
  
