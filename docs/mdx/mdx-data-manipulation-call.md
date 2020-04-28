---
title: Callcenter-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: de74590ac4c43a9141c0ab2092babf41ffd23ba5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
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
>  Wenn die gespeicherte Prozedur nicht auf dem Client registriert ist, versucht die **-Anweisung, die gespeicherte** Prozedur von einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]aufzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Daten Bearbeitungsanweisungen &#40;MDX-&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Verwenden von gespeicherten Prozeduren &#40;MDX&#41;](../mdx/using-stored-procedures-mdx.md)  
  
  
