---
title: SQL-Konformitätsstufen (ODBC-Treiber für Oracle) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300680"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>SQL-Konformitätsgrad (ODBC-Treiber für Oracle)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Der ODBC-Treiber für Oracle unterstützt die Minimale SQL-Grammatik und Core SQL-Grammatik und unterstützt auch die folgenden ODBC-Erweiterungen für SQL:  
  
-   Datums-, Uhrzeit- und Zeitstempeldaten  
  
-   Linke und rechte äußere Verknüpfungen  
  
-   Numerische Funktionen:  
  
    |||||  
    |-|-|-|-|  
    |Abs|Log|round|tan|  
    |Ceiling|Log10|second|truncate|  
    |Cos|Mod|Signieren||  
    |Exp|Pi|sin||  
    |Etage|Power|sqrt||  
  
-   Datumsfunktionen:  
  
    |||||  
    |-|-|-|-|  
    |Curdate|Dayofweek|Monthname|second|  
    |Curtime|Dayofyear|minute|week|  
    |Tagesname|Hour|now|year|  
    |Tagdesmonat|Monat|quarter||  
  
-   Zeichenfolgenfunktionen:  
  
    |||||  
    |-|-|-|-|  
    |Ascii|Left|Rechts|Ucase|  
    |Char|Länge|Rtrim||  
    |Concat|Ltrim|Soundex||  
    |Lcase|Replace|substring||  
  
-   Typ-Konvertierungsfunktion:  
  
    ||  
    |-|  
    |Convert|  
  
-   Systemfunktionen:  
  
    ||  
    |-|  
    |Ifnull|  
    |Benutzer|
