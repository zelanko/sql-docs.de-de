---
title: Literalpräfixe und-Suffixe | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f4eabc3e0c354e02ad8df790d896dc43ae49c9bd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63313010"
---
# <a name="literal-prefixes-and-suffixes"></a>Literalpräfixe und -suffixe
In einer SQL­Anweisung eine *literal* ist eine breitzeichendarstellung eines Werts für die tatsächlichen Daten. Beispielsweise sind in der folgenden Anweisung, ABC, FFFF und 10 Literale:  
  
```  
SELECT CharCol, BinaryCol, IntegerCol FROM MyTable  
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10  
```  
  
 Literale für einige Datentypen erfordern spezielle Präfixe und Suffixe an. Klicken Sie im vorherigen Beispiel Zeichenliterals (ABC) erfordert ein einfaches Anführungszeichen (') als ein Präfix und Suffix, binären Literals (FFFF) erfordert die Zeichen 0 X als Präfix und die Integer-literal (10) nicht benötigen ein Präfix oder suffix.  
  
 Für alle Datentypen mit Ausnahme von Datum, Uhrzeit und Zeitstempel, interoperable Anwendungen ausführen können sollten die Rückgabewerte in den LITERAL_PREFIX-Zeichen und LITERAL_SUFFIX Spalten im Resultset erstellt verwenden **SQLGetTypeInfo**. Für Datum, Uhrzeit, Zeitstempel und Datetime-Intervall-Literale sollten interoperable Anwendungen ausführen können, die Escapesequenzen, die im vorherigen Abschnitt beschrieben verwenden.
