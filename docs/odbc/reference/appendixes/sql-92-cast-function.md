---
title: SQL-92 CAST-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09d2a2de710dafd4e744166c4219f4c903fd3321
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305061"
---
# <a name="sql-92-cast-function"></a>SQL-92 CAST-Funktion
Die in SQL-92 definierte **CAST-Funktion** entspricht der in ODBC definierten **CONVERT-Funktion.** Die Syntax der entsprechenden Funktionen ist wie folgt:  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 Die FUNKTION SQL-92 **CAST** schreibt vor, welche Datentypen in welche anderen Datentypen konvertiert werden können. (Weitere Informationen finden Sie in der SQL-92-Spezifikation.) Die **CAST-Funktion** wird auf FIPS-Übergangsebene unterstützt.  
  
 Eine Anwendung kann die Unterstützung für die **CAST-Funktion** wie folgt bestimmen:  
  
1.  Rufen Sie **SQLGetInfo** mit dem SQL_SQL_CONFORMANCE-Informationstyp auf. Wenn der Rückgabewert für den Informationstyp SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE oder SQL_SC_SQL92_FULL ist, wird die **CAST-Funktion** unterstützt.  
  
2.  Wenn der Rückgabewert des SQL_SQL_CONFORMANCE-Informationstyps SQL_SC_ENTRY_LEVEL oder 0 ist, rufen Sie **SQLGetInfo** mit dem SQL_SQL92_VALUE_EXPRESSIONS-Informationstyp auf. Wenn das SQL_SVE_CAST Bit gesetzt ist, wird die **CAST-Funktion** unterstützt.
