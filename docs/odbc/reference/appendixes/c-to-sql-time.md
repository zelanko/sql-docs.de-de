---
description: 'C zu SQL: Uhrzeit'
title: 'C zu SQL: Zeit | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], time
- time data type [ODBC]
- converting data from c to SQL types [ODBC], time
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e1711d6a5acffa73a640a0e25f647c53b3daa868
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449042"
---
# <a name="c-to-sql-time"></a>C zu SQL: Uhrzeit
Der Bezeichner für den Zeit-ODBC-C-Datentyp:  
  
 SQL_C_TYPE_TIME  
  
 In der folgenden Tabelle werden die ODBC-SQL-Datentypen angezeigt, in die die C-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von C in SQL-Datentypen](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|SQL-Typbezeichner|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Spalten Byte Länge >= 8<br /><br /> Spalten Byte Länge < 8<br /><br /> Der Datenwert ist keine gültige Zeit.|–<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Spalten Zeichenlänge >= 8<br /><br /> Spalten Zeichenlänge < 8<br /><br /> Der Datenwert ist keine gültige Zeit.|–<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|Der Datenwert ist eine gültige Zeit.<br /><br /> Der Datenwert ist keine gültige Zeit.|–<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Der Datenwert ist ein gültiger Zeitpunkt [a]<br /><br /> Der Datenwert ist keine gültige Zeit.|–<br /><br /> 22007|  
  
 [a] der Datums Teil des Zeitstempels wird auf das aktuelle Datum festgelegt, und der Teil der Sekundenbruchteile des Zeitstempels wird auf 0 (null) festgelegt.  
  
 Informationen dazu, welche Werte in einer SQL_C_TYPE_TIME Struktur gültig sind, finden Sie unter [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md)weiter oben in diesem Anhang.  
  
 Wenn Zeit-C-Daten in Zeichen-SQL-Daten konvertiert werden, sind die resultierenden Zeichendaten im Format "*HH*:*mm*:*SS*".  
  
 Der Treiber ignoriert den Längen-/indikatorenwert beim Umrechnen von Daten aus dem Time-c-Datentyp und geht davon aus, dass die Größe des Daten Puffers die Größe des c-Datentyps ist. Der Wert für die Länge/den Indikator wird im *StrLen_Or_Ind* -Argument in **SQLPutData** und in dem Puffer übergeben, der mit dem *StrLen_or_IndPtr* -Argument in **SQLBindParameter**angegeben wird. Der Datenpuffer wird mit dem *DataPtr* -Argument in **SQLPutData** und dem *ParameterValuePtr* -Argument in **SQLBindParameter**angegeben.
