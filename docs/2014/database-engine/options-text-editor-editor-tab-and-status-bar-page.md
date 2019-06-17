---
title: "Optionen (Text-Editor: Registerkarte ' Editor ' und Statusleiste) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.editorcontextsettings
- VS.ToolsOptionsPages.Text_Editor.EditorTabAndStatusBar
ms.assetid: e4815678-7885-4631-878f-c6a2b857ee05
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 01098f2181085f17788429608afb7bdda15fb504
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66089241"
---
# <a name="options-text-editor-editor-tab-and-status-bar-page"></a>Optionen (Text-Editor: Seite zu Registerkarte „Editor“ und Statusleiste)
  Auf der Seite **Registerkarte "Editor" und Statusleiste** können Sie die von den [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] -Abfrage-Editoren angezeigten Informationen anpassen. Sie können die Ebene der Informationen angeben, die auf der Registerkarte und der Statusleiste des Abfrage-Editor-Fensters angezeigt werden, sowie festlegen, ob die Statusleiste im Editor-Fenster oben oder unten angezeigt wird.  
  
## <a name="option-settings-by-editor"></a>Optionseinstellungen nach Editor  
 Die Editorregisterkarte und die Statusleiste sind in allen [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] -Editoren verfügbar, bieten jedoch unterschiedliche Grade an Funktionalität.  
  
 Der Abfrage-Editor der Datenbank-Engine kann eine Verbindung mit einer Servergruppe herstellen. In diesem Fall werden Verbindungen für alle Instanzen in der Servergruppe geöffnet, und eine Abfrage kann über alle Verbindungen gleichzeitig ausgeführt werden. In diesem Dialogfeld können Sie festlegen, dass die Statusleiste bei einer Verbindung mit mehreren Instanzen andere Farben aufweist als bei einer Verbindung mit nur einer Instanz. Zum Ändern der Multiserver-Ergebnisoptionen verwenden Sie die Seite [Optionen (Abfrageergebnisse/SQL Server/Für mehrere Server)](../../2014/database-engine/options-query-results-sql-server-multi-server.md).  
  
## <a name="status-bar-content"></a>Inhalt der Statusleiste  
 Gibt die Informationen an, die in der Statusleiste des Abfrage-Editors angezeigt werden.  
  
 **Ausführungszeit anzeigen**  
 Schließt die Skriptausführungszeit ein. Die Einstellungen lauten wie folgt:  
  
 **Keine**  
 Die Statusleiste zeigt keine Zeitinformationen an.  
  
 **End**  
 Auf der Statusleiste wird während der Skriptausführung die aktuelle Uhrzeit angezeigt. Bei Abschluss des Skripts wird die Uhrzeit angezeigt, zu der das Skript abgeschlossen wurde.  
  
 **Verstrichen**  
 Auf der Statusleiste wird die Zeit angezeigt, die das Skript bereits ausgeführt wurde. Bei Abschluss des Skripts wird die Zeit angezeigt, die zum Ausführen des Skripts benötigt wurde.  
  
 **Datenbanknamen einschließen**  
 Schließt den Namen der aktuellen Datenbank für die Verbindung ein. Wenn der Abfrage-Editor zuerst geöffnet wird, ist dies die Standarddatenbank für die Anmeldung. Der Datenbankkontext kann später mit der USE-Anweisung von Transact-SQL geändert werden.  
  
 **Anmeldenamen einschließen**  
 Schließt den Anmeldenamen ein.  
  
 **Zeilenanzahl einschließen**  
 Schließt die Anzahl der Zeilen ein, die vom derzeit ausgeführten Skript verarbeitet wurden.  
  
 **Servernamen einschließen**  
 Schließt den Servernamen ein. Bei lokalen Verbindungen ist dies der Instanzname. Bei Remoteverbindungen ist dies der Remotecomputername und Instanzname.  
  
## <a name="status-bar-layout-and-colors"></a>Layout und Farben der Statusleiste  
 Gibt die Farben für Elemente in der Statusleiste des Abfrage-Editors an.  
  
 **Verbindungen gruppieren**  
 Gibt die Farbe der Statusleiste an, wenn der Abfrage-Editor mehr als eine Verbindung aufweist.  
  
 **Einzelne serververbindungen**  
 Gibt die Farbe der Statusleiste an, wenn der Abfrage-Editor eine einzelne Verbindung aufweist.  
  
 **Speicherort der Statusleiste**  
 Gibt die Position der Statusleiste an. Die Einstellungen lauten wie folgt:  
  
 **Top**  
 Die Statusleiste wird am oberen Rand des Abfrage-Editor-Fensters angezeigt.  
  
 **Bottom**  
 Die Statusleiste wird am unteren Rand des Abfrage-Editor-Fensters angezeigt.  
  
## <a name="tab-text"></a>Registerkartentext  
 Gibt den Text an, der in der Registerkarte am oberen Rand eines Abfrage-Editor-Fensters angezeigt wird. Wenn der Text für die Anzeige zu lang ist, können Sie die vollständige Zeichenfolge in einer QuickInfo anzeigen, die angezeigt wird, wenn Sie den Mauszeiger über die Registerkarte führen.  
  
 **Datenbanknamen einschließen**  
 Schließt den Namen der aktuellen Datenbank für die Verbindung ein. Wenn der Abfrage-Editor zuerst geöffnet wird, ist dies die Standarddatenbank für die Anmeldung. Der Datenbankkontext kann später mit der USE-Anweisung von Transact-SQL geändert werden.  
  
 **Dateinamen einschließen**  
 Schließt den Namen der Datei ein, in der das Skript gespeichert ist.  
  
 **Ordner einschließen**  
 Schließt den Pfad des Ordners ein, in dem die Skriptdatei gespeichert ist.  
  
 **Anmeldenamen einschließen**  
 Schließt den Anmeldenamen ein.  
  
 **Servernamen einschließen**  
 Schließt den Servernamen ein. Bei lokalen Verbindungen ist dies der Instanzname. Bei Remoteverbindungen ist dies der Remotecomputername und Instanzname.  
  
## <a name="see-also"></a>Siehe auch  
 [Optionen &#40;Umgebung: Schriftarten und Farben-Seite&#41;](../ssms/menu-help/options-environment-fonts-and-colors-page.md)   
 [Farbcodierung im Abfrage-Editor](../relational-databases/scripting/color-coding-in-query-editors.md)  
  
  
