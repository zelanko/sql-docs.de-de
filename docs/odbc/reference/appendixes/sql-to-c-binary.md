---
title: 'SQL zu C: Binär | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 70b0ce72f650e61b83ec99b0727752612d18da52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298823"
---
# <a name="sql-to-c-binary"></a>SQL zu C: binär
Die Bezeichner für die binären ODBC SQL-Datentypen sind:  
  
 SQL_BINARY  
  
 SQL_VARBINARY  
  
 SQL_LONGVARBINARY  
  
 Die folgende Tabelle zeigt die ODBC C-Datentypen, in die binäre SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typ-Idonid|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|(Byte-Länge der Daten) \* 2 < *BufferLength*<br /><br /> (Byte-Länge der Daten) \* 2 >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes|–<br /><br /> 01004|  
|SQL_C_WCHAR|(Zeichenlänge der Daten) \* 2 < *BufferLength*<br /><br /> (Zeichenlänge der Daten) \* 2 >= *BufferLength*|Daten<br /><br /> Abgeschnittene Daten|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen|–<br /><br /> 01004|  
|SQL_C_BINARY|Bytelänge der Daten <= *BufferLength*<br /><br /> Byte-Länge der Daten > *BufferLength*|Daten<br /><br /> Abgeschnittene Daten|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes|–<br /><br /> 01004|  
  
 Wenn binäre SQL-Daten in Zeichen-C-Daten konvertiert werden, wird jedes Byte (8 Bit) der Quelldaten als zwei ASCII-Zeichen dargestellt. Diese Zeichen sind die ASCII-Zeichendarstellung der Zahl in ihrer hexadezimalen Form. Beispielsweise wird ein binäres 00000001 in "01" und ein Binärformat 11111111 in "FF" konvertiert.  
  
 Der Treiber konvertiert immer einzelne Bytes in Paare hexadezimaler Ziffern und beendet die Zeichenfolge mit einem Nullbyte. Aus diesem Grund wird das letzte Byte des **TargetValuePtr-Puffers* nicht verwendet, wenn *BufferLength* gerade und kleiner als die Länge der konvertierten Daten ist. (Die konvertierten Daten erfordern eine gerade Anzahl von Bytes, das vorletzte Byte ist ein NULL-Byte, und das letzte Byte kann nicht verwendet werden.)  
  
> [!NOTE]  
>  Anwendungsentwickler nadieren davon ab, binäre SQL-Daten an einen Zeichen-C-Datentyp zu binden. Diese Konvertierung ist in der Regel ineffizient und langsam.
