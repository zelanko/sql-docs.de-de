---
title: 'Optionen (Text-Editor: XML: Seite "Registerkarten") | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
ms.assetid: 13bf5f8c-aba3-4c05-b8bb-eb475797c9bd
author: rothja
ms.author: jroth
ms.openlocfilehash: 43f97832e4afc7565c472d3da58127ea679d85c3
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84929604"
---
# <a name="options-text-editorxmltabs-page"></a>Optionen (Text-Editor: XML: Seite „Tabstopps“)
  Mithilfe dieses Dialogfelds können Sie das Tabulatorverhalten des XML-Editors ändern, der für die Bearbeitung von XML-Dokumenten verwendet wird. Zum Anzeigen dieser Einstellungen klicken Sie im Menü **Extras** auf **Optionen** , und erweitern Sie anschließend den Ordner **Text-Editor** , dann den Unterordner **XML** , und klicken Sie dann auf **Tabstopps**.  
  
## <a name="setting-options-in-multiple-locations"></a>Festlegen der Optionen an mehreren Stellen  
 Optionen für den XML-Editor können auch im Dialogfeld **Alle Sprachen/Allgemein** festgelegt werden. Wenn Sie die Dialogfelder **alle Sprachen** verwenden, um verschiedene Optionen für die anderen [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Editoren festzulegen, z. b. den DMX-oder MDX-Editoren, müssen Sie die XML-Editor-Optionen mithilfe dieses Dialog Felds zurücksetzen  
  
## <a name="indenting"></a>Einzug  
 **None**  
 Wenn diese Option ausgewählt ist, wird die neue Zeile, die nach dem Drücken der EINGABETASTE erstellt wird, nicht eingerückt. Der Cursor wird in der ersten Spalte der neuen Zeile platziert.  
  
 **Blockieren**  
 Wenn diese Option ausgewählt ist, wird die nach dem Drücken der Eingabetaste erstellte Zeile automatisch so weit eingerückt wie die vorige Zeile.  
  
 **Intelligent**  
 Wenn diese Option ausgewählt ist, wird die nach dem Drücken der Eingabetaste erstellte Zeile je nach Kontext eingerückt. Nach einer öffnenden geschweiften Klammer ({) werden beispielsweise die eingeschlossenen Zeilen automatisch um einen zusätzlichen Tabstopp eingerückt. Die dazugehörige schließende geschweifte Klammer (}) wird wieder auf die öffnende Klammer ausgerichtet.  
  
## <a name="tabs"></a>Registerkarten  
 **Tabulatorgröße**  
 Legt den Abstand zwischen den Tabstopps fest. Der Standardwert ist vier Leerzeichen.  
  
 **Einzugsgröße**  
 Legt die Größe des automatischen Einzugs in Leerzeichen fest. Der Standardwert ist vier Leerzeichen. Es werden entweder Tabstopps, Leerzeichen oder beide verwendet, um den angegebenen Raum zu füllen.  
  
 **Leerzeichen einfügen**  
 Wenn diese Option ausgewählt ist, werden bei Einzugsfunktionen nur Leerzeichen eingefügt, keine Tabulatorzeichen. Wenn die Einzugs **Größe** z. b. auf 5 festgelegt ist, werden fünf Leerzeichen eingefügt, wenn Sie die Tab-Taste drücken oder auf der Symbolleiste im Hauptfenster auf die Schaltfläche **Einzug vergrößern** klicken [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .  
  
 **Tabulatoren beibehalten**  
 Wenn diese Option ausgewählt ist, werden bei Einzugsfunktionen so viele Tabulatorzeichen wie möglich eingefügt. Jedes Tabulatorzeichen nimmt den Platz so vieler Leerzeichen ein, wie im Feld **Tabulatorgröße**definiert wurden. Wenn die **Einzugsgröße** kein ganzes Vielfaches der **Tabulatorgröße**ist, werden zum Auffüllen der Differenz Leerzeichen verwendet.  
  
  
