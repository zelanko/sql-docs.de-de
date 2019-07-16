---
title: SQL-92 CAST-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6682ae98f2da64f6936049bee96fe2fff2a84db
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057058"
---
# <a name="sql-92-cast-function"></a>SQL-92 CAST-Funktion
Die **Umwandlung** in SQL-92 definierten Funktion entspricht der **konvertieren** in ODBC definierte Funktion. Die Syntax der entsprechenden Funktionen lautet wie folgt aus:  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 Die SQL-92 **Umwandlung** Funktion ist es erforderlich, welche Datentypen in die andere Datentypen konvertiert werden können. (Weitere Informationen finden Sie in der SQL-92-Spezifikation.) Die **Umwandlung** -Funktion wird auf der FIPS-Transitional Ebene unterstützt.  
  
 Eine Anwendung kann die Unterstützung für bestimmen die **Umwandlung** -Funktion wie folgt:  
  
1.  Rufen Sie **SQLGetInfo** mit dem Typ der SQL_SQL_CONFORMANCE-Informationen. Wenn der Rückgabewert für den Informationstyp SQL_SC_FIPS127_2_TRANSITIONAL SQL_SC_SQL92_INTERMEDIATE oder SQL_SC_SQL92_FULL, ist die **Umwandlung** -Funktion wird unterstützt.  
  
2.  Wenn der Rückgabewert des Typs Informationen SQL_SQL_CONFORMANCE SQL_SC_ENTRY_LEVEL oder 0 ist, rufen Sie **SQLGetInfo** mit dem Typ der SQL_SQL92_VALUE_EXPRESSIONS-Informationen. Wenn das SQL_SVE_CAST Bit festgelegt ist, die **Umwandlung** -Funktion wird unterstützt.
