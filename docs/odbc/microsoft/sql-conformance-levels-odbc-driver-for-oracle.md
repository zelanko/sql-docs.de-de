---
description: SQL-Konformitätsgrad (ODBC-Treiber für Oracle)
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
ms.openlocfilehash: 78e98aed952ef8b15a4654be9f82e355d1b4177b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483423"
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
