---
title: SQL-Konformitätsgrad (ODBC-Treiber für Oracle) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0bf63b831dace7678f5d3fdf952a9d6d5f60aa6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63313388"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>SQL-Konformitätsgrad (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Der ODBC-Treiber für Oracle unterstützt die minimale SQL-Grammatik und Core-SQL-Grammatik und unterstützt auch die folgenden ODBC-Erweiterungen für SQL:  
  
-   Date, Time und Timestamp-Daten  
  
-   Linke und Rechte äußere joins  
  
-   Numerische Funktionen:  
  
    |||||  
    |-|-|-|-|  
    |Abs|Log|round|tan|  
    |Obergrenze|Log10|second|truncate|  
    |Cos|Mod|Anmelden||  
    |Exponential|Pi|sin||  
    |Floor|Power|sqrt||  
  
-   Datumsfunktionen:  
  
    |||||  
    |-|-|-|-|  
    |CURDATE|DayOfWeek|MonthName|second|  
    |Curtime|Dayofyear|minute|week|  
    |DAYNAME|Hour|jetzt|year|  
    |DayOfMonth|Month|Quartal||  
  
-   Zeichenfolgenfunktionen:  
  
    |||||  
    |-|-|-|-|  
    |Ascii|Left|Richting|UCase|  
    |Char|Länge|rtrim||  
    |Concat|Ltrim|SOUNDEX||  
    |Lcase|Ersetzen|substring||  
  
-   Typkonvertierungs-Funktion:  
  
    ||  
    |-|  
    |Konvertieren|  
  
-   Systemfunktionen:  
  
    ||  
    |-|  
    |IFNULL|  
    |Benutzer|
