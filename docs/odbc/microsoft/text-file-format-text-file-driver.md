---
title: Text Datei Format (Text Datei Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- delimited text lines
- fixed-width text files
- text format [ODBC]
- text file driver [ODBC], text format
ms.assetid: f53cd4b5-0721-4562-a90f-4c55e6030cb9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5801433e0180bb07cb2d09a59db2bb74be012cdf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303091"
---
# <a name="text-file-format-text-file-driver"></a>Textformat (Textdateitreiber)
Der ODBC-Text Treiber unterstützt sowohl Textdateien mit Trennzeichen als auch Textdateien mit fester Breite. Eine Textdatei besteht aus einer optionalen Kopfzeile und 0 (null) oder mehr Textzeilen.  
  
 Obwohl die Kopfzeile dasselbe Format wie die anderen Zeilen in der Textdatei verwendet, interpretiert der ODBC-Text Treiber die Header Zeilen Einträge als Spaltennamen und nicht als Daten.  
  
 Eine durch Trennzeichen getrennte Textzeile enthält einen oder mehrere Datenwerte, die durch Trennzeichen getrennt sind: Kommas, Registerkarten oder ein benutzerdefiniertes Trennzeichen. Das gleiche Trennzeichen muss in der gesamten Datei verwendet werden. NULL-Datenwerte werden durch zwei Trennzeichen in einer Zeile ohne Daten zwischen Ihnen bezeichnet. Zeichen folgen in einer durch Trennzeichen getrennten Textzeile können in doppelte Anführungszeichen ("") eingeschlossen werden. Es können keine Leerzeichen vor oder nach durch Trennzeichen getrennten Werten vorkommen.  
  
 Die Breite jedes Daten Eintrags in einer Textzeile mit fester Breite wird in einem Schema angegeben. NULL-Datenwerte werden durch Leerzeichen gekennzeichnet.  
  
 Tabellen sind auf maximal 255 Felder beschränkt. Feldnamen sind auf 64 Zeichen beschränkt, und die Feldbreite ist auf 32.766 Zeichen beschränkt. Datensätze sind auf 65.000 Bytes beschränkt.  
  
 Eine Textdatei kann nur für einen einzelnen Benutzer geöffnet werden. Mehrere Benutzer werden nicht unterstützt.  
  
 Die folgende, für Programmierer geschriebene Grammatik definiert das Format einer Textdatei, die vom ODBC-Text Treiber gelesen werden kann:  
  
|Format|Darstellung|  
|------------|--------------------|  
|Nicht kursiv|Zeichen, die wie gezeigt eingegeben werden müssen|  
|*Kursiv*|Argumente, die an anderer Stelle in der Grammatik definiert sind|  
|eckige Klammern ([])|Optionale Elemente|  
|geschweifte{}Klammern ()|Eine Liste der sich gegenseitig ausschließenden Optionen|  
|vertikale Balken (&#124;)|Trennen von gegenseitig ausschließenden Optionen|  
|Auslassungszeichen (...)|Elemente, die einmal oder mehrmals wiederholt werden können|  
  
 Das Format einer Textdatei lautet:  
  
```  
text-file ::=  
   [delimited-header-line] [delimited-text-line]... end-of-file |  
   [fixed-width-header-line] [fixed-width-text-line]... end-of-file  
delimited-header-line ::= delimited-text-line  
delimited-text-line ::=  
   blank-line |  
   delimited-data [delimiter delimited-data]... end-of-line  
fixed-width-header-line ::= fixed-width-text-line  
fixed-width-text-line ::=  
   blank-line |  
   fixed-width-data [fixed-width-data]... end-of-line  
end-of-file ::= <EOF>  
blank-line ::= end-of-line  
delimited-data ::= delimited-string | number | date | delimited-null  
fixed-width-data ::= fixed-width-string | number | date | fixed-width-null  
```  
  
> [!NOTE]  
>  Die Breite jeder Spalte in einer Textdatei mit fester Breite wird in der Datei "Schema. ini" angegeben.  
  
```  
  
      end-of-line ::= <CR> | <LF> | <CR><LF>  
delimited-string ::= unquoted-string | quoted-stringunquoted-string ::= [character | digit] [character | digit | quote-character]...  
quoted-string ::=  
   quote-character  
   [character | digit | delimiter | end-of-line | embedded-quoted-string]...  
   quote-characterembedded-quoted-string ::=   quote-characterquote-character  
   [character | digit | delimiter | end-of-line]  
   quote-characterquote-characterfixed-width-string ::= [character | digit | delimiter | quote-character] ...  
character ::= any character except:  
   delimiterdigitend-of-fileend-of-linequote-characterdigit ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9  
delimiter ::= , | <TAB> |   
custom-delimitercustom-delimiter ::= any character except:  
   end-of-fileend-of-linequote-character  
```  
  
> [!NOTE]  
>  Das Trennzeichen in einer benutzerdefinierten, durch Trennzeichen getrennten Textdatei wird in der Datei "Schema. ini" angegeben.  
  
```  
quote-character ::= "  
number ::= exact-number | approximate-number  
exact-number ::= [+ | -] {unsigned-integer[.unsigned-integer] |  
   unsigned-integer. |  
   .unsigned-integer}  
approximate-number ::= exact-number{e | E}[+ | -]unsigned-integer  
unsigned-integer ::= {digit}...  
date ::=  
   mm date-separator dd date-separator yy |  
   mmm date-separator dd date-separator yy |  
   dd date-separator mmm date-separator yy |  
   yyyy date-separator mm date-separator dd |  
   yyyy date-separator mmm date-separator dd  
mm ::= digit [digit]  
dd ::= digit [digit]  
yy ::= digit digit  
yyyy ::= digit digit digit digit  
mmm ::= Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec  
date-separator ::= - | / | .  
delimited-null ::=  
```  
  
> [!NOTE]  
>  Bei durch Trennzeichen getrennten Dateien wird ein NULL-Wert durch keine Daten zwischen zwei Trennzeichen dargestellt.  
  
```  
fixed-width-null ::= <SPACE>...  
```  
  
> [!NOTE]  
>  Bei Dateien mit fester Breite wird NULL durch Leerzeichen dargestellt.
