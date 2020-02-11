---
title: SQL-92-CAST Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68057058"
---
# <a name="sql-92-cast-function"></a>SQL-92 CAST-Funktion
Die in SQL-92 definierte **Cast** -Funktion entspricht der in ODBC definierten **Convert** -Funktion. Die Syntax der äquivalenten Funktionen lautet wie folgt:  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 Die SQL-92- **Cast** Funktion gibt an, welche Datentypen in welche anderen Datentypen konvertiert werden können. (Weitere Informationen finden Sie in der SQL-92-Spezifikation.) Die **Cast** -Funktion wird auf der Übergangs Ebene "fps" unterstützt.  
  
 Eine Anwendung kann die Unterstützung für die **Cast** -Funktion wie folgt bestimmen:  
  
1.  Aufrufen von **SQLGetInfo** mit dem SQL_SQL_CONFORMANCE Informationstyp. Wenn der Rückgabewert für den Informationstyp SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE oder SQL_SC_SQL92_FULL ist, wird die **Cast** -Funktion unterstützt.  
  
2.  Wenn der Rückgabewert des SQL_SQL_CONFORMANCE-Informations Typs SQL_SC_ENTRY_LEVEL oder 0 ist, nennen Sie **SQLGetInfo** mit dem SQL_SQL92_VALUE_EXPRESSIONS Informationstyp. Wenn das SQL_SVE_CAST Bit festgelegt ist, wird die **Cast** -Funktion unterstützt.
