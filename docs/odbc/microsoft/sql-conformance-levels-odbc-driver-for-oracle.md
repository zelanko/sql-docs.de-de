---
title: SQL-Konformitäts Ebenen (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- ODBC driver for Oracle [ODBC], conformance levels
ms.assetid: 077a6c6a-2c57-42c9-a4fd-4cf0e65cf7e2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 969296e377d398615ad95cf1337c3f9f97d5eb5c
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363400"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>SQL-Konformitätsgrad (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Der ODBC-Treiber für Oracle unterstützt die minimale SQL-Grammatik und Core SQL-Grammatik und unterstützt außerdem die folgenden ODBC-Erweiterungen für SQL:  
  
-   Datums-, Uhrzeit-und Zeitstempel Daten  
  
-   Linke und Rechte äußere Joins  
  
-   Numerische Funktionen:  

    :::row:::
        :::column:::
            Abs  
            Ceiling  
            Cos  
            Exp  
            Etage  
        :::column-end:::
        :::column:::
            Log  
            Log10  
            Mod  
            Pi  
            Stromversorgung  
        :::column-end:::
        :::column:::
            round  
            second  
            Signieren  
            sin  
            sqrt  
        :::column-end:::
        :::column:::
            tan  
            truncate  
        :::column-end:::
    :::row-end:::
    
-   Datumsfunktionen:  

    :::row:::
        :::column:::
            CURDATE  
            Cursor Zeit  
            Tagname  
            DayOfMonth  
        :::column-end:::
        :::column:::
            DayOfWeek  
            Dayofyear  
            Stunde  
            Month (Monat)  
        :::column-end:::
        :::column:::
            MonthName  
            minute  
            now  
            quarter  
        :::column-end:::
        :::column:::
            second  
            week  
            year  
        :::column-end:::
    :::row-end:::

-   Zeichenfolgenfunktionen:  

    :::row:::
        :::column:::
            Ascii  
            Char  
            Concat  
            Lcase  
        :::column-end:::
        :::column:::
            Left  
            Länge  
            Ltrim  
            Replace  
        :::column-end:::
        :::column:::
            Rechts  
            RTRIM  
            SOUNDEX  
            substring  
        :::column-end:::
        :::column:::
            UCase  
        :::column-end:::
    :::row-end:::

-   Typkonvertierungs Funktion:  

    Convert  

-   System Funktionen:  
  
    IFNULL  
    Benutzer
