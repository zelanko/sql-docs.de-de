---
title: 'C zu SQL: GUID | Microsoft-Dokumentation'
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306621"
---
# <a name="c-to-sql-guid"></a>C zu SQL: GUID
Der Bezeichner für den GUID ODBC-C-Datentyp lautet:  
  
 SQL_C_GUID  
  
 In der folgenden Tabelle werden die ODBC-SQL-Datentypen angezeigt, in die GUID-C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|Spalten Byte Länge >= 36|Nicht zutreffend|  
|SQL_VARCHAR|Spalten Byte Länge < 36|22001|  
|SQL_LONGVARCHAR|Der Datenwert ist keine gültige GUID.|22018|  
|SQL_WCHAR|Spalten Zeichenlänge >= 36|Nicht zutreffend|  
|SQL_WVARCHAR|Spalten Zeichenlänge < 36|22001|  
|SQL_WLONGVARCHAR|Der Datenwert ist keine gültige GUID.|22018|  
|SQL_GUID|Keine [a]|Nicht zutreffend|  
  
 [a] alle hexadezimalen Werte sind als GUID gültig.  
  
 Der Treiber ignoriert den Längen-/indikatorenwert beim Umrechnen von Daten aus dem Datentyp GUID c und geht davon aus, dass die Größe des Daten Puffers der Größe des Datentyps GUID c entspricht. Der Wert für die Länge/den Indikator wird im *StrLen_Or_Ind* -Argument in **SQLPutData** und in dem Puffer übergeben, der mit dem *StrLen_or_IndPtr* -Argument in **SQLBindParameter**angegeben wird. Der Datenpuffer wird mit dem *DataPtr* -Argument in **SQLPutData** und dem *ParameterValuePtr* -Argument in **SQLBindParameter**angegeben.
