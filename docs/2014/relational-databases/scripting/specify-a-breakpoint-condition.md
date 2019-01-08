---
title: Angeben einer Breakpointbedingung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b70305d832c06388bc5977cdbcc560c3c8be8860
ms.sourcegitcommit: 40c3b86793d91531a919f598dd312f7e572171ec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53327630"
---
# <a name="specify-a-breakpoint-condition"></a>Angeben einer Breakpointbedingung
  Eine Breakpointbedingung ist ein [!INCLUDE[tsql](../../includes/tsql-md.md)] -Ausdruck, der vom Debugger ausgewertet wird, wenn der Breaktpoint erreicht wird. Wenn die Bedingungen erfüllt ist und eine angegebene Trefferanzahl erreicht ist, unterbricht der Debugger die Ausführung, oder er führt die für den Breakpoint angegebene Aktion aus.  
  
## <a name="specifying-conditions"></a>Angeben von Bedingungen  
 Der angegebene Ausdruck muss ein gültiger Transact-SQL-Ausdruck sein, der zu einem booleschen Wert ausgewertet wird. Weitere Informationen finden Sie unter [Expressions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql).  
  
 Wenn Sie eine Breakpointbedingung mit ungültiger Syntax angeben, wird sofort eine Warnmeldung angezeigt. Wenn Sie eine Bedingung mit gültiger Syntax, jedoch ungültiger Semantik angeben, wird beim ersten Erreichen des Breakpoints eine Warnmeldung angezeigt. In jedem Fall unterbricht der Debugger die Ausführung, wenn der ungültige Breakpoint erreicht wird.  
  
#### <a name="to-specify-a-condition"></a>So geben Sie eine Bedingung an  
  
1.  Klicken Sie im Editor-Fenster mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Bedingung** .  
  
     -oder-  
  
     Klicken Sie im **Breakpointfenster** mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Bedingung** .  
  
2.  Geben Sie im Dialogfeld **Haltepunktbedingung** einen gültigen booleschen Ausdruck im Feld **Bedingung** ein.  
  
3.  Wählen Sie **ist "true"** sollten Sie unterbrechen, wenn der Ausdruck ergibt `true`, oder wählen Sie **hat sich geändert** sollten Sie unterbrechen, wenn der Wert des Ausdrucks geändert hat.  
  
    > [!NOTE]  
    >  Der Debugger wertet den booleschen Ausdruck erst aus, wenn der Breakpoint das erste Mal erreicht wird. Wenn Sie **wurde geändert**auswählen, interpretiert der Debugger die erste Auswertung nicht als Änderung. Daher wird die Ausführung nicht bei der ersten Auswertung unterbrochen.  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben einer Trefferanzahl](specify-a-hit-count.md)   
 [Angeben einer Breakpointaktion](specify-a-breakpoint-action.md)  
