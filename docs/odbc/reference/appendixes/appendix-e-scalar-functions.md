---
title: 'Anhang E: Skalare Funktionen | Microsoft Docs'
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
ms.openlocfilehash: ea354a7f882bd1a75c5f16fb19350d69ca11d375
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292490"
---
# <a name="appendix-e-scalar-functions"></a>Anhang E: Skalarfunktionen
ODBC gibt die folgenden Arten von Skalarfunktionen an, wobei detaillierte Informationen zu jedem dieser Funktionstypen in den entsprechenden Abschnitten dieses Anhangs bereitgestellt werden. Die Funktionsbeschreibungen enthalten die zugehörige Syntax.  
  
 Dieser Anhang enthält die folgenden Themen.  
  
-   [Zeichenfolgenfunktionen](../../../odbc/reference/appendixes/string-functions.md)  
  
-   [Numerische Funktionen](../../../odbc/reference/appendixes/numeric-functions.md)  
  
-   [Uhrzeit-, Datums- und Intervallfunktionen](../../../odbc/reference/appendixes/time-date-and-interval-functions.md)  
  
-   [Systemfunktionen](../../../odbc/reference/appendixes/system-functions.md)  
  
-   [Explicit Data Type Conversion Function (Explizite Datentyp-Konvertierungsfunktion)](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)  
  
-   [SQL-92 CAST-Funktion](../../../odbc/reference/appendixes/sql-92-cast-function.md)  
  
 ODBC schreibt keinen Datentyp für Rückgabewerte aus skalaren Funktionen vor, da die Funktionen häufig datenquellenspezifisch sind. Anwendungen sollten die scalar-Funktion CONVERT verwenden, wann immer dies möglich ist, um die Datentypkonvertierung zu erzwingen.  
  
## <a name="odbc-and-sql-92-scalar-functions"></a>ODBC- und SQL-92-Skalarfunktionen  
 Die Tabellen in diesem Anhang enthalten Funktionen, die in ODBC 3.0 hinzugefügt wurden, um sie an SQL-92 auszurichten. Die Funktionen, die für einen bestimmten Typ von Skalarfunktion hinzugefügt werden, wie in ODBC definiert, sind in jedem Abschnitt angegeben.  
  
 ODBC und SQL-92 klassifizieren ihre Skalarfunktionen unterschiedlich. ODBC klassifiziert skalare Funktionen nach Argumenttyp; SQL-92 klassifiziert sie nach Rückgabewert. Die EXTRACT-Funktion wird z. B. von ODBC als Zeitdatumsfunktion klassifiziert, da das Argument "Extraktfeld" ein datetime-Schlüsselwort ist und das Argument "Extract-Source" ein Datetime- oder Intervallausdruck ist. SQL-92 hingegen klassifiziert EXTRACT als numerische Skalarfunktion, da der Rückgabewert ein numerischer Wert ist.  
  
 Eine Anwendung kann bestimmen, welche Skalarfunktionen ein Treiber unterstützt, indem sie **SQLGetInfo**aufruft. Informationstypen sind sowohl für ODBC als auch für SQL-92-Klassifizierungen von Skalarfunktionen enthalten. Da diese Klassifizierungen unterschiedlich sind, kann die Unterstützung für einige skalare Funktionen in Informationstypen angegeben werden, die nicht ODBC und SQL-92 entsprechen. Die Unterstützung für EXTRACT in ODBC wird z. B. durch den SQL_TIMEDATE_FUNCTIONS-Informationstyp angegeben. Unterstützung für EXTRACT in SQL-92 hingegen wird durch den SQL_SQL92_NUMERIC_VALUE_FUNCTIONS-Informationstyp angezeigt.
