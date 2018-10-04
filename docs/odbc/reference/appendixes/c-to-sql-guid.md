---
title: 'C to SQL: GUID | Microsoft-Dokumentation'
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
manager: craigg
ms.openlocfilehash: af0ed8307652ccf45e7fbfffb6c00355c8a8b004
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745798"
---
# <a name="c-to-sql-guid"></a>C zu SQL: GUID
Der Bezeichner für den GUID-ODBC-C-Datentyp ist:  
  
 SQL_C_GUID  
  
 Die folgende Tabelle zeigt die ODBC-SQL-Datentypen, die auf die GUID C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten von C-in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typ-ID|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|Spalte-Byte-Länge > = 36|–|  
|SQL_VARCHAR|Spalte Byte Länge < 36|22001|  
|SQL_LONGVARCHAR|Wert ist keine gültige GUID|22018|  
|SQL_WCHAR|Spalte Zeichenlänge > = 36|–|  
|SQL_WVARCHAR|Spalte Zeichen Länge < 36|22001|  
|SQL_WLONGVARCHAR|Wert ist keine gültige GUID|22018|  
|SQL_GUID|Keine [a]|–|  
  
 [a] alle Hexadezimalwerte sind gültig, als GUID.  
  
 Der Treiber den Längenindikator /-Wert ignoriert, wenn Daten aus der GUID-C-Datentyp zu konvertieren und setzt voraus, dass die Größe des Datenpuffers die Größe der GUID-C-Datentyp ist. Der Längenindikator /-Wert übergeben wird die *StrLen_or_Ind* -Argument in **SQLPutData** und in den Puffer, der mit angegebenen die *StrLen_or_IndPtr* -Argument in **SQLBindParameter**. Der Datenpuffer wird angegeben, mit der *DataPtr* -Argument in **SQLPutData** und die *ParameterValuePtr* -Argument in **SQLBindParameter**.
