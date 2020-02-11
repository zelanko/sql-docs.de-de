---
title: Optionen (Text-Editor-alle Sprachen-Seite "Allgemein") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: bf18907c-94e2-4c09-9b2b-0925ac04c627
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 385380e6e51c3b8519e7dbc6ec3d934e1ef14846
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66089250"
---
# <a name="options-text-editor---all-languages---general-page"></a>Optionen (Text-Editor – Alle Sprachen – Seite „Allgemein“)
  Mit diesem Dialogfeld können Sie die allgemeinen Bearbeitungsoptionen für alle fünf Editoren von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]festlegen. Zum Anzeigen dieser Optionen klicken Sie im Menü **Extras** auf **Optionen** . Wählen Sie den Ordner **Text-Editor** aus, erweitern Sie den Ordner **Alle Sprachen** , und klicken Sie dann auf **Allgemein**.  
  
## <a name="option-settings-by-editor"></a>Optionseinstellungen nach Editor  
 Mit den Dialogfeldern **Alle Sprachen** können Sie die Optionen für den DMX-, MDX- und SQL Server Compact-Editor festlegen. Die hier festgelegten Optionen werden auch auf den Nur-Text, den Transact-SQL- und den XML-Editor angewendet, Sie können die Optionen für diese Editoren jedoch separat festlegen, indem Sie die Unterordner für diese Sprachen erweitern und die entsprechenden Optionsseiten auswählen.  
  
> [!CAUTION]  
>  Wenn Sie in diesem Dialogfeld eine Option festlegen, für den Nur-Text-, den Transact-SQL- oder den XML-Editor jedoch eine andere Einstellung wünschen, müssen Sie die Optionen für diese Editoren festlegen, nachdem Sie die Auswahl im Dialogfeld **Alle Sprachen** übernommen haben.  
  
 Die auf dieser Seite angegebenen Optionen werden nicht von allen Editoren unterstützt. Wenn eine Option auf der Seite **Allgemein** des Dialogfelds **Optionen** nur für einige Programmiersprachen ausgewählt wurde, wird ein schattiertes Häkchen angezeigt.  
  
## <a name="statement-completion"></a>Anweisungsabschluss  
 **Elemente automatisch auflisten**  
 Popup-Listen mit verfügbaren Elementen, Eigenschaften bzw. Werten während der Eingabe in den Editor anzeigen. Wählen Sie ein Element aus der Popupliste aus, um es in Ihren Code einzufügen. Bei Aktivierung dieses Kontrollkästchens wird die Option **Erweiterte Member ausblenden** aktiviert.  
  
 **Erweiterte Member ausblenden**  
 Popuplisten für die Anweisungsvervollständigung kürzen, indem nur die am häufigsten verwendeten Member angezeigt werden. Die anderen Elemente werden aus der Liste gefiltert. Diese Option ist nicht verfügbar, wenn keine Member als erweiterte Member gekennzeichnet sind.  
  
 **Parameter Informationen**  
 Im Editor an allen verfügbaren Parametern links von der Einfügemarke die vollständige Syntax für die aktuelle Deklaration bzw. Prozedur anzeigen. Der nächste zuweisbare Parameter ist fett hervorgehoben.  
  
## <a name="settings"></a>Einstellungen  
 **Virtuellen Bereich aktivieren**  
 Kommentare immer an der gleichen Position neben dem Code einfügen. Wenn dieses Kontrollkästchen aktiviert ist, können Sie den Cursor hinter dem letzten Zeichen in der Zeile positionieren. Während der Eingabe werden Tabulatoren oder Leerzeichen automatisch hinzugefügt, um die Zeile bis zur Einfügemarke zu vervollständigen.  
  
 **Zeilenumbruch**  
 Zeigt in der nächsten Zeile den Abschnitt einer Zeile an, der über den sichtbaren horizontalen Bereich des Editors hinausgeht. Mit Aktivierung dieses Kontrollkästchens wird auch die Option **Visuelle Symbole für Zeilenumbruch anzeigen** aktiviert.  
  
 **Visuelle Symbole für Zeilenumbruch anzeigen**  
 Zeigt an der Stelle, an der eine lange Zeile auf die nächste Zeile umbricht, einen Eingabepfeil als Markierung an.  
  
> [!NOTE]  
>  Diese Markierungspfeile werden nicht in den Code eingefügt und auch nicht gedruckt. Sie dienen lediglich als Hinweis. Diese Funktion ist nicht in allen Typen von Abfrage-Editoren verfügbar.  
  
 **Befehle zum Ausschneiden oder Kopieren bei fehlender Auswahl auf leere Zeilen anwenden**  
 Legt fest, wie sich der Editor verhalten soll, wenn Sie die Einfügemarke in eine Leerzeile setzen und auf **Kopieren** oder **Ausschneiden**klicken, ohne eine Auswahl zu treffen.  
  
 Bei aktiviertem Kontrollkästchen wird die Leerzeile kopiert bzw. ausgeschnitten. Wenn Sie anschließend auf **Einfügen**klicken, wird die Leerzeile eingefügt.  
  
 Bei deaktiviertem Kontrollkästchen werden keine Leerzeilen kopiert oder ausgeschnitten. Wenn Sie nun auf **Einfügen**klicken, wird der zuletzt kopierte Inhalt eingefügt. Wenn Sie zuvor nichts kopiert haben, wird kein Inhalt eingefügt.  
  
 Bei nicht leeren Zeilen hat diese Einstellung keine Auswirkungen auf die Befehle **Kopieren** und **Ausschneiden** . Wenn nichts ausgewählt ist, wird die gesamte Zeile kopiert oder ausgeschnitten. Wenn Sie dann auf **Einfügen**klicken, wird die gesamte Textzeile einschließlich des Zeichens am Zeilenende eingefügt.  
  
## <a name="display"></a>Anzeige  
 **Zeilennummern**  
 Zeigt für jede Codezeile eine Zeilennummer an.  
  
> [!NOTE]  
>  Die Zeilennummern werden nicht in den Code eingefügt und auch nicht gedruckt. Sie dienen lediglich als Hinweis.  
  
 **Einfaches Klicken für URLs aktivieren**  
 Bei Auswahl dieser Option nimmt der Cursor die Form einer zeigenden Hand an, wenn er im Editor über eine URL bewegt wird. Sie können auf die URL klicken, um die angegebene Seite im Webbrowser anzuzeigen.  
  
 **Navigationsleiste**  
 Eine Navigationsleiste am oberen Rand des Code-Editors anzeigen. In den Dropdownlisten **Objekte** und **Prozeduren** können Sie ein bestimmtes Objekt in Ihrem Code auswählen, eine Auswahl aus den zugehörigen Prozeduren treffen und eine Instanz der ausgewählten Prozedur einfügen. Die Navigationsleiste ist nicht für alle Codetypen verfügbar.  
  
  
