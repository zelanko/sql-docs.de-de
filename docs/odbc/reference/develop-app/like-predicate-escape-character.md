---
title: WIE Prädikat Escapezeichen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30547551cc1793622eaa981c07bbc002d07a094d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63312920"
---
# <a name="like-predicate-escape-character"></a>Escapezeichen des LIKE-Prädikats
In einem **wie** Prädikat, das Prozentzeichen (%) entspricht null oder mehr beliebige Zeichen und den Unterstrich (_) entspricht einem einzelnen Zeichen. Eine tatsächliche Prozentzeichen übereinstimmen oder Unterstrich einem **wie** -Prädikats muss ein Escapezeichen vor dem Prozentzeichen oder Unterstrich stammen. Die Escape-Sequenz, die definiert die **wie** Prädikat Escape-Zeichen ist:  
  
 **{Escapezeichen '** *Escapezeichen* **'}**  
  
 wo *Escapezeichen* ist ein beliebiges Zeichen, die von der Datenquelle unterstützt.  
  
 Weitere Informationen zu den LIKE escape-Sequenz, finden Sie unter [wie Escapesequenz](../../../odbc/reference/appendixes/like-escape-sequence.md) in Anhang C: SQL-Grammatik.  
  
 Z. B. erstellen folgenden SQL-Anweisungen Sie das gleiche Resultset des Kunden ab, die mit den Zeichen "% AAA" beginnen. Die erste Anweisung verwendet die Syntax der Escapesequenz. Die zweite Anweisung verwendet die systemeigene Syntax für Microsoft® Access und ist nicht interoperabel. Beachten Sie, die in jeder der zweiten Prozentzeichen **wie** Prädikat ist ein Platzhalterzeichen, das 0 (null) oder mehr beliebige Zeichen entspricht.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Um zu bestimmen, ob die **wie** Prädikat Escape-Zeichen, die von einer Datenquelle unterstützt wird, eine Anwendung ruft **SQLGetInfo** mit der Option SQL_LIKE_ESCAPE_CLAUSE.
