---
title: Transfer Oktett Länge | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4204b47816747506a5672241eeeef736eca54856
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302811"
---
# <a name="transfer-octet-length"></a>Länge der Übertragungsoktette
Die Übertragungsoktettlänge einer Spalte ist die maximale Anzahl von Bytes, die an die Anwendung zurückgegeben werden, wenn Daten in den Standarddatentyp C übertragen werden. Bei Zeichendaten enthält die Übertragungsoktettlänge keinen Platz für das Null-Beendigungszeichen. Die Übertragungsoktettlänge einer Spalte kann von der Anzahl der Bytes abweichen, die zum Speichern der Daten in der Datenquelle erforderlich sind.  
  
 Die für jeden ODBC SQL-Datentyp definierte Übertragungsoktettlänge wird in der folgenden Tabelle angezeigt.  
  
|SQL-Typbezeichner|Länge|  
|-------------------------|------------|  
|Alle Zeichentypen[a]|Die definierte oder die maximale Länge (für variablen Typ) der Spalte in Bytes. Dies ist der gleiche Wert wie das Deskriptorfeld SQL_DESC_OCTET_LENGTH.|  
|SQL_DECIMAL<br />SQL_NUMERIC|Die Anzahl der Bytes, die erforderlich sind, um die Zeichendarstellung dieser Daten zu halten, wenn der Zeichensatz ANSI ist, und doppelt so viele, wenn der Zeichensatz UNICODE ist. Dies ist die maximale Anzahl von Ziffern plus zwei, da die Daten als Zeichenfolge zurückgegeben werden und Zeichen für die Ziffern, ein Vorzeichen und ein Dezimalkomma benötigt werden. Die Übertragungslänge einer spaltenden Spalte, die als NUMERIC(10,3) definiert ist, beträgt beispielsweise 12.|  
|SQL_TINYINT|1|  
|SQL_SMALLINT|2|  
|SQL_INTEGER|4|  
|SQL_BIGINT| 8 |  
|SQL_REAL|4|  
|SQL_FLOAT|8|  
|SQL_DOUBLE|8|  
|SQL_BIT|1|  
|Alle binären Typen[a]|Die Anzahl der Bytes, die erforderlich sind, um die definierte (für feste Typen) oder die maximale Anzahl (für Variablentypen) Zeichen zu enthalten.|  
|SQL_TYPE_DATE<br />SQL_TYPE_TIME|6 (die Größe der SQL_DATE_STRUCT oder SQL_TIME_STRUCT Struktur).|  
|SQL_TYPE_TIMESTAMP|16 (die Größe der SQL_TIMESTAMP_STRUCT Struktur).|  
|Alle Intervalldatentypen|34 (die Größe der Intervallstruktur).|  
|SQL_GUID|16 (die Größe der GUID-Struktur).|  
| &nbsp; | &nbsp; |

 [a] Wenn der Treiber die Spalten- oder Parameterlänge für Variablentypen nicht bestimmen kann, gibt er SQL_NO_TOTAL zurück.
