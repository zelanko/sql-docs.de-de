---
title: Befehl SET EXACT | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997725"
---
# <a name="set-exact-command"></a>SET EXACT-Befehl
Legt die Regeln zum Vergleichen von zwei Zeichenfolgen unterschiedlicher Länge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET EXACT ON | OFF  
```  
  
## <a name="arguments"></a>Argumente  
 ON  
 Gibt an, dass Ausdrücke Zeichen für Zeichen, die Äquivalenz entsprechen müssen. Alle nachgestellten Leerzeichen in den Ausdrücken werden für den Vergleich ignoriert. Für den Vergleich wird der kürzere der beiden Ausdrücke auf der rechten Seite mit Leerzeichen, entsprechend der Länge des längeren Ausdrucks aufgefüllt.  
  
 OFF  
 (Standard). Gibt an, um gleichwertig zu sein, Ausdrücke entsprechen müssen Zeichen für Zeichen, bis das Ende des Ausdrucks auf der rechten Seite erreicht ist.  
  
## <a name="remarks"></a>Hinweise  
 Die SET EXACT Einstellung hat keine Auswirkungen, wenn beide Zeichenfolgen die gleiche Länge aufweisen.  
  
## <a name="string-comparisons"></a>Vergleich von Zeichenfolgen  
 Visual FoxPro verfügt über zwei relationale Operatoren, die auf Gleichheit zu testen.  
  
 Die = Operator führt einen Vergleich zwischen zwei Werten desselben Typs. Dieser Operator wird zum Vergleichen von Zeichen, numerischen, Datums- und logischer Daten geeignet.  
  
 Jedoch beim Vergleichen von Zeichenausdrücke, mit der =-Operator, die Ergebnisse möglicherweise nicht genau Ihren Erwartungen. Zeichenausdrücke verglichen werden Zeichen für Zeichen von links nach rechts, bis einer der Ausdrücke bis zum Ende des Ausdrucks auf der rechten Seite der nicht gleich dem anderem ist die = (SET EXACT OFF), Operator erreicht wird oder bis die Enden der beiden Ausdrücke sind erreicht (SET EXACT ON).  
  
 Die ==-Operator kann verwendet werden, wenn ein exakter Vergleich mit Zeichendaten benötigt wird. Wenn zwei Zeichenausdrücken mit verglichen werden die == Operator, die Ausdrücke auf beiden Seiten der dem == Operator muss genau die gleichen Zeichen enthalten, einschließlich Leerzeichen als gleich betrachtet werden. Die SET EXACT Einstellung wird ignoriert, beim Vergleich von Zeichenfolgen mithilfe von ==.  
  
 Die folgende Tabelle zeigt die Auswirkungen der Wahl des Operators und die Einstellung SET EXACT Vergleiche. (Der ein Unterstrich stellt ein Leerzeichen dar.)  
  
|Vergleich|= DIE GENAUE DEAKTIVIEREN|= DIE GENAUE AUF|== GENAUE ON oder OFF|  
|----------------|------------------|-----------------|--------------------------|  
|"abc" = "abc"|Übereinstimmung|Übereinstimmung|Übereinstimmung|  
|"ab" = "abc"|Keine Übereinstimmung|Keine Übereinstimmung|Keine Übereinstimmung|  
|"abc" = "ab"|Übereinstimmung|Keine Übereinstimmung|Keine Übereinstimmung|  
|"abc" = "ab_"|Keine Übereinstimmung|Keine Übereinstimmung|Keine Übereinstimmung|  
|"ab" = "ab_"|Keine Übereinstimmung|Übereinstimmung|Keine Übereinstimmung|  
|"ab_" = "ab"|Übereinstimmung|Übereinstimmung|Keine Übereinstimmung|  
|"" = "ab"|Keine Übereinstimmung|Keine Übereinstimmung|Keine Übereinstimmung|  
|"ab" = ""|Übereinstimmung|Keine Übereinstimmung|Keine Übereinstimmung|  
|"__" = ""|Übereinstimmung|Übereinstimmung|Keine Übereinstimmung|  
|"" = "___"|Keine Übereinstimmung|Übereinstimmung|Keine Übereinstimmung|  
|TRIM("___") = ""|Übereinstimmung|Übereinstimmung|Übereinstimmung|  
|"" TRIM("___") =|Übereinstimmung|Übereinstimmung|Übereinstimmung|  
  
## <a name="see-also"></a>Siehe auch  
 [Befehl SET ANSI](../../odbc/microsoft/set-ansi-command.md)
