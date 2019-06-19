---
title: Angeben einer Breakpointbedingung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 63043009d9c908ad5edc3771e5d353cf2f66b010
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65821927"
---
# <a name="specify-a-breakpoint-condition"></a>Angeben einer Breakpointbedingung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Eine Breakpointbedingung ist ein [!INCLUDE[tsql](../../includes/tsql-md.md)] -Ausdruck, der vom Debugger ausgewertet wird, wenn der Breaktpoint erreicht wird. Wenn die Bedingungen erfüllt ist und eine angegebene Trefferanzahl erreicht ist, unterbricht der Debugger die Ausführung, oder er führt die für den Breakpoint angegebene Aktion aus.  
  
## <a name="specifying-conditions"></a>Angeben von Bedingungen  
 Der angegebene Ausdruck muss ein gültiger Transact-SQL-Ausdruck sein, der zu einem booleschen Wert ausgewertet wird. Weitere Informationen finden Sie unter [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 Wenn Sie eine Breakpointbedingung mit ungültiger Syntax angeben, wird sofort eine Warnmeldung angezeigt. Wenn Sie eine Bedingung mit gültiger Syntax, jedoch ungültiger Semantik angeben, wird beim ersten Erreichen des Breakpoints eine Warnmeldung angezeigt. In jedem Fall unterbricht der Debugger die Ausführung, wenn der ungültige Breakpoint erreicht wird.  
  
#### <a name="to-specify-a-condition"></a>So geben Sie eine Bedingung an  
  
1.  Klicken Sie im Editor-Fenster mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Bedingung** .  
  
     -oder-  
  
     Klicken Sie im **Breakpointfenster** mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Bedingung** .  
  
2.  Geben Sie im Dialogfeld **Haltepunktbedingung** einen gültigen booleschen Ausdruck im Feld **Bedingung** ein.  
  
3.  Wählen Sie **Ist "True"** aus, wenn die Ausführung bei der Auswertung des Ausdrucks zu **true**unterbrochen werden soll, oder wählen Sie **wurde geändert** aus, wenn die Ausführung bei einer Änderung des Ausdrucks unterbrochen werden soll.  
  
    > [!NOTE]  
    >  Der Debugger wertet den booleschen Ausdruck erst aus, wenn der Breakpoint das erste Mal erreicht wird. Wenn Sie **wurde geändert**auswählen, interpretiert der Debugger die erste Auswertung nicht als Änderung. Daher wird die Ausführung nicht bei der ersten Auswertung unterbrochen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben einer Trefferanzahl](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Angeben einer Breakpointaktion](../../relational-databases/scripting/specify-a-breakpoint-action.md)  
