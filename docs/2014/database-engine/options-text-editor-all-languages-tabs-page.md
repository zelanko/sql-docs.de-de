---
title: Optionen (Text-Editor – alle Sprachen – Seite "Tabstopps") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
ms.assetid: bd715d6b-f873-41d4-aa10-57b7098b61cc
caps.latest.revision: 21
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2cc5922ed04933dcb7a6b09995353e7fd64a3163
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287856"
---
# <a name="options-text-editor---all-languages--tabs-page"></a>Optionen (Text-Editor – alle Sprachen – Seite "Tabstopps")
  Mit diesem Dialogfeld können Sie das Tabulatorverhalten für alle fünf Editoren von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] festlegen. Zum Anzeigen dieser Optionen klicken Sie im Menü **Extras** auf **Optionen** . Wählen Sie den Ordner **Text-Editor** aus, erweitern Sie den Ordner **Alle Sprachen**, und klicken Sie dann auf **Tabstopps**.  
  
## <a name="tabbing-options-by-editor"></a>Tabulatoroptionen für einzelne Editoren  
 Mit den Dialogfeldern **Alle Sprachen** können Sie die Optionen für den DMX-, MDX- und SQL Server Compact-Editor festlegen. Die hier festgelegten Optionen werden auch auf den Nur-Text, den Transact-SQL- und den XML-Editor angewendet, Sie können die Optionen für diese Editoren jedoch separat festlegen, indem Sie die Unterordner für diese Sprachen erweitern und die entsprechenden Optionsseiten auswählen. In einigen Sprachen werden nicht alle Tabulatoroptionen unterstützt.  
  
> [!CAUTION]  
>  Wenn Sie in diesem Dialogfeld eine Option festlegen, für den Nur-Text-, den Transact-SQL- oder den XML-Editor jedoch eine andere Einstellung wünschen, müssen Sie die Optionen für diese Editoren festlegen, nachdem Sie die Auswahl im Dialogfeld **Alle Sprachen** übernommen haben.  
  
 Wenn für einen bestimmten Editor verschiedene Einstellungen ausgewählt wurden, wird die Meldung "Die Einzugs- (oder Tabstopp-)Einstellungen für einzelne Textformate stehen miteinander im Konflikt" angezeigt. Diese Erinnerung wird beispielsweise dann angezeigt, wenn für **Nur-Text** die Einzugsoption **Block**, für **XML** jedoch die Option **Keiner** ausgewählt wurde.  
  
## <a name="indenting"></a>Einzug  
 **Keine**  
 Wenn diese Option ausgewählt ist, wird die neue Zeile, die nach dem Drücken der EINGABETASTE erstellt wird, nicht eingerückt. Der Cursor wird in der ersten Spalte der neuen Zeile platziert.  
  
 **Block**  
 Wenn diese Option ausgewählt ist, wird die nach dem Drücken der Eingabetaste erstellte Zeile automatisch so weit wie die vorige Zeile eingerückt.  
  
 **Intelligente**  
 Wenn diese Option ausgewählt ist, wird die nach dem Drücken der Eingabetaste erstellte Zeile je nach Kontext eingerückt.  
  
## <a name="tabs"></a>Tabstopps  
 **Tabulatorgröße**  
 Legt den Abstand zwischen den Tabstopps fest. Der Standardwert ist vier Leerzeichen.  
  
 **Einzugsgröße**  
 Legt die Größe des automatischen Einzugs in Leerzeichen fest. Der Standardwert ist vier Leerzeichen. Es werden entweder Tabstopps, Leerzeichen oder beides verwendet, um den angegebenen Raum zu füllen.  
  
 **Leerzeichen einfügen**  
 Wenn diese Option ausgewählt ist, werden bei Einzugsfunktionen nur Leerzeichen eingefügt, keine Tabulatorzeichen. Wenn die **Einzugsgröße** z.B. auf 5 festgelegt ist, werden fünf Leerzeichen eingefügt, wenn Sie die TABULATORTASTE drücken oder im Hauptfenster von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] auf der Symbolleiste auf die Schaltfläche **Einzug vergrößern** klicken.  
  
 **Tabstopps beibehalten**  
 Wenn diese Option ausgewählt ist, werden bei Einzugsfunktionen so viele Tabulatorzeichen wie möglich eingefügt. Jedes Tabulatorzeichen nimmt den Platz so vieler Leerzeichen ein, wie im Feld **Tabulatorgröße**definiert wurden. Wenn die **Einzugsgröße** kein ganzes Vielfaches der **Tabulatorgröße**ist, werden zum Auffüllen der Differenz Leerzeichen verwendet.  
  
  
