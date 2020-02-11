---
title: 'Anhang D: Datentypen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], defined
- SQL data types [ODBC], defined
- data types [ODBC]
- data types [ODBC], about data types
ms.assetid: 981d49c3-3531-4543-aa75-5bd9e4f67000
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7e709c74062e31483b042c3930572fb63ca8c786
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67996216"
---
# <a name="appendix-d-data-types"></a>Anhang D:-Datentypen
ODBC definiert zwei Sätze von Datentypen: SQL-Datentypen und C-Datentypen. SQL-Datentypen geben den Datentyp der Daten an, die in der Datenquelle gespeichert sind. C-Datentypen geben den Datentyp der in Anwendungs Puffern gespeicherten Daten an.  
  
 SQL-Datentypen werden von jedem DBMS gemäß dem SQL-92-Standard definiert. Für jeden SQL-Datentyp, der im SQL-92-Standard angegeben ist, definiert ODBC einen Typbezeichner. Hierbei handelt es sich um einen **#define** Wert, der als Argument in ODBC-Funktionen oder in den Metadaten eines Resultsets zurückgegeben wird. Die einzigen SQL-92-Datentypen, die nicht von ODBC unterstützt werden, sind Bit (der ODBC-SQL_BIT Typ weist andere Merkmale auf), BIT_VARYING, TIME_WITH_TIMEZONE, TIMESTAMP_WITH_TIMEZONE und NATIONAL_CHARACTER. Treiber sind für das Mapping von Datenquellen spezifischen SQL-Datentypen zu ODBC-SQL-Datentyp bezeichern und treiberspezifischen SQL-Datentyp bezeichern verantwortlich. Der SQL-Datentyp wird im SQL_DESC_CONCISE_TYPE-Feld eines Implementierungs Deskriptors angegeben.  
  
 ODBC definiert die C-Datentypen und ihre entsprechenden ODBC-Typbezeichner. Eine Anwendung gibt den c-Datentyp des Puffers an, der Resultsetdaten empfängt, indem der entsprechende C-Typbezeichner im *TargetType* -Argument in einem **SQLBindCol** -oder **SQLGetData**-Befehl übergeben wird. Er gibt den c-Typ des Puffers an, der einen Anweisungs Parameter enthält, indem er den entsprechenden c-Typbezeichner im *ValueType* -Argument in einem **SQLBindParameter**-Befehl übergibt. Der C-Datentyp wird im SQL_DESC_CONCISE_TYPE-Feld eines Anwendungs Deskriptors angegeben.  
  
> [!NOTE]  
>  Es sind keine treiberspezifischen C-Datentypen vorhanden.  
  
 Jeder SQL-Datentyp entspricht einem ODBC-C-Datentyp. Vor dem Zurückgeben von Daten aus der Datenquelle konvertiert der Treiber Sie in den angegebenen C-Datentyp. Vor dem Senden von Daten an die Datenquelle konvertiert der Treiber ihn vom angegebenen C-Datentyp.  
  
 Dieser Anhang enthält die folgenden Themen:  
  
-   [Verwenden von Datentypbezeichnern](../../../odbc/reference/appendixes/using-data-type-identifiers.md)  
  
-   [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md)  
  
-   [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md)  
  
-   [Datentypbezeichner und Deskriptoren](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)  
  
-   [Pseudotypbezeichner](../../../odbc/reference/appendixes/pseudo-type-identifiers.md)  
  
-   [Übertragen von Daten in ihrer binären Form](../../../odbc/reference/appendixes/transferring-data-in-its-binary-form.md)  
  
-   [Richtlinien für die Datentypen „Intervall“ und „Numerisch“](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md)  
  
-   [Einschränkungen des gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)  
  
-   [Spaltengröße, Dezimalstellen, Länge der Übertragungsoktette und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
-   [Konvertieren von Daten von SQL- zu C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)  
  
-   [Konvertieren von Daten von C- zu SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)  
  
 Eine Erläuterung der ODBC-Datentypen finden Sie unter [Datentypen in ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md). Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.
