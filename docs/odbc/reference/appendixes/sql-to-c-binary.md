---
title: 'SQL zu C: binär | | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], binary
- binary data type [ODBC]
- data conversions from SQL to C types [ODBC], binary
- binary data transfers [ODBC]
ms.assetid: 8c519072-ae4c-4d32-9d4e-775e3d3d6389
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e280afb03eeac46a58943d276137e2019340a0a2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056998"
---
# <a name="sql-to-c-binary"></a>SQL zu C: binär
Die Bezeichner für die binären ODBC-SQL-Datentypen lauten wie folgt:  
  
 SQL_BINARY  
  
 SQL_VARBINARY  
  
 SQL_LONGVARBINARY  
  
 In der folgenden Tabelle werden die ODBC-C-Datentypen angezeigt, in die binäre SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typbezeichner|Test|**Targetvalueptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|(Byte Länge der Daten) \* 2 < *BufferLength*<br /><br /> (Byte Länge der Daten) \* 2 >= *BufferLength*|Data<br /><br /> Abgeschnittene Daten|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes|–<br /><br /> 01004|  
|SQL_C_WCHAR|(Zeichen Länge von Daten) \* 2 < *BufferLength*<br /><br /> (Zeichen Länge von Daten) \* 2 >= *BufferLength*|Data<br /><br /> Abgeschnittene Daten|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen|–<br /><br /> 01004|  
|SQL_C_BINARY|Byte Länge der Daten <= *BufferLength*<br /><br /> Byte Länge der Daten > *BufferLength*|Data<br /><br /> Abgeschnittene Daten|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes|–<br /><br /> 01004|  
  
 Wenn binäre SQL-Daten in Zeichen-C-Daten konvertiert werden, werden die einzelnen Bytes (8 Bits) der Quelldaten als zwei ASCII-Zeichen dargestellt. Diese Zeichen sind die ASCII-Zeichen Darstellung der Zahl in der hexadezimalen Form. Beispielsweise wird ein binäres 00000001 in "01" konvertiert, und eine binäre 11111111 wird in "FF" konvertiert.  
  
 Der Treiber konvertiert einzelne Bytes immer in Paare von hexadezimalen Ziffern und beendet die Zeichenfolge mit einem NULL-Byte. Wenn *BufferLength* gerade ist und kleiner als die Länge der konvertierten Daten ist, wird das letzte Byte des **targetvalueptr* -Puffers nicht verwendet. (Die konvertierten Daten erfordern eine gerade Anzahl von Bytes, das Next-to-Last-Byte ist ein NULL-Byte, und das letzte Byte kann nicht verwendet werden.)  
  
> [!NOTE]  
>  Anwendungsentwickler werden davon abgeraten, binäre SQL-Daten an einen C-Zeichen Datentyp zu binden. Diese Konvertierung ist in der Regel ineffizient und langsam.
