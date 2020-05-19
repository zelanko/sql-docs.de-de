---
title: Abfrage- und Text-Editoren
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio]
- Code Editor [SQL Server Management Studio], about Query Editor
- Query Editor [SQL Server Management Studio], full screen mode
- Query Editor [Database Engine], templates
- full screen mode [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], templates
- writing scripts
- modifying scripts
- SQL Server Management Studio [SQL Server], query editor
- Query Editor [SQL Server Management Studio], about Query Editor
- writing queries
- SQL Server Management Studio [SQL Server], editor
- scripts [SQL Server], SQL Server Management Studio
- queries [SQL Server], SQL Server Management Studio
ms.assetid: 062051e4-4b77-4969-98ae-d2547c24ce3e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8c3e064358b58844726daa6499dc6c2ed0eeedd1
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703795"
---
# <a name="query-and-text-editors-sql-server-management-studio"></a>Abfrage- und Text-Editoren (SQL Server Management Studio)
  Mit den Editoren in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] lassen sich [!INCLUDE[tsql](../../includes/tsql-md.md)]-, MDX-, DMX- oder XML/A-Skripts interaktiv bearbeiten und testen sowie XML- oder einfache Textdateien bearbeiten. Die einzelnen Editoren werden durch einen sprachspezifischen Dienst unterstützt, der Schlüsselwörter farblich kennzeichnet und den Code auf Syntaxfehler überprüft. Der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor enthält einen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger, mit dem Sie Probleme in [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code beheben können.  
  
## <a name="sql-server-management-studio-editors"></a>Editoren in SQL Server Management Studio  
 Die vier Editoren in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] weisen die gleiche Architektur auf. Der Text-Editor implementiert die Basisfunktionalitätsstufe und kann als grundlegender Editor für Textdateien verwendet werden. Die anderen drei Editoren oder Abfrage-Editoren bieten erweiterte Funktionalität, indem sie einen Sprachdienst einschließen, der die Syntax von einer der in SQL Server unterstützten Sprachen definiert. Die Abfrage-Editoren implementieren darüber hinaus verschiedene Ebenen der Unterstützung für Editor-Funktionen, z. B. IntelliSense und Debugging. Die Abfrage-Editoren beinhalten den Abfrage-Editor der Datenbank-Engine zur Verwendung bei der Erstellung von Skripts mit Transact-SQL- und XQuery-Anweisungen, den MDX-Editor für die MDX-Sprache, den DMX-Editor für die DMX-Sprache sowie den XML/A-Editor für die XML for Analysis-Sprache.  
  
## <a name="common-components"></a>Allgemeine Komponenten  
 Alle Editoren in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] enthalten diese Komponenten:  
  
 **Codebereich**  
 Der Bereich, in den Sie die Abfragen oder den Text eingeben. In den Abfrage-Editoren enthält er die Funktionen für den Anweisungs-Generator, die für Ihre Sprache zur Verfügung stehen. Die Textbearbeitungsumgebung unterstützt Funktionen wie Suchen und Ersetzen, Massenkommentare und benutzerdefinierte Schriftarten und Farben.  
  
 Sie können Optionen festlegen, die das Verhalten des Texts im Codebereich beeinflussen in Bezug auf den Einzug, das Registerformat, Ziehen und Ablegen von Text usw. Abfragefenster können so konfiguriert werden, dass sie als Registerkarten im Dokumentfenster oder in separaten Dokumenten verfügbar sind.  
  
 **Auswahl Rand**  
 Eine Spalte mit Leerzeichen zwischen der Randindikatorleiste und dem Codetext, auf die Sie zur Auswahl von Textzeilen klicken können. Sie können den Auswahlrand ausblenden oder anzeigen.  
  
 **Horizontale und vertikale Bildlaufleisten**  
 Ermöglichen Ihnen das Durchführen eines Bildlaufes durch den Codebereich in horizontaler und vertikaler Richtung, sodass Sie Code anzeigen können, der außerhalb des angezeigten Codebereichs liegt.  
  
 **Zeilennummerierung**  
 Zeigt im Editor links vom Text oder Code Zeilennummern an. Sie können zu bestimmten Zeilennummern navigieren.  
  
 **Zeilenumbruch**  
 Zeigt lange Text- oder Codezeilen über mehrere Zeilen verteilt an. Dadurch wird der gesamte Text einer Zeile angezeigt. Der Zeilenumbruch hat keinen Einfluss auf die Darstellung des Texts, wenn er ausgeführt oder gedruckt wird. Der Zeilenumbruch wird unter **Extras**über das Dialogfeld **Optionen** auf der Seite „Text-Editor“ &gt; „Alle Sprachen“ &gt; „Allgemein“ oder auf einer bestimmten Seite des Editors aktiviert.  
  
## <a name="code-editor-components"></a>Komponenten des Code-Editors  
 Die Code-Editoren enthalten zusätzlich zu den Funktionen, die sie mit dem Text- und XML-Editor gemeinsam haben, folgende Funktionen:  
  
 **Ergebnisse**  
 In diesem Fenster können Sie die Ergebnisse einer Abfrage anzeigen. Im Fenster können die Ergebnisse in Rastern oder Text angezeigt werden. Alternativ können die Ereignisse an eine Datei weitergeleitet werden. Ergebnisraster können in Form von einzelnen Fenstern im Registerformat angezeigt werden.  
  
 **IntelliSense**  
 Zeigen Sie im Editor im Menü **Bearbeiten** auf **IntelliSense**, um die [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense-Optionen anzuzeigen.  
  
 **Farbcodierung**  
 Zeigt verschiedene Farben für die einzelnen Syntaxelementtypen an, wodurch die Lesbarkeit von komplexen Anweisungen verbessert wird.  
  
 **Codegliederung**  
 Zeigt Codegruppen mit Gliederungslinien links vom Code an. Zur einfacheren Überprüfung des Codes lassen sich Codegruppen reduzieren und erweitern.  
  
 **Vorlage**  
 Vorlagen sind Dateien, die die grundlegende Struktur der Anweisungen enthalten. Diese Struktur wird beim Erstellen von Objekten in einer Datenbank benötigt. Sie können zum Beschleunigen der Skripterstellung verwendet werden.  
  
 **Meldungen**  
 Zeigt Fehler, Warnungen und Informationsmeldungen an, die beim Ausführen eines Skripts vom Server zurückgegeben werden. Die Liste von Meldungen ändert sich nicht, bis das Skript erneut ausgeführt wird.  
  
 **Statusleiste**  
 Zeigt Systeminformationen an, die dem Abfrage-Editorfenster zugeordnet sind, beispielsweise mit welcher Instanz der Abfrage-Editor verbunden ist.  
  
## <a name="database-engine-query-editor-components"></a>Komponenten des Datenbank-Engine-Abfrage-Editors  
 Diese Komponenten sind nur in dem Datenbank-Engine-Abfrage-Editor verfügbar:  
  
 **Debugger**  
 Ermöglicht es, die Ausführung des Codes für bestimmte Anweisungen anzuhalten. Sie können dann Daten und Systeminformationen anzeigen, die bei der Suche nach Fehlern im Code helfen.  
  
 **Fehlerliste**  
 Zeigt von IntelliSense gefundene Syntax und Semantikfehler an. Die Fehlerliste ändert sich dynamisch, während Sie [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts bearbeiten.  
  
 **Grafischer Showplan**  
 Zeigt die in den Ausführungsplan einer [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung integrierten logischen Schritte an.  
  
 **Clientstatistiken**  
 Zeigt Informationen zur Ausführung der Abfrage nach Kategorien geordnet an. Wenn **Clientstatistiken einschließen** vom Menü **Abfrage** ausgewählt ist, wird das Fenster **Clientstatistiken** nach jedem Ausführen einer Abfrage angezeigt. Statistiken von aufeinander ausgeführten Abfragen werden mit Durchschnittswerten aufgelistet. Wählen Sie **Clientstatistiken zurücksetzen** im Menü **Abfrage** aus, um den Durchschnitt zurückzusetzen.  
  
 **Code Ausschnitte**  
 Vorlagen, die Sie als Ausgangspunkt beim Hinzufügen von Anweisungen in dem Datenbank-Engine-Abfrage-Editor verwenden können. Sie können die vordefinierten in SQL Server enthaltenen Ausschnitte einfügen oder eigene Ausschnitte hinzufügen.  
  
 **SQLCMD-Modus**  
 Führt [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts aus, die den vom sqlcmd-Hilfsprogramm unterstützten Satz von Befehlen enthalten. Weitere Informationen finden Sie in den [Themen zur Vorgehensweise für sqlcmd](../../database-engine/sqlcmd-how-to-topics.md).  
  
## <a name="editor-tasks"></a>Editor-Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt, wie die grundlegenden Funktionen im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor angezeigt und verwendet werden.|[Abfrage-Editor der Datenbank-Engine &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md)|  
|Beschreibt, wie die grundlegenden Funktionen im MDX-Abfrage-Editor angezeigt und verwendet werden.|[MDX-Abfrage-Editor &#40;Analysis Services – Mehrdimensionale Daten&#41;](../../analysis-services/mdx-query-editor-analysis-services-multidimensional-data.md)|  
|Beschreibt, wie die grundlegenden Funktionen im DMX-Abfrage-Editor angezeigt und verwendet werden.|[DMX-Abfrage-Editor &#40;Analysis Services &mdash; Data Mining&#41;](../../analysis-services/dmx-query-editor-analysis-services-data-mining.md)|  
|Beschreibt, wie die grundlegenden Funktionen im XML/A-Abfrage-Editor angezeigt und verwendet werden.|[XML-Editor &#40;SQL Server Management Studio&#41;](xml-editor-sql-server-management-studio.md)|  
|Beschreibt, wie Optionen für die verschiedenen Editoren konfiguriert werden, z. B. Zeilennummerierung und IntelliSense-Optionen.|[Konfigurieren von Editoren &#40;SQL Server Management Studio&#41;](configure-editors-sql-server-management-studio.md)|  
|Beschreibt die verschiedenen Methoden zum Öffnen der Editoren in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].|[Öffnen eines Editors &#40;SQL Server Management Studio&#41;](open-an-editor-sql-server-management-studio.md)|  
|Beschreibt, wie der Anzeigemodus, z. B. Zeilenumbruch, Aufteilen eines Fensters oder Registerkarten, verwaltet wird.|[Verwalten des Editors und des Ansichtsmodus](manage-the-editor-and-view-mode.md)|  
|Beschreibt, wie Formatierungsoptionen festgelegt werden, z. B. ausgeblendeter Text oder Einzug.|[Verwalten der Codeformatierung](manage-code-formatting.md)|  
|Beschreibt, wie Sie mit Funktionen wie der inkrementellen Suche oder "Gehe zu" durch den Text in einem Editor-Fenster navigieren.|[Navigieren in Code und Text](navigate-code-and-text.md)|  
|Beschreibt, wie Farbcodierungsoptionen für verschiedene Syntaxklassen festgelegt werden, wodurch das Lesen komplexer Anweisungen vereinfacht wird.|[Farbcodierung im Abfrage-Editor](color-coding-in-query-editors.md)|  
|Beschreibt, wie Codegliederung verwendet wird, um Teile komplexer Skripts auszublenden, an denen Sie derzeit nicht arbeiten.|[Codegliederung](code-outlining.md)|  
|Beschreibt, wie Text von einer Position in einem Skript gezogen und an einer anderen Position abgelegt wird.|[Verschieben von Text mit Drag und Drop](drag-and-drop-text.md)|  
|Beschreibt, wie globales Suchen und Ersetzen durchgeführt wird, z. B. beim Ändern von Spaltennamen.|[Suchen und Ersetzen](search-and-replace.md)|  
|Beschreibt, wie Lesezeichen festgelegt werden, damit wichtige Codeteile leichter wiedergefunden werden können.|[Verwalten von Lesezeichen](../native-client-ole-db-rowsets/bookmarks.md)|  
|Beschreibt, wie Skripts oder die Ergebnisse in einem Fenster oder einem Raster gedruckt werden.|[Drucken von Code und Ergebnissen](print-code-and-results.md)|  
|Beschreibt, wie die sqlcmd-Funktionen im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor verwendet werden.|[Bearbeiten von SQLCMD-Skripts mit dem Abfrage-Editor](edit-sqlcmd-scripts-with-query-editor.md)|  
|Beschreibt, wie IntelliSense-Funktionen verwendet werden, z. B. das automatische Vervollständigen von Objektnamen bei der Eingabe oder das Sicherstellen, dass Breakpoints an gültigen Positionen eingefügt werden.|[IntelliSense &#40;SQL Server Management Studio&#41;](intellisense-sql-server-management-studio.md)|  
|Beschreibt, wie Codeausschnitte im [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor verwendet werden. Ausschnitte sind Vorlagen für häufig verwendete Anweisungen oder Blöcke. Sie können angepasst oder erweitert werden, um sitespezifische Ausschnitte einzuschließen.|[Transact-SQL-Codeausschnitte](transact-sql-code-snippets.md)|  
|Beschreibt, wie der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger verwendet wird, um Code in Einzelschritten auszuführen und Debuggininformationen anzuzeigen, z. B. die Werte in Variablen und Parametern.|[Transact-SQL-Debugger](transact-sql-debugger.md)|  
|Beschreibt, wie benutzerdefinierte Farben für verschiedene Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)]und diese Farben als Hintergrund der Statusleiste in [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor-Fenstern festgelegt werden.|[Statusleiste &#40;Abfrage-Editor der Datenbank-Engine&#41;](status-bar-database-engine-query-editor.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tastenkombinationen für SQL Server Management Studio](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
