---
title: Dialogfeld 'Schnellüberwachung'
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
f1_keywords:
- vs.debug.quickwatch
helpviewer_keywords:
- QuickWatch Dialog [Transact-SQL]
ms.assetid: d6bbb373-1452-41f2-bdc5-86ae689c3dc0
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 03/14/2017
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: af12ca6fb0b8eb0b4461d95e75e8c1a3c62ed77e
ms.sourcegitcommit: add39e028e919df7d801e8b6bb4f8ac877e60e17
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2019
ms.locfileid: "74119245"
---
# <a name="transact-sql-debugger---quickwatch-dialog-box"></a>Transact-SQL-Debugger – Dialogfeld „Schnellüberwachung“

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mithilfe des Dialogfelds **Schnellüberwachung** können Sie beim Debuggen von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code schnell den Datentyp und den Wert eines [!INCLUDE[tsql](../../includes/tsql-md.md)] -Ausdrucks anzeigen, wie z. B. einer Variable oder eines Parameters. Um mehrere Ausdrücke zu beobachten, können Sie den Ausdruck auch einem **Überwachungsfenster** hinzufügen.  

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]

## <a name="task-list"></a>Aufgabenliste

 **So greifen Sie auf das Dialogfeld Schnellüberwachung zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Schnellüberwachung**.  
  
 **So zeigen Sie die Informationen zu einem Ausdruck an**  
  
1.  Geben Sie den gewünschten Ausdruck im Listenfeld **Ausdruck** ein, oder wählen Sie ihn aus. Die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Ausdrücke werden unterstützt:  
  
    -   Variablen  
  
    -   Parameter.  
  
    -   Systemfunktionen, deren Name mit „@@“ beginnt.  
  
    -   Ausdrücke, die durch Anwenden von Operatoren auf eine oder mehrere Variablen, Parameter oder Systemfunktionen erstellt werden, z.B. "@IntegerCounter + 1" oder "FirstName + LastName"  
  
    -   Transact-SQL-Anweisungen, die einen einzelnen Wert zurückgeben, z. B.: SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.  
  
2.  Klicken Sie auf **Neu auswerten**.  
  
 **So fügen Sie den Ausdruck der Schnellüberwachung einem Überwachungsfenster hinzu**  
  
-   Klicken Sie auf **Überwachung hinzufügen**.  
  
 **So ändern Sie den Wert des Ausdrucks der Schnellüberwachung**  
  
-   Klicken mit der rechten Maustaste auf den Ausdruck, und wählen Sie anschließend **Wert bearbeiten**aus.  
  
## <a name="options"></a>enthalten  
 **Ausdruckliste**  
 Zeigt den aktuell ausgewählten Ausdruck an. Die Dropdownliste enthält einen Satz von Ausdrücken, deren Anzeige Sie auswählen können. In der Liste sind jene Ausdrücke aufgeführt, die im Bereich des Stapelrahmens verfügbar sind, der im Fenster **Aufrufliste** aktuell ausgewählt ist. Um einen anderen Ausdruck anzuzeigen, geben Sie entweder den Ausdruck ein, oder wählen Sie ihn aus der Liste aus. Der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Debugger unterstützt die folgenden Ausdrücke: Variablen, Parameter und die Systemfunktionen, deren Namen mit @@ beginnen.  
  
 **Werteraster**  
 Zeigt die Eigenschaften des Ausdrucks an, der gerade beobachtet wird.  
  
 **Name**  
 Entspricht dem [!INCLUDE[tsql](../../includes/tsql-md.md)] -Ausdruck, der beobachtet wird.  
  
 **ReplTest1**  
 Zeigt den Wert an, der dem Ausdruck derzeit zugewiesen ist. Ein Leerzeichen wird angezeigt, wenn der Ausdruck gerade über keinen Wert verfügt.  
  
 Wenn die Länge eines Ausdrucks größer als die Breite der Spalte **Wert** ist, wird der vollständige Wert in einer QuickInfo angezeigt, wenn Sie den Mauszeiger über die **Wertzelle** für diesen Ausdruck bewegen.  
  
 Ein Lupensymbol in einer **Wertzelle** zeigt an, dass die [!INCLUDE[tsql](../../includes/tsql-md.md)] Debuggerschnellansicht verfügbar ist. In der Liste können Sie **Text-Schnellansicht**, **XML-Schnellansicht**oder **HTML-Schnellansicht**angeben. Um eine Debuggerschnellansicht zu starten, klicken Sie auf das Lupensymbol. Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger öffnet ein Dialogfeld, in dem die Daten in einem für den Datentyp geeigneten Format angezeigt werden.  
  
 **Typ**  
 Zeigt den Datentyp des Ausdrucks an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transact-SQL-Debugger](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Transact-SQL-Debuggerinformationen](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [Überwachung (Fenster)](../../relational-databases/scripting/transact-sql-debugger-watch-window.md)   
 [Lokal (Fenster)](../../relational-databases/scripting/transact-sql-debugger-locals-window.md)   
 [Fenster 'Aufrufliste'](../../relational-databases/scripting/transact-sql-debugger-call-stack-window.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
