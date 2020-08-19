---
description: 'SQL zu C: Zeitstempel'
title: 'SQL zu C: Timestamp | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- timestamp data type [ODBC]
- converting data from SQL to C types [ODBC], timestamp
- data conversions from SQL to C types [ODBC], timestamp
ms.assetid: 6a0617cf-d8c0-4316-8bb4-e6ddb45d7bf1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2a2904f01b5ecadbfc224d052366197e41163cd9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429542"
---
# <a name="sql-to-c-timestamp"></a>SQL zu C: Zeitstempel

Der Bezeichner für den Zeitstempel-ODBC-SQL-Datentyp lautet wie folgt:

- SQL_TYPE_TIMESTAMP  

In der folgenden Tabelle werden die ODBC-C-Datentypen aufgeführt, in die SQL-Daten mit Zeitstempel konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|C-Typbezeichner|Test|**Targetvalueptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|Länge des *pufflength* -> Zeichens<br /><br /> 20 <= *BufferLength* <= Zeichen Byte Länge<br /><br /> *BufferLength* < 20|Daten<br /><br /> Abgeschnittene Daten [b]<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Länge der Daten in Bytes<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Länge der *BufferLength* -> Zeichen<br /><br /> 20 <= *BufferLength* <= Zeichen Länge<br /><br /> *BufferLength* < 20|Daten<br /><br /> Abgeschnittene Daten [b]<br /><br /> Nicht definiert|Länge der Daten in Zeichen<br /><br /> Länge der Daten in Zeichen<br /><br /> Nicht definiert|–<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Byte Länge der Daten <= *BufferLength*<br /><br /> Byte Länge der Daten > *BufferLength*|Daten<br /><br /> Nicht definiert|Länge der Daten in Bytes<br /><br /> Nicht definiert|–<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Der Uhrzeit Teil des Zeitstempels ist 0 (null) [a]<br /><br /> Der Uhrzeit Teil des Zeitstempels ist ungleich 0 (null) [a]|Daten<br /><br /> Abgeschnittene Daten [c]|6 [f]<br /><br /> 6 [f]|–<br /><br /> 01S07|  
|SQL_C_TYPE_TIME|Der Teil des Zeitstempels der Sekundenbruchteile ist 0 (null) [a]<br /><br /> Der Teil des Zeitstempels in Sekundenbruchteilen ist ungleich 0 (null) [a]|Daten [d]<br /><br /> Abgeschnittene Daten [d], [e]|6 [f]<br /><br /> 6 [f]|–<br /><br /> 01S07|  
|SQL_C_TYPE_TIMESTAMP|Der Teil des Zeitstempels der Sekundenbruchteile wird nicht abgeschnitten [a]<br /><br /> Teil des Zeitstempels mit Sekundenbruchteilen wird abgeschnitten [a]|Daten [e]<br /><br /> Abgeschnittene Daten [e]|16 [f]<br /><br /> 16 [f]|–<br /><br /> 01S07|  

 [a] der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **targetvalueptr* die Größe des C-Datentyps ist.  
  
 [b] die Sekundenbruchteile des Zeitstempels werden abgeschnitten.  
  
 [c] der Uhrzeit Teil des Zeitstempels wird abgeschnitten.  
  
 [d] der Datums Teil des Zeitstempels wird ignoriert.  
  
 [e] der Teil der Sekundenbruchteile des Zeitstempels wird abgeschnitten.  
  
 [f] Dies ist die Größe des entsprechenden C-Datentyps.  

Wenn SQL-Zeitstempel Daten in Zeichen-C-Daten konvertiert werden, befindet sich die resultierende Zeichenfolge im Format "*JJJJ* - *mm* - *DD* *HH*:*mm*:*SS*[.* f...*] " das Format, in dem bis zu neun Ziffern für Sekundenbruchteile verwendet werden können. Dieses Format wird von der Einstellung für das Windows-® Land nicht beeinträchtigt. (Mit Ausnahme des Dezimal Trennzeichens und der Sekundenbruchteile muss das gesamte Format verwendet werden, unabhängig von der Genauigkeit des SQL-Datentyps Zeitstempel.)
