---
title: Optionen (Seite "Text-Editor - Transact-SQL - Tabstopps") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.Tabs
dev_langs:
- TSQL
ms.assetid: a4499784-67f7-46ef-9f7c-2d0fdd117a52
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 7dd6e11704497bd37fa4eb78948376587ece1119
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844754"
---
# <a name="options-text-editor---transact-sql---tabs-page"></a>Optionen (Seite "Text-Editor - Transact-SQL - Registerkarten")
  Verwenden Sie dieses Dialogfeld, um das Tabulatorverhalten des [!INCLUDE[ssDE](../includes/ssde-md.md)]-Abfrage-Editors zu ändern, der zur Programmierung von [!INCLUDE[tsql](../includes/tsql-md.md)]-Skripts verwendet wird. Zum Anzeigen dieser Einstellungen klicken Sie im Menü **Extras** auf **Optionen**, erweitern nacheinander den Ordner **Text-Editor** und den Unterordner **Transact-SQL** und klicken dann auf **Tabstopps**.  
  
## <a name="setting-options-in-multiple-locations"></a>Festlegen der Optionen an mehreren Stellen  
 Optionen für den [!INCLUDE[ssDE](../includes/ssde-md.md)]-Abfrage-Editor können auch im Dialogfeld **Alle Sprachen** festgelegt werden. Wenn Sie die Dialogfelder unter **Alle Sprachen** verwenden, um verschiedene Optionen für die anderen [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] -Editoren wie z. B. die DMX- oder MDX-Editoren einzustellen, müssen Sie die Optionen des [!INCLUDE[ssDE](../includes/ssde-md.md)] -Abfrage-Editors mithilfe dieses Dialogfelds zurücksetzen.  
  
## <a name="indenting"></a>Einzug  
 **Keine**  
 Wenn diese Option ausgewählt ist, wird die neue Zeile, die nach dem Drücken der EINGABETASTE erstellt wird, nicht eingerückt. Der Cursor wird in der ersten Spalte der neuen Zeile platziert.  
  
 **Block**  
 Wenn diese Option ausgewählt ist, wird die nach dem Drücken der Eingabetaste erstellte Zeile automatisch so weit eingerückt wie die vorige Zeile.  
  
 **Smart**  
 Diese Option ist nicht verfügbar.  
  
## <a name="tabs"></a>Tabstopps  
 **Tabulatorgröße**  
 Legt den Abstand zwischen den Tabstopps fest. Der Standardwert ist vier Leerzeichen.  
  
 **Einzugsgröße**  
 Legt die Größe des automatischen Einzugs in Leerzeichen fest. Der Standardwert ist vier Leerzeichen. Es werden entweder Tabstopps, Leerzeichen oder beide verwendet, um den angegebenen Raum zu füllen.  
  
 **Leerzeichen einfügen**  
 Wenn diese Option ausgewählt ist, werden bei Einzugsfunktionen nur Leerzeichen eingefügt, keine Tabulatorzeichen. Wenn die **Einzugsgröße** z. B. auf 5 festgelegt ist, werden fünf Leerzeichen eingefügt, wenn Sie die TAB-Taste drücken oder im Hauptfenster von **auf der Symbolleiste auf die Schaltfläche** Einzug vergrößern [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] klicken.  
  
 **Tabstopps beibehalten**  
 Wenn diese Option ausgewählt ist, werden bei Einzugsfunktionen so viele Tabulatorzeichen wie möglich eingefügt. Jedes Tabulatorzeichen nimmt den Platz so vieler Leerzeichen ein, wie im Feld **Tabulatorgröße**definiert wurden. Wenn die **Einzugsgröße** kein ganzes Vielfaches der **Tabulatorgröße**ist, werden zum Auffüllen der Differenz Leerzeichen verwendet.  
  
  
