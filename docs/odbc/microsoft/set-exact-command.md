---
title: Exakten Befehl festlegen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET EXACT command [ODBC]
ms.assetid: 9533d3e0-e7c1-49de-a3a3-0cc4373a91cb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 686ecc89f44bac4b219b760e55160f451a15c503
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67997725"
---
# <a name="set-exact-command"></a>SET EXACT-Befehl
Gibt die Regeln für den Vergleich von zwei Zeichen folgen mit unterschiedlichen Längen an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET EXACT ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 EIN  
 Gibt an, dass Ausdrücke mit Zeichen übereinstimmen müssen, damit das Zeichen Äquivalent ist. Alle nachfolgenden Leerzeichen in den Ausdrücken werden für den Vergleich ignoriert. Für den Vergleich wird die kürzere der beiden Ausdrücke auf der rechten Seite mit Leerzeichen aufgefüllt, um die Länge des längeren Ausdrucks abzugleichen.  
  
 OFF  
 (Standard) Gibt an, dass Ausdrücke für ein entsprechendes Zeichen übereinstimmen müssen, bis das Ende des Ausdrucks auf der rechten Seite erreicht ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Einstellung exakte festlegen hat keine Auswirkung, wenn beide Zeichen folgen dieselbe Länge haben.  
  
## <a name="string-comparisons"></a>Zeichen folgen Vergleiche  
 Visual FoxPro verfügt über zwei relationale Operatoren, die auf Gleichheit testen.  
  
 Der Operator = führt einen Vergleich zwischen zwei Werten desselben Typs durch. Dieser Operator eignet sich zum Vergleichen von Zeichen-, numerischen, Datums-und logischen Daten.  
  
 Wenn Sie Zeichen Ausdrücke jedoch mit dem =-Operator vergleichen, entsprechen die Ergebnisse möglicherweise nicht genau Ihren Erwartungen. Zeichen Ausdrücke werden für ein Zeichen von links nach rechts verglichen, bis einer der Ausdrücke nicht gleich dem anderen Ausdruck ist, bis das Ende des Ausdrucks auf der rechten Seite des =-Operators erreicht (exakte Menge festgelegt) wird oder bis die Enden beider Ausdrücke erreicht (genau festlegen für).  
  
 Der Operator = = kann verwendet werden, wenn ein genauer Vergleich der Zeichendaten erforderlich ist. Wenn zwei Zeichen Ausdrücke mit dem Operator = = verglichen werden, müssen die Ausdrücke auf beiden Seiten des = =-Operators genau die gleichen Zeichen (einschließlich Leerzeichen) enthalten, damit Sie als gleich betrachtet werden. Die Einstellung exakte festlegen wird ignoriert, wenn Zeichen folgen mithilfe von = = verglichen werden.  
  
 In der folgenden Tabelle wird gezeigt, wie sich die Auswahl des Operators und die Einstellung für die genaue Einstellung auf Vergleiche auswirken. (Ein Unterstrich stellt einen leeren Bereich dar.)  
  
|Vergleich|= Exact aus|= genau am|= = Genau ein/aus|  
|----------------|------------------|-----------------|--------------------------|  
|"ABC" = "ABC"|Match|Match|Match|  
|"ab" = "ABC"|Keine Entsprechung|Keine Entsprechung|Keine Entsprechung|  
|"ABC" = "ab"|Match|Keine Entsprechung|Keine Entsprechung|  
|"ABC" = "AB_"|Keine Entsprechung|Keine Entsprechung|Keine Entsprechung|  
|"ab" = "AB_"|Keine Entsprechung|Match|Keine Entsprechung|  
|"AB_" = "ab"|Match|Match|Keine Entsprechung|  
|"" = "ab"|Keine Entsprechung|Keine Entsprechung|Keine Entsprechung|  
|"ab" = ""|Match|Keine Entsprechung|Keine Entsprechung|  
|"__" = ""|Match|Match|Keine Entsprechung|  
|"" = "___"|Keine Entsprechung|Match|Keine Entsprechung|  
|Trim ("___") = ""|Match|Match|Match|  
|"" = Trim ("___")|Match|Match|Match|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SET ANSI-Befehl](../../odbc/microsoft/set-ansi-command.md)
