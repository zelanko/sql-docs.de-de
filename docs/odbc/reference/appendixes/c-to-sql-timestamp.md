---
description: 'C zu SQL: Zeitstempel'
title: 'C zu SQL: Timestamp | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], timestamp
- timestamp data type [ODBC]
- converting data from c to SQL types [ODBC], timestamp
ms.assetid: 0e08bfff-68f9-4648-9558-09b57fea08ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e51d82e8acd59c8b4e6f5a8385720b0bd38eba4c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449032"
---
# <a name="c-to-sql-timestamp"></a>C zu SQL: Zeitstempel
Der Bezeichner für den Zeitstempel-ODBC-C-Datentyp lautet:  
  
 SQL_C_TYPE_TIMESTAMP  
  
 In der folgenden Tabelle werden die ODBC-SQL-Datentypen aufgeführt, in die Zeitstempel-C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Spalten Byte Länge >= Zeichen Byte Länge<br /><br /> 19 <= Spalten Byte Länge < Länge des Zeichen bytes<br /><br /> Spalten Byte Länge < 19<br /><br /> Der Datenwert ist kein gültiger Zeitstempel.|–<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Spalten Zeichen Länge >= Zeichen Länge von Daten<br /><br /> 19 <= Spalten Zeichen Länge < Zeichen Länge von Daten<br /><br /> Spalten Zeichenlänge < 19<br /><br /> Der Datenwert ist kein gültiger Zeitstempel.|–<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Zeitfelder sind 0 (null)<br /><br /> Zeitfelder ungleich NULL<br /><br /> Der Datenwert enthält kein gültiges Datum.|–<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIME|Felder für Sekundenbruchteile sind 0 (null) [a]<br /><br /> Sekundenbruchteile sind nicht 0 (null) [a]<br /><br /> Der Datenwert enthält keine gültige Zeit.|–<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Felder mit Sekundenbruchteilen werden nicht abgeschnitten.<br /><br /> Felder mit Sekundenbruchteilen werden abgeschnitten.<br /><br /> Der Datenwert ist kein gültiger Zeitstempel.|–<br /><br /> 22008<br /><br /> 22007|  
  
 [a] die Datumsfelder der Zeitstempel Struktur werden ignoriert.  
  
 Informationen dazu, welche Werte in einer SQL_C_TIMESTAMP Struktur gültig sind, finden Sie unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md)weiter oben in diesem Anhang.  
  
 Wenn Zeitstempel-C-Daten in Zeichen-SQL-Daten konvertiert werden, befinden sich die resultierenden Zeichendaten im "*JJJJ* - *mm* - *DD* *HH*:*mm*:*SS*[.* f...*] " Ges.  
  
 Der Treiber ignoriert den Längen-/indikatorenwert beim Umrechnen von Daten aus dem Datentyp Zeitstempel c und geht davon aus, dass die Größe des Daten Puffers die Größe des Zeitstempel-c-Datentyps ist. Der Wert für die Länge/den Indikator wird im *StrLen_Or_Ind* -Argument in **SQLPutData** und in dem Puffer übergeben, der mit dem *StrLen_or_IndPtr* -Argument in **SQLBindParameter**angegeben wird. Der Datenpuffer wird mit dem *DataPtr* -Argument in **SQLPutData** und dem *ParameterValuePtr* -Argument in **SQLBindParameter**angegeben.
