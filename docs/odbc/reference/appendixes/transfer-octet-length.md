---
title: Oktettlänge übertragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
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
ms.openlocfilehash: ff187d5d2b67c5fc3d40a80a136ff9f0c65b2ed2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070044"
---
# <a name="transfer-octet-length"></a>Länge der Übertragungsoktette
Die Oktettlänge Übertragung einer Spalte ist die maximale Anzahl von Bytes, die an die Anwendung zurückgegeben werden, wenn Daten, für den Standard-C-Datentyp übertragen werden. Bei Zeichendaten ist die Oktettlänge Übertragung nicht den verbliebenen Speicherplatz für die Null-Terminierungszeichen. Die Oktettlänge Übertragung einer Spalte möglicherweise anders als die Anzahl der Bytes, die zum Speichern der Daten in der Datenquelle erforderlich sind.  
  
 Die Übertragung Oktettlänge definiert, die für jede ODBC-SQL-Datentyp wird in der folgenden Tabelle angezeigt.  
  
|SQL-Typ-ID|Länge|  
|-------------------------|------------|  
|Alle Typen mit Zeichen [a]|Die definiert oder die (für Variablentyp) maximale Länge der Spalte in Bytes. Dies ist der gleiche Wert wie das Deskriptorfeld SQL_DESC_OCTET_LENGTH.|  
|SQL_DECIMAL<br />SQL_NUMERIC|Die Anzahl von Bytes erforderlich, um die Darstellung dieser Daten aufzunehmen, ist der Zeichensatz ANSI und zweimal mithilfe dieser Zahl der Zeichensatz UNICODE ist. Dies ist die maximale Anzahl von Ziffern plus zwei, da die Daten als Zeichenfolge zurückgegeben werden und die Zeichen für die Ziffern, ein Vorzeichen und ein Dezimaltrennzeichen erforderlich sind. Beispielsweise ist die Übertragung Länge einer Spalte, die als NUMERIC(10,3) definiert 12.|  
|SQL_TINYINT|1|  
|SQL_SMALLINT|2|  
|SQL_INTEGER|4|  
|SQL_BIGINT|Die Anzahl von Bytes erforderlich, um die Darstellung dieser Daten aufzunehmen, ist der Zeichensatz ANSI und zweimal mithilfe dieser Zahl der Zeichensatz UNICODE ist, da dieser Datentyp wird standardmäßig als Zeichenfolge zurückgegeben wird. Die Darstellung von Zeichen besteht aus 20 Zeichen: 19 Ziffern und ein Zeichen, wenn angemeldet, oder 20 Ziffern, falls ohne Vorzeichen. Aus diesem Grund ist die Länge 20.|  
|SQL_REAL|4|  
|SQL_FLOAT|8|  
|SQL_DOUBLE|8|  
|SQL_BIT|1|  
|[A] alle binären Typen|Die Anzahl der Bytes, die erforderlich, um die definierten (bei festen Typen) aufzunehmen oder (für Variablentypen) maximale Anzahl von Zeichen.|  
|SQL_TYPE_DATE<br />SQL_TYPE_TIME|6 (die Größe der Struktur SQL_DATE_STRUCT oder SQL_TIME_STRUCT).|  
|SQL_TYPE_TIMESTAMP|16 (die Größe der Struktur SQL_TIMESTAMP_STRUCT).|  
|Alle Interval-Datentypen|34 (die Größe der Intervall-Struktur).|  
|SQL_GUID|16 (die Größe der GUID-Struktur).|  
  
 [a] Wenn der Treiber die Spalte oder des Parameters Länge Variablentypen nicht ermitteln kann, gibt er SQL_NO_TOTAL zurück.
