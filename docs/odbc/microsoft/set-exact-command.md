---
title: SET EXACT Befehl | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e754fff35b6b948ac63d19361067b2d65a07fdd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300870"
---
# <a name="set-exact-command"></a>SET EXACT-Befehl
Gibt die Regeln für den Vergleich von zwei Zeichenfolgen unterschiedlicher Länge an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET EXACT ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 EIN  
 Gibt an, dass Ausdrücke mit zeichen übereinstimmen müssen, damit das Zeichen äquivalent ist. Alle nachfolgenden Leerzeichen in den Ausdrücken werden für den Vergleich ignoriert. Zum Vergleich wird der kürzere der beiden Ausdrücke auf der rechten Seite mit Leerzeichen aufgepolstert, um der Länge des längeren Ausdrucks zu entsprechen.  
  
 OFF  
 (Standard.) Gibt an, dass Ausdrücke, um äquivalent zu sein, mit dem Zeichen für das Zeichen übereinstimmen müssen, bis das Ende des Ausdrucks auf der rechten Seite erreicht ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Set EXACT-Einstellung hat keinen Einfluss, wenn beide Zeichenfolgen die gleiche Länge haben.  
  
## <a name="string-comparisons"></a>String-Vergleiche  
 Visual FoxPro verfügt über zwei relationale Operatoren, die auf Gleichheit testen.  
  
 Der Operator = führt einen Vergleich zwischen zwei Werten desselben Typs durch. Dieser Operator eignet sich zum Vergleichen von Zeichen-, numerischen, Datums- und logischen Daten.  
  
 Wenn Sie jedoch Zeichenausdrücke mit dem Operator = vergleichen, entsprechen die Ergebnisse möglicherweise nicht genau dem, was Sie erwarten. Zeichenausdrücke werden für Zeichen von links nach rechts verglichen, bis einer der Ausdrücke nicht gleich dem anderen ist, bis das Ende des Ausdrucks auf der rechten Seite des =-Operators erreicht ist (SET EXACT OFF), oder bis die Enden beider Ausdrücke erreicht sind (SET EXACT ON).  
  
 Der == Operator kann verwendet werden, wenn ein genauer Vergleich von Zeichendaten erforderlich ist. Wenn zwei Zeichenausdrücke mit dem Operator ==verglichen werden, müssen die Ausdrücke auf beiden Seiten des Operators == genau die gleichen Zeichen enthalten, einschließlich Leerzeichen, um als gleich zu gelten. Die SET EXACT-Einstellung wird ignoriert, wenn Zeichenfolgen mit ==verglichen werden.  
  
 Die folgende Tabelle zeigt, wie sich die Auswahl des Operators und die Einstellung SET EXACT auf Vergleiche auswirken. (Ein Unterstrich stellt ein Leerzeichen dar.)  
  
|Vergleich|= EXAKT AUS|= EXAKT AUF|== EXACT ON oder OFF|  
|----------------|------------------|-----------------|--------------------------|  
|"abc" = "abc"|Match|Match|Match|  
|"ab" = "abc"|Keine Übereinstimmung|Keine Übereinstimmung|Keine Übereinstimmung|  
|"abc" = "ab"|Match|Keine Übereinstimmung|Keine Übereinstimmung|  
|"abc" = "ab_"|Keine Übereinstimmung|Keine Übereinstimmung|Keine Übereinstimmung|  
|"ab" = "ab_"|Keine Übereinstimmung|Match|Keine Übereinstimmung|  
|"ab_" = "ab"|Match|Match|Keine Übereinstimmung|  
|"" = "ab"|Keine Übereinstimmung|Keine Übereinstimmung|Keine Übereinstimmung|  
|"ab" = ""|Match|Keine Übereinstimmung|Keine Übereinstimmung|  
|"__" = ""|Match|Match|Keine Übereinstimmung|  
|"" = "___"|Keine Übereinstimmung|Match|Keine Übereinstimmung|  
|TRIM("___") = ""|Match|Match|Match|  
|"" = TRIM("___")|Match|Match|Match|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehl SET ANSI](../../odbc/microsoft/set-ansi-command.md)
