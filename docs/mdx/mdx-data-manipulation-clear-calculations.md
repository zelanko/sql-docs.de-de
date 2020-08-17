---
description: MDX-Datenbearbeitung – CLEAR CALCULATIONS
title: Clear Berechnungen-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 06f3fc9d29630f3f69b994c2b4e7cf809b6b9efd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387004"
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
  
  
