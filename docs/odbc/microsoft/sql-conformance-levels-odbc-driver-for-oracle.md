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
ms.openlocfilehash: 241f4f3da12f63c15d917a0e47cb13ad0e96e6e3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063349"
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
    |Exponential|PI|sin||  
    |Floor|Power|"SQRT"||  
  
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
    |ASCII|Links|Richting|UCase|  
    |Char|Länge|RTrim||  
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
