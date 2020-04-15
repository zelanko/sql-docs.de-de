---
title: Literale Präfixe und Suffixe | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], literal prefixes and suffixes
- literals [ODBC], prefixes and suffixes
ms.assetid: 29f468f2-f557-4a92-b31d-569c63cc6272
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d52ca54c329353e3d9dc67ca35d89b2d28cedf74
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287982"
---
# <a name="literal-prefixes-and-suffixes"></a>Literalpräfixe und -suffixe
In einer SQL-Anweisung ist ein *Literal* eine Zeichendarstellung eines tatsächlichen Datenwerts. In der folgenden Anweisung sind BEISPIELSWEISE ABC, FFFF und 10 Literale:  
  
```  
SELECT CharCol, BinaryCol, IntegerCol FROM MyTable  
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10  
```  
  
 Literale für einige Datentypen erfordern spezielle Präfixe und Suffixe. Im vorherigen Beispiel erfordert das Zeichenliteral (ABC) ein einfaches Anführungszeichen (') als Präfix und Suffix, das Binärliteral (FFFF) die Zeichen 0x als Präfix und das Ganzzahlliteral (10) kein Präfix oder Suffix.  
  
 Für alle Datentypen außer Datum, Uhrzeit und Zeitstempel sollten interoperable Anwendungen die in der LITERAL_PREFIX zurückgegebenen und LITERAL_SUFFIX Spalten in dem von **SQLGetTypeInfo**erstellten Resultset verwenden. Für Datums-, Uhrzeit-, Zeitstempel- und Datumszeitintervallliterale sollten interoperable Anwendungen die escape-Sequenzen verwenden, die im vorherigen Abschnitt erläutert werden.
