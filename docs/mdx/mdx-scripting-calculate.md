---
description: CALCULATE-Anweisung (MDX)
title: Berechnen-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6ec4d0e86c2719613527ec7ea8206f980deebc3a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429762"
---
# <a name="mdx-scripting---calculate"></a>MDX-Skripts – CALCULATE


  Füllt jede Zelle in einem Cube mit einem Aggregatwert auf.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>Argumente  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Die CALCULATE-Anweisung wird beim Erstellen eines Cubes mithilfe von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] automatisch als erste Anweisung in das MDX-Skript des Cubes eingefügt. Die CALCULATE-Anweisung weist alle Zellen im Cube an, beim Aggregieren mit Zellen geringerer Granularität zu beginnen. Wenn nach dem Aggregieren einer Zelle anschließend Zellen geringerer Granularität mithilfe von Ausdrücken aufgefüllt werden, hat dies Auswirkungen auf die aggregierten Werte von Zellen höherer Granularität. Diese Aggregation ist in der Regel erwünscht, Sie können jedoch die Anweisung bei Bedarf entfernen oder andere Anweisungen vor dieser ausführen lassen.  
  
 Die CALCULATE-Anweisung kann nicht in einen geschachtelten Teilcube innerhalb des MDX-Skripts eingeschlossen werden. Geschachtelte Teilcubes werden mithilfe der SCOPE-Anweisung definiert. Weitere Informationen zur SCOPE-Anweisung finden Sie unter [SCOPE-Anweisung &#40;MDX-&#41;](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Berechnete Elemente werden nicht aggregiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Skript Anweisungen &#40;MDX-&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Grundlagen der MDX-Skripterstellung &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services)   
 [Definieren von Zuweisungen und anderen Skriptbefehlen](https://docs.microsoft.com/analysis-services/multidimensional-models/define-assignments-and-other-script-commands)  
  
  
