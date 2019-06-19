---
title: Fenster „Lokal“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Locals Window [Transact-SQL]
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 654cde2b035892cb153da475ab1fa514ad67b11b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65821720"
---
# <a name="transact-sql-debugger---locals-window"></a>Transact-SQL-Debugger – Fenster „Lokal“
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Transact-SQL-Debugger](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Transact-SQL-Debuggerinformationen](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [Überwachung (Fenster)](../../relational-databases/scripting/transact-sql-debugger-watch-window.md)   
 [Fenster 'Aufrufliste'](../../relational-databases/scripting/transact-sql-debugger-call-stack-window.md)   
 [Dialogfeld 'Schnellüberwachung'](../../relational-databases/scripting/transact-sql-debugger-quickwatch-dialog-box.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
