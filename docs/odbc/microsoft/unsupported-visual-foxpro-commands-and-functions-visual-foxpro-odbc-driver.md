---
title: Nicht unterstützte Visual FoxPro-Befehle und Funktionen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6b69c8bf15b4d56872c4030725638e4b61571e6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633370"
---
# <a name="unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver"></a>Nicht unterstützte Visual FoxPro-Befehle und -Funktionen (Visual FoxPro-ODBC-Treiber)
Die folgende Tabelle enthält die FoxPro-Befehle und Funktionen, die von Microsoft® Visual FoxPro unterstützt werden, werden von der Visual FoxPro-ODBC-Treiber nicht unterstützt.  
  
 Wenn Ihre Anwendung mit Daten, deren Regeln, Trigger, Standardwerte interagiert oder gespeicherte Prozeduren, diese Visual FoxPro-Befehle oder Funktionen aufrufen, kann der Treiber ein Fehler generiert.  
  
## <a name="unsupported-visual-foxpro-commands-and-functions"></a>Nicht unterstützte Visual FoxPro-Befehle und Funktionen  
  
||||  
|-|-|-|  
|#DEFINE #UNDEF|#IF... Präprozessor #ENDIF-Anweisung|#IFDEF &#124; #IFNDEF|  
|# Präprozessor INCLUDEDIREKTIVE|:: Bereichsauflösungsoperator|! Befehl (finden Sie unter Ausführung &#124; ! -Befehl)|  
|? &#124; ?? Befehl|??? Befehl|\ &#124; \\\ Befehl|  
|@ ... BOX-Befehl|@ ... CLASS-Befehl|@ ... Befehl zum Löschen|  
|@ ... Bearbeiten: Felder Befehl Bearbeiten|@ ... Geben Sie Befehl|@ ... GET|  
|@ ... KONTEXTMENÜBEFEHL von ""|@ ... PROMPT-Befehl|@ ... Angenommen, Befehl|  
|@ ... Bildlauf-Befehl|@ ... -Befehl||  
  
## <a name="a"></a>A  
  
||||  
|-|-|-|  
|Befehl akzeptieren|ACLASS ()-Funktion|KONTEXTMENÜBEFEHL von "" aktivieren|  
|POPUP-Befehl aktivieren|Bildschirm-Befehl aktivieren|Aktivieren des Befehls "Fenster"|  
|ActivateCell-Methode|Befehl "Klasse hinzufügen"|ADIR ()-Funktion|  
|AFONT ()-Funktion|AINSTANCE ()-Funktion|Arbeitsspeicher-Systemvariable _ALIGNMENT|  
|AMEMBERS ()-Funktion|ANSITOOEM ()-Funktion|APRINTERS ()-Funktion|  
|ASELOBJ ()-Funktion|Hilfe-Befehl||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|BALKEN ()-Funktion|BARCOUNT ()-Funktion|BARPROMPT( ) Function|  
|Arbeitsspeicher-Systemvariable _BEAUTIFY|Arbeitsspeicher-Systemvariable _BOX|Befehl Suchen|  
|Arbeitsspeicher-Systemvariable _BROWSER|Erstellen von APP-Befehl|Erstellen Sie die EXE-Befehl|  
|BUILD Projektbefehl|Arbeitsspeicher-Systemvariable _BUILDER||  
  
## <a name="c"></a>c  
  
||||  
|-|-|-|  
|Arbeitsspeicher-Systemvariable _CALCVALUE|Arbeitsspeicher-Systemvariable _CLIPTEXT|Arbeitsspeicher-Systemvariable _CONVERTER|  
|Arbeitsspeicher-Systemvariable _CUROBJ|Aufrufbefehl für|CANCEL-Befehl|  
|CAPSLOCK ()-Funktion|Befehl "CD"|Befehl zum Ändern|  
|CHDIR-Befehl|CHRSAW ()-Funktion|Schließen MEMO-Befehl|  
|CNTBAR ()-Funktion|CNTPAD( ) Function|Spalte ()-Funktion|  
|Kompilieren Sie Befehl|Kompilieren Sie die DATABASE-Befehl|Kompilieren Sie die FORM-Befehl|  
|COMPOBJ ()-Funktion|Container-Objekt|Control-Objekt|  
|Befehl "Datei kopieren"|Kopieren Sie MEMO-Befehl|Erstellen Sie den Befehl Klasse|  
|Erstellen Sie CLASSLIB-Befehl|Erstellen Sie die Farbe SET-Befehl|CREATE-Befehl|  
|CONNECTION-Befehl erstellen|Erstellen Sie die DATABASE-Befehl|Formular erstellen|  
|VOM Befehl erstellen|Erstellen von LABEL-Befehl|KONTEXTMENÜBEFEHL von "" erstellen|  
|Befehl "Projekt" erstellen|Abfragebefehl zu erstellen|Bericht-Befehl erstellen|  
|Bildschirm-Befehl erstellen|SQL-Ansicht-Befehl erstellen|Erstellen von TRIGGER-Befehl|  
|Erstellen von VIEW (Befehl)|CREATEOBJECT ()-Funktion|CURDIR ()-Funktion|  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|Arbeitsspeicher-Systemvariable _DBLCLICK|Arbeitsspeicher-Systemvariable _DIARYDATE|DBSETPROP ()-Funktion|  
|DDE-Funktionen|KONTEXTMENÜBEFEHL von "" deaktivieren|Deaktivieren Sie POPUP-Befehl|  
|Deaktivieren des Befehls "Fenster"|DECLARE - DLL-Befehl|Deklarieren Sie Befehl|  
|LEISTE den Befehl definieren|Definieren Sie im Feld Befehl|Definieren Sie den Befehl Klasse|  
|KONTEXTMENÜBEFEHL von "" definieren|Definieren von PAD-Befehl|Definieren der POPUP-Befehl|  
|Definieren des Befehls "Fenster"|Verbindungsbefehl "löschen"|Datenbankbefehl "löschen"|  
|Dateibefehl "löschen"|TRIGGER-Befehl "löschen"|Ansichtsbefehl "löschen"|  
|Befehl "DIR"|DIRECTORY-Befehl|Anzeigebefehl|  
|Anzeige VERBINDUNGEN-Befehl|DATABASE-Anzeigebefehl|Anzeige DLLS-Befehl|  
|FILES-Anzeigebefehl|Befehl "Arbeitsspeicher" anzeigen|Objekte-Anzeigebefehl|  
|Die PROZEDUREN Anzeigebefehl|Anzeige-Statusbefehls|Befehl der Anzeige-Struktur|  
|Tabellen-Anzeigebefehl|Ansichten-Anzeigebefehl|Befehl bilden|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|BEARBEITUNGSBEFEHL|Fehler-Befehl||  
|Befehl löschen|Externer Befehl|EXPORT-Befehl|  
|Befehl Auswerfen|Befehl "Seite" Auswerfen||  
  
## <a name="f"></a>V  
  
||||  
|-|-|-|  
|Arbeitsspeicher-Systemvariable _FOXDOC|Arbeitsspeicher-Systemvariable _FOXGRAPH|FEOF ()-Funktion|  
|FCLOSE ()-Funktion|FCREATE ()-Funktion|FGETS ()-Funktion|  
|FERROR ()-Funktion|FFLUSH ()-Funktion|FKLABEL ()-Funktion|  
|Filter-Befehl|Befehl "Suchen"|FOPEN ()-Funktion|  
|FKMAX( ) Function|FONTMETRIC ()-Funktion|FSEEK ()-Funktion|  
|FPUTS ()-Funktion|FREAD( ) Function||  
|FWRITE ()-Funktion|FCHSIZE ()-Funktion||  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|Arbeitsspeicher-Systemvariable _GENGRAPH|Arbeitsspeicher-Systemvariable _GENMENU|Arbeitsspeicher-Systemvariable _GENPD|  
|Arbeitsspeicher-Systemvariable _GENSCRN|Arbeitsspeicher-Systemvariable _GENXTAB|GETBAR ()-Funktion|  
|GETCOLOR ()-Funktion|GETDIR ()-Funktion|GETEXPR-Befehl|  
|GETFILE ()-Funktion|GETFONT ()-Funktion|GETOBJECT-()-Funktion|  
|GETPAD ()-Funktion|GETPICT ()-Funktion|GETPRINTER ()-Funktion|  
  
## <a name="h"></a>H  
  
||||  
|-|-|-|  
|Befehl "Hilfe"|KONTEXTMENÜBEFEHL von "" ausblenden|Ausblenden der POPUP-Befehl|  
|Ausblenden des Befehls "Fenster"|HOME ()-Funktion||  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IMESTATUS ()-Funktion|IMPORT-Befehl|Eingabe-Befehl|  
|INDEX für den Befehl|INKEY( ) Function|ISCOLOR ()-Funktion|  
|Einfügen (Befehl)|INSMODE ()-Funktion||  
|ISMOUSE ()-Funktion|Arbeitsspeicher-Systemvariable _INDENT||  
  
## <a name="j"></a>J  
  
||||  
|-|-|-|  
|JOIN-Befehl|||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|Tastenkombination|||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|Arbeitsspeicher-Systemvariable _LMARGIN|LABEL-Befehl|LASTKEY( ) Function|  
|"LineNo" ()-Funktion|Auflisten der Befehle|VERBINDUNGEN auflisten (Befehl)|  
|-Befehl|LocFile ABGELEGT ()-Funktion||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|MCOL ()-Funktion|MD-Befehl|Menü ", Befehl|  
|Arbeitsspeicher ()-Funktion|KONTEXTMENÜBEFEHL von ""|MKDIR-Befehl|  
|Menü ()-Funktion|MESSAGEBOX ()-Funktion|Ändern der CONNECTION-Befehl|  
|Ändern Sie den Befehl Klasse|Ändern der COMMAND-Befehl|Ändern Sie FORM-Befehl|  
|Ändern Sie die DATABASE-Befehl|Befehl "FILE" ändern|Ändern Sie MEMO-Befehl|  
|Ändern Sie allgemeine-Befehl|Ändern Sie Bezeichnung-Befehl|Ändern Sie die Projekt-Befehl|  
|KONTEXTMENÜBEFEHL von "" ändern|Ändern der PROCEDURE-Befehl|Ändern der Bildschirm-Befehl|  
|Ändern der Abfragebefehl|Ändern Sie BERICHTSSERVER-Befehl|Ändern Sie im Fenster-Befehl|  
|Ändern Sie die Struktur-Befehl|Ändern von VIEW (Befehl)|Verschieben des Befehls "Fenster"|  
|Der Befehl für Maus|Verschieben Sie POPUP-Befehl|MROW ()-Funktion|  
|MRKBAR ()-Funktion|MRKPAD( ) Function||  
|MWINDOW ()-Funktion|MDOWN ()-Funktion||  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NUM-Taste ()-Funktion|||  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|OBJNUM ()-Funktion|OBJTOCLIENT ()-Funktion|AUF MENÜLEISTE den Befehl|  
|OEMTOANSI ()-Funktion|AUF APLABOUT-Befehl|KONTEXTMENÜBEFEHL von auf "Beenden"|  
|AUF der Escapebefehl|AUF der LEISTE-Befehl "Beenden"|Schlüssel =-Befehl|  
|ON EXIT-PAD-Befehl|ON EXIT-POPUP-Befehl|ON-PAD-Befehl|  
|ZUM Befehl "Beschriftung"|AUF MACHELP-Befehl|ZUM LEISTE-Befehl "Auswahl"|  
|AUF der Seite "-Befehl|AUF READERROR-Befehl|AUF Auswahl POPUP-Befehl|  
|AUF den Menübefehl für die Auswahl|ZUM PAD-Befehl "Auswahl"||  
|AUF den Befehl "Herunterfahren"|OBJVAR ()-Funktion||  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|Arbeitsspeicher-Systemvariable _PADVANCE|Arbeitsspeicher-Systemvariable _PAGENO|Arbeitsspeicher-Systemvariable _PBPAGE|  
|Arbeitsspeicher-Systemvariable _PCOLNO|Arbeitsspeicher-Systemvariable _PCOPIES|Arbeitsspeicher-Systemvariable _PDRIVER|  
|Arbeitsspeicher-Systemvariable _PDSETUP|Arbeitsspeicher-Systemvariable _PECODE|Arbeitsspeicher-Systemvariable _PEJECT|  
|Arbeitsspeicher-Systemvariable _PEPAGE|Arbeitsspeicher-Systemvariable _PLENGTH|Arbeitsspeicher-Systemvariable _PLINENO|  
|Arbeitsspeicher-Systemvariable _PLOFFSET|Arbeitsspeicher-Systemvariable _PPITCH|Arbeitsspeicher-Systemvariable _PQUALITY|  
|Arbeitsspeicher-Systemvariable _PRETEXT|Arbeitsspeicher-Systemvariable _PSCODE|Arbeitsspeicher-Systemvariable _PSPACING|  
|Arbeitsspeicher-Systemvariable _PWAIT|PACK-DATABASE-Befehl|PAD( ) Function|  
|PCOL ()-Funktion|PEMSTATUS ()-Funktion|MAKRO-Befehl "WIEDERGEBEN"|  
|POPUPFENSTER Tastaturbefehl|POP Menübefehl|POP-POPUP-Befehl|  
|Popups ()-Funktion|PRINTJOB... ENDPRINTJOB-Befehl|PRINTSTATUS ()-Funktion|  
|PRMBAR ()-Funktion|PRMPAD ()-Funktion|PROMPT ()-Funktion|  
|PROW ()-Funktion|PRTINFO ()-Funktion|WICHTIGE PUSH-Befehl|  
|KONTEXTMENÜBEFEHL von "PUSH"|PUSH-POPUP-Befehl|PUTFILE-()-Funktion|  
  
## <a name="q"></a>Q  
  
||||  
|-|-|-|  
|Befehl "Beenden"|||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|Arbeitsspeicher-Systemvariable _RMARGIN|Remotedesktop-Befehl|READKEY( ) Function|  
|Befehl lesen|KONTEXTMENÜBEFEHL von "" Lesen|RELEASE-BALKEN-Befehl|  
|Refresh()-Funktion|NEUINDIZIEREN-Befehl|RELEASE-LIBRARY-Befehl|  
|Version CLASSLIB-Befehl|RELEASE-Befehl|RELEASE-PAD-Befehl|  
|RELEASE-MENÜS-Befehl|RELEASE-MODULE-Befehl|Version von WINDOWS-Befehl|  
|RELEASE-POPUPS-Befehl|RELEASE-PROCEDURE-Befehl|Umbenennen eines Menübefehls|  
|Befehl "Klasse" entfernen|Benennen Sie den Befehl Klasse|Benennen Sie VIEW (Befehl)|  
|Verbindungsbefehl umbenennen|Benennen Sie die TABLE-Befehl|Wiederherstellen von Befehl|  
|Bericht-Befehl|REQUERY ()-Funktion|Fenster-Befehl "Wiederherstellen"|  
|MAKROS-Befehl "Wiederherstellen"|Bildschirm-Befehl "Wiederherstellen"|RGBSCHEME( ) Function|  
|Befehl "fortsetzen"|RGB ()-Funktion|RUN &#124; ! Befehl|  
|RMDIR-Befehl|Zeile ()-Funktion||  
|RUNSCRIPT-Befehl|RDLEVEL ()-Funktion||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|Speichern Sie den Befehl MAKROS|Speichern Sie die Bildschirm-Befehl|Befehl Speichern|  
|Speichern Sie die WINDOWS-Befehl|Schema ()-Funktion|SCOLS ()-Funktion|  
|Bildlauf-Befehl|Arbeitsspeicher-Systemvariable Entwurfsfeatures|SET-Befehl|  
|Alternative SET-Befehl|SET ANSI-Befehl|SET-APLABOUT-Befehl|  
|SET-AUTOSAVE-Befehl|SET-BELL-Befehl|SET-BLINK-Befehl|  
|SET-Rahmen-Befehl|Einfacher BRSTATUS-Befehl SET|SET-CLASSLIB-Befehl|  
|Befehl zum Löschen festlegen|SET-Uhr-Befehl|Farbe des SET-Befehls|  
|SET-Farbe des Schema-Befehl|SET-COLOR-SET-Befehls|Befehl SET Farbe|  
|SET-Befehls-kompatibel|SET-CONFIRM-Befehl|SET-Konsolenbefehl|  
|SET-CPCOMPILE|SET-CPDIALOG|SET-CURRENCY-Befehl|  
|SET CURSOR (Befehl)|SET-DATASESSION-Befehl|SET-DEBUG-Befehl|  
|Die DEZIMALSTELLEN Befehl SET|SET-TRENNZEICHEN-Befehl|SET-DEVELOPMENT-Befehl|  
|SET-DEVICE-Befehl|SET-Anzeige-Befehl|SET-DOHISTORY-Befehl|  
|SET ECHO-Befehl|SET-ESCAPE-Befehl|Befehl SET-FORMAT|  
|Befehl der SET-Funktion|SET-Überschriften (Befehl)|SET-HELP-Befehl|  
|SET-HELPFILTER-Befehl|SET-INTENSITÄT-Befehl|SET-KEY-Befehls|  
|SET-KEYCOMP-Befehl|SET-LOGERRORS-Befehl|SET-MACDESKTOP-Befehl|  
|SET-MACHELP-Befehl|SET-MACKEY-Befehl|SET-MARGIN-Befehl|  
|Markieren Sie SET-Befehls|Festlegen Sie Markierung Befehl|SET-MEMOWIDTH-Befehl|  
|Befehl SET-Nachricht|SET-Maus-Befehl|SET-KILOMETERSTAND-Befehl|  
|OLEOBJECT-Befehl SET|SET-PALETTE (Befehl)|SET-PDSETUP-Befehl|  
|SET-Punkt-Befehl|SET-PRINTER-Befehl|SET-READBORDER-Befehl|  
|SET-REFRESH-Befehl|Befehl SET-Ressource|SET-Sicherheit-Befehl|  
|SET-ANZEIGETAFEL-Befehl|SET-Sekunden-Befehl|SET-TRENNZEICHEN-Befehl|  
|Zeichnen von SCHATTEN-Befehl SET|Überspringen der SET-Befehls|SET-SPACE-Befehl|  
|Befehl SET-STATUS|Festlegen der Statusleiste (Befehl)|SET-Schritt-Befehl|  
|KURZNOTIZ SET-Befehl|SET-SYSFORMATS-Befehl|SET-SYSMENU-Befehl|  
|SET-TALK-Befehl|SET-TEXTMERGE-Befehl|SET TEXTMERGE TRENNZEICHEN-Befehl|  
|Befehl SET-TOPIC|Befehl SET Thema-ID|SET-TRBETWEEN-Befehl|  
|SET-TYPEAHEAD-Befehl|Befehl SET-Ansicht|Festes ZEITFENSTER, MEMO-Befehl|  
|SET-XCMDFILE-Befehl|Arbeitsspeicher-Systemvariable _SHELL|GET-Befehl "SHOW"|  
|ANZEIGEN (Befehl) Ruft|KONTEXTMENÜBEFEHL von "anzeigen"|OBJECT-Befehl anzeigen|  
|POPUP-Befehl anzeigen|Befehl "SHOW-Fenster"|Größe POPUP-Befehl|  
|Fenster-Befehl Größe|SKPBAR ()-Funktion|SKPPAD( ) Function|  
|SOUNDEX ()-Funktion|Arbeitsspeicher-Systemvariable _SPELLCHK|SQL-Funktionen|  
|SROWS ()-Funktion|Arbeitsspeicher-Systemvariable _STARTUP|Befehl "Anhalten"|  
|Sys()-Funktionen mit Ausnahme von SYS(2011)|SYSMETRIC( ) Function||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|Arbeitsspeicher-Systemvariable _TABS|TEXTS WIRD AUFGEHOBEN... ENDTEXT-Befehl|TXTWIDTH ()-Funktion|  
|TRANSFORMIEREN ()-Funktion|Arbeitsspeicher-Systemvariable _TRANSPORT||  
|Befehlseingabe|Arbeitsspeicher-Systemvariable _THROTTLE||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|AKTUALISIERTE ()-Funktion|Verwenden Sie den Befehl||  
  
## <a name="v"></a>B  
  
||||  
|-|-|-|  
|Überprüfen Sie die DATABASE-Befehl|VARREAD ()-Funktion|VERSION ()-Funktion|  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|_WINDOWS-Systemvariablen für Arbeitsspeicher|Arbeitsspeicher-Systemvariable _WIZARD|WCHILD ()-Funktion|  
|Warten Sie, Befehl|WBORDER ()-Funktion|WFONT ()-Funktion|  
|WCOLS ()-Funktion|WEXIST ()-Funktion|WLROW ()-Funktion|  
|MIT... ENDWITH-Befehl|WLAST ()-Funktion|WONTOP ()-Funktion|  
|WMAXIMUM ()-Funktion|WLCOL ()-Funktion|WREAD( ) Function|  
|WOUTPUT ()-Funktion|WMINIMUM ()-Funktion|WVISIBLE ()-Funktion|  
|WPARENT ()-Funktion|WTITLE ()-Funktion||  
|WROWS ()-Funktion|Arbeitsspeicher-Systemvariable _WRAP||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|ZOOM-Befehls "Fenster"|||
