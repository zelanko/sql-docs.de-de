---
title: Clear Berechnungen-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1b0766cb002960a96d702184ac9719abe7610afd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67938024"
---
# <a name="mdx-data-manipulation---clear-calculations"></a>MDX-Datenbearbeitung – CLEAR CALCULATIONS


  Entfernt alle Berechnungen aus dem Cube und setzt den Cube auf den Berechnungsdurchlauf 0 zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Expression*  
 Ein gültiger MDX-Cubeausdruck (Multidimensional Expressions).  
  
## <a name="remarks"></a>Bemerkungen  
 Die **from** -Klausel kann ausgelassen werden, wenn der Kontext des Cubes bekannt ist, z. b. in einem MDX-Skript.  
  
> [!NOTE]  
>  Diese Anweisung kann nur von einem Server- oder Datenbankadministrator oder einem Mitglied einer Rolle mit Zugriff auf die Quelldaten des Cubes (das heißt ReadSourceData=true) ausgeführt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Daten Bearbeitungsanweisungen &#40;MDX-&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
