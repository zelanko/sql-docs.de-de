---
title: LIKE Prädikat Flucht Charakter | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e4f04b12911145eede3354532736cb92f1ae413
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306151"
---
# <a name="like-predicate-escape-character"></a>Escapezeichen des LIKE-Prädikats
In **LIKE** einem LIKE-Prädikat wird das Prozentzeichen (%) entspricht null oder mehr eines beliebigen Zeichens, und der Unterstrich (_) entspricht einem beliebigen Zeichen. Um ein tatsächliches Prozentzeichen oder **LIKE** einen Unterstrich in einem LIKE-Prädikat abzugleichen, muss ein Escapezeichen vor das Prozentzeichen oder den Unterstrich gestellt werden. Die Escapesequenz, die das ESCAPE-Escapezeichen **LIKE** definiert, lautet:  
  
 **"Flucht- '** *Escape-Zeichen* **'**  
  
 wobei *Escape-Zeichen* ein beliebiges Zeichen ist, das von der Datenquelle unterstützt wird.  
  
 Weitere Informationen zur LIKE-Escapesequenz finden Sie unter [LIKE Escape Sequence](../../../odbc/reference/appendixes/like-escape-sequence.md) in Anhang C: SQL Grammar.  
  
 Die folgenden SQL-Anweisungen erstellen z. B. denselben Satz von Kundennamen, die mit den Zeichen "%AAA" beginnen. Die erste Anweisung verwendet die Escape-Sequenz-Syntax. Die zweite Anweisung verwendet die systemeigene Syntax für Microsoft® Access und ist nicht interoperabel. Beachten Sie, dass das **LIKE** zweite Prozentzeichen in jedem LIKE-Prädikat ein Platzhalterzeichen ist, das null oder mehr eines beliebigen Zeichens entspricht.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Um zu **LIKE** bestimmen, ob das LIKE-Prädikat-Escapezeichen von einer Datenquelle unterstützt wird, ruft eine Anwendung **SQLGetInfo** mit der Option SQL_LIKE_ESCAPE_CLAUSE auf.
