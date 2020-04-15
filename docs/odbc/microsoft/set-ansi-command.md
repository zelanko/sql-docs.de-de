---
title: SET ANSI-Befehl | Microsoft Docs
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
ms.openlocfilehash: 97269642b4147b966fdd71003f5f81ebe7905282
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300910"
---
# <a name="set-ansi-command"></a>SET ANSI-Befehl
Bestimmt, wie Vergleiche zwischen Zeichenfolgen unterschiedlicher Länge mit dem Operator = in Visual FoxPro SQL-Befehlen durchgeführt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 EIN  
 (Standard für den Treiber; die Standardeinstellung für Visual FoxPro ist AUS.) Pads die kürzere Zeichenfolge mit den Leerzeichen, die benötigt werden, um sie der Länge der längeren Zeichenfolge gleich zu machen. Die beiden Zeichenfolgen werden dann für ihre gesamte Länge als Zeichen verglichen. Betrachten Sie diesen Vergleich:  
  
```  
'Tommy' = 'Tom'  
```  
  
 Das Ergebnis ist False (. F.) wenn SET ANSI eingeschaltet ist, denn wenn "Tom" gepolstert ist, wird es zu 'Tom' und die Saiten 'Tom' und 'Tommy' stimmen nicht mit Charakter für Charakter überein.  
  
 Der Operator == verwendet diese Methode für Vergleiche in Visual FoxPro SQL-Befehlen.  
  
 OFF  
 Gibt an, dass die kürzere Zeichenfolge nicht mit Leerzeichen aufgepolstert wird. Die beiden Zeichenfolgen werden für Zeichen verglichen, bis das Ende der kürzeren Zeichenfolge erreicht ist. Betrachten Sie diesen Vergleich:  
  
```  
'Tommy' = 'Tom'  
```  
  
 Das Ergebnis ist True (. T.) wenn SET ANSI ausgeschaltet ist, da der Vergleich nach 'Tom' endet.  
  
## <a name="remarks"></a>Bemerkungen  
 SET ANSI bestimmt, ob die kürzere von zwei Zeichenfolgen mit Leerzeichen aufgepolstert wird, wenn ein SQL-Zeichenfolgenvergleich durchgeführt wird. SET ANSI hat keine Auswirkungen auf den Operator ==; Wenn Sie den Operator ==verwenden, wird die kürzere Zeichenfolge für den Vergleich immer mit Leerzeichen aufgepolstert.  
  
## <a name="string-order"></a>String-Reihenfolge  
 In SQL-Befehlen ist die Links-nach-Rechts-Reihenfolge der beiden Zeichenfolgen in einem Vergleich irrelevant, wenn eine Zeichenfolge von einer Seite des =- oder ==-Operators auf die andere wechselt, hat keinen Einfluss auf das Ergebnis des Vergleichs.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SELECT - SQL-Befehl](../../odbc/microsoft/select-sql-command.md)   
 [Befehl SET EXACT](../../odbc/microsoft/set-exact-command.md)
