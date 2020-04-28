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
ms.openlocfilehash: e283bbc13f0d0dda055b047b027f7b9816502df5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300680"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>SQL-Konformitätsgrad (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Der ODBC-Treiber für Oracle unterstützt die minimale SQL-Grammatik und Core SQL-Grammatik und unterstützt außerdem die folgenden ODBC-Erweiterungen für SQL:  
  
-   Datums-, Uhrzeit-und Zeitstempel Daten  
  
-   Linke und Rechte äußere Joins  
  
-   Numerische Funktionen:  
  
    |||||  
    |-|-|-|-|  
    |Abs|Protokoll|round|tan|  
    |Ceiling|Log10|second|truncate|  
    |Cos|Mod|Signieren||  
    |Exp|Pi|sin||  
    |Etage|Power|sqrt||  
  
-   Datumsfunktionen:  
  
    |||||  
    |-|-|-|-|  
    |CURDATE|DayOfWeek|MonthName|second|  
    |Cursor Zeit|Dayofyear|minute|week|  
    |Tagname|Hour|now|year|  
    |DayOfMonth|Monat|quarter||  
  
-   Zeichenfolgenfunktionen:  
  
    |||||  
    |-|-|-|-|  
    |Ascii|Left|Rechts|UCase|  
    |Char|Länge|RTRIM||  
    |Concat|Ltrim|SOUNDEX||  
    |Lcase|Replace|substring||  
  
-   Typkonvertierungs Funktion:  
  
    ||  
    |-|  
    |Convert|  
  
-   System Funktionen:  
  
    ||  
    |-|  
    |IFNULL|  
    |Benutzer|
