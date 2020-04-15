---
title: 'SQL zu C: Jahres-Monatsintervalle | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba79a4d6165a43676634a6b79db56b88f5bcc234
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296390"
---
# <a name="sql-to-c-year-month-intervals"></a>SQL zu C: Jahr-Monat-Intervalle

Die Bezeichner für das Jahres-Monats-Intervall ODBC SQL-Datentypen sind die folgenden:

- SQL_INTERVAL_MONTH
- SQL_INTERVAL_YEAR
- SQL_INTERVAL_YEAR_TO_MONTH

Die folgende Tabelle zeigt die ODBC C-Datentypen, in die SQL-Daten für das Jahres-Monats-Intervall konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|C-Typ-Idonid|Test|TargetValuePtr|StrLen_or_IndPtr|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_INTERVAL_MONTH[a]<br /><br /> SQL_C_INTERVAL_YEAR[a]<br /><br /> SQL_C_INTERVAL_YEAR_TO_MONTH[a]|Trailing-Felder-Teil nicht abgeschnitten<br /><br /> Trailing-Felder-Teil abgeschnitten<br /><br /> Führende Genauigkeit des Ziels ist nicht groß genug, um Daten aus der Quelle zu halten|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes<br /><br /> Nicht definiert|–<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT[b]<br /><br /> SQL_C_UTINYINT[b]<br /><br /> SQL_C_USHORT[b]<br /><br /> SQL_C_SHORT[b]<br /><br /> SQL_C_SLONG[b]<br /><br /> SQL_C_ULONG[b]<br /><br /> SQL_C_NUMERIC[b]<br /><br /> SQL_C_BIGINT[b]|Intervallgenauigkeit war ein einzelnes Feld und die Daten wurden ohne Abschneide konvertiert<br /><br /> Intervallgenauigkeit war ein einzelnes Feld und abgeschnitten<br /><br /> Intervallgenauigkeit war kein einzelnes Feld|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Größe des Datentyps C<br /><br /> Länge der Daten in Bytes<br /><br /> Größe des Datentyps C|–<br /><br /> 22003<br /><br /> 22015|  
|SQL_C_BINARY|Bytelänge der Daten <= *BufferLength*<br /><br /> Byte-Länge der Daten > *BufferLength*|Daten<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_CHAR|Zeichenbytelänge < *BufferLength*<br /><br /> Anzahl der ganzen (im Gegensatz zu bruchstückhzu- ) Ziffern < *BufferLength*<br /><br /> Anzahl der ganzen (im Gegensatz zu fraktionierten) Ziffern >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Größe des Datentyps C<br /><br /> Größe des Datentyps C<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Zeichenlänge < *BufferLength*<br /><br /> Anzahl der ganzen (im Gegensatz zu bruchstückhzu- ) Ziffern < *BufferLength*<br /><br /> Anzahl der ganzen (im Gegensatz zu fraktionierten) Ziffern >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten<br /><br /> Nicht definiert|Größe des Datentyps C<br /><br /> Größe des Datentyps C<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
  
 [a] Ein Jahres-Monats-Intervall SQL-Typ kann in jeden Jahres-Monats-Intervall-C-Typ konvertiert werden.  
  
 [b] Wenn es sich bei der Intervallgenauigkeit um ein einzelnes Feld (ein Feld von YEAR oder MONTH) handelt, kann der INTERVALL-SQL-Typ in eine beliebige numerische (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG oder SQL_C_NUMERIC) konvertiert werden.  

## <a name="default-conversions"></a>Standardkonvertierungen

Die Standardkonvertierung eines Intervall-SQL-Typs ist der entsprechende C-Intervalldatentyp. Die Anwendung bindet dann die Spalte oder den Parameter (oder legt das SQL_DESC_DATA_PTR Feld im entsprechenden Datensatz der ARD fest), um auf die initialisierte SQL_INTERVAL_STRUCT-Struktur zu verweisen (oder übergibt einen Zeiger an die SQL_ INTERVAL_STRUCT Struktur als *TargetValuePtr-Argument* in einem Aufruf von **SQLGetData**).
