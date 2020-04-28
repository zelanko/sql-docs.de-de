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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2fcf8e7c80b2712313cba81199489dc7cb06dce0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301137"
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>Unterstützung für Regeln, Trigger, Standardwerte und gespeicherte Prozeduren (Visual FoxPro-ODBC-Treiber)
Mithilfe des Visual FoxPro-ODBC-Treibers können keine Visual FoxPro-Regeln, Trigger, Standardwerte oder gespeicherten Prozeduren erstellt werden. Die Anwendung kann jedoch mit vorhandenen Regeln, Triggern, Standardwerten oder gespeicherten Prozeduren interagieren, wenn Sie in einer Datenbank gespeicherte Visual FoxPro-Daten einfügt, aktualisiert oder löscht.  
  
 In der folgenden Tabelle werden die Visual FoxPro-Befehle und-Funktionen aufgelistet, die vom Visual FoxPro-ODBC-Treiber unterstützt werden, wenn die Befehle oder Funktionen in Regeln, Triggern, Standardwerten oder gespeicherten Prozeduren vorhanden sind  
  
 Wenn Ihre Anwendung mit Daten interagiert, deren Regeln, Trigger, Standardwerte oder gespeicherte Prozeduren beliebige andere Visual FoxPro-Befehle oder-Funktionen aufzurufen, generiert der Treiber einen Fehler. Eine Liste der Befehle und Funktionen, die nicht vom Treiber unterstützt werden, finden Sie unter [nicht unterstützte Visual FoxPro-Befehle und-Funktionen](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md) .  
  
> [!TIP]  
>  Wenn Sie bedingten Code in Regeln, Trigger oder gespeicherte Prozeduren einfügen möchten, die die Befehle bestimmen, die beim Aufrufen durch den Treiber ausgeführt werden sollen, können Sie die **Version ()** -Funktion verwenden. Die **Version ()** -Funktion gibt "Visual FoxPro-ODBC-Treiber * \<Version>*" zurück, wenn Sie vom Treiber aufgerufen wird.  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>In Regeln, Triggern, Standardwerten und gespeicherten Prozeduren unterstützte Visual FoxPro-Befehle und-Funktionen  
  
||||  
|-|-|-|  
|$-Operator|%-Operator|&-Befehl|  
|&& -Befehl|* Befehl|=-Befehl|  
  
## <a name="a"></a>Ein  
  
||||  
|-|-|-|  
|Abs ()-Funktion|Acopy ()-Funktion|Befehl Tabellen hinzufügen|  
|Adatabases ()-Funktion|Adbobjects ()-Funktion|AERROR ()-Funktion|  
|Adel ()-Funktion|Aelement ()-Funktion|Alen ()-Funktion|  
|AFields ()-Funktion|AINS ()-Funktion|ALTER TABLE (SQL-Befehl)|  
|Alias ()-Funktion|ALLTRIM ()-Funktion|Befehl "aus Array anfügen"|  
|AND-Operator|Befehl Anfügen|Memo Befehl Anfügen|  
|Befehl "aus" Anfügen|Befehl "Allgemein anhängen"|Ascan ()-Funktion|  
|Befehl "Prozeduren anhängen"|ASC ()-Funktion|Asubscript ()-Funktion|  
|ASIN ()-Funktion|Asort ()-Funktion|Atan ()-Funktion|  
|AT ()-Funktion|AT_C ()-Funktion|Atcline ()-Funktion|  
|ATC ()-Funktion|ATCC ()-Funktion|Out ()-Funktion|  
|Atline ()-Funktion|ATN2 ()-Funktion||  
|Average-Befehl|Acos ()-Funktion||  
  
## <a name="b"></a>B  
  
||||  
|-|-|-|  
|BEGIN TRANSACTION-Befehl|BETWEEN ()-Funktion|Bitnot ()-Funktion|  
|BITCLEAR ()-Funktion|BITLSHIFT ()-Funktion|Bitset ()-Funktion|  
|BITOR ()-Funktion|BITRSHIFT ()-Funktion|Leerer Befehl|  
|Bittest ()-Funktion|BITXOR ()-Funktion||  
|BOF ()-Funktion|BITAND ()-Funktion||  
  
## <a name="c"></a>C  
  
||||  
|-|-|-|  
|Befehl berechnen|Candidate ()-Funktion|Chr ()-Funktion|  
|CDX ()-Funktion|Ceiling ()-Funktion|Befehle schließen|  
|CHRTRAN ()-Funktion|Chrtranc ()-Funktion|Befehl zum Kopieren von Indizes|  
|Cmonth ()-Funktion|Befehl "Continue"|Erweiterten Befehl "Struktur kopieren"|  
|Befehl "Befehle Kopieren"|Befehl "Struktur kopieren"|In Befehl Kopieren|  
|Befehl "Tag kopieren"|Befehl "in Array kopieren"|Cpconvert ()-Funktion|  
|COS ()-Funktion|COUNT-Befehl|CTOD ()-Funktion|  
|Cpcurrent ()-Funktion|Cpdbf ()-Funktion|Currsorsetprop ()-Funktion|  
|CTOT ()-Funktion|Currsorgetprop ()-Funktion||  
|Currval ()-Funktion|CDOW ()-Funktion||  
  
## <a name="d"></a>D  
  
||||  
|-|-|-|  
|Date ()-Funktion|DateTime ()-Funktion|Day ()-Funktion|  
|DBC ()-Funktion|DBF ()-Funktion|DBGetProp ()-Funktion|  
|Dbused ()-Funktion|DELETE (SQL-Befehl)|DELETE-Befehl|  
|DELETE TAG-Befehl|DELETED ()-Funktion|Absteigende ()-Funktion|  
|Difference ()-Funktion|Dimensions Befehl|DISKSPACE ()-Funktion|  
|DMY ()-Funktion|Do Case... ENDCASE-Befehl|Do-Befehl|  
|Do While... ENDDO-Befehl|Dow ()-Funktion|Dto c ()-Funktion|  
|Dtor ()-Funktion|DTOs ()-Funktion|DTOT ()-Funktion|  
  
## <a name="e"></a>E  
  
||||  
|-|-|-|  
|Empty ()-Funktion|Evaluieren ()-Funktion|Exit-Befehl|  
|Error ()-Funktion|Exp ()-Funktion||  
|Befehl "Transaktions Ende"|EOF ()-Funktion||  
  
## <a name="f"></a>F  
  
||||  
|-|-|-|  
|F count ()-Funktion|Sdate ()-Funktion|Field ()-Funktion|  
|FILE ()-Funktion|Filter ()-Funktion|Fldlist ()-Funktion|  
|Flock ()-Funktion|Floor ()-Funktion|Flush-Befehl|  
|Für... Endfor-Befehl|FOR ()-Funktion|Found ()-Funktion|  
|Befehl "freie Tabelle"|F Size ()-Funktion|"F time ()"-Funktion|  
|FullPath ()-Funktion|Funktionsbefehl|FV ()-Funktion|  
  
## <a name="g"></a>G  
  
||||  
|-|-|-|  
|Gather-Befehl|GETNEXTMODIFIED ()-Funktion|Gehe-/GOTO-Befehl|  
|GETFLDSTATE ()-Funktion|Gomonth ()-Funktion||  
|Getcp ()-Funktion|Getenv ()-Funktion||  
  
## <a name="h"></a>H  
  
|||  
|-|-|  
|Header ()-Funktion|Hour ()-Funktion|  
  
## <a name="i"></a>I  
  
||||  
|-|-|-|  
|Idxcollate ()-Funktion|Wenn... Befehl "umdif"|IIf ()-Funktion|  
|Einzbc ()-Funktion|INDEX-Befehl|InList ()-Funktion|  
|INSERT-SQL-Befehl|INT ()-Funktion|Isalpha ()-Funktion|  
|Isblank ()-Funktion|IsDigit ()-Funktion|Isexclusive ()-Funktion|  
|Isleadbyte ()-Funktion|IsLower ()-Funktion|IsNull ()-Funktion|  
|Isschreib only ()-Funktion|IsUpper ()-Funktion||  
  
## <a name="k"></a>K  
  
||||  
|-|-|-|  
|Key ()-Funktion|Keymatch ()-Funktion||  
  
## <a name="l"></a>L  
  
||||  
|-|-|-|  
|Left ()-Funktion|LEFTC ()-Funktion|Likec ()-Funktion|  
|LENC ()-Funktion|Like ()-Funktion|Lock ()-Funktion|  
|Lokaler Befehl|Befehl Suchen|Lookup ()-Funktion|  
|Log ()-Funktion|Log10 ()-Funktion|LTRIM ()-Funktion|  
|Lower ()-Funktion|LPARAMETERS-Befehl||  
|LUpdate ()-Funktion|LEN ()-Funktion||  
  
## <a name="m"></a>M  
  
||||  
|-|-|-|  
|System Speicher Variable _MLINE|Max ()-Funktion|MDX ()-Funktion|  
|MDY ()-Funktion|Memlines ()-Funktion|Message ()-Funktion|  
|MIN ()-Funktion|Minute ()-Funktion|MLINE ()-Funktion|  
|MOD ()-Funktion|MONTH ()-Funktion|MTON ()-Funktion|  
  
## <a name="n"></a>N  
  
||||  
|-|-|-|  
|NDX ()-Funktion|Normalize ()-Funktion|Not-Operator|  
|Hinweis Befehl|NTOM ()-Funktion|NvL ()-Funktion|  
  
## <a name="o"></a>O  
  
||||  
|-|-|-|  
|Vorkommen ()-Funktion|OLDVAL ()-Funktion|Befehl bei Fehler|  
|Befehl "on Key"|ON ()-Funktion|Befehl "Datenbank öffnen"|  
|OR-Operator|Order ()-Funktion|OS ()-Funktion|  
  
## <a name="p"></a>P  
  
||||  
|-|-|-|  
|Pack-Befehl|Parameters ()-Funktion|Payment ()-Funktion|  
|Parameter Befehl|Primary ()-Funktion|Privater Befehl|  
|PI ()-Funktion|Program ()-Funktion|Proper ()-Funktion|  
|Prozedur Befehl|PV ()-Funktion||  
|Öffentlicher Befehl|PADL () &#124; PADR () &#124; padc ()-Funktionen||  
  
## <a name="r"></a>R  
  
||||  
|-|-|-|  
|Rand ()-Funktion|Rat ()-Funktion|RATC ()-Funktion|  
|Ratline ()-Funktion|Rückruf Befehl|Reccount ()-Funktion|  
|RecNo ()-Funktion|Recsize ()-Funktion|Regionaler Befehl|  
|Relation ()-Funktion|Befehl "Tabelle entfernen"|Replace-Befehl|  
|Aus Array ersetzen (Befehl)|Replizieren ()-Funktion|Befehl "Wiederholen"|  
|Rückgabe Befehl|Right ()-Funktion|Rightc ()-Funktion|  
|Rlock ()-Funktion|Rollback-Befehl|Round ()-Funktion|  
|Rtod ()-Funktion|RTRIM ()-Funktion||  
  
## <a name="s"></a>E  
  
||||  
|-|-|-|  
|Scan Vorgang... Endscan-Befehl|Punkt Befehl|SEC ()-Funktion|  
|SECONDS ()-Funktion|Seek-Befehl|Seek ()-Funktion|  
|Befehl auswählen|Select ()-Funktion|SELECT-SQL-Befehl|  
|SET BLOCKSIZE-Befehl|Befehl "ausführen" festlegen|Jahrhundert festlegen|  
|SET COLLATE-Befehl|Datenbankbefehl festlegen|Befehl "Datum festlegen"|  
|Standardbefehl festlegen|SET DELETED-Befehl|SET EXACT-Befehl|  
|SET EXCLUSIVE-Befehl|Befehl "f" festlegen|Befehl "Felder festlegen"|  
|Filter Befehl festlegen|Fixed-Befehl festlegen|Befehl "FullPath festlegen"|  
|Befehl "f-Woche festlegen"|Befehl "Stunden festlegen"|Befehl "Index festlegen"|  
|Befehl "Lock festlegen"|Befehl "MULTILOCKS festlegen"|Near-Befehl festlegen|  
|Befehl "nocptrans" festlegen|Benachrichtigungs Befehl festlegen|SET NULL-Befehl|  
|Befehl "optimieren" festlegen|Befehl "Bestellung festlegen"|SET PATH-Befehl|  
|Befehl "Prozedur festlegen"|Beziehungs Befehl festlegen|Befehl "Beziehung aus festlegen"|  
|SET REPROCESS-Befehl|Befehl "Skip" festlegen|Befehl "udfparser festlegen"|  
|SET UNIQUE-Befehl|Befehl "Volume festlegen"|Set ()-Funktion|  
|Setfldstate ()-Funktion|Sign ()-Funktion|Sin ()-Funktion|  
|Skip-Befehl|Sortier Befehl|Space ()-Funktion|  
|SQRT ()-Funktion|Store-Befehl|Str ()-Funktion|  
|"Strauv ()"-Funktion|"Stretran ()"-Funktion|Stuff ()-Funktion|  
|Stuffc ()-Funktion|Substr ()-Funktion|SUBSTRC ()-Funktion|  
|Sum-Befehl|SYS (2011)-Funktion||  
  
## <a name="t"></a>T  
  
||||  
|-|-|-|  
|System Speicher Variable _TALLY|System Speicher Variable _TRIGGERLEVEL|Tagcount ()-Funktion|  
|TABLEUPDATE ()-Funktion|Tag ()-Funktion|Target ()-Funktion|  
|Tagno ()-Funktion|Tan ()-Funktion|Trim ()-Funktion|  
|Time ()-Funktion|Befehl Gesamt|Txnlevel ()-Funktion|  
|Tto c ()-Funktion|Ttod ()-Funktion||  
|Type ()-Funktion|Tablerevert ()-Funktion||  
  
## <a name="u"></a>U  
  
||||  
|-|-|-|  
|Unique ()-Funktion|Befehl zum Entsperren|Befehl verwenden|  
|Befehl "Aktualisieren"|Upper ()-Funktion||  
|USED ()-Funktion|UPDATE (SQL-Befehl)||  
  
## <a name="v"></a>V  
  
||||  
|-|-|-|  
|Val ()-Funktion|Version ()-Funktion||  
  
## <a name="w"></a>W  
  
||||  
|-|-|-|  
|Week ()-Funktion|||  
  
## <a name="y"></a>J  
  
||||  
|-|-|-|  
|Year ()-Funktion|||  
  
## <a name="z"></a>Z  
  
||||  
|-|-|-|  
|Befehl "zap"|||
