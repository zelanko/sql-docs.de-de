---
title: Anhang d:-Datentypen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: cfaecb5b3705e2c5affe8c2cda3e42eeaddf4156
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47669378"
---
# <a name="appendix-d-data-types"></a>Anhang D:-Datentypen
ODBC definiert zwei Sätze von Datentypen: SQL-Datentypen und C-Datentypen. SQL-Datentypen angeben, den Datentyp, der in der Datenquelle gespeicherten Daten. C-Datentypen angeben, den Datentyp der im Anwendungspuffer gespeicherten Daten.  
  
 SQL-Datentypen werden vom jeweiligen Datenbankverwaltungssystem in Übereinstimmung mit der SQL-92-Standard definiert. Für jeden SQL-Datentyp, der in der SQL-92-Standard angegeben wird, ODBC definiert einen Typbezeichner, d.h. eine **#define** -Wert, der als Argument in ODBC-Funktionen übergeben oder in den Metadaten eines Resultsets zurückgegeben. Die einzige SQL-92 nicht von ODBC unterstützte Datentypen sind BIT (verfügt über unterschiedliche Eigenschaften der Typ ODBC SQL_BIT) BIT_VARYING, TIME_WITH_TIMEZONE, TIMESTAMP_WITH_TIMEZONE und NATIONAL_CHARACTER. Treiber sind verantwortlich für die Zuordnung von Daten datenquellenspezifischen SQL-Datentypen zu ODBC-SQL-Datentypbezeichner und treiberspezifischen SQL-Datentypbezeichner. Der SQL-Datentyp, die im Feld SQL_DESC_CONCISE_TYPE einen Deskriptor Implementierung angegeben ist.  
  
 ODBC definiert die C-Datentypen und ihre entsprechenden ODBC-Typ-IDs. Eine Anwendung gibt an, die C-Datentyp des Puffers, der Resultsetdaten erhält, übergeben Sie die entsprechenden C-Typ-ID in der *TargetType* Argument in einem Aufruf von **SQLBindCol** oder  **SQLGetData**. Es gibt an, der C-Typ des Puffers, die Anweisungsparameter enthält, übergeben Sie die entsprechenden C-Typ-ID in der *ValueType* Argument in einem Aufruf von **SQLBindParameter**. Die C-Datentyp angegeben ist im Feld SQL_DESC_CONCISE_TYPE einen Anwendungsdienst-Deskriptor.  
  
> [!NOTE]  
>  Es gibt keine Treiber-spezifischen C-Datentypen.  
  
 Jede SQL-Datentyp entspricht einem ODBC-C-Datentyp. Vor der Rückgabe von Daten aus der Datenquelle, konvertiert der Treiber in den angegebenen C-Datentyp. Vor dem Senden von Daten an die Datenquelle, konvertiert der Treiber aus dem angegebenen C-Datentyp.  
  
 Dieser Anhang enthält die folgenden Themen.  
  
-   [Using Data Type Identifiers (Verwenden von Datentypbezeichnern)](../../../odbc/reference/appendixes/using-data-type-identifiers.md)  
  
-   [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md)  
  
-   [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md)  
  
-   [Datentypbezeichnungen und Deskriptoren](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)  
  
-   [Pseudo-Typ-IDs](../../../odbc/reference/appendixes/pseudo-type-identifiers.md)  
  
-   [Übertragen von Daten in ihrer binären Form](../../../odbc/reference/appendixes/transferring-data-in-its-binary-form.md)  
  
-   [Richtlinien für das Intervall und numerische Datentypen](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md)  
  
-   [Einschränkungen des gregorianischen Kalenders](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)  
  
-   [Column Size, Decimal Digits, Transfer Octet Length, and Display Size (Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße)](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
-   [Konvertieren von Daten von SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)  
  
-   [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)  
  
 Eine Erläuterung der ODBC-Datentypen, finden Sie unter [Datentypen in ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md). Informationen zu Treiber-spezifische SQL-Datentypen finden Sie in der vom Treiber-Dokumentation.
