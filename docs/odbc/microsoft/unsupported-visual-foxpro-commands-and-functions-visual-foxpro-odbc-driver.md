---
title: Nicht unterstützte Visual FoxPro-Befehle und -Funktionen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307651"
---
# <a name="unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver"></a>Nicht unterstützte Visual FoxPro-Befehle und -Funktionen (Visual FoxPro-ODBC-Treiber)
In der folgenden Tabelle sind FoxPro-Befehle und -Funktionen aufgeführt, die vom Visual FoxPro ODBC-Treiber nicht unterstützt, aber von Microsoft® Visual FoxPro® unterstützt werden.  
  
 Wenn Ihre Anwendung mit Daten interagiert, deren Regeln, Trigger, Standardwerte oder gespeicherte Prozeduren diese Visual FoxPro-Befehle oder -Funktionen aufrufen, kann der Treiber einen Fehler generieren.  
  
## <a name="unsupported-visual-foxpro-commands-and-functions"></a>Nicht unterstützte Visual FoxPro-Befehle und -Funktionen  
  
||||  
|-|-|-|  
|#DEFINE ... #UNDEF|#IF ... #ENDIF Präprozessorrichtlinie|#IFDEF &#124; #IFNDEF #IFDEF|  
|#INCLUDE Präprozessorrichtlinie|:: Scope Resolution Operator|! Befehl (siehe RUN &#124; ! Befehl)|  
|? &#124; ?? Get-Help|??? Get-Help|• \\&#124; Befehl|  
|@ ... BOX-Befehl|@ ... CLASS-Befehl|@ ... CLEAR-Befehl|  
|@ ... EDIT - Befehl Boxen bearbeiten|@ ... FILL-Befehl|@ ... Erhalten|  
|@ ... MENU-Befehl|@ ... PROMPT-Befehl|@ ... SAY-Befehl|  
|@ ... SCROLL-Befehl|@ ... TO-Befehl||  
  
## <a name="a"></a>Ein  
  
||||  
|-|-|-|  
|ACCEPT-Befehl|ACLASS( ) Funktion|ACTIVATE MENU-Befehl|  
|ACTIVATE POPUP-Befehl|ACTIVATE SCREEN-Befehl|ACTIVATE WINDOW-Befehl|  
|ActivateCell-Methode|ADD CLASS-Befehl|ADIR( ) Funktion|  
|AFONT( ) Funktion|AINSTANCE( ) Funktion|_ALIGNMENT Systemspeichervariable|  
|AMEMBERS( ) Funktion|ANSITOOEM( ) Funktion|APRINTERS( ) Funktion|  
|ASELOBJ( ) Funktion|ASSIST-Befehl||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|BAR( ) Funktion|BARCOUNT( ) Funktion|BARPROMPT( ) Funktion|  
|_BEAUTIFY Systemspeichervariable|_BOX Systemspeichervariable|BROWSE-Befehl|  
|_BROWSER Systemspeichervariable|BUILD APP-Befehl|BUILD EXE-Befehl|  
|BUILD PROJECT-Befehl|_BUILDER Systemspeichervariable||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|_CALCVALUE Systemspeichervariable|_CLIPTEXT Systemspeichervariable|_CONVERTER Systemspeichervariable|  
|_CUROBJ Systemspeichervariable|CALL-Befehl|CANCEL-Befehl|  
|CAPSLOCK( ) Funktion|CD-Befehl|CHANGE-Befehl|  
|CHDIR-Befehl|CHRSAW( ) Funktion|CLOSE MEMO-Befehl|  
|CNTBAR( ) Funktion|CNTPAD( ) Funktion|COL( ) Funktion|  
|COMPILE-Befehl|COMPILE DATABASE-Befehl|COMPILE FORM-Befehl|  
|COMPOBJ( ) Funktion|Containerobjekt|Kontrollobjekt|  
|BEFEHL COPY FILE|COPY MEMO-Befehl|CREATE CLASS-Befehl|  
|CREATE CLASSLIB-Befehl|CREATE COLOR SET-Befehl|CREATE-Befehl|  
|CREATE CONNECTION-Befehl|CREATE DATABASE-Befehl|CREATE FORM-Befehl|  
|CREATE FROM-Befehl|CREATE LABEL-Befehl|CREATE MENU-Befehl|  
|CREATE PROJECT-Befehl|CREATE QUERY-Befehl|CREATE REPORT-Befehl|  
|CREATE SCREEN-Befehl|CREATE SQL VIEW-Befehl|CREATE TRIGGER-Befehl|  
|CREATE VIEW-Befehl|CREATEOBJECT( ) Funktion|CURDIR( ) Funktion|  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|_DBLCLICK Systemspeichervariable|_DIARYDATE Systemspeichervariable|DBSETPROP( ) Funktion|  
|DDE-Funktionen|DEACTIVATE MENU-Befehl|DEACTIVATE POPUP-Befehl|  
|DEACTIVATE WINDOW-Befehl|DECLARE - DLL-Befehl|DECLARE-Befehl|  
|DEFINE BAR-Befehl|BEFEHL DEFINE BOX|DEFINE CLASS-Befehl|  
|DEFINE MENU-Befehl|DEFINE PAD-Befehl|DEFINE POPUP-Befehl|  
|DEFINE WINDOW-Befehl|DELETE CONNECTION-Befehl|DELETE DATABASE-Befehl|  
|DELETE FILE-Befehl|DELETE TRIGGER-Befehl|DELETE VIEW-Befehl|  
|DIR-Befehl|DIRECTORY-Befehl|DISPLAY-Befehl|  
|DISPLAY CONNECTIONS Befehl|DISPLAY DATABASE-Befehl|DISPLAY DLLS-Befehl|  
|DISPLAY FILES Befehl|DISPLAY MEMORY-Befehl|BEFEHL DISPLAY OBJECTS|  
|BEFEHL DISPLAY PROCEDURES|DISPLAY STATUS Befehl|DISPLAY STRUCTURE Befehl|  
|DISPLAY TABLES Befehl|DISPLAY VIEWS Befehl|DO FORM-Befehl|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|EDIT-Befehl|ERROR-Befehl||  
|ERASE-Befehl|EXTERNAL-Befehl|EXPORT-Befehl|  
|EJECT-Befehl|EJECT PAGE-Befehl||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|_FOXDOC Systemspeichervariable|_FOXGRAPH Systemspeichervariable|FEOF( ) Funktion|  
|FCLOSE( ) Funktion|FCREATE( ) Funktion|FGETS( ) Funktion|  
|FERROR( ) Funktion|FFLUSH( ) Funktion|FKLABEL( ) Funktion|  
|FILER-Befehl|FIND-Befehl|FOPEN( ) Funktion|  
|FKMAX( ) Funktion|FONTMETRIC( ) Funktion|FSEEK( ) Funktion|  
|FPUTS( ) Funktion|FREAD( ) Funktion||  
|FWRITE( ) Funktion|FCHSIZE( ) Funktion||  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|_GENGRAPH Systemspeichervariable|_GENMENU Systemspeichervariable|_GENPD Systemspeichervariable|  
|_GENSCRN Systemspeichervariable|_GENXTAB Systemspeichervariable|GETBAR( ) Funktion|  
|GETCOLOR( ) Funktion|GETDIR( ) Funktion|GETEXPR-Befehl|  
|GETFILE( ) Funktion|GETFONT( ) Funktion|GETOBJECT( ) Funktion|  
|GETPAD( ) Funktion|GETPICT( ) Funktion|GETPRINTER( ) Funktion|  
  
## <a name="h"></a>H  
  
||||  
|-|-|-|  
|HELP-Befehl|HIDE MENU-Befehl|HIDE POPUP-Befehl|  
|HIDE WINDOW-Befehl|HOME( ) Funktion||  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IMESTATUS( ) Funktion|IMPORT-Befehl|INPUT-Befehl|  
|INDEX ON Befehl|INKEY( ) Funktion|ISCOLOR( ) Funktion|  
|INSERT-Befehl|INSMODE( ) Funktion||  
|ISMOUSE( ) Funktion|_INDENT Systemspeichervariable||  
  
## <a name="j"></a>J  
  
||||  
|-|-|-|  
|JOIN-Befehl|||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|KEYBOARD-Befehl|||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|_LMARGIN Systemspeichervariable|LABEL-Befehl|LASTKEY( ) Funktion|  
|LINENO( ) Funktion|LIST-Befehle|LIST CONNECTIONS-Befehl|  
|LOAD-Befehl|LOCFILE( ) Funktion||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|MCOL( ) Funktion|MD-Befehl|MENÜ TO-Befehl|  
|MEMORY( ) Funktion|MENU-Befehl|MKDIR-Befehl|  
|MENU( ) Funktion|MESSAGEBOX( ) Funktion|MODIFY CONNECTION-Befehl|  
|MODIFY CLASS-Befehl|MODIFY COMMAND-Befehl|MODIFY FORM-Befehl|  
|MODIFY DATABASE-Befehl|MODIFY FILE-Befehl|MODIFY MEMO-Befehl|  
|MODIFY GENERAL Befehl|MODIFY LABEL-Befehl|MODIFY PROJECT-Befehl|  
|MODIFY MENU-Befehl|MODIFY PROCEDURE-Befehl|MODIFY SCREEN-Befehl|  
|MODIFY QUERY-Befehl|MODIFY REPORT-Befehl|MODIFY WINDOW-Befehl|  
|MODIFY STRUCTURE-Befehl|MODIFY VIEW-Befehl|MOVE WINDOW-Befehl|  
|MOUSE-Befehl|MOVE POPUP-Befehl|MROW( ) Funktion|  
|MRKBAR( ) Funktion|MRKPAD( ) Funktion||  
|MWINDOW( ) Funktion|MDOWN( ) Funktion||  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NUMLOCK( ) Funktion|||  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|OBJNUM( ) Funktion|OBJTOCLIENT( ) Funktion|ON BAR-Befehl|  
|OEMTOANSI( ) Funktion|ON APLABOUT-Befehl|ON EXIT MENU Befehl|  
|ON ESCAPE-Befehl|ON EXIT BAR Befehl|ON KEY = Befehl|  
|ON EXIT PAD Befehl|ON EXIT POPUP Befehl|ON PAD-Befehl|  
|ON KEY LABEL Befehl|ON MACHELP Befehl|ON SELECTION BAR Befehl|  
|ON PAGE-Befehl|ON READERROR-Befehl|ON SELECTION POPUP Befehl|  
|ON SELECTION MENU Befehl|ON SELECTION PAD Befehl||  
|ON SHUTDOWN-Befehl|OBJVAR( ) Funktion||  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|_PADVANCE Systemspeichervariable|_PAGENO Systemspeichervariable|_PBPAGE Systemspeichervariable|  
|_PCOLNO Systemspeichervariable|_PCOPIES Systemspeichervariable|_PDRIVER Systemspeichervariable|  
|_PDSETUP Systemspeichervariable|_PECODE Systemspeichervariable|_PEJECT Systemspeichervariable|  
|_PEPAGE Systemspeichervariable|_PLENGTH Systemspeichervariable|_PLINENO Systemspeichervariable|  
|_PLOFFSET Systemspeichervariable|_PPITCH Systemspeichervariable|_PQUALITY Systemspeichervariable|  
|_PRETEXT Systemspeichervariable|_PSCODE Systemspeichervariable|_PSPACING Systemspeichervariable|  
|_PWAIT Systemspeichervariable|PACK DATABASE-Befehl|PAD( ) Funktion|  
|PCOL( ) Funktion|PEMSTATUS( ) Funktion|PLAY MACRO-Befehl|  
|POP KEY-Befehl|POP MENU-Befehl|POP POPUP-Befehl|  
|POPUP( ) Funktion|Printjob... ENDPRINTJOB-Befehl|PRINTSTATUS( ) Funktion|  
|PRMBAR( ) Funktion|PRMPAD( ) Funktion|PROMPT( ) Funktion|  
|PROW( ) Funktion|PRTINFO( ) Funktion|PUSH KEY-Befehl|  
|PUSH MENU-Befehl|PUSH POPUP Befehl|PUTFILE( ) Funktion|  
  
## <a name="q"></a>Q  
  
||||  
|-|-|-|  
|QUIT-Befehl|||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|_RMARGIN Systemspeichervariable|RD-Befehl|READKEY( ) Funktion|  
|READ-Befehl|READ MENU-Befehl|RELEASE BAR-Befehl|  
|REFRESH() Funktion|REINDEX-Befehl|RELEASE LIBRARY-Befehl|  
|RELEASE CLASSLIB Befehl|RELEASE-Befehl|RELEASE PAD-Befehl|  
|RELEASE MENUS-Befehl|RELEASE MODULE-Befehl|RELEASE WINDOWS-Befehl|  
|RELEASE POPUPS-Befehl|RELEASE PROCEDURE-Befehl|RENAME-Befehl|  
|REMOVE CLASS-Befehl|RENAME CLASS-Befehl|RENAME VIEW-Befehl|  
|RENAME CONNECTION-Befehl|RENAME TABLE-Befehl|RESTORE VON Befehl|  
|BERICHT-Befehl|REQUERY( ) Funktion|RESTORE WINDOW Befehl|  
|RESTORE MACROS-Befehl|RESTORE SCREEN Befehl|RGBSCHEME( ) Funktion|  
|RESUME-Befehl|RGB( ) Funktion|RUN &#124; ! Get-Help|  
|RMDIR-Befehl|ROW( ) Funktion||  
|RUNSCRIPT-Befehl|RDLEVEL( ) Funktion||  
  
## <a name="s"></a>E  
  
||||  
|-|-|-|  
|SAVE MACROS-Befehl|SAVE SCREEN-Befehl|SAVE TO Befehl|  
|SAVE WINDOWS-Befehl|SCHEME( ) Funktion|SCOLS( ) Funktion|  
|SCROLL-Befehl|_SCREEN Systemspeichervariable|SET-Befehl|  
|SET ALTERNATE-Befehl|SET ANSI-Befehl|SET APLABOUT-Befehl|  
|SET AUTOSAVE-Befehl|SET BELL Befehl|SET BLINK-Befehl|  
|SET BORDER-Befehl|SET BRSTATUS Befehl|SET CLASSLIB-Befehl|  
|SET CLEAR-Befehl|SET CLOCK-Befehl|SET COLOR OF Befehl|  
|SET FARBE VON SCHEME-Befehl|SET COLOR SET-Befehl|SET COLOR TO Befehl|  
|SET COMPATIBLE Befehl|SET CONFIRM-Befehl|SET CONSOLE-Befehl|  
|EINSTELLEN VON CPCOMPILE|EINSTELLEN VON CPDIALOG|SET CURRENCY-Befehl|  
|SET CURSOR-Befehl|SET DATASESSION Befehl|SET DEBUG-Befehl|  
|SET DECIMALS-Befehl|SET DELIMITERS-Befehl|SET DEVELOPMENT-Befehl|  
|SET DEVICE-Befehl|SET DISPLAY-Befehl|SET DOHISTORY Befehl|  
|SET ECHO-Befehl|SET ESCAPE-Befehl|SET FORMAT Befehl|  
|SET FUNCTION Befehl|SET HEADINGS-Befehl|SET HELP-Befehl|  
|SET HELPFILTER Befehl|SET INTENSITY-Befehl|SET KEY-Befehl|  
|SET KEYCOMP-Befehl|SET LOGERRORS Befehl|SET MACDESKTOP-Befehl|  
|SET MACHELP-Befehl|SET MACKEY-Befehl|SET MARGIN-Befehl|  
|SET MARK DES Befehls|SET MARK TO Befehl|SET MEMOWIDTH-Befehl|  
|SET MESSAGE-Befehl|SET MOUSE-Befehl|SET ODOMETER Befehl|  
|SET OLEOBJECT-Befehl|SET PALETTE-Befehl|SET PDSETUP-Befehl|  
|SET POINT-Befehl|SET PRINTER-Befehl|SET READBORDER-Befehl|  
|SET REFRESH-Befehl|SET RESOURCE-Befehl|SET SAFETY Befehl|  
|SET SCOREBOARD Befehl|SET SECONDS-Befehl|SET SEPARATOR-Befehl|  
|SET SHADOWS-Befehl|SET SKIP OF Command|SET SPACE-Befehl|  
|SET STATUS-Befehl|SET STATUS BAR Befehl|SET STEP Befehl|  
|SET STICKY Befehl|SET SYSFORMATS-Befehl|SET SYSMENU-Befehl|  
|SET TALK-Befehl|SET TEXTMERGE Befehl|SET TEXTMERGE DELIMITERS Befehl|  
|SET TOPIC-Befehl|SET TOPIC ID-Befehl|SET TRBETWEEN-Befehl|  
|SET TYPEAHEAD-Befehl|SET VIEW-Befehl|SET-FENSTER DES MEMO-Befehls|  
|SET XCMDFILE-Befehl|_SHELL Systemspeichervariable|SHOW GET-Befehl|  
|SHOW GETS Befehl|SHOW MENU Befehl|SHOW OBJECT-Befehl|  
|SHOW POPUP Befehl|SHOW WINDOW Befehl|SIZE POPUP-Befehl|  
|SIZE WINDOW-Befehl|SKPBAR( ) Funktion|SKPPAD( ) Funktion|  
|SOUNDEX( ) Funktion|_SPELLCHK Systemspeichervariable|SQL-Funktionen|  
|SROWS( ) Funktion|_STARTUP Systemspeichervariable|SUSPEND-Befehl|  
|SYS() Funktionen außer SYS(2011)|SYSMETRIC( ) Funktion||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|_TABS Systemspeichervariable|Text... ENDTEXT-Befehl|TXTWIDTH( ) Funktion|  
|TRANSFORM( ) Funktion|_TRANSPORT Systemspeichervariable||  
|TYPE-Befehl|_THROTTLE Systemspeichervariable||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|AKTUALISIERT( ) Funktion|USE-Befehl||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|VALIDATE DATABASE-Befehl|VARREAD( ) Funktion|VERSION( ) Funktion|  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|_WINDOWS Systemspeichervariable|_WIZARD Systemspeichervariable|WCHILD( ) Funktion|  
|WAIT-Befehl|WBORDER( ) Funktion|WFONT( ) Funktion|  
|WCOLS( ) Funktion|WEXIST( ) Funktion|WLROW( ) Funktion|  
|Mit... ENDWITH-Befehl|WLAST( ) Funktion|WONTOP( ) Funktion|  
|WMAXIMUM( ) Funktion|WLCOL( ) Funktion|WREAD( ) Funktion|  
|WOUTPUT( ) Funktion|WMINIMUM( ) Funktion|WVISIBLE( ) Funktion|  
|WPARENT( ) Funktion|WTITLE( ) Funktion||  
|WROWS( ) Funktion|_WRAP Systemspeichervariable||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|ZOOM WINDOW-Befehl|||
