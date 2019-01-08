---
title: Fenster „Lokal“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22090b4bdb1827be4add47ec2f539cde0ea70827
ms.sourcegitcommit: 40c3b86793d91531a919f598dd312f7e572171ec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53327400"
---
# <a name="locals-window"></a>Lokal (Fenster)
  Im Fenster **Lokal** werden Informationen über die lokalen Ausdrücke im aktuellen Bereich des [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debuggers angezeigt. Der Bereich wird auf den aktuellen Aufruflistenrahmen festgelegt, der im Fenster **Aufrufliste** ausgewählt ist. Sie müssen sich im Debugmodus befinden, um die lokalen Ausdrücke anzuzeigen.  
  
## <a name="task-list"></a>Aufgabenliste  
 **So greifen Sie auf das Fenster Lokal zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Fenster**, und klicken Sie dann auf **Lokal**.  
  
 **So ändern Sie den Wert eines Ausdrucks**  
  
-   Klicken mit der rechten Maustaste auf den Ausdruck, und wählen Sie anschließend **Wert bearbeiten**aus.  
  
## <a name="columns"></a>Spalte  
 **Name**  
 Der Name des lokalen Ausdrucks. Der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Debugger führt Variablen, Parameter und die Systemfunktionen, deren Namen mit @@ beginnen, auf.  
  
 **Value**  
 Zeigt den Wert an, der dem lokalen Ausdruck derzeit zugewiesen ist. Diese Spalte ist leer, wenn dem Ausdruck kein Wert zugewiesen wurde.  
  
 Wenn die Länge eines Ausdrucks größer als die Breite der Spalte **Wert** ist, wird der vollständige Wert in einer QuickInfo angezeigt, wenn Sie den Mauszeiger über die **Wertzelle** für diesen Ausdruck bewegen.  
  
 Ein Lupensymbol in einer **Wertzelle** zeigt an, dass die [!INCLUDE[tsql](../../includes/tsql-md.md)] Debuggerschnellansicht verfügbar ist. In der Liste können Sie **Text-Schnellansicht**, **XML-Schnellansicht**oder **HTML-Schnellansicht**angeben. Um eine Debuggerschnellansicht zu starten, klicken Sie auf das Lupensymbol. Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger öffnet ein Dialogfeld, in dem die Daten in einem für den Datentyp geeigneten Format angezeigt werden.  
  
 **Typ**  
 Zeigt den Datentyp des Ausdrucks an.  
  
## <a name="see-also"></a>Siehe auch  
 [Transact-SQL-Debugger](transact-sql-debugger.md)   
 [Transact-SQL-Debuggerinformationen](transact-sql-debugger-information.md)   
 [Überwachung (Fenster)](transact-sql-debugger-watch-window.md)   
 [Fenster 'Aufrufliste'](transact-sql-debugger-call-stack-window.md)   
 [Dialogfeld 'Schnellüberwachung'](transact-sql-debugger-quickwatch-dialog-box.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)  
