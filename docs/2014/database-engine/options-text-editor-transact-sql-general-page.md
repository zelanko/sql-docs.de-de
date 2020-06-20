---
title: Optionen (Text-Editor-Transact-SQL-Seite "Allgemein") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.SQL.General
dev_langs:
- TSQL
ms.assetid: 7021ecb7-8fb5-4d8c-b984-3d34fcde8be2
author: rothja
ms.author: jroth
ms.openlocfilehash: 513fe574fa19d743a69b7c92943d04e44d7f3334
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84929782"
---
# <a name="options-text-editor---transact-sql--general-page"></a>Optionen (Text-Editor-Transact-SQL-Seite "Allgemein")
  Mit den Optionen im Dialogfeld **Allgemein** können Sie das allgemeine Bearbeitungsverhalten des [!INCLUDE[ssDE](../includes/ssde-md.md)] -Abfrageeditors beim Bearbeiten von [!INCLUDE[tsql](../includes/tsql-md.md)] -Skripts ändern. Sie können diese Einstellungen anzeigen, indem Sie im Menü **Extras** auf **Optionen** klicken. Erweitern Sie dann den Unterordner **Transact-SQL**, und klicken Sie auf **Allgemein**.  
  
## <a name="setting-options-in-multiple-locations"></a>Festlegen der Optionen an mehreren Stellen  
 Die Optionen für den [!INCLUDE[ssDE](../includes/ssde-md.md)] -Abfrageeditor können auch unter **Alle Sprachen** im Dialogfeld Allgemein eingestellt werden. Wenn Sie die Dialogfelder **alle Sprachen** verwenden, um verschiedene Optionen für die anderen [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Editoren festzulegen, z. b. den DMX-oder MDX-Editoren, müssen Sie die Abfrage-Editor- [!INCLUDE[ssDE](../includes/ssde-md.md)] Optionen mithilfe dieses Dialog Felds zurücksetzen  
  
## <a name="statement-completion"></a>Anweisungsabschluss  
 **Elemente automatisch auflisten**  
 Wenn dieses Kontrollkästchen aktiviert ist, werden während der Eingabe im Editor Datenbank- und Schemaobjekte, Spalten, Tabellenwertfunktionen oder Funktionen angezeigt. Wählen Sie ein Element aus der Popupliste aus, um es in Ihren Code einzufügen.  
  
 **Erweiterte Member ausblenden**  
 Dieses Kontrollkästchen ist nicht verfügbar.  
  
 **Parameterinformationen**  
 Wenn dieses Kontrollkästchen aktiviert ist, werden Parameterinformationen für eine gespeicherte Prozedur oder Funktion angezeigt, die sich unmittelbar links von der Einfügemarke (Cursor) befindet. Die Informationen umfassen eine Liste der verfügbaren Parameter mit ihren Namen und Datentypen.  
  
## <a name="settings"></a>Einstellungen  
 **Virtuellen Bereich aktivieren**  
 Wenn dieses Kontrollkästchen aktiviert ist, können Sie auf eine beliebige Stelle nach dem Ende einer Codezeile klicken und mit der Eingabe beginnen. Aktivieren Sie dieses Kontrollkästchen, wenn Kommentare immer an der gleichen Position neben dem Code eingefügt werden sollen. Durch Aktivieren dieses Kontrollkästchens wird das Kontrollkästchen **Zeilenumbruch** deaktiviert.  
  
 **Zeilenumbruch**  
 Wenn dieses Kontrollkästchen aktiviert ist, wird jeder Teil einer Zeile, der über den anzeigbaren Bereich des Editors hinausragt, automatisch auf der nächsten Zeile angezeigt. Mit Aktivierung dieses Kontrollkästchens wird auch das Kontrollkästchen **Visuelle Symbole für Zeilenumbruch anzeigen** aktiviert und das Kontrollkästchen **Virtuellen Bereich aktivieren** deaktiviert.  
  
 **Visuelle Symbole für Zeilenumbruch anzeigen**  
 Wenn dieses Kontrollkästchen aktiviert ist, wird an den Stellen, an denen eine lange Zeile auf die nächste Zeile umbricht, ein Eingabepfeil als Markierung angezeigt.  
  
 **Befehle zum Ausschneiden oder Kopieren bei fehlender Auswahl auf leere Zeilen anwenden**  
 Legt fest, wie sich der Editor verhalten soll, wenn Sie die Einfügemarke in eine Leerzeile setzen und auf **Kopieren** oder **Ausschneiden**klicken, ohne eine Auswahl zu treffen.  
  
 Bei aktiviertem Kontrollkästchen wird die Leerzeile kopiert bzw. ausgeschnitten. Wenn Sie anschließend auf **Einfügen**klicken, wird die Leerzeile eingefügt.  
  
 Bei deaktiviertem Kontrollkästchen werden keine Leerzeilen kopiert oder ausgeschnitten. Wenn Sie nun auf **Einfügen**klicken, wird der zuletzt kopierte Inhalt eingefügt. Wenn Sie zuvor nichts kopiert haben, wird kein Inhalt eingefügt.  
  
 Bei nicht leeren Zeilen hat diese Einstellung keine Auswirkungen auf die Befehle **Kopieren** und **Ausschneiden** . Wenn nichts ausgewählt ist, wird die gesamte Zeile kopiert oder ausgeschnitten. Wenn Sie dann auf **Einfügen**klicken, wird die gesamte Textzeile einschließlich des Zeichens am Zeilenende eingefügt.  
  
## <a name="display"></a>Anzeige  
 **Zeilennummern**  
 Wenn dieses Kontrollkästchen aktiviert ist, wird neben jeder Codezeile eine Zeilennummer angezeigt.  
  
> [!NOTE]  
>  Die Zeilennummern werden nicht in den Code eingefügt und auch nicht gedruckt. Sie dienen lediglich als Hinweis.  
  
 **Einfaches Klicken für URLs aktivieren**  
 Wenn dieses Kontrollkästchen aktiviert ist, nimmt der Cursor die Form einer zeigenden Hand an, wenn er im Editor über eine URL bewegt wird. Sie können auf die URL klicken, um die angegebene Seite im Webbrowser anzuzeigen.  
  
 **Navigationsleiste**  
 Dieses Kontrollkästchen ist nicht verfügbar.  
  
  
