---
title: 'Anhang D: Datentypen | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c1abadb962e3a1ee9327bbb8d84e52d180b4a7e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292460"
---
# <a name="appendix-d-data-types"></a>Anhang D:-Datentypen
ODBC definiert zwei Sätze von Datentypen: SQL-Datentypen und C-Datentypen. SQL-Datentypen geben den Datentyp der in der Datenquelle gespeicherten Daten an. C-Datentypen geben den Datentyp der in Anwendungspuffern gespeicherten Daten an.  
  
 SQL-Datentypen werden von jedem DBMS gemäß dem SQL-92-Standard definiert. Für jeden SQL-Datentyp, der im SQL-92-Standard angegeben ist, definiert ODBC einen Typbezeichner, der ein **#define** Wert ist, der als Argument in ODBC-Funktionen übergeben oder in den Metadaten eines Resultsets zurückgegeben wird. Die einzigen SQL-92-Datentypen, die von ODBC nicht unterstützt werden, sind BIT (der ODBC-SQL_BIT Typ hat unterschiedliche Merkmale), BIT_VARYING, TIME_WITH_TIMEZONE, TIMESTAMP_WITH_TIMEZONE und NATIONAL_CHARACTER. Treiber sind für die Zuordnung von datenquellenspezifischen SQL-Datentypen zu ODBC SQL-Datentypbezeichnern und treiberspezifischen SQL-Datentypbezeichnern verantwortlich. Der SQL-Datentyp wird im Feld SQL_DESC_CONCISE_TYPE eines Implementierungsdeskriptors angegeben.  
  
 ODBC definiert die C-Datentypen und die entsprechenden ODBC-Typ-IDs. Eine Anwendung gibt den C-Datentyp des Puffers an, der Resultsetdaten empfängt, indem der entsprechende C-Typbezeichner im *TargetType-Argument* in einem Aufruf von **SQLBindCol** oder **SQLGetData**übergeben wird. Es gibt den C-Typ des Puffers an, der einen Anweisungsparameter enthält, indem der entsprechende C-Typbezeichner im *ValueType-Argument* in einem Aufruf von **SQLBindParameter**übergeben wird. Der C-Datentyp wird im SQL_DESC_CONCISE_TYPE Feld eines Anwendungsdeskriptors angegeben.  
  
> [!NOTE]  
>  Es gibt keine treiberspezifischen C-Datentypen.  
  
 Jeder SQL-Datentyp entspricht einem ODBC C-Datentyp. Vor der Rückgabe von Daten aus der Datenquelle konvertiert der Treiber diese in den angegebenen C-Datentyp. Vor dem Senden von Daten an die Datenquelle konvertiert der Treiber diese aus dem angegebenen C-Datentyp.  
  
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
  
 Eine Erläuterung der ODBC-Datentypen finden Sie unter [Datentypen in ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md). Informationen zu treiberspezifischen SQL-Datentypen finden Sie in der Dokumentation des Treibers.
