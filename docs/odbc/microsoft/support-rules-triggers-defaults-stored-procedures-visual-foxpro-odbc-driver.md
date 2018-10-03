---
title: Unterstützung für Regeln, Trigger, Standardwerte und gespeicherte Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], stored procedures
- FoxPro ODBC driver [ODBC], commands and functions
- commands for FoxPro ODBC driver [ODBC]
- FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], triggers
- stored procedures [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], rules
- FoxPro commands and functions [ODBC]
- rules [ODBC]
- Visual FoxPro ODBC driver [ODBC], default values
- FoxPro ODBC driver [ODBC], rules
- functions [ODBC], Visual FoxPro
- default values [ODBC]
- Visual FoxPro ODBC driver [ODBC], commands and functions
- Visual FoxPro ODBC driver [ODBC], triggers
- FoxPro ODBC driver [ODBC], stored procedures
- Visual FoxPro commands and functions [ODBC]
ms.assetid: e449de20-d6ca-4902-9f8e-814eb6e86650
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47795998b019df22b01852519f75f6e8d3d274dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655008"
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>Unterstützung für Regeln, Trigger, Standardwerte und gespeicherte Prozeduren (Visual FoxPro-ODBC-Treiber)
Sie können keine Visual FoxPro-Regeln, Trigger, Standardwerte und gespeicherte Prozeduren unter Verwendung der Visual FoxPro-ODBC-Treiber erstellen. Allerdings kann die Anwendung mit vorhandenen Regeln, Trigger, Standardwerte und gespeicherte Prozeduren interagieren, wie eingefügt, aktualisiert oder Visual FoxPro-Daten in einer Datenbank gespeichert löscht.  
  
 Die folgende Tabelle enthält die Visual FoxPro-Befehle und Funktionen, die von der Visual FoxPro-ODBC-Treiber unterstützt werden, wenn die Befehle oder Funktionen an, die in Regeln, Trigger, Standardwerte und gespeicherte Prozeduren vorhanden sind.  
  
 Wenn Ihre Anwendung mit Daten, deren Regeln, Trigger, Standardwerte interagiert oder gespeicherte Prozeduren, alle anderen Visual FoxPro-Befehle oder Funktionen aufrufen, generiert der Treiber einen Fehler aus. Finden Sie unter [nicht unterstützte Visual FoxPro-Befehle und Funktionen](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md) eine Liste von Befehlen und Funktionen, die vom Treiber nicht unterstützt.  
  
> [!TIP]  
>  Wenn Sie möchten Ihre Regeln, Trigger oder gespeicherte Prozeduren, die bestimmt, die Befehle zum Ausführen, wenn vom Treiber aufgerufen bedingten Code einzufügen, können Sie mithilfe der **VERSION ()** Funktion. Die **VERSION ()** Funktion gibt "Visual FoxPro-ODBC-Treiber  *\<Version >*" beim Aufruf durch den Treiber.  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>Visual FoxPro-Befehle und Funktionen, die in Regeln, Trigger, Standardwerte und gespeicherte Prozeduren unterstützt  
  
||||  
|-|-|-|  
|$-Operator|Operator "%"|& Befehl|  
|& & Befehl|*-Befehl|=-Befehl|  
  
## <a name="a"></a>A  
  
||||  
|-|-|-|  
|ABS ()-Funktion|ACOPY ()-Funktion|TABLE-Befehl "hinzufügen"|  
|ADATABASES ()-Funktion|ADBOBJECTS ()-Funktion|AERROR ()-Funktion|  
|ADEL ()-Funktion|AELEMENT ()-Funktion|ALEN ()-Funktion|  
|AFIELDS ()-Funktion|Des Anbieters AINS ()-Funktion|ALTER TABLE (SQL-Befehl)|  
|ALIAS ()-Funktion|ALLTRIM ()-Funktion|ANFÜGEN von ARRAY-Befehl|  
|AND -Operator|APPEND (Befehl)|Fügen Sie MEMO-Befehl|  
|Fügen Sie vom Befehl|Fügen Sie die allgemeine-Befehl|KANN ()-Funktion|  
|Fügen Sie PROZEDUREN-Befehl|ASC ()-Funktion|ASUBSCRIPT ()-Funktion|  
|ASIN ()-Funktion|ASORT ()-Funktion|ATAN ()-Funktion|  
|Bei der ()-Funktion|AT_C ()-Funktion|ATCLINE ()-Funktion|  
|ATC ()-Funktion|ATCC ()-Funktion|AUSED ()-Funktion|  
|ATLINE ()-Funktion|ATN2 ()-Funktion||  
|Durchschnittliche-Befehl|ACOS ()-Funktion||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|BEGIN TRANSACTION-Befehl|ZWISCHEN ()-Funktion|BITNOT-()-Funktion|  
|BITCLEAR ()-Funktion|BITLSHIFT ()-Funktion|BITSET ()-Funktion|  
|BITOR ()-Funktion|BITRSHIFT ()-Funktion|LEEREN Kommandozeile|  
|BITTEST ()-Funktion|BITXOR-()-Funktion||  
|BOF ()-Funktion|BITAND ()-Funktion||  
  
## <a name="c"></a>c  
  
||||  
|-|-|-|  
|Berechnen der Befehl|KANDIDAT ()-Funktion|' Chr ' ()-Funktion|  
|CDX ()-Funktion|CEILING ()-Funktion|CLOSE-Befehle|  
|CHRTRAN ()-Funktion|CHRTRANC ()-Funktion|Kopieren Sie INDIZES-Befehl|  
|CMONTH ()-Funktion|Befehl fortfahren|Kopieren Sie die erweiterten Befehl Struktur|  
|Kopieren Sie PROZEDUREN-Befehl|Struktur-Kopierbefehl|Kopieren auf einen Menübefehl|  
|Kopieren Sie die TAG-Befehl|ARRAY-Befehl Kopieren|CPCONVERT ()-Funktion|  
|COS ()-Funktion|COUNT-Befehl|CTOD ()-Funktion|  
|CPCURRENT ()-Funktion|CPDBF ()-Funktion|CURSORSETPROP ()-Funktion|  
|CTOT ()-Funktion|CURSORGETPROP ()-Funktion||  
|CURVAL ()-Funktion|CDOW ()-Funktion||  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|Datum ()-Funktion|"DateTime" ()-Funktion|Tag ()-Funktion|  
|DBC ()-Funktion|DBF ()-Funktion|DBGETPROP ()-Funktion|  
|DBUSED ()-Funktion|DELETE (SQL-Befehl)|Befehl "löschen"|  
|DELETE TAG-Befehl|GELÖSCHT ()-Funktion|ABSTEIGENDE ()-Funktion|  
|DIFFERENCE ()-Funktion|DIMENSION-Befehl|Speicherplatz auf dem Datenträger ()-Funktion|  
|DMY ()-Funktion|FÜHREN SIE FALL... ENDCASE-Befehl|Führen Sie Befehl|  
|WÄHREND SIE DAS... ENDDO-Befehl|DOW ()-Funktion|DTOC ()-Funktion|  
|DTOR ()-Funktion|DTOS ()-Funktion|DTOT ()-Funktion|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|(Leer)-Funktion|Auswerten von ()-Funktion|Befehl "Beenden"|  
|Fehler ()-Funktion|EXP ()-Funktion||  
|END TRANSACTION-Befehl|EOF ()-Funktion||  
  
## <a name="f"></a>V  
  
||||  
|-|-|-|  
|FCOUNT ()-Funktion|FDATE ()-Funktion|Feld ()-Funktion|  
|Datei ()-Funktion|FILTER ()-Funktion|FLDLIST ()-Funktion|  
|Bestand ()-Funktion|FLOOR ()-Funktion|FLUSH-Befehl|  
|FOR... ENDFOR-Befehl|FÜR ()-Funktion|()-Funktion gefunden|  
|KOSTENLOSE TABLE-Befehl|FSIZE ()-Funktion|FTIME ()-Funktion|  
|Vollständiger Pfad ()-Funktion|Funktion-Befehl|ZW ()-Funktion|  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|Befehl sammeln|GETNEXTMODIFIED ()-Funktion|Wechseln Sie/GOTO-Befehl|  
|Und übergibt ihr ()-Funktion|GOMONTH ()-Funktion||  
|GETCP ()-Funktion|GETENV ()-Funktion||  
  
## <a name="h"></a>H  
  
|||  
|-|-|  
|HEADER ()-Funktion|Stunde ()-Funktion|  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|IDXCOLLATE ()-Funktion|IF... ENDIF-Befehl|IIF ()-Funktion|  
|INDBC ()-Funktion|INDEX-Befehl|InList-Prozedur ()-Funktion|  
|INSERT-SQL-Befehl|INT ()-Funktion|ISALPHA ()-Funktion|  
|ISBLANK ()-Funktion|ISDIGIT ()-Funktion|ISEXCLUSIVE ()-Funktion|  
|ISLEADBYTE ()-Funktion|ISLOWER ()-Funktion|ISNULL ()-Funktion|  
|ISREADONLY-()-Funktion|ISUPPER ()-Funktion||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|Schlüssel ()-Funktion|KEYMATCH ()-Funktion||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|LINKEN ()-Funktion|LEFTC ()-Funktion|LIKEC ()-Funktion|  
|LENC ()-Funktion|WIE ()-Funktion|SPERRE ()-Funktion|  
|LOKALEN Befehl|Suchen Sie-Befehl|Suche ()-Funktion|  
|LOG ()-Funktion|LOG10 ()-Funktion|LTRIM ()-Funktion|  
|LOWER ()-Funktion|LPARAMETERS-Befehl||  
|LUPDATE ()-Funktion|Funktion "LEN")||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|Arbeitsspeicher-Systemvariable _MLINE|MAX ()-Funktion|MDX ()-Funktion|  
|MDY ()-Funktion|MEMLINES ()-Funktion|Nachricht ()-Funktion|  
|MIN ()-Funktion|MINUTE ()-Funktion|MLINE ()-Funktion|  
|MOD ()-Funktion|Monat ()-Funktion|MTON ()-Funktion|  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|Wie NDX ()-Funktion|NORMALISIEREN von ()-Funktion|NOT-Operator|  
|Hinweis-Befehl|NTOM ()-Funktion|NVL ()-Funktion|  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|Tritt auf, ()-Funktion|OLDVAL ()-Funktion|ZUM Befehl "Fehler"|  
|ZUM Befehl "Schlüssel"|Klicken Sie auf ()-Funktion|OPEN DATABASE-Befehl|  
|OR -Operator|ORDER ()-Funktion|Betriebssystem ()-Funktion|  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|Befehl "PACK"|Parameter ()-Funktion|Zahlung ()-Funktion|  
|Parameter-Befehl|PRIMÄRE ()-Funktion|PRIVATE-Befehl|  
|PI ()-Funktion|Programm ()-Funktion|RICHTIGE ()-Funktion|  
|PROCEDURE-Befehl|PV ()-Funktion||  
|Öffentliche-Befehl|PADL( ) &#124; PADR( ) &#124; PADC( ) Functions||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|RAND ()-Funktion|RATTE ()-Funktion|RATC ()-Funktion|  
|RATLINE ()-Funktion|RÜCKRUFBEFEHL|RECCOUNT ()-Funktion|  
|RECNO ()-Funktion|RECSIZE ()-Funktion|REGIONALE-Befehl|  
|Beziehung ()-Funktion|Entfernen Sie die TABLE-Befehl|Befehl "ersetzen"|  
|ARRAY-Befehl ersetzen|Replizieren von ()-Funktion|Wiederholen SIE Befehl|  
|Befehl zurück|RECHTS ()-Funktion|RIGHTC ()-Funktion|  
|RLOCK ()-Funktion|Befehl "ROLLBACK"|ROUND ()-Funktion|  
|RTOD ()-Funktion|RTRIM ()-Funktion||  
  
## <a name="s"></a>S  
  
||||  
|-|-|-|  
|ÜBERPRÜFUNG... ENDSCAN-Befehl|PUNKTDIAGRAMM-Befehl|S ()-Funktion|  
|Sekunden ()-Funktion|SEEK-Befehl|SEEK ()-Funktion|  
|Wählen Sie den Befehl|SELECT ()-Funktion|SELECT-SQL-Befehl|  
|SET BLOCKSIZE-Befehl|SET-CARRY-Befehl|SET-JAHRHUNDERT-Befehl|  
|SET COLLATE-Befehl|SET-DATABASE-Befehl|SET-DATE-Befehls|  
|SET-Standardbefehl|SET DELETED-Befehl|SET EXACT-Befehl|  
|SET EXCLUSIVE-Befehl|SET-FDOW-Befehl|Befehl SET-Felder|  
|Befehl "SET-FILTER"|FESTE SET-Befehl|SET-FULLPATH-Befehl|  
|SET-FWEEK-Befehl|Befehl festgelegte Stunden|Befehl "SET-INDEX"|  
|Befehl SET-SPERREN|SET-MULTILOCKS der Wert (Befehl)|Legen Sie in der Nähe von Befehl|  
|SET-NOCPTRANS-Befehl|SET-Benachrichtigungsbefehl|SET NULL-Befehl|  
|SET-OPTIMIZE-Befehl|SET-ORDER-Befehl|SET PATH-Befehl|  
|SET-PROCEDURE-Befehl|SET-Beziehung (Befehl)|SET-Beziehung aus Befehl|  
|SET REPROCESS-Befehl|Befehl "Überspringen" festlegen|SET-UDFPARMS-Befehl|  
|SET UNIQUE-Befehl|SET-Befehl "Lautstärke"|SET ()-Funktion|  
|SETFLDSTATE ()-Funktion|SIGN ()-Funktion|SIN ()-Funktion|  
|Befehl "Überspringen"|SORT-Befehl|Leerzeichen ()-Funktion|  
|SQRT ()-Funktion|STORE-Befehl|STR ()-Funktion|  
|STRCONV ()-Funktion|STRTRAN ()-Funktion|STUFF ()-Funktion|  
|STUFFC ()-Funktion|SUBSTR ()-Funktion|SUBSTRC ()-Funktion|  
|SUM-Befehl|Sys(2011)-Funktion||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|Arbeitsspeicher-Systemvariable _TALLY|Arbeitsspeicher-Systemvariable _TRIGGERLEVEL|TAGCOUNT ()-Funktion|  
|TABLEUPDATE ()-Funktion|TAG ()-Funktion|Ziel ()-Funktion|  
|TAGNO ()-Funktion|TAN ()-Funktion|TRIM ()-Funktion|  
|Zeit ()-Funktion|Gesamt-Befehl|TXNLEVEL ()-Funktion|  
|TTOC ()-Funktion|TTOD ()-Funktion||  
|Typ ()-Funktion|TABLEREVERT ()-Funktion||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|EINDEUTIGE ()-Funktion|UNLOCK-Befehl|Verwenden Sie den Befehl|  
|Befehl "UPDATE"|OBERE ()-Funktion||  
|VERWENDET ()-Funktion|UPDATE (SQL-Befehl)||  
  
## <a name="v"></a>B  
  
||||  
|-|-|-|  
|VAL ()-Funktion|VERSION ()-Funktion||  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|Woche ()-Funktion|||  
  
## <a name="y"></a>J  
  
||||  
|-|-|-|  
|Jahr ()-Funktion|||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|ZAP-Befehl|||
