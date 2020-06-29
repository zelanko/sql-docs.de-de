---
title: Operatoren (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, operators
- SQL Server Integration Services, operators
- operators [Integration Services]
- expressions [Integration Services], operators
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2851d5b0f8681b46a8c5b4efc714620fa5cd64f0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428307"
---
# <a name="operators-ssis-expression"></a>Operatoren (SSIS-Ausdruck)
  In diesem Abschnitt werden die von der Ausdruckssprache bereitgestellten Operatoren sowie die Operatorenrangfolge und die Assoziativität der Ausdrucksauswertung beschrieben.  
  
 In der folgenden Tabelle sind Themen zu Operatoren in diesem Abschnitt aufgeführt.  
  
|Operator|BESCHREIBUNG|  
|--------------|-----------------|  
|[CAST &#40;SSIS-Ausdruck&#41;](cast-ssis-expression.md)|Konvertiert einen Ausdruck in einen anderen Datentyp.|  
|[&#40;&#41; &#40;Klammern&#41; &#40;SSIS-Ausdruck&#41;](parentheses-ssis-expression.md)|Identifiziert die Auswertungsreihenfolge von Ausdrücken.|  
|[+ &#40;Addieren&#41; &#40;SSIS&#41;](add-ssis.md)|Addiert zwei numerische Ausdrücke.|  
|[+ &#40;Verketten&#41; &#40;SSIS-Ausdruck&#41;](concatenate-ssis-expression.md)|Verkettet zwei Ausdrücke.|  
|[- &#40;Subtrahieren&#41; &#40;SSIS-Ausdruck&#41;](subtract-ssis-expression.md)|Subtrahiert den zweiten numerischen Ausdruck vom ersten.|  
|[- &#40;Negation&#41; &#40;SSIS-Ausdruck&#41;](negate-ssis-expression.md)|Negiert einen numerischen Ausdruck.|  
|[&#42; &#40;Multiplizieren&#41; &#40;SSIS-Ausdruck&#41;](multiply-ssis-expression.md)|Multipliziert zwei numerische Ausdrücke.|  
|[Division &#40;SSIS-Ausdruck&#41;](divide-ssis-expression.md)|Dividiert den ersten numerischen Ausdruck durch den zweiten numerischen Ausdruck.|  
|[&#40;Modulo&#41; &#40;SSIS-Ausdrücke&#41;](modulo-ssis-expression.md)|Stellt den ganzzahligen Rest einer Division des ersten numerischen Ausdrucks durch den zweiten bereit.|  
|[&#124;&#124; &#40;Logisches OR&#41; &#40;SSIS-Ausdruck&#41;](logical-or-ssis-expression.md)|Führt eine logische OR-Operation aus.|  
|[&& &#40;Logisches AND&#41; &#40;SSIS-Ausdruck&#41;](logical-and-ssis-expression.md)|Führt eine logische AND-Operation aus.|  
|[\! &#40;Logisches NOT&#41; &#40;SSIS-Ausdruck&#41;](logical-not-ssis-expression.md)|Negiert einen booleschen Operanden.|  
|[&#124; &#40;Bitweises inklusives OR&#41; &#40;SSIS-Ausdruck&#41;](bitwise-inclusive-or-ssis-expression.md)|Führt eine bitweise OR-Operation mit zwei ganzzahligen Werten aus.|  
|[^ &#40;Bitweises exklusives OR&#41; &#40;SSIS-Ausdruck&#41;](bitwise-exclusive-or-ssis-expression.md)|Führt eine bitweise exklusive OR-Operation mit zwei ganzzahligen Werten aus.|  
|[& &#40;Bitweises AND&#41; &#40;SSIS-Ausdruck&#41;](bitwise-and-ssis-expression.md)|Führt eine bitweise AND-Operation mit zwei ganzzahligen Werten aus.|  
|[~ &#40;Bitweises Not&#41; &#40;SSIS-Ausdruck&#41;](bitwise-not-ssis-expression.md)|Führt eine bitweise Negation einer ganzen Zahl aus.|  
|[== &#40;Gleich&#41; &#40;SSIS-Ausdruck&#41;](equal-ssis-expression.md)|Führt einen Vergleich aus, um zu ermitteln, ob zwei Ausdrücke gleich sind.|  
|[\!= &#40;Ungleich&#41; &#40;SSIS-Ausdruck&#41;](unequal-ssis-expression.md)|Führt einen Vergleich aus, um zu ermitteln, ob zwei Ausdrücke ungleich sind.|  
|[&#62; &#40;Größer als&#41; &#40;SSIS-Ausdruck&#41;](greater-than-ssis-expression.md)|Führt einen Vergleich aus, um zu ermitteln, ob der erste Ausdruck größer ist als der zweite.|  
|[&#60; &#40;Kleiner als&#41; &#40;SSIS-Ausdruck&#41;](less-than-ssis-expression.md)|Führt einen Vergleich aus, um zu ermitteln, ob der erste Ausdruck kleiner ist als der zweite.|  
|[&#62;= &#40;Größer oder gleich&#41; &#40;SSIS-Ausdruck&#41;](greater-than-or-equal-to-ssis-expression.md)|Führt einen Vergleich aus, um zu ermitteln, ob der erste Ausdruck größer oder gleich dem zweiten Ausdruck ist.|  
|[&#60;= &#40;Kleiner oder gleich&#41; &#40;SSIS-Ausdruck&#41;](less-than-or-equal-to-ssis-expression.md)|Führt einen Vergleich aus, um zu ermitteln, ob der erste Ausdruck kleiner oder gleich dem zweiten Ausdruck ist.|  
|[? : &#40;Bedingt&#41; &#40;SSIS-Ausdruck&#41;](conditional-ssis-expression.md)|Gibt einen von zwei Ausdrücken basierend auf der Auswertung eines booleschen Ausdrucks zurück.|  
  
 Informationen zum Platzieren der Operatoren in der Rangfolgenhierarchie finden Sie unter [Operator Precedence and Associativity](operator-precedence-and-associativity.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)   
 [Beispiele für erweiterte SQL Server Integration Services-Ausdrücke](examples-of-advanced-integration-services-expressions.md)   
 [Integration Services-Ausdrücke &#40;SSIS&#41;](integration-services-ssis-expressions.md)  
  
  
