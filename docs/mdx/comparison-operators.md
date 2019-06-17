---
title: Vergleichsoperatoren | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ae175665c2a62caa2d3b7b845c68fefebcfd4c32
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181525"
---
# <a name="comparison-operators"></a>Vergleichsoperatoren


  Sie verwenden Vergleichsoperatoren mit skalaren Daten. Sie können Vergleichsoperatoren in jedem MDX-Ausdruck (Multidimensional Expressions) verwenden.  
  
 Um eine Bedingung zu überprüfen, können Sie auch Vergleichsoperatoren in MDX-Anweisungen und Funktionen, z. B. der MDX-Abfrage [IIf](../mdx/iif-mdx.md) Funktion. Wenn Sie mit Vergleichsoperatoren eine Bedingung überprüfen und dann anhand dieser Bedingung Daten ändern möchten, sollten Sie sich vorher allerdings vergewissern, dass Sie die entsprechenden Berechtigungen haben. Jeder Benutzer, der Zugriff auf die tatsächlichen Daten hat und diese Daten abfragen kann, kann Vergleichsoperatoren in zusätzlichen Abfragen verwenden. Dieser Zugriff bedeutet aber nicht, dass diese Benutzer die entsprechenden Berechtigungen zum Ändern von Daten haben oder haben sollten. Außerdem sollte, damit die Datenintegrität erhalten bleibt, die Anzahl der Benutzer beschränkt werden, die Daten abfragen und ändern können.  
  
 Vergleichsoperatoren ergeben einen booleschen Datentyp, der Rückgabe "true" oder "false" basierend auf dem Ergebnis der getesteten Bedingung.  
  
 MDX unterstützt die Vergleichsoperatoren, die in der folgenden Tabelle aufgelistet sind.  
  
|Operator|Description|  
|--------------|-----------------|  
|[= (Equal To) (= (Gleich))](../mdx/equal-to-mdx.md)|Gibt für Argumente, die nicht NULL enthalten, TRUE zurück, wenn das linke Argument gleich dem rechten Argument ist. Gibt andernfalls FALSE zurück.<br /><br /> Wenn mindestens eines der Argumente zu einem NULL-Wert ausgewertet wird, gibt der Operator einen NULL-Wert zurück, es sei denn, der Vergleich `0=null` wird ausgeführt; in diesem Fall enthält der boolesche Wert TRUE.|  
|[<> (Not Equal To) (<> (Ungleich))](../mdx/not-equal-to-mdx.md)|Gibt für Argumente, die nicht NULL enthalten, TRUE zurück, wenn das linke Argument ungleich dem rechten Argument ist. Gibt andernfalls FALSE zurück.<br /><br /> Wenn mindestens eines der Argumente zu einem NULL-Wert ausgewertet wird, gibt der Operator einen NULL-Wert zurück.|  
|[> (Greater Than) (> (Größer als))](../mdx/greater-than-mdx.md)|Gibt für Argumente, die nicht NULL enthalten, TRUE zurück, wenn das linke Argument einen Wert hat, der größer ist als der Wert des rechten Arguments. Gibt andernfalls FALSE zurück.<br /><br /> Wenn mindestens eines der Argumente zu einem NULL-Wert ausgewertet wird, gibt der Operator einen NULL-Wert zurück.|  
|[>= (Greater Than or Equal To) (>= (Größer als oder gleich)](../mdx/greater-than-or-equal-to-mdx.md)|Gibt für Argumente, die nicht NULL enthalten, TRUE zurück, wenn das linke Argument einen Wert hat, der größer gleich dem Wert des rechten Arguments ist. Gibt andernfalls FALSE zurück.<br /><br /> Wenn mindestens eines der Argumente zu einem NULL-Wert ausgewertet wird, gibt der Operator einen NULL-Wert zurück.|  
|[< (Less Than) (< (Kleiner als))](../mdx/less-than-mdx.md)|Für nicht-Null-Argumente gibt "true" zurück, wenn das linke Argument einen Wert aufweist, der kleiner als das rechte Argument ist; andernfalls "false".<br /><br /> Wenn mindestens eines der Argumente zu einem NULL-Wert ausgewertet wird, gibt der Operator einen NULL-Wert zurück.|  
|[<= (Less Than or Equal To) (<= (Kleiner als oder gleich))](../mdx/less-than-or-equal-to-mdx.md)|Gibt für Argumente, die nicht NULL enthalten, TRUE zurück, wenn das linke Argument einen Wert hat, der kleiner gleich dem Wert des rechten Arguments ist. Gibt andernfalls FALSE zurück.<br /><br /> Wenn mindestens eines der Argumente zu einem NULL-Wert ausgewertet wird, gibt der Operator einen NULL-Wert zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Operatoren &#40;MDX-Syntax&#41;](../mdx/operators-mdx-syntax.md)  
  
  
