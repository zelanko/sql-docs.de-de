---
title: 'C zu SQL: GUID | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b3b559499273e885e23da10d9093a0ce9ff92393
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306621"
---
# <a name="c-to-sql-guid"></a>C zu SQL: GUID
Der Bezeichner für den GUID ODBC C-Datentyp lautet:  
  
 SQL_C_GUID  
  
 Die folgende Tabelle zeigt die ODBC SQL-Datentypen, in die GUID C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|Spaltenbytelänge >= 36|–|  
|SQL_VARCHAR|Säulenbytelänge < 36|22001|  
|SQL_LONGVARCHAR|Der Datenwert ist keine gültige GUID|22018|  
|SQL_WCHAR|Spaltenzeichenlänge >= 36|–|  
|SQL_WVARCHAR|Spaltenzeichenlänge < 36|22001|  
|SQL_WLONGVARCHAR|Der Datenwert ist keine gültige GUID|22018|  
|SQL_GUID|Keine[a]|–|  
  
 [a] Alle hexidezimalen Werte sind als GUID gültig.  
  
 Der Treiber ignoriert den Längen-/Indikatorwert beim Konvertieren von Daten aus dem GUID C-Datentyp und geht davon aus, dass die Größe des Datenpuffers die Größe des GUID C-Datentyps hat. Der Längen-/Indikatorwert wird im *Argument StrLen_or_Ind* in **SQLPutData** und im Puffer übergeben, der mit dem *Argument StrLen_or_IndPtr* in **SQLBindParameter**angegeben ist. Der Datenpuffer wird mit dem *DataPtr-Argument* in **SQLPutData** und dem *ParameterValuePtr-Argument* in **SQLBindParameter**angegeben.
