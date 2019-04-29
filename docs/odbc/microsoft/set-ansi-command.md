---
title: Befehl SET ANSI | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set ANSI command [ODBC]
ms.assetid: cf9a01b2-14bf-458c-a73c-2a58ddef32d8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5af98bd8f16d7278b932ad89f1c81c58ddb1fb54
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127865"
---
# <a name="set-ansi-command"></a>SET ANSI-Befehl
Bestimmt, wie Vergleiche zwischen Zeichenfolgen unterschiedlicher Länge verfährt vorgenommen werden, mit dem Operator =-Operator in Visual FoxPro-SQL-Befehlen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 ON  
 (Standard für den Treiber; der Standardwert für Visual FoxPro ist OFF). Bereiche, die, denen die kürzere Zeichenfolge mit dem Leerzeichen erforderlich sind. erleichtern je länger gleich Zeichenfolgenlänge. Die beiden Zeichenfolgen werden dann im Vergleich Zeichen für Zeichen, die für ihre gesamte Längen. Betrachten Sie diesen Vergleich:  
  
```  
'Tommy' = 'Tom'  
```  
  
 Das Ergebnis ist "false" (. F.), wenn SET ANSI aktiviert ist, da beim Auffüllen werden 'Tom' wird "Tom", und die Zeichenfolgen "Peter" und 'Torsten' keine Zeichen für Zeichen übereinstimmen.  
  
 Dem == Operator verwendet diese Methode für Vergleiche in Visual FoxPro-SQL-Befehlen.  
  
 OFF  
 Gibt an, dass die kürzere Zeichenfolge nicht mit Leerzeichen aufgefüllt werden. Die beiden Zeichenfolgen verglichen werden Zeichen für Zeichen, bis das Ende die kürzere Zeichenfolge erreicht ist. Betrachten Sie diesen Vergleich:  
  
```  
'Tommy' = 'Tom'  
```  
  
 Das Ergebnis ist "true" (. Wenn SET ANSI deaktiviert ist, da "t".) nach "Peter" wird der Vergleich beendet.  
  
## <a name="remarks"></a>Hinweise  
 SET ANSI bestimmt, ob es sich bei den kürzeren der beiden Zeichenfolgen mit Leerzeichen aufgefüllt wird, wenn ein SQL-Zeichenfolgenvergleich vorgenommen wird. SET ANSI hat keine Auswirkungen auf den Operator ==-Operator; Bei Verwendung von dem == Operator, die kürzere Zeichenfolge wird immer mit Leerzeichen für den Vergleich aufgefüllt.  
  
## <a name="string-order"></a>Zeichenfolge-Reihenfolge  
 SQL-Befehlen, die links-nach-rechts-Reihenfolge der beiden Zeichenfolgen in einem Vergleich wird Irrelevantswitching eine Zeichenfolge mit einer Seite die = oder == Operator, um die andere wirkt sich nicht auf das Ergebnis des Vergleichs.  
  
## <a name="see-also"></a>Siehe auch  
 [SELECT – SQL-Befehl](../../odbc/microsoft/select-sql-command.md)   
 [Befehl SET EXACT](../../odbc/microsoft/set-exact-command.md)
