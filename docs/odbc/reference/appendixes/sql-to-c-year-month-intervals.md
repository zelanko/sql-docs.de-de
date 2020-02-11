---
title: 'SQL zu C: Jahr-Monat-Intervalle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], about converting
- data conversions from SQL to C types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
ms.assetid: 1233634b-8214-420f-b872-3b2630105ba4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2c7412226dd0674022da022b0a0a63e5bf2063cf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68065043"
---
# <a name="sql-to-c-year-month-intervals"></a>SQL zu C: Jahr-Monat-Intervalle

Die Bezeichner für die ODBC-SQL-Datentypen für das Jahr-Monat-Intervall lauten wie folgt:

- SQL_INTERVAL_MONTH
- SQL_INTERVAL_YEAR
- SQL_INTERVAL_YEAR_TO_MONTH

In der folgenden Tabelle werden die ODBC-C-Datentypen angezeigt, in die SQL-Daten im Jahr-Monat-Intervall konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|C-Typbezeichner|Test|Targetvalueptr|StrLen_or_IndPtr|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_INTERVAL_MONTH [a]<br /><br /> SQL_C_INTERVAL_YEAR [a]<br /><br /> SQL_C_INTERVAL_YEAR_TO_MONTH [a]|Teil der nachfolgenden Felder nicht abgeschnitten<br /><br /> Teil der nachfolgenden Felder abgeschnitten<br /><br /> Die führende Genauigkeit des Ziels ist nicht groß genug zum Speichern von Daten aus der Quelle.|Data<br /><br /> Abgeschnittene Daten<br /><br /> Undefined|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes<br /><br /> Undefined|–<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT [b]<br /><br /> SQL_C_UTINYINT [b]<br /><br /> SQL_C_USHORT [b]<br /><br /> SQL_C_SHORT [b]<br /><br /> SQL_C_SLONG [b]<br /><br /> SQL_C_ULONG [b]<br /><br /> SQL_C_NUMERIC [b]<br /><br /> SQL_C_BIGINT [b]|Die Intervall Genauigkeit war ein einzelnes Feld, und die Daten wurden ohne Abschneiden konvertiert.<br /><br /> Intervall Genauigkeit war ein einzelnes Feld und ein abgeschnittenes ganzes<br /><br /> Intervall Genauigkeit war kein einzelnes Feld|Data<br /><br /> Abgeschnittene Daten<br /><br /> Undefined|Größe des C-Datentyps<br /><br /> Länge der Daten in Bytes<br /><br /> Größe des C-Datentyps|–<br /><br /> 22003<br /><br /> 22015|  
|SQL_C_BINARY|Byte Länge der Daten <= *BufferLength*<br /><br /> Byte Länge der Daten > *BufferLength*|Data<br /><br /> Undefined|Länge der Daten in Bytes<br /><br /> Undefined|–<br /><br /> 22003|  
|SQL_C_CHAR|Zeichen Byte Länge < *BufferLength*<br /><br /> Anzahl ganzer (im Gegensatz zu Bruch Ziffern) Ziffern < *BufferLength*<br /><br /> Anzahl ganzer (im Gegensatz zu Bruch Ziffern) Ziffern >= *BufferLength*|Data<br /><br /> Abgeschnittene Daten<br /><br /> Undefined|Größe des C-Datentyps<br /><br /> Größe des C-Datentyps<br /><br /> Undefined|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Zeichen Länge < *BufferLength*<br /><br /> Anzahl ganzer (im Gegensatz zu Bruch Ziffern) Ziffern < *BufferLength*<br /><br /> Anzahl ganzer (im Gegensatz zu Bruch Ziffern) Ziffern >= *BufferLength*|Data<br /><br /> Abgeschnittene Daten<br /><br /> Undefined|Größe des C-Datentyps<br /><br /> Größe des C-Datentyps<br /><br /> Undefined|–<br /><br /> 01004<br /><br /> 22003|  
  
 [a] ein Jahr-Monat-Intervall-SQL-Typ kann in einen beliebigen Jahr-Monat-Intervall-C-Typ konvertiert werden.  
  
 [b] Wenn die Intervall Genauigkeit ein einzelnes Feld (ein Jahr oder ein Monat) ist, kann der SQL-Datentyp für das Intervall in eine exakte numerische (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG oder SQL_C_NUMERIC) konvertiert werden.  

## <a name="default-conversions"></a>Standard Konvertierungen

Die Standard Konvertierung eines SQL-Datentyps für das Intervall erfolgt in den entsprechenden Datentyp von C-Intervall. Die Anwendung bindet dann die Spalte oder den Parameter (oder legt das SQL_DESC_DATA_PTR Feld im entsprechenden Datensatz der ARD) so fest, dass Sie auf die initialisierte SQL_INTERVAL_STRUCT Struktur verweist (oder übergibt einen Zeiger an die SQL_ INTERVAL_STRUCT Struktur als *targetvalueptr* -Argument in einem **SQLGetData**-Befehl).
