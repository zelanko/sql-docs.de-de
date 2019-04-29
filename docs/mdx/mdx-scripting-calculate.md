---
title: CALCULATE-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 389c5f470cb3bf00cfe668a9405e36cd4ac8950e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187626"
---
# <a name="mdx-scripting---calculate"></a>MDX-Skripts – CALCULATE


  Füllt jede Zelle in einem Cube mit einem Aggregatwert auf.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>Argumente  
 None  
  
## <a name="remarks"></a>Hinweise  
 Die CALCULATE-Anweisung wird beim Erstellen eines Cubes mithilfe von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] automatisch als erste Anweisung in das MDX-Skript des Cubes eingefügt. Die CALCULATE-Anweisung weist alle Zellen im Cube an, beim Aggregieren mit Zellen geringerer Granularität zu beginnen. Wenn nach dem Aggregieren einer Zelle anschließend Zellen geringerer Granularität mithilfe von Ausdrücken aufgefüllt werden, hat dies Auswirkungen auf die aggregierten Werte von Zellen höherer Granularität. Diese Aggregation ist in der Regel erwünscht, Sie können jedoch die Anweisung bei Bedarf entfernen oder andere Anweisungen vor dieser ausführen lassen.  
  
 Die CALCULATE-Anweisung kann nicht in einen geschachtelten Teilcube innerhalb des MDX-Skripts eingeschlossen werden. Geschachtelte Teilcubes werden mithilfe der SCOPE-Anweisung definiert. Weitere Informationen zur SCOPE-Anweisung finden Sie unter [SCOPE-Anweisung &#40;MDX&#41;](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  Berechnete Elemente werden nicht aggregiert.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Skriptanweisungen &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Grundlegendes zu MDX-Skripts &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Definieren von Zuweisungen und anderen Skriptbefehlen](../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md)  
  
  
