---
title: Dialogfeld „Schnellüberwachung“ Dialogfeld | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.quickwatch
helpviewer_keywords:
- QuickWatch Dialog [Transact-SQL]
ms.assetid: d6bbb373-1452-41f2-bdc5-86ae689c3dc0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00f54c136441050a5e6e460e7578789f41a569d7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48162710"
---
# <a name="quickwatch-dialog-box"></a>Dialogfeld 'Schnellüberwachung'
  Mithilfe des Dialogfelds **Schnellüberwachung** können Sie beim Debuggen von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code schnell den Datentyp und den Wert eines [!INCLUDE[tsql](../../includes/tsql-md.md)] -Ausdrucks anzeigen, wie z. B. einer Variable oder eines Parameters. Um mehrere Ausdrücke zu beobachten, können Sie den Ausdruck auch einem **Überwachungsfenster** hinzufügen.  
  
## <a name="task-list"></a>Aufgabenliste  
 **So greifen Sie auf das Dialogfeld Schnellüberwachung zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Schnellüberwachung**.  
  
 **So zeigen Sie die Informationen zu einem Ausdruck an**  
  
1.  Geben Sie den gewünschten Ausdruck im Listenfeld **Ausdruck** ein, oder wählen Sie ihn aus. Die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Ausdrücke werden unterstützt:  
  
    -   Variablen  
  
    -   Parameter.  
  
    -   Systemfunktionen, deren Name mit „@@“ beginnt.  
  
    -   Ausdrücke, die durch Anwenden von Operatoren auf eine oder mehrere Variablen, Parameter oder Systemfunktionen erstellt werden, z.B. "@IntegerCounter + 1" oder "FirstName + LastName"  
  
    -   Transact-SQL-Anweisungen, die einen einzelnen Wert zurückgeben, z. B.: "SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1"  
  
2.  Klicken Sie auf **Neu auswerten**.  
  
 **So fügen Sie den Ausdruck der Schnellüberwachung einem Überwachungsfenster hinzu**  
  
-   Klicken Sie auf **Überwachung hinzufügen**.  
  
 **So ändern Sie den Wert des Ausdrucks der Schnellüberwachung**  
  
-   Klicken mit der rechten Maustaste auf den Ausdruck, und wählen Sie anschließend **Wert bearbeiten**aus.  
  
## <a name="options"></a>Tastatur  
 **Ausdruckliste**  
 Zeigt den aktuell ausgewählten Ausdruck an. Die Dropdownliste enthält einen Satz von Ausdrücken, deren Anzeige Sie auswählen können. In der Liste sind jene Ausdrücke aufgeführt, die im Bereich des Stapelrahmens verfügbar sind, der im Fenster **Aufrufliste** aktuell ausgewählt ist. Um einen anderen Ausdruck anzuzeigen, geben Sie entweder den Ausdruck ein, oder wählen Sie ihn aus der Liste aus. Der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Debugger unterstützt die folgenden Ausdrücke: Variablen, Parameter und die Systemfunktionen, deren Namen mit @@ beginnen.  
  
 **Werteraster**  
 Zeigt die Eigenschaften des Ausdrucks an, der gerade beobachtet wird.  
  
 **Name**  
 Entspricht dem [!INCLUDE[tsql](../../includes/tsql-md.md)] -Ausdruck, der beobachtet wird.  
  
 **Wert**  
 Zeigt den Wert an, der dem Ausdruck derzeit zugewiesen ist. Ein Leerzeichen wird angezeigt, wenn der Ausdruck gerade über keinen Wert verfügt.  
  
 Wenn die Länge eines Ausdrucks größer als die Breite der Spalte **Wert** ist, wird der vollständige Wert in einer QuickInfo angezeigt, wenn Sie den Mauszeiger über die **Wertzelle** für diesen Ausdruck bewegen.  
  
 Ein Lupensymbol in einer **Wertzelle** zeigt an, dass die [!INCLUDE[tsql](../../includes/tsql-md.md)] Debuggerschnellansicht verfügbar ist. In der Liste können Sie **Text-Schnellansicht**, **XML-Schnellansicht**oder **HTML-Schnellansicht**angeben. Um eine Debuggerschnellansicht zu starten, klicken Sie auf das Lupensymbol. Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger öffnet ein Dialogfeld, in dem die Daten in einem für den Datentyp geeigneten Format angezeigt werden.  
  
 **Typ**  
 Zeigt den Datentyp des Ausdrucks an.  
  
## <a name="see-also"></a>Siehe auch  
 [Transact-SQL-Debugger](transact-sql-debugger.md)   
 [Transact-SQL-Debuggerinformationen](transact-sql-debugger-information.md)   
 [Überwachung (Fenster)](transact-sql-debugger-watch-window.md)   
 [Lokal (Fenster)](transact-sql-debugger-locals-window.md)   
 [Fenster 'Aufrufliste'](transact-sql-debugger-call-stack-window.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)  
  
  
