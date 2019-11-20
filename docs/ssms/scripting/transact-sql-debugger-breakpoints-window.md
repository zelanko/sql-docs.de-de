---
title: Fenster „Breakpoints“ | Microsoft-Dokumentation
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 11/04/2019
helpviewer_keywords:
- Breakpoints Window [Transact-SQL]
ms.assetid: bad88d10-fdd5-4d3d-b5ea-a4f063847485
monikerRange: '>= sql-server-2014 || = sqlallproducts-allversions'
ms.openlocfilehash: cc5600a7cd9e933046700204a8dac916199832c6
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73638013"
---
# <a name="transact-sql-debugger---breakpoints-window"></a>Transact-SQL-Debugger – Fenster „Breakpoints“

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Im Fenster **Breakpoints** werden alle Breakpoints aufgelistet, die im aktuellen [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor festgelegt sind. Um die Breakpoints zu verwalten, verwenden Sie die Symbolleiste im Fenster **Breakpoints** . Breakpoints sind Positionen im Code, an denen die Ausführung im Debugmodus angehalten wird, sodass Sie Debugdaten anzeigen können.

## <a name="task-list"></a>Aufgabenliste

**So greifen Sie auf das Fenster Breakpoints zu**

- Klicken Sie im Menü **Debuggen** erst auf **Fenster** und anschließend auf **Breakpoints**.

## <a name="breakpoints-window-columns"></a>Spalten des Fensters 'Breakpoints'

Standardmäßig listet das Fenster **Breakpoints** die folgenden Spalten auf.  

**Name**  
Zeigt den Namen des Breakpoints an. Breakpointnamen werden vom Debugger bereitgestellt. Dieser Name umfasst den Namen aus dem Abfrage-Editor-Fenster der Datenbank-Engine, die den Breakpoint enthält, und die Zeilennummer im Abfrage-Editor, auf die der Breakpoint festgelegt wurde.  

**Bedingung**  
Zeigt **(Keine Bedingung)** an. Der Debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] unterstützt das Festlegen von Breakpointbedingungen nicht.

**Trefferanzahl**  
Zeigt **breaks always** (Immer anhalten) an.

Sie können die folgenden Spalten hinzufügen und entfernen, indem Sie sie in der Liste **Spalten** auswählen.  

**Filter**  
Zeigt **(Keine)** an. Der Debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] unterstützt das Festlegen von Breakpointfiltern nicht.

**Bei Treffer**  
Zeigt **Unterbrechen**an.

**Sprache**  
Zeigt **Transact-SQL** für [!INCLUDE[tsql](../../includes/tsql-md.md)]an.  

**Funktion**  
Zeigt die Nummer der Zeile an, auf der der Breakpoint festgelegt wurde.  

**File**  
Zeigt den Namen der Quelldatei an, die den Breakpoint enthält, und die Nummer der Zeile, auf der der Breakpoint festgelegt wurde.

**Adresse**  
Der Debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] unterstützt dieses Feature nicht.  

**Verarbeiten**  
Zeigt **[SQL]** an, um darauf hinzuweisen, dass es sich um einen [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Prozess handelt. Danach folgt der Name der Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] , in der der Code ausgeführt wird.

## <a name="breakpoints-window-toolbar"></a>Symbolleiste des Fensters 'Breakpoints'

Wenn das aktuelle [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor-Fenster aktive Breakpoints enthält, wird im Fenster **Breakpoints** eine Symbolleiste angezeigt, die zum Verwalten der Breakpoints verwendet werden kann.

**Löschen**  
Löscht den ausgewählten Breakpoint.

**Alle Breakpoints löschen**  
Löscht alle Breakpoints, die im Fenster **Breakpoints** angezeigt werden.  

**Alle Breakpoints deaktivieren**  
Deaktiviert alle Breakpoints, sodass sie die Codeausführung nicht mehr anhalten; die Breakpoints werden jedoch beibehalten. Wenn alle Breakpoints deaktiviert sind, wird diese Schaltfläche als **Breakpoints aktivieren**angezeigt.

**Breakpoints aktivieren**  
Aktiviert alle Breakpoints, sodass sie die Codeausführung anhalten. Wenn alle Breakpoints aktiviert sind, wird diese Schaltfläche als **Alle Breakpoints deaktivieren**angezeigt.  

**Gehe zu Quellcode**  
Positioniert den Cursor im Abfrage-Editor auf der Zeile, die den ausgewählten Breakpoint enthält.

**Spalten**  
Listet alle Spalten auf, die im Fenster **Breakpoints** angezeigt werden können. Ein Kontrollkästchen gibt die Spalten an, die angezeigt werden. Um eine Spalte im Fenster **Breakpoints** hinzuzufügen oder zu entfernen, wählen Sie die Spalte in der Liste aus.

## <a name="see-also"></a>Weitere Informationen

[Transact-SQL-Debugger](../../relational-databases/scripting/transact-sql-debugger.md)
