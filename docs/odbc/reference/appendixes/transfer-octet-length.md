---
title: Länge des Oktetts übertragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transfer octet length of data types [ODBC]
- size of data types [ODBC]
- SQL data types [ODBC], column characteristics
- data types [ODBC], transfer octet length
ms.assetid: 9fdc9762-e203-4cff-9212-54f450bf18d9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a92a9ead66736ff2b72813d6d4cbec5acfcda4fe
ms.sourcegitcommit: 82b70c39550402a2b0b327db32bf5ecf88b50d3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73032971"
---
# <a name="transfer-octet-length"></a>Länge der Übertragungsoktette
Die Länge eines Spalten Übertragungs-Oktetts ist die maximale Anzahl von Bytes, die an die Anwendung zurückgegeben werden, wenn Daten in den Standard-C-Datentyp übertragen werden. Bei Zeichendaten enthält die Länge des okteckzeichens für die Übertragung keinen Platz für das NULL-Terminierungs Zeichen. Die Länge der Übertragungs Oktett einer Spalte kann sich von der Anzahl der Bytes unterscheiden, die zum Speichern der Daten in der Datenquelle erforderlich sind.  
  
 In der folgenden Tabelle ist die Länge des Übertragungs-Oktetts angegeben, die für jeden ODBC-SQL-Datentyp definiert ist.  
  
|SQL-Typbezeichner|Länge|  
|-------------------------|------------|  
|Alle Zeichen Typen [a]|Die definierte oder die maximale Länge (für Variablentyp) der Spalte in Bytes. Dies ist der gleiche Wert wie das Deskriptorfeld SQL_DESC_OCTET_LENGTH.|  
|SQL_DECIMAL<br />SQL_NUMERIC|Die Anzahl von Bytes, die zum Speichern der Zeichen Darstellung dieser Daten erforderlich sind, wenn der Zeichensatz ANSI ist, und zweimal diese Zahl, wenn der Zeichensatz Unicode ist. Dies ist die maximale Anzahl von Ziffern plus zwei, da die Daten als Zeichenfolge zurückgegeben werden und Zeichen für die Ziffern, ein Vorzeichen und einen Dezimaltrennzeichen benötigt werden. Beispielsweise ist die Übertragungs Länge einer Spalte, die als numerisch (10, 3) definiert ist, 12.|  
|SQL_TINYINT|1|  
|SQL_SMALLINT|2|  
|SQL_INTEGER|4|  
|SQL_BIGINT| 8 |  
|SQL_REAL|4|  
|SQL_FLOAT|8|  
|SQL_DOUBLE|8|  
|SQL_BIT|1|  
|Alle binären Typen [a]|Die Anzahl von Bytes, die zum Speichern der definierten Zeichen (für feste Typen) oder der maximalen Anzahl (für Variablen Typen) erforderlich sind.|  
|SQL_TYPE_DATE<br />SQL_TYPE_TIME|6 (die Größe der SQL_DATE_STRUCT-oder SQL_TIME_STRUCT-Struktur).|  
|SQL_TYPE_TIMESTAMP|16 (die Größe der SQL_TIMESTAMP_STRUCT-Struktur).|  
|Alle Intervall Datentypen|34 (die Größe der Intervall Struktur).|  
|SQL_GUID|16 (die Größe der GUID-Struktur).|  
| &nbsp; | &nbsp; |

 [a] Wenn der Treiber die Spalten-oder Parameter Länge für Variablen Typen nicht bestimmen kann, wird SQL_NO_TOTAL zurückgegeben.
