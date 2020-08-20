---
description: Escapezeichen des LIKE-Prädikats
title: LIKE-Prädikat Escapezeichen | Microsoft-Dokumentation
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
ms.openlocfilehash: 5304068e21dd6faf0e737a94add0cce177c4dabc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476552"
---
# <a name="like-predicate-escape-character"></a>Escapezeichen des LIKE-Prädikats
In einem **like** -Prädikat das Prozentzeichen (%) entspricht 0 (null) oder mehr beliebigen Zeichen, und der Unterstrich (_) entspricht einem beliebigen Zeichen. Um einem tatsächlichen Prozentzeichen oder Unterstrich in einem **like** -Prädikat zu entsprechen, muss ein Escapezeichen vor dem Prozentzeichen oder Unterstrich stehen. Die Escapesequenz, die das **like** -Prädikat Escapezeichen definiert, ist:  
  
 **{Escape '** *Escapezeichen* **'}**  
  
 Where *Escapezeichen* ist ein beliebiges Zeichen, das von der Datenquelle unterstützt wird.  
  
 Weitere Informationen zur like-Escapesequenz finden Sie unter [like-Escapesequenz](../../../odbc/reference/appendixes/like-escape-sequence.md) in Anhang C: SQL-Grammatik.  
  
 Beispielsweise werden mit den folgenden SQL-Anweisungen die gleichen Resultsets von Kundennamen erstellt, die mit den Zeichen "% AAA" beginnen. In der ersten Anweisung wird die Escapesequenzsyntax verwendet. Die zweite Anweisung verwendet die native Syntax für Microsoft® Access und ist nicht interoperabel. Beachten Sie, dass das zweite Prozentzeichen in jedem **like** -Prädikat ein Platzhalter Zeichen ist, das NULL oder mehr von einem beliebigen Zeichen entspricht.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Um zu ermitteln, ob das **like** -Prädikat-Escapezeichen von einer Datenquelle unterstützt wird, ruft eine Anwendung **SQLGetInfo** mit der SQL_LIKE_ESCAPE_CLAUSE-Option auf.
