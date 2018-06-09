---
title: CLEAR CALCULATIONS-Anweisung (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cdc4b2d3e948f0123eb15e38a6140e63009907bc
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742389"
---
# <a name="mdx-data-manipulation---clear-calculations"></a>Datenbearbeitung für MDX - CLEAR CALCULATIONS


  Entfernt alle Berechnungen aus dem Cube und setzt den Cube auf den Berechnungsdurchlauf 0 zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Expression*  
 Ein gültiger MDX-Cubeausdruck (Multidimensional Expressions).  
  
## <a name="remarks"></a>Hinweise  
 Die **FROM** -Klausel kann ausgelassen werden, wenn der Kontext des Cubes bekannt, z. B. in einem MDX-Skript ist.  
  
> [!NOTE]  
>  Diese Anweisung kann nur von einem Server- oder Datenbankadministrator oder einem Mitglied einer Rolle mit Zugriff auf die Quelldaten des Cubes (das heißt ReadSourceData=true) ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Datenbearbeitungsanweisungen &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
