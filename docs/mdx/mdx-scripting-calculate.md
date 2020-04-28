---
title: Berechnen-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a873c2a6a60e3e6283c3c24fa4b9d28757e57ffb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68893353"
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
  
  
