---
title: 'C in SQL: GUID | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], guid
- data conversions from C to SQL types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: 9168b0b6-a828-4fef-b8cd-bdf439776f23
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5863935ddf595409d48be79dc646c0994ddeb0b8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019323"
---
# <a name="c-to-sql-guid"></a>C in SQL: GUID
Der Bezeichner für den GUID-ODBC-C-Datentyp ist:  
  
 SQL_C_GUID  
  
 Die folgende Tabelle zeigt die ODBC-SQL-Datentypen, die auf die GUID C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typ-ID|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|Spalte-Byte-Länge > = 36|n/v|  
|SQL_VARCHAR|Spalte Byte Länge < 36|22001|  
|SQL_LONGVARCHAR|Wert ist keine gültige GUID|22018|  
|SQL_WCHAR|Spalte Zeichenlänge > = 36|n/v|  
|SQL_WVARCHAR|Spalte Zeichen Länge < 36|22001|  
|SQL_WLONGVARCHAR|Wert ist keine gültige GUID|22018|  
|SQL_GUID|Keine [a]|n/v|  
  
 [a] alle Hexadezimalwerte sind gültig, als GUID.  
  
 Der Treiber den Längenindikator /-Wert ignoriert, wenn Daten aus der GUID-C-Datentyp zu konvertieren und setzt voraus, dass die Größe des Datenpuffers die Größe der GUID-C-Datentyp ist. Der Längenindikator /-Wert übergeben wird die *StrLen_or_Ind* -Argument in **SQLPutData** und in den Puffer, der mit angegebenen die *StrLen_or_IndPtr* -Argument in **SQLBindParameter**. Der Datenpuffer wird angegeben, mit der *DataPtr* -Argument in **SQLPutData** und die *ParameterValuePtr* -Argument in **SQLBindParameter**.
