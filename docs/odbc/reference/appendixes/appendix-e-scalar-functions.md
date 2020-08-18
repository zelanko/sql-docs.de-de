---
description: 'Anhang E: Skalarfunktionen'
title: 'Anhang E: skalare Funktionen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL-92 functions [ODBC]
- scalar functions [ODBC]
- functions [ODBC], scalar
ms.assetid: 59c7cd5e-32d6-43ab-bac3-7010322d105a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4a814de22df4a97e3c3b3abd0ddc30266fe02a30
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411436"
---
# <a name="appendix-e-scalar-functions"></a>Anhang E: Skalarfunktionen
ODBC gibt die folgenden Typen von skalaren Funktionen mit detaillierten Informationen zu jedem dieser Funktionstypen an, die in den entsprechenden Abschnitten dieses Anhangs bereitgestellt werden. Die Funktionsbeschreibungen enthalten zugeordnete Syntax.  
  
 Dieser Anhang enthält die folgenden Themen:  
  
-   [Zeichenfolgenfunktionen](../../../odbc/reference/appendixes/string-functions.md)  
  
-   [Numerische Funktionen](../../../odbc/reference/appendixes/numeric-functions.md)  
  
-   [Uhrzeit-, Datums- und Intervallfunktionen](../../../odbc/reference/appendixes/time-date-and-interval-functions.md)  
  
-   [Systemfunktionen](../../../odbc/reference/appendixes/system-functions.md)  
  
-   [Explicit Data Type Conversion Function (Explizite Datentyp-Konvertierungsfunktion)](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)  
  
-   [SQL-92 CAST-Funktion](../../../odbc/reference/appendixes/sql-92-cast-function.md)  
  
 ODBC stellt keinen Datentyp für Rückgabewerte von skalaren Funktionen dar, da die Funktionen häufig Datenquellen spezifisch sind. Anwendungen sollten die Convert-Skalarfunktion verwenden, wenn dies möglich ist, um die Datentyp Konvertierung zu erzwingen.  
  
## <a name="odbc-and-sql-92-scalar-functions"></a>ODBC-und SQL-92-Skalarfunktionen  
 Die Tabellen in diesem Anhang enthalten Funktionen, die in ODBC 3,0 hinzugefügt wurden, um Sie an SQL-92 auszurichten. Die Funktionen, die für einen bestimmten Typ von skalaren Funktionen wie in ODBC definiert hinzugefügt wurden, werden in jedem Abschnitt angezeigt.  
  
 ODBC und SQL-92 klassifizieren ihre Skalarfunktionen anders. ODBC klassifiziert skalare Funktionen nach Argumenttyp. SQL-92 klassifiziert diese nach Rückgabewert. Beispielsweise wird die Extract-Funktion von ODBC als timedate-Funktion klassifiziert, da das Extract-Field-Argument ein DateTime-Schlüsselwort ist und das Extract-Source-Argument ein DateTime-oder Interval-Ausdruck ist. SQL-92 hingegen klassifiziert Extract als numerische Skalarfunktion, da der Rückgabewert numerisch ist.  
  
 Eine Anwendung kann ermitteln, welche Skalarfunktionen ein Treiber durch Aufrufen von **SQLGetInfo**unterstützt. Informationstypen sind sowohl für ODBC als auch für SQL-92-Klassifizierungen von skalaren Funktionen enthalten. Da diese Klassifizierungen unterschiedlich sind, kann die Unterstützung für einige skalare Funktionen in Informationstypen angegeben werden, die nicht ODBC und SQL-92 entsprechen. Beispielsweise wird die Unterstützung für Extract in ODBC durch den SQL_TIMEDATE_FUNCTIONS Informationstyp angegeben. die Unterstützung für Extract in SQL-92 wird hingegen durch den SQL_SQL92_NUMERIC_VALUE_FUNCTIONS Informationstyp angegeben.
