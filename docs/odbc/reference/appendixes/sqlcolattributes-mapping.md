---
title: SQLColAttributes-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a7a1508d10431ba9975c44a2002faa4e5b913312
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199407"
---
# <a name="sqlcolattributes-mapping"></a>SQLColAttributes-Zuordnung
Wenn eine Anwendung ruft **SQLColAttributes** über einen ODBC 3.*.x* Treiber, den Aufruf von **SQLColAttributes** zugeordnet **SQLColAttribute** wie folgt:  
  
> [!NOTE]
>  Das Präfix in verwendet *FieldIdentifier* Werte in ODBC 3.*.x* wurde von diesem verwendet ODBC 2 geändert. *X*. Das neue Präfix ist "SQL_DESC"; das alte Präfix ist "SQL_COLUMN".  
  
1.  Wenn die Anwendung eine ODBC-2 ist. *x* Anwendung *fDescType* SQL_COLUMN_TYPE ist, und der zurückgegebene Typ ist ein präziser DATETIME-Typ, der Treiber-Manager-Zuordnungen, die die Rückgabe für Datum, Uhrzeit und Timestamp-Codes Werte.  
  
2.  Wenn *fDescType* ist SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE oder SQL_COLUMN_COUNT, die Treiber-Manager ruft **SQLColAttribute** im Treiber mit der *FieldIdentifier* Argument zugeordnet, SQL_DESC_NAME SQL_DESC_NULLABLE oder SQL_DESC_COUNT, nach Bedarf *.* Alle anderen Werte des *fDescType* an den Treiber übergeben werden.  
  
 Eine ODBC 3.*.x* Treiber muss die ODBC 3. unterstützen *.x* *FieldIdentifiers* aufgeführten **SQLColAttribute**.  
  
 Eine ODBC 3.*.x* Treiber muss SQL_COLUMN_PRECISION und SQL_DESC_PRECISION, SQL_COLUMN_SCALE und SQL_DESC_SCALE, und SQL_COLUMN_LENGTH und SQL_DESC_LENGTH unterstützen. Diese Werte unterscheiden, da mit einfacher Genauigkeit, Dezimalstellen und Länge in ODBC 3. unterschiedlich definiert sind *.x* als Kacheln in ODBC 2. *X*. Weitere Informationen finden Sie unter [Spaltengröße, Dezimalstellen, Oktettlänge Übertragung und Anzeigegröße](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) in Anhang D: Datentypen.
