---
title: Literale Präfixe und Suffixe | Microsoft-Dokumentation
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
ms.openlocfilehash: 56ee50071f622c114bd6d8d04444e78c0fb69d67
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915564"
---
# <a name="literal-prefixes-and-suffixes"></a>Literalpräfixe und -suffixe
In einer SQL-Anweisung ist ein *Literalzeichen* eine Zeichen Darstellung eines tatsächlichen Datenwerts. In der folgenden Anweisung sind z. b. "ABC", "FFFF" und "10" Literale:  
  
```  
SELECT CharCol, BinaryCol, IntegerCol FROM MyTable  
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10  
```  
  
 Literale für einige Datentypen erfordern spezielle Präfixe und Suffixe. Im vorherigen Beispiel erfordert das Zeichen Literale (ABC) ein einzelnes Anführungszeichen (') sowohl als Präfix als auch als Suffix, das binäre Literale (FFFF) erfordert die Zeichen 0x als Präfix, und für das ganzzahlige Literale (10) ist kein Präfix oder Suffix erforderlich.  
  
 Für alle Datentypen außer Date, Time und Timestamps sollten interoperable Anwendungen die Werte verwenden, die in den LITERAL_PREFIX-und LITERAL_SUFFIX Spalten im Resultset zurückgegeben werden, das von **SQLGetTypeInfo**erstellt wurde. Bei Datums-, Zeit-, Zeitstempel-und DateTime-Intervall literalen sollten interoperable Anwendungen die im vorherigen Abschnitt beschriebenen Escapesequenzen verwenden.
