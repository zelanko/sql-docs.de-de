---
title: 'Anhang E: Skalare Funktionen | Microsoft-Dokumentation'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bb5f16485312979e9fb2ad6b3a95dacb79b695d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67996182"
---
# <a name="appendix-e-scalar-functions"></a>Anhang E: Skalarfunktionen
ODBC gibt die folgenden Typen von Skalarfunktionen mit detaillierten Informationen zu den einzelnen Funktionstypen in den entsprechenden Abschnitten in diesem Anhang bereitgestellt. Zugeordnete Syntax wird von die Beschreibungen der Funktionen einschließen.  
  
 Dieser Anhang enthält die folgenden Themen.  
  
-   [Zeichenfolgenfunktionen](../../../odbc/reference/appendixes/string-functions.md)  
  
-   [Numerische Funktionen](../../../odbc/reference/appendixes/numeric-functions.md)  
  
-   [Uhrzeit-, Datums- und Intervallfunktionen](../../../odbc/reference/appendixes/time-date-and-interval-functions.md)  
  
-   [Systemfunktionen](../../../odbc/reference/appendixes/system-functions.md)  
  
-   [Explicit Data Type Conversion Function (Explizite Datentyp-Konvertierungsfunktion)](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)  
  
-   [SQL-92 CAST-Funktion](../../../odbc/reference/appendixes/sql-92-cast-function.md)  
  
 ODBC ist keinen Datentyp für die Rückgabe von Werten aus skalaren Funktionen vorgeben, da die Funktionen häufig Daten datenquellenspezifische sind. Anwendungen sollten die CONVERT-Skalarfunktion nach Möglichkeit, um die datentypkonvertierung erzwingen verwenden.  
  
## <a name="odbc-and-sql-92-scalar-functions"></a>ODBC und SQL-92-Skalarfunktionen  
 Die Tabellen in diesem Anhang enthalten Funktionen, die ODBC 3.0 an einer Verbindung mit SQL-92 hinzugefügt wurden. Diese Funktionen, die für einen bestimmten Typ von skalaren Funktion hinzugefügt wird, wie definiert in ODBC werden in den einzelnen Abschnitten angegeben.  
  
 ODBC und SQL-92 klassifizieren ihre skalaren Funktionen unterschiedlich. ODBC klassifiziert Skalarfunktionen von Argumenttyp; SQL-92 klassifiziert werden nach Wert zurückgibt. Beispielsweise ist die EXTRACT-Funktion als Funktion Timedate durch ODBC, klassifiziert, da das Extract-Feld-Argument ein Datetime-Schlüsselwort ist und das Extract-Source-Argument ein DateTime-Wert oder ein Intervall Ausdruck ist. SQL-92 klassifiziert EXTRAHIEREN auf der anderen Seite als numerische skalare Funktion, da der Rückgabewert ein numerischer ist.  
  
 Eine Anwendung kann bestimmen, welche skalaren Funktionen, die ein Treiber unterstützt werden, durch den Aufruf **SQLGetInfo**. Informationstypen sind sowohl für ODBC als auch für SQL-92-Klassifizierungen von skalaren Funktionen berücksichtigt. Da diese Klassifizierungen unterschiedlich sind, kann die Unterstützung für einige skalaren Funktionen in Informationstypen angegeben werden, die nicht auf ODBC und SQL-92 entsprechen. Unterstützung für EXTRACT in ODBC wird z. B. den Informationstyp SQL_TIMEDATE_FUNCTIONS angezeigt; Unterstützung für EXTRACT in SQL-92, wird durch den Typ der SQL_SQL92_NUMERIC_VALUE_FUNCTIONS Informationen auf der anderen Seite angegeben.
