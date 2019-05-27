---
title: Schrittweises Durchlaufen von Transact-SQL-Code | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, debugging code
- Transact-SQL debugger, step over
- Transact-SQL debugger, step out
- Transact-SQL debugger, step into
ms.assetid: e09079b8-c4c9-42b4-821b-4ce81a98a086
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e79a92bc1756003341cbb9e0581ade42a2bcee8b
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66090011"
---
# <a name="step-through-transact-sql-code"></a>Schrittweises Durchlaufen von Transact-SQL-Code
  Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger ermöglicht es Ihnen, zu bestimmen, welche [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen in einem [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor-Fenster ausgeführt werden. Sie können den Debugger bei einzelnen Anweisungen unterbrechen und dann den Status der Codeelemente an diesem Punkt anzeigen.  
  
## <a name="breakpoints"></a>Breakpoints  
 Ein Breakpoint signalisiert dem Debugger, die Ausführung bei einer bestimmten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung anzuhalten. Weitere Informationen über Breakpoints finden Sie unter "Verwenden von Transact-SQL-Breakpoints".  
  
## <a name="controlling-statement-execution"></a>Steuern der Anweisungsausführung  
 Im [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger können Sie die folgenden Optionen für das Ausführen der aktuellen Anweisung im [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code angeben:  
  
-   Den Vorgang bis zum nächsten Breakpoint ausführen  
  
-   Einen Einzelschritt in die nächste Anweisung ausführen  
  
     Wenn die nächste Anweisung eine gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozedur, eine Funktion oder einen Trigger aufruft, zeigt der Debugger ein neues Abfrage-Editor-Fenster an, das den Code des Moduls enthält. Das Fenster befindet sich im Debuggingmodus, und die Ausführung hält bei der ersten Anweisung im Modul an. Sie können sich dann durch den Modulcode bewegen, indem Sie z. B. Breakpoints festlegen oder den Code schrittweise durchlaufen.  
  
-   Einen Einzelschritt in die nächste Anweisung überspringen  
  
     Die nächste Anweisung wird ausgeführt. Wenn die Anweisung jedoch eine gespeicherte Prozedur, eine Funktion oder einen Trigger aufruft, wird der Modulcode bis zum Ende ausgeführt, und die Ergebnisse werden an den aufrufenden Code zurückgegeben. Wenn Sie sicher sind, dass in der gespeicherten Prozedur keine Fehler vorliegen, können Sie sie überspringen. Die Ausführung hält bei der Anweisung an, die dem Aufruf der gespeicherten Prozedur, der Funktion oder dem Trigger folgt.  
  
-   Eine gespeicherte Prozedur, eine Funktion oder einen Trigger bis zum Rücksprung ausführen  
  
     Die Ausführung hält bei der Anweisung an, die dem Aufruf der gespeicherten Prozedur, der Funktion oder dem Trigger folgt.  
  
-   Den Vorgang von der aktuellen Position bis zur aktuellen Position des Zeigers ausführen und alle Breakpoints ignorieren  
  
 Die folgende Tabelle enthält die verschiedenen Möglichkeiten, mit denen Sie bestimmen können, wie Anweisungen im [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger ausgeführt werden.  
  
|Aktion|Prozedur|  
|------------|---------------|  
|Ausführen aller Anweisungen von der aktuellen Anweisung bis zum nächsten Breakpoint|Auf der **Debuggen** Menü klicken Sie auf **Weiter**.<br /><br /> Auf der **Debuggen** -Symbolleiste klicken Sie auf die **Weiter** Schaltfläche.|  
|Ausführen eines Einzelschritts in die nächste Anweisung oder in das nächste Modul|Auf der **Debuggen** Menü klicken Sie auf **Einzelschritt**.<br /><br /> Auf der **Debuggen** -Symbolleiste klicken Sie auf die **Einzelschritt** Schaltfläche.<br /><br /> Drücken Sie F11.|  
|Überspringen der nächsten Anweisung oder des nächsten Moduls|Auf der **Debuggen** Menü klicken Sie auf **Prozedurschritt**.<br /><br /> Auf der **Debuggen** -Symbolleiste klicken Sie auf die **Prozedurschritt** Schaltfläche.<br /><br /> Drücken Sie F10.|  
|Ausführen eines Moduls bis Rücksprung|Auf der **Debuggen** Menü klicken Sie auf **Ausführen bis Rücksprung**.<br /><br /> Auf der **Debuggen** -Symbolleiste klicken Sie auf die **Ausführen bis Rücksprung** Schaltfläche.<br /><br /> Drücken Sie UMSCHALT+F11.|  
|Ausführen bis zur aktuellen Cursorposition|Klicken Sie mit der rechten Maustaste auf das Abfrage-Editor-Fenster, und klicken Sie dann auf **Ausführen bis Cursorposition**.<br /><br /> Drücken Sie STRG+F10.|  
  
## <a name="see-also"></a>Siehe auch  
 [Transact-SQL-Debuggerinformationen](transact-sql-debugger-information.md)  
  
  
