---
description: 'C zu SQL: Jahr-Monat-Intervalle'
title: 'C zu SQL: Jahr-Monat-Intervalle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
- data conversions from C to SQL types [ODBC], year-month intervals
ms.assetid: a0eb7b55-9db0-4375-9210-bddec4593880
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ffd9a3f7f14ff6af93f15521738bebdbc63a8f58
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449022"
---
# <a name="c-to-sql-year-month-intervals"></a>C zu SQL: Jahr-Monat-Intervalle
Die Bezeichner für die ODBC-C-Datentypen Year-Month Interval lauten:  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 In der folgenden Tabelle werden die ODBC-SQL-Datentypen aufgeführt, in die die C-Daten des Jahres Monats Intervalls konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR [a]<br /><br /> SQL_VARCHAR [a]<br /><br /> SQL_LONGVARCHAR [a]|Spalten Byte Länge >= Zeichen Byte Länge<br /><br /> Spalten Byte Länge < Zeichen Byte Länge [a]<br /><br /> Der Datenwert ist kein gültiges intervallliterale.|–<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR [a]<br /><br /> SQL_WVARCHAR [a]<br /><br /> SQL_WLONGVARCHAR [a]|Spalten Zeichen Länge >= Zeichen Länge von Daten<br /><br /> Spalten Zeichenlänge < Zeichen Länge von Daten [a]<br /><br /> Der Datenwert ist kein gültiges intervallliterale.|–<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|Die Konvertierung eines einzelnen Feld Intervalls führte nicht zum Abschneiden ganzer Ziffern.<br /><br /> Die Konvertierung führte zum Abschneiden ganzer Ziffern.|–<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|Der Datenwert wurde ohne Abschneiden beliebiger Felder konvertiert.<br /><br /> Mindestens ein Feld mit einem Datenwert wurde während der Konvertierung abgeschnitten.|–<br /><br /> 22015|  
  
 [a] alle C-Intervall Datentypen können in einen Zeichen Datentyp konvertiert werden.  
  
 [b] Wenn das typanfeld in der Intervall Struktur so ist, dass es sich bei dem Intervall um ein einzelnes Feld (SQL_YEAR oder SQL_MONTH) handelt, kann der C-Typ des Intervalls in alle exakten numerischen Werte (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL oder SQL_NUMERIC) konvertiert werden.  
  
 Die Standard Konvertierung eines Interval-C-Typs erfolgt in den entsprechenden SQL-Typ des Jahres Monats Intervalls.  
  
 Der Treiber ignoriert den Längen-/indikatorenwert beim Umrechnen von Daten aus dem Datentyp Interval c und geht davon aus, dass die Größe des Daten Puffers der Größe des Datentyps Interval c entspricht. Der Wert für die Länge/den Indikator wird im *StrLen_Or_Ind* -Argument in **SQLPutData** und in dem Puffer übergeben, der mit dem *StrLen_or_IndPtr* -Argument in **SQLBindParameter**angegeben wird. Der Datenpuffer wird mit dem *DataPtr* -Argument in **SQLPutData** und dem *ParameterValuePtr* -Argument in **SQLBindParameter**angegeben.
