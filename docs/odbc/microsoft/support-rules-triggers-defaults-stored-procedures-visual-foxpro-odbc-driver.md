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
ms.openlocfilehash: a02aeea8f33e3a4d87fc771a7b0fa7b1a0067b6d
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363360"
---
# <a name="support-for-rules-triggers-default-values-and-stored-procedures-visual-foxpro-odbc-driver"></a>Unterstützung für Regeln, Trigger, Standardwerte und gespeicherte Prozeduren (Visual FoxPro-ODBC-Treiber)
Mithilfe des Visual FoxPro-ODBC-Treibers können keine Visual FoxPro-Regeln, Trigger, Standardwerte oder gespeicherten Prozeduren erstellt werden. Die Anwendung kann jedoch mit vorhandenen Regeln, Triggern, Standardwerten oder gespeicherten Prozeduren interagieren, wenn Sie in einer Datenbank gespeicherte Visual FoxPro-Daten einfügt, aktualisiert oder löscht.  
  
 In der folgenden Tabelle werden die Visual FoxPro-Befehle und-Funktionen aufgelistet, die vom Visual FoxPro-ODBC-Treiber unterstützt werden, wenn die Befehle oder Funktionen in Regeln, Triggern, Standardwerten oder gespeicherten Prozeduren vorhanden sind  
  
 Wenn Ihre Anwendung mit Daten interagiert, deren Regeln, Trigger, Standardwerte oder gespeicherte Prozeduren beliebige andere Visual FoxPro-Befehle oder-Funktionen aufzurufen, generiert der Treiber einen Fehler. Eine Liste der Befehle und Funktionen, die nicht vom Treiber unterstützt werden, finden Sie unter [nicht unterstützte Visual FoxPro-Befehle und-Funktionen](../../odbc/microsoft/unsupported-visual-foxpro-commands-and-functions-visual-foxpro-odbc-driver.md) .  
  
> [!TIP]  
>  Wenn Sie bedingten Code in Regeln, Trigger oder gespeicherte Prozeduren einfügen möchten, die die Befehle bestimmen, die beim Aufrufen durch den Treiber ausgeführt werden sollen, können Sie die **Version ()** -Funktion verwenden. Die **Version ()** -Funktion gibt "Visual FoxPro-ODBC-Treiber" zurück, *\<version>* Wenn Sie vom Treiber aufgerufen wird.  
  
## <a name="visual-foxpro-commands-and-functions-supported-in-rules-triggers-default-values-and-stored-procedures"></a>In Regeln, Triggern, Standardwerten und gespeicherten Prozeduren unterstützte Visual FoxPro-Befehle und-Funktionen  

:::row:::
    :::column:::
        $-Operator  
        %-Operator  
    :::column-end:::
    :::column:::
        &-Befehl  
        && -Befehl  
    :::column-end:::
    :::column:::
        \*-Befehl  
        =-Befehl  
    :::column-end:::
:::row-end:::

## <a name="a"></a>Ein  

:::row:::
    :::column:::
        Abs ()-Funktion  
        Acopy ()-Funktion  
        Acos ()-Funktion  
        Adatabases ()-Funktion  
        Adbobjects ()-Funktion  
        Befehl Tabellen hinzufügen  
        Adel ()-Funktion  
        Aelement ()-Funktion  
        AERROR ()-Funktion  
        AFields ()-Funktion  
        AINS ()-Funktion  
        Alen ()-Funktion  
        Alias ()-Funktion  
    :::column-end:::
    :::column:::
        ALLTRIM ()-Funktion  
        ALTER TABLE (SQL-Befehl)  
        AND-Operator  
        Befehl Anfügen  
        Befehl "aus" Anfügen  
        Befehl "aus Array anfügen"  
        Befehl "Allgemein anhängen"  
        Memo Befehl Anfügen  
        Befehl "Prozeduren anhängen"  
        ASC ()-Funktion  
        Ascan ()-Funktion  
        ASIN ()-Funktion  
        Asort ()-Funktion  
    :::column-end:::
    :::column:::
        Asubscript ()-Funktion  
        AT ()-Funktion  
        AT_C ()-Funktion  
        Atan ()-Funktion  
        ATC ()-Funktion  
        ATCC ()-Funktion  
        Atcline ()-Funktion  
        Atline ()-Funktion  
        ATN2 ()-Funktion  
        Out ()-Funktion  
        Average-Befehl  
    :::column-end:::
:::row-end:::

## <a name="b"></a>B  

:::row:::
    :::column:::
        BEGIN TRANSACTION-Befehl  
        BETWEEN ()-Funktion  
        BITAND ()-Funktion  
        BITCLEAR ()-Funktion  
        BITLSHIFT ()-Funktion  
    :::column-end:::
    :::column:::
        Bitnot ()-Funktion  
        BITOR ()-Funktion  
        BITRSHIFT ()-Funktion  
        Bitset ()-Funktion  
        Bittest ()-Funktion  
    :::column-end:::
    :::column:::
        BITXOR ()-Funktion  
        Leerer Befehl  
        BOF ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="c"></a>C  

:::row:::
    :::column:::
        Befehl berechnen  
        Candidate ()-Funktion  
        CDOW ()-Funktion  
        CDX ()-Funktion  
        Ceiling ()-Funktion  
        Chr ()-Funktion  
        CHRTRAN ()-Funktion  
        Chrtranc ()-Funktion  
        Befehle schließen  
        Cmonth ()-Funktion  
    :::column-end:::
    :::column:::
        Befehl "Continue"  
        Befehl zum Kopieren von Indizes  
        Befehl "Befehle Kopieren"  
        Befehl "Struktur kopieren"  
        Erweiterten Befehl "Struktur kopieren"  
        Befehl "Tag kopieren"  
        In Befehl Kopieren  
        Befehl "in Array kopieren"  
        COS ()-Funktion  
        COUNT-Befehl  
    :::column-end:::
    :::column:::
        Cpconvert ()-Funktion  
        Cpcurrent ()-Funktion  
        Cpdbf ()-Funktion  
        CTOD ()-Funktion  
        CTOT ()-Funktion  
        Currsorgetprop ()-Funktion  
        Currsorsetprop ()-Funktion  
        Currval ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="d"></a>D  

:::row:::
    :::column:::
        Date ()-Funktion  
        DateTime ()-Funktion  
        Day ()-Funktion  
        DBC ()-Funktion  
        DBF ()-Funktion  
        DBGetProp ()-Funktion  
        Dbused ()-Funktion  
        DELETE (SQL-Befehl)  
    :::column-end:::
    :::column:::
        DELETE-Befehl  
        Befehl DELETE TAG  
        DELETED ()-Funktion  
        Absteigende ()-Funktion  
        Difference ()-Funktion  
        Dimensions Befehl  
        DISKSPACE ()-Funktion  
        DMY ()-Funktion  
    :::column-end:::
    :::column:::
        Do-Befehl  
        Do Case... ENDCASE-Befehl  
        Do While... ENDDO-Befehl  
        Dow ()-Funktion  
        Dto c ()-Funktion  
        Dtor ()-Funktion  
        DTOs ()-Funktion  
        DTOT ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="e"></a>E  

:::row:::
    :::column:::
        Empty ()-Funktion  
        Befehl "Transaktions Ende"  
        EOF ()-Funktion  
    :::column-end:::
    :::column:::
        Error ()-Funktion  
        Evaluieren ()-Funktion  
        Exit-Befehl  
    :::column-end:::
    :::column:::
        Exp ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="f"></a>F  

:::row:::
    :::column:::
        F count ()-Funktion  
        Sdate ()-Funktion  
        Field ()-Funktion  
        FILE ()-Funktion  
        Filter ()-Funktion  
        Fldlist ()-Funktion  
    :::column-end:::
    :::column:::
        Flock ()-Funktion  
        Floor ()-Funktion  
        Flush-Befehl  
        FOR ()-Funktion  
        Für... Endfor-Befehl  
        Found ()-Funktion  
    :::column-end:::
    :::column:::
        Befehl "freie Tabelle"  
        F Size ()-Funktion  
        "F time ()"-Funktion  
        FullPath ()-Funktion  
        Funktionsbefehl  
        FV ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="g"></a>G  

:::row:::
    :::column:::
        Gather-Befehl  
        Getcp ()-Funktion  
        Getenv ()-Funktion  
    :::column-end:::
    :::column:::
        GETFLDSTATE ()-Funktion  
        GETNEXTMODIFIED ()-Funktion  
        Gehe-/GOTO-Befehl  
    :::column-end:::
    :::column:::
        Gomonth ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="h"></a>H  

:::row:::
    :::column:::
        Header ()-Funktion
    :::column-end:::
    :::column:::
        Hour ()-Funktion
    :::column-end:::
:::row-end:::

## <a name="i"></a>I  

:::row:::
    :::column:::
        Idxcollate ()-Funktion  
        Wenn... Befehl "umdif"  
        IIf ()-Funktion  
        Einzbc ()-Funktion  
        Befehl INDEX  
        InList ()-Funktion  
    :::column-end:::
    :::column:::
        INSERT-SQL-Befehl  
        INT ()-Funktion  
        Isalpha ()-Funktion  
        Isblank ()-Funktion  
        IsDigit ()-Funktion  
        Isexclusive ()-Funktion  
    :::column-end:::
    :::column:::
        Isleadbyte ()-Funktion  
        IsLower ()-Funktion  
        IsNull ()-Funktion  
        Isschreib only ()-Funktion  
        IsUpper ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="k"></a>K  

:::row:::
    :::column:::
        Key ()-Funktion
    :::column-end:::
    :::column:::
        Keymatch ()-Funktion
    :::column-end:::
:::row-end:::

## <a name="l"></a>L  

:::row:::
    :::column:::
        Left ()-Funktion  
        LEFTC ()-Funktion  
        LEN ()-Funktion  
        LENC ()-Funktion  
        Like ()-Funktion  
        Likec ()-Funktion  
    :::column-end:::
    :::column:::
        Lokaler Befehl  
        Befehl Suchen  
        Lock ()-Funktion  
        Log ()-Funktion  
        Log10 ()-Funktion  
        Lookup ()-Funktion  
    :::column-end:::
    :::column:::
        Lower ()-Funktion  
        LPARAMETERS-Befehl  
        LTRIM ()-Funktion  
        LUpdate ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="m"></a>M  

:::row:::
    :::column:::
        Max ()-Funktion  
        MDX ()-Funktion  
        MDY ()-Funktion  
        Memlines ()-Funktion  
    :::column-end:::
    :::column:::
        Message ()-Funktion  
        MIN ()-Funktion  
        Minute ()-Funktion  
        System Speicher Variable _MLINE  
    :::column-end:::
    :::column:::
        MLINE ()-Funktion  
        MOD ()-Funktion  
        MONTH ()-Funktion  
        MTON ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="n"></a>N  

:::row:::
    :::column:::
        NDX ()-Funktion  
        Normalize ()-Funktion  
    :::column-end:::
    :::column:::
        Not-Operator  
        Hinweis Befehl  
    :::column-end:::
    :::column:::
        NTOM ()-Funktion  
        NvL ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="o"></a>O  

:::row:::
    :::column:::
        Vorkommen ()-Funktion  
        OLDVAL ()-Funktion  
        ON ()-Funktion  
    :::column-end:::
    :::column:::
        Befehl bei Fehler  
        Befehl "on Key"  
        Befehl "Datenbank öffnen"  
    :::column-end:::
    :::column:::
        OR-Operator  
        Order ()-Funktion  
        OS ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="p"></a>P  

:::row:::
    :::column:::
        Pack-Befehl  
        PADL () &#124; PADR () &#124; padc ()-Funktionen  
        Parameter Befehl  
        Parameters ()-Funktion  
        Payment ()-Funktion  
    :::column-end:::
    :::column:::
        PI ()-Funktion  
        Primary ()-Funktion  
        Privater Befehl  
        Prozedur Befehl  
        Program ()-Funktion  
    :::column-end:::
    :::column:::
        Proper ()-Funktion  
        Öffentlicher Befehl  
        PV ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="r"></a>R  

:::row:::
    :::column:::
        Rand ()-Funktion  
        Rat ()-Funktion  
        RATC ()-Funktion  
        Ratline ()-Funktion  
        Rückruf Befehl  
        Reccount ()-Funktion  
        RecNo ()-Funktion  
        Recsize ()-Funktion  
    :::column-end:::
    :::column:::
        Regionaler Befehl  
        Relation ()-Funktion  
        Befehl "Tabelle entfernen"  
        Replace-Befehl  
        Aus Array ersetzen (Befehl)  
        Replizieren ()-Funktion  
        Befehl "Wiederholen"  
        Rückgabe Befehl  
    :::column-end:::
    :::column:::
        Right ()-Funktion  
        Rightc ()-Funktion  
        Rlock ()-Funktion  
        Rollback-Befehl  
        Round ()-Funktion  
        Rtod ()-Funktion  
        RTRIM ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="s"></a>E  

:::row:::
    :::column:::
        Scan Vorgang... Endscan-Befehl  
        Punkt Befehl  
        SEC ()-Funktion  
        SECONDS ()-Funktion  
        Seek-Befehl  
        Seek ()-Funktion  
        Befehl auswählen  
        Select ()-Funktion  
        SELECT-SQL-Befehl  
        Set ()-Funktion  
        Befehl SET BLOCKSIZE  
        Befehl "ausführen" festlegen  
        Jahrhundert festlegen  
        Befehl SET COLLATE  
        Datenbankbefehl festlegen  
        Befehl "Datum festlegen"  
        Standardbefehl festlegen  
        Befehl SET DELETED  
        Befehl SET EXACT  
        Befehl SET EXCLUSIVE  
        Befehl "f" festlegen  
    :::column-end:::
    :::column:::
        Befehl "Felder festlegen"  
        Filter Befehl festlegen  
        Fixed-Befehl festlegen  
        Befehl "FullPath festlegen"  
        Befehl "f-Woche festlegen"  
        Befehl "Stunden festlegen"  
        Befehl "Index festlegen"  
        Befehl "Lock festlegen"  
        Befehl "MULTILOCKS festlegen"  
        Near-Befehl festlegen  
        Befehl "nocptrans" festlegen  
        Benachrichtigungs Befehl festlegen  
        Befehl SET NULL  
        Befehl "optimieren" festlegen  
        Befehl "Bestellung festlegen"  
        Befehl SET PATH  
        Befehl "Prozedur festlegen"  
        Beziehungs Befehl festlegen  
        Befehl "Beziehung aus festlegen"  
        Befehl SET REPROCESS  
        Befehl "Skip" festlegen  
    :::column-end:::
    :::column:::
        Befehl "udfparser festlegen"  
        Befehl SET UNIQUE  
        Befehl "Volume festlegen"  
        Setfldstate ()-Funktion  
        Sign ()-Funktion  
        Sin ()-Funktion  
        Skip-Befehl  
        Sortier Befehl  
        Space ()-Funktion  
        SQRT ()-Funktion  
        Store-Befehl  
        Str ()-Funktion  
        "Strauv ()"-Funktion  
        "Stretran ()"-Funktion  
        Stuff ()-Funktion  
        Stuffc ()-Funktion  
        Substr ()-Funktion  
        SUBSTRC ()-Funktion  
        Sum-Befehl  
        SYS (2011)-Funktion  
    :::column-end:::
:::row-end:::

## <a name="t"></a>T  

:::row:::
    :::column:::
        Tablerevert ()-Funktion  
        TABLEUPDATE ()-Funktion  
        Tag ()-Funktion  
        Tagcount ()-Funktion  
        Tagno ()-Funktion  
        System Speicher Variable _TALLY  
    :::column-end:::
    :::column:::
        Tan ()-Funktion  
        Target ()-Funktion  
        Time ()-Funktion  
        Befehl Gesamt  
        System Speicher Variable _TRIGGERLEVEL  
        Trim ()-Funktion  
    :::column-end:::
    :::column:::
        Tto c ()-Funktion  
        Ttod ()-Funktion  
        Txnlevel ()-Funktion  
        Type ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="u"></a>U  

:::row:::
    :::column:::
        Unique ()-Funktion  
        Befehl zum Entsperren  
        Befehl "Aktualisieren"  
    :::column-end:::
    :::column:::
        UPDATE (SQL-Befehl)  
        Upper ()-Funktion  
        Befehl verwenden  
    :::column-end:::
    :::column:::
        USED ()-Funktion  
    :::column-end:::
:::row-end:::

## <a name="v"></a>V  

:::row:::
    :::column:::
        Val ()-Funktion
    :::column-end:::
    :::column:::
        Version ()-Funktion
    :::column-end:::
:::row-end:::

## <a name="w"></a>W  

Week ()-Funktion

## <a name="y"></a>J  

Year ()-Funktion

## <a name="z"></a>Z  

Befehl "zap"
