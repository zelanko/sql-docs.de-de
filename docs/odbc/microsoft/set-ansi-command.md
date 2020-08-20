---
description: SET ANSI-Befehl
title: ANSI-Befehl festlegen | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4a9f9c576199905c23994af4dc6b031114f4ad72
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466402"
---
# <a name="set-ansi-command"></a>SET ANSI-Befehl
Bestimmt, wie Vergleiche zwischen Zeichen folgen mit unterschiedlichen Längen mit dem =-Operator in Visual FoxPro-SQL-Befehlen durchgeführt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 EIN  
 (Standardwert für den Treiber; der Standardwert für Visual FoxPro ist off.) Füllt die kürzere Zeichenfolge mit den Leerzeichen, die erforderlich sind, damit Sie der Länge der längeren Zeichenfolge entspricht. Die beiden Zeichen folgen werden dann mit einem Zeichen für Ihre gesamte Länge verglichen. Beachten Sie diesen Vergleich:  
  
```  
'Tommy' = 'Tom'  
```  
  
 Das Ergebnis ist false (. F.) Wenn SET ANSI auf ON festgelegt ist, da "Tom" beim Auffüllen von "Tom" und die Zeichen folgen "Tom" und "Torsten" nicht mit dem Zeichen für das Zeichen identisch sind.  
  
 Der = =-Operator verwendet diese Methode für Vergleiche in Visual FoxPro-SQL-Befehlen.  
  
 OFF  
 Gibt an, dass die kürzere Zeichenfolge nicht mit Leerzeichen aufgefüllt werden soll. Die beiden Zeichen folgen werden mit einem Zeichen verglichen, bis das Ende der kürzeren Zeichenfolge erreicht ist. Beachten Sie diesen Vergleich:  
  
```  
'Tommy' = 'Tom'  
```  
  
 Das Ergebnis ist "true" (. T.), wenn SET ANSI auf OFF festgelegt ist, da der Vergleich nach ' Tom ' beendet wird.  
  
## <a name="remarks"></a>Bemerkungen  
 SET ANSI bestimmt, ob der kürzere von zwei Zeichen folgen mit Leerzeichen aufgefüllt wird, wenn ein SQL-Zeichen folgen Vergleich durchgeführt wird. SET ANSI hat keine Auswirkung auf den = =-Operator; Wenn Sie den = =-Operator verwenden, wird die kürzere Zeichenfolge für den Vergleich immer mit Leerzeichen aufgefüllt.  
  
## <a name="string-order"></a>Zeichenfolge  
 In SQL-Befehlen ist die Reihenfolge der beiden Zeichen folgen in einem Vergleich von links nach rechts eine Zeichenfolge, die eine Zeichenfolge von einer Seite des =-oder = =-Operators auf die andere nicht beeinträchtigt. Dies wirkt sich nicht auf das Ergebnis des Vergleichs aus.  
  
## <a name="see-also"></a>Siehe auch  
 [SELECT-SQL-Befehl](../../odbc/microsoft/select-sql-command.md)   
 [Befehl SET EXACT](../../odbc/microsoft/set-exact-command.md)
