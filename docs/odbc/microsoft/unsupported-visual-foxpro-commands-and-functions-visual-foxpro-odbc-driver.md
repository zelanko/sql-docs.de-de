---
title: Nicht unterstützte Visual FoxPro-Befehle und-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- FoxPro ODBC driver [ODBC], commands and functions
- functions [ODBC], Visual FoxPro
- Visual FoxPro ODBC driver [ODBC], commands and functions
- Visual FoxPro commands and functions
- FoxPro ODBC driver
ms.assetid: afdb6b7e-738d-42ca-8053-67ae50873ca6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7e5b8ed06ad9f996d644df0dfb99d15adcff86bc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307651"
---
# <a name="unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver"></a>Nicht unterstützte Visual FoxPro-Befehle und -Funktionen (Visual FoxPro-ODBC-Treiber)
In der folgenden Tabelle sind FoxPro-Befehle und Funktionen aufgeführt, die nicht vom Visual FoxPro-ODBC-Treiber unterstützt werden, sondern von Microsoft® Visual FoxPro-® unterstützt werden.  
  
 Wenn die Anwendung mit Daten interagiert, deren Regeln, Trigger, Standardwerte oder gespeicherte Prozeduren diese Visual FoxPro-Befehle oder-Funktionen aufzurufen, kann der Treiber einen Fehler generieren.  
  
## <a name="unsupported-visual-foxpro-commands-and-functions"></a>Nicht unterstützte Visual FoxPro-Befehle und-Funktionen  
  
||||  
|-|-|-|  
|#DEFINE... #undef|#If... #endif Präprozessordirektive|#IFDEF &#124; #ifndef|  
|#INCLUDE-Präprozessordirektive|:: Scope Resolution-Operator|! (Siehe Ausführen von &#124;! S|  
|? &#124;? Get-Help|??? Get-Help|Befehl \ \\&#124; \|  
|@ ... Box-Befehl|@ ... Class-Befehl|@ ... Befehl "Löschen"|  
|@ ... Befehl "Bearbeiten-Felder bearbeiten"|@ ... Befehl "ausfüllen"|@ ... Erhalten|  
|@ ... Menübefehl|@ ... Befehl zur Eingabeaufforderung|@ ... Befehl zum Beispiel|  
|@ ... Scrollbefehl|@ ... TO-Befehl||  
  
## <a name="a"></a>Ein  
  
||||  
|-|-|-|  
|Accept-Befehl|AClass ()-Funktion|Menübefehl "aktivieren"|  
|Popup Befehl aktivieren|Bildschirm Befehl aktivieren|Befehl "Fenster aktivieren"|  
|Activatecell-Methode|Klassen Befehl hinzufügen|ADIR ()-Funktion|  
|Afont ()-Funktion|Ainstance ()-Funktion|System Speicher Variable _ALIGNMENT|  
|AMEMBERS ()-Funktion|Ansigeoem ()-Funktion|Aprinters ()-Funktion|  
|Aselobj ()-Funktion|Assist-Befehl||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|Bar ()-Funktion|Barcount ()-Funktion|Barprompt ()-Funktion|  
|System Speicher Variable _BEAUTIFY|System Speicher Variable _BOX|Befehl zum Durchsuchen|  
|System Speicher Variable _BROWSER|Befehl "App erstellen"|Befehl "Build exe"|  
|Build Project-Befehl|System Speicher Variable _BUILDER||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|System Speicher Variable _CALCVALUE|System Speicher Variable _CLIPTEXT|System Speicher Variable _CONVERTER|  
|System Speicher Variable _CUROBJ|Befehl "Befehl"|Cancel-Befehl|  
|CapsLock ()-Funktion|CD-Befehl|Befehl "ändern"|  
|Chdir-Befehl|Chrsaw ()-Funktion|Befehl "Schließen"|  
|Cntbar ()-Funktion|Cntpad ()-Funktion|Col ()-Funktion|  
|Kompilierungs Befehl|Befehl "Datenbank kompilieren"|Befehl "Formular kompilieren"|  
|COMPOBJ ()-Funktion|Container Objekt|Control-Objekt|  
|Befehl "Datei kopieren"|Memo Befehl Kopieren|Create Class-Befehl|  
|Befehl "classlib erstellen"|Befehl "Farbsatz erstellen"|Create-Befehl|  
|Befehl "Verbindung erstellen"|CREATE DATABASE-Befehl|Befehl "Formular erstellen"|  
|Create from-Befehl|Befehl "Bezeichnung erstellen"|Menübefehl "erstellen"|  
|Create Project-Befehl|Create Query-Befehl|Befehl "Bericht erstellen"|  
|Bildschirm Befehl erstellen|Befehl zum Erstellen einer SQL-Ansicht|Create-Befehl-Befehl|  
|CREATE VIEW-Befehl|Funktion "up Object ()"|Cursor ()-Funktion|  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|System Speicher Variable _DBLCLICK|System Speicher Variable _DIARYDATE|DBSETPROP ()-Funktion|  
|DDE-Funktionen|Menübefehl "deaktivieren"|Popup Befehl deaktivieren|  
|Befehl "Fenster deaktivieren"|DECLARE-DLL-Befehl|DECLARE-Befehl|  
|Balken Befehl definieren|Befehl "Feld definieren"|Befehl "Klasse definieren"|  
|Menübefehl "definieren"|Befehl "Pad definieren"|Popup Befehl definieren|  
|Befehl "Fenster definieren"|Befehl "Verbindung löschen"|Befehl zum Löschen einer Datenbank|  
|Befehl "Datei löschen"|DELETE-Befehl zum Löschen|Befehl "Ansicht löschen"|  
|DIR-Befehl|Verzeichnis Befehl|Anzeige Befehl|  
|Befehl "Verbindungen anzeigen"|Befehl "Datenbank anzeigen"|Befehl "DLLs anzeigen"|  
|Befehl "Dateien anzeigen"|Befehl "Speicher anzeigen"|Befehl "Objekte anzeigen"|  
|Befehl "Befehle anzeigen"|Befehl "Status anzeigen"|Befehl "Struktur anzeigen"|  
|Befehl "Tabellen anzeigen"|Befehl "Ansichten anzeigen"|Befehl "Do Form"|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|Befehl "Bearbeiten"|Fehler Befehl||  
|Löschbefehl|Externer Befehl|Export Befehl|  
|Eject-Befehl|Befehl "Eject page"||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|System Speicher Variable _FOXDOC|System Speicher Variable _FOXGRAPH|Feof ()-Funktion|  
|Funktion "f Close ()"|Funktion "f Create ()"|Funktion "f Gets ()"|  
|Ferror ()-Funktion|Fflush ()-Funktion|Sklabel ()-Funktion|  
|Filer-Befehl|Befehl Suchen|Funktion "f Open ()"|  
|Funktion "Funktion"|FONTMETRIC ()-Funktion|Funktion "f Seek ()"|  
|F ()-Funktion|Fread ()-Funktion||  
|Funktion "f schreiben ()"|F-Size ()-Funktion||  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|System Speicher Variable _GENGRAPH|System Speicher Variable _GENMENU|System Speicher Variable _GENPD|  
|System Speicher Variable _GENSCRN|System Speicher Variable _GENXTAB|Getbar ()-Funktion|  
|GetColor ()-Funktion|GETDIR ()-Funktion|Getexpr-Befehl|  
|GetFile ()-Funktion|GetFont ()-Funktion|GetObject ()-Funktion|  
|Getpad ()-Funktion|Getpict ()-Funktion|GetPrinter ()-Funktion|  
  
## <a name="h"></a>H  
  
||||  
|-|-|-|  
|Hilfe Befehl|Menübefehl ausblenden|Popup Befehl Ausblenden|  
|Fenster Befehl Ausblenden|Home ()-Funktion||  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IMEStatus ()-Funktion|Import Befehl|Eingabe Befehl|  
|Index für Befehl|Inkey ()-Funktion|IsColor ()-Funktion|  
|Befehl Einfügen|Insmode ()-Funktion||  
|Ismouse ()-Funktion|System Speicher Variable _INDENT||  
  
## <a name="j"></a>J  
  
||||  
|-|-|-|  
|Joinbefehl|||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|Tastatur Befehl|||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|System Speicher Variable _LMARGIN|Befehl "Bezeichnung"|LastKey ()-Funktion|  
|LineNo ()-Funktion|Befehle auflisten|Befehl "Verbindungen auflisten"|  
|Befehl "Laden"|LocFile ()-Funktion||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|MCol ()-Funktion|MD-Befehl|Menü zu Befehl|  
|Memory ()-Funktion|Menübefehl|Mkdir-Befehl|  
|Menu ()-Funktion|MessageBox ()-Funktion|Verbindungs Befehl ändern|  
|Befehl "Klasse ändern"|Befehl "Befehl ändern"|Befehl "Formular ändern"|  
|Befehl zum Ändern der Datenbank|Befehl "Datei ändern"|Memo Befehl ändern|  
|Befehl "Allgemein ändern"|Befehl "Bezeichnung ändern"|Befehl "Projekt ändern"|  
|Menübefehl "ändern"|Modify PROCEDURE-Befehl|Bildschirm Befehl ändern|  
|Abfragebefehl ändern|Befehl "Bericht ändern"|Befehl "Fenster ändern"|  
|Struktur ändern (Befehl)|Befehl "Ansicht ändern"|Befehl "Fenster verschieben"|  
|Maus Befehl|Popup Befehl Verschieben|Mrow ()-Funktion|  
|Mrkbar ()-Funktion|Mrkpad ()-Funktion||  
|Mwindow ()-Funktion|Mdown ()-Funktion||  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NumLock ()-Funktion|||  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|Objnum ()-Funktion|Objto Client ()-Funktion|ON-Bar-Befehl|  
|Oemto ANSI ()-Funktion|Befehl "on aplabout"|Menübefehl "beenden"|  
|Befehl bei Escapezeichen|Befehl beim Beenden der Leiste|ON Key =-Befehl|  
|ON Exit Pad-Befehl|Befehl "on Exit Popup"|ON-Pad-Befehl|  
|Befehl "Schlüssel Bezeichnung"|Auf dem Befehl "machelp"|Befehl auf der Auswahl Leiste|  
|On Page-Befehl|ON ReadError-Befehl|Popup Befehl bei Auswahl|  
|Befehl im Menü "Auswahl"|Befehl "on Selection Pad"||  
|Befehl zum Herunterfahren|ObjVar ()-Funktion||  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|System Speicher Variable _PADVANCE|System Speicher Variable _PAGENO|System Speicher Variable _PBPAGE|  
|System Speicher Variable _PCOLNO|System Speicher Variable _PCOPIES|System Speicher Variable _PDRIVER|  
|System Speicher Variable _PDSETUP|System Speicher Variable _PECODE|System Speicher Variable _PEJECT|  
|System Speicher Variable _PEPAGE|System Speicher Variable _PLENGTH|System Speicher Variable _PLINENO|  
|System Speicher Variable _PLOFFSET|System Speicher Variable _PPITCH|System Speicher Variable _PQUALITY|  
|System Speicher Variable _PRETEXT|System Speicher Variable _PSCODE|System Speicher Variable _PSPACING|  
|System Speicher Variable _PWAIT|Pack-Datenbankbefehl|Pad ()-Funktion|  
|PCOL ()-Funktion|Pemstatus ()-Funktion|Befehl "wiedergeben"|  
|Pop-Schlüssel Befehl|Pop-Menübefehl|Popup Befehl Pop|  
|Popup ()-Funktion|PrintJob... Befehl "endprintjob"|PRINTSTATUS ()-Funktion|  
|Prmbar ()-Funktion|Prmpad ()-Funktion|Prompt ()-Funktion|  
|Prow ()-Funktion|Prtinfo ()-Funktion|Befehl "Push Key"|  
|Menübefehl "Push"|Befehl "Push Popup"|PutFile ()-Funktion|  
  
## <a name="q"></a>Q  
  
||||  
|-|-|-|  
|Befehl "beenden"|||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|System Speicher Variable _RMARGIN|RD-Befehl|Read Key ()-Funktion|  
|Lesebefehl|Menübefehl lesen|Befehl der releaseleiste|  
|Refresh ()-Funktion|REINDEX-Befehl|Release Library-Befehl|  
|Release classlib-Befehl|Releasebefehl|Release Pad-Befehl|  
|Befehl für releasemenüs|Releasemodulbefehl|Befehl "Windows veröffentlichen"|  
|Befehl "Popups freigeben"|Befehl "Release Procedure"|Befehl Umbenennen|  
|Befehl "Klasse entfernen"|Class-Befehl Umbenennen|Befehl "View"|  
|Verbindungs Befehl Umbenennen|Befehl Tabellen umbenennen|Restore from-Befehl|  
|Bericht Befehl|Requery ()-Funktion|Befehl "Wiederherstellen"|  
|Restore Makros-Befehl|Befehl zum Wiederherstellen|RGBSCHEME ()-Funktion|  
|Resume-Befehl|RGB ()-Funktion|Führen Sie &#124; aus. Get-Help|  
|Rmdir-Befehl|Row ()-Funktion||  
|Befehl "RunScript"|Rdlevel ()-Funktion||  
  
## <a name="s"></a>E  
  
||||  
|-|-|-|  
|Befehl zum Speichern von Makros|Bildschirm Befehl speichern|In Befehl speichern|  
|Windows-Befehl speichern|Scheme ()-Funktion|Scols ()-Funktion|  
|Scrollbefehl|System Speicher Variable _SCREEN|SET-Befehl|  
|Alternativen Befehl festlegen|SET ANSI-Befehl|Befehl "aplabout" festlegen|  
|Befehl "Autosave" festlegen|Befehl "Glocken festlegen"|Befehl "blink festlegen"|  
|Befehl "Rahmen festlegen"|Befehl "brstatus" festlegen|Befehl "classlib festlegen"|  
|Befehl "Löschen" festlegen|Befehl "Uhr festlegen"|Farbe des Befehls festlegen|  
|Befehl "Schema Farbe festlegen"|Befehl "Farbsatz festlegen"|Farbe auf Befehl festlegen|  
|Kompatiblen Befehl festlegen|Befehl "bestätigen" festlegen|Konsolen Befehl festlegen|  
|Festlegen von cpcompile|Festlegen von cpdialog|Befehl "Währung festlegen"|  
|Befehl "Cursor festlegen"|Set DataSession-Befehl|Befehl "Debug festlegen"|  
|Set decimals-Befehl|Set Delimiters-Befehl|Befehl zum Festlegen der Entwicklung|  
|Geräte Befehl festlegen|Anzeige Befehl festlegen|Befehl "dohistory festlegen"|  
|Befehl "Echo festlegen"|Befehl "Escape" festlegen|Befehl "Format festlegen"|  
|Set Function-Befehl|Befehl "Befehle festlegen"|Befehl "Hilfe festlegen"|  
|Befehl "HELPFILTER festlegen"|Befehl "Intensität festlegen"|Befehl "Schlüssel festlegen"|  
|Befehl "keycomp festlegen"|Befehl "logerrors festlegen"|Befehl "macdesktop festlegen"|  
|Befehl "machelp festlegen"|Befehl "Mackey festlegen"|Befehl "Rand festlegen"|  
|Markierung des Befehls festlegen|Markierung auf Befehl festlegen|Befehl "memowidth festlegen"|  
|Befehl "Nachricht festlegen"|Befehl "Maus festlegen"|Set Odometer-Befehl|  
|OLEObject-Befehl festlegen|Befehl "Palette festlegen"|Festlegen des pdsetup-Befehls|  
|Befehl "Punkt festlegen"|Drucker Befehl festlegen|Befehl "Read border festlegen"|  
|Befehl "Aktualisieren" festlegen|Ressourcen Befehl festlegen|Befehl "Sicherheit festlegen"|  
|Befehl zum Festlegen der Anzeige|Befehl "Sekunden festlegen"|Befehl "Separator festlegen"|  
|Befehl "Shadows" festlegen|Befehl zum Überspringen des Befehls festlegen|Befehl "Bereich festlegen"|  
|Befehl "Status festlegen"|Befehl "Status Leiste festlegen"|Befehl "Schritt festlegen"|  
|Befehl "kurz festlegen"|Befehl "sysformats festlegen"|Befehl "sysmenu festlegen"|  
|Talk-Befehl festlegen|TEXTMERGE-Befehl festlegen|TEXTMERGE-Trennzeichen festlegen (Befehl)|  
|Befehl "Thema festlegen"|Befehl "Topic-ID festlegen"|Befehl "trbetween" festlegen|  
|Befehl "typeahead" festlegen|Befehl "Ansicht festlegen"|Fenster des Memo Befehls festlegen|  
|Set xcmdfile-Befehl|System Speicher Variable _SHELL|Befehl "Get" anzeigen|  
|Befehl "Befehle anzeigen"|Menübefehl anzeigen|Befehl "Objekt anzeigen"|  
|Popup Befehl anzeigen|Befehl "Fenster anzeigen"|Popup Befehl "Größe"|  
|Befehl "Größen Fenster"|Skpbar ()-Funktion|Skppad ()-Funktion|  
|SOUNDEX ()-Funktion|System Speicher Variable _SPELLCHK|SQL-Funktionen|  
|Srows ()-Funktion|System Speicher Variable _STARTUP|Suspend-Befehl|  
|Sys ()-Funktionen mit Ausnahme von sys (2011)|Sysmetric ()-Funktion||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|System Speicher Variable _TABS|Text... ENDTEXT-Befehl|TxtWidth ()-Funktion|  
|Transform ()-Funktion|System Speicher Variable _TRANSPORT||  
|Befehl "Type"|System Speicher Variable _THROTTLE||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|Aktualisierte ()-Funktion|Befehl verwenden||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|VALIDATE DATABASE-Befehl|Varread ()-Funktion|Version ()-Funktion|  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|System Speicher Variable _WINDOWS|System Speicher Variable _WIZARD|Wchild ()-Funktion|  
|Wait-Befehl|Wborder ()-Funktion|Wfont ()-Funktion|  
|Wcols ()-Funktion|Wexist ()-Funktion|Wlrow ()-Funktion|  
|Mit... Befehl "EndWith"|Wlast ()-Funktion|WONTOP ()-Funktion|  
|Wmaximum ()-Funktion|Wlcol ()-Funktion|Wread ()-Funktion|  
|Woutput ()-Funktion|Wminimal ()-Funktion|Wvisible ()-Funktion|  
|Wparent ()-Funktion|Wtitle ()-Funktion||  
|Wrows ()-Funktion|System Speicher Variable _WRAP||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|Befehl "Zoom Fenster"|||
