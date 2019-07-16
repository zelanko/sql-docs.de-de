---
title: Data Mining-Erweiterungen (DMX)-Operator (Referenz) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4e0dfafb74e6e86185872ea8e736b95dce7d4058
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070913"
---
# <a name="data-mining-extensions-dmx-operator-reference"></a>Data Mining-Erweiterungen (DMX) - Operatorreferenz
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Die Sprache Data Mining Extensions (DMX) in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt arithmetische, Zuweisung, Vergleichsoperatoren, logische und unäre Operatoren. In der folgenden Tabelle sind die Operatoren aufgeführt, die DMX unterstützt.  
  
|Operator|Beschreibung|  
|--------------|-----------------|  
|[+ &#40;Hinzufügen&#41; &#40;DMX&#41;](../dmx/add-dmx.md)|Ein arithmetischer Operator, der zwei Zahlen addiert.|  
|[- &#40;Subtract&#41; &#40;DMX&#41;](../dmx/subtract-dmx.md)|Ein arithmetischer Operator, der eine Zahl von einer anderen Zahl subtrahiert.|  
|[&#42;&#40;Multiplizieren&#41; &#40;DMX&#41;](../dmx/multiply-dmx.md)|Ein arithmetischer Operator, der eine Zahl mit einer anderen Zahl multipliziert.|  
|[&#40;Divide&#41; &#40;DMX&#41;](../dmx/divide-dmx.md)|Ein arithmetischer Operator, der eine Zahl durch eine andere Zahl dividiert.|  
|[&#60;&#40;Kleiner als&#41; &#40;DMX&#41;](../dmx/less-than-dmx.md)|Ein Vergleichsoperator. Für Argumente, die ausgewertet ungleich Null sind, gibt "true", wenn der Wert des Arguments auf der linken Seite kleiner als der Wert des Arguments auf der rechten Seite ist; Andernfalls wird "false" zurückgegeben. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[&#62;&#40;Größer als&#41; &#40;DMX&#41;](../dmx/greater-than-dmx.md)|Ein Vergleichsoperator. Gibt für Argumente, die ausgewertet ungleich NULL sind, TRUE zurück, wenn der Wert des Arguments auf der linken Seite größer ist als der Wert des Arguments auf der rechten Seite; gibt anderenfalls FALSE zurück. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[= &#40;Gleich&#41; &#40;DMX&#41;](../dmx/equal-to-dmx.md)|Ein Vergleichsoperator. Gibt für Argumente, die ausgewertet ungleich NULL sind, TRUE zurück, wenn der Wert des Arguments auf der linken Seite gleich dem Wert des Arguments auf der rechten Seite ist; gibt anderenfalls FALSE zurück. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[&#60;&#62;&#40;Ungleich&#41; &#40;DMX&#41;](../dmx/not-equal-to-dmx.md)|Ein Vergleichsoperator. Gibt für Argumente, die ausgewertet ungleich NULL sind, TRUE zurück, wenn der Wert des Arguments auf der linken Seite ungleich dem Wert des Arguments auf der rechten Seite ist; gibt anderenfalls FALSE zurück. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[&#60;= &#40;Kleiner als oder gleich&#41; &#40;DMX&#41;](../dmx/less-than-or-equal-to-dmx.md)|Ein Vergleichsoperator. Für Argumente, die ausgewertet ungleich Null sind, gibt TRUE zurück, wenn der Wert des Arguments auf der linken Seite kleiner als oder gleich dem Wert des Arguments auf der rechten Seite ist; Andernfalls wird "false" zurückgegeben. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[&#62;= &#40;Größer als oder gleich&#41; &#40;DMX&#41;](../dmx/greater-than-or-equal-to-dmx.md)|Ein Vergleichsoperator. Gibt für Argumente, die ausgewertet ungleich NULL sind, TRUE zurück, wenn der Wert des Arguments auf der linken Seite größer gleich dem Wert des Arguments auf der rechten Seite ist; gibt anderenfalls FALSE zurück. Wenn eines der Argumente oder beide Argumente ausgewertet gleich NULL sind, gibt der Operator einen NULL-Wert zurück.|  
|[UND &#40;DMX&#41;](../dmx/and-dmx.md)|Ein logischer Operator, der eine Konjunktion zweier numerischer Ausdrücke ausführt.|  
|[NICHT &#40;DMX&#41;](../dmx/not-dmx.md)|Ein logischer Operator, der eine Negation für einen numerischen Ausdruck ausführt.|  
|[ODER &#40;DMX&#41;](../dmx/or-dmx.md)|Ein logischer Operator, der eine Disjunktion zweier numerischer Ausdrücke ausführt.|  
|[+ &#40;Positive&#41; &#40;DMX&#41;](../dmx/positive-dmx.md)|Ein unärer Operator, der den positiven Wert eines numerischen Ausdrucks zurückgibt.|  
|[- &#40;Negative&#41; &#40;DMX&#41;](../dmx/negative-dmx.md)|Ein unärer Operator, der den negativen Wert eines numerischen Ausdrucks zurückgibt.|  
|[Doppelten Schrägstrich &#40;Kommentar&#41; &#40;DMX&#41;](../dmx/double-slash-comment-dmx.md)|Kennzeichnet eine Textzeichenfolge, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht ausführen soll. Sie können Kommentare in einer DMX-Anweisung schachteln, am Ende einer Codezeile anfügen oder in eine eigene Zeile einfügen.|  
|[-- &#40;Kommentar&#41; &#40;DMX&#41; Zusammenfassung](../dmx/comment-dmx-summary.md)|Kennzeichnet eine Textzeichenfolge, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht ausführen soll. Sie können Kommentare in einer DMX-Anweisung schachteln, am Ende einer Codezeile anfügen oder in eine eigene Zeile einfügen.|  
|[Schrägstrich-Stern &#40;Kommentar&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md)|Kennzeichnet eine Textzeichenfolge, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nicht ausführen soll. Sie können Kommentare in einer DMX-Anweisung schachteln, am Ende einer Codezeile anfügen oder in eine eigene Zeile einfügen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Syntaxkonventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Syntaxelemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Operatoren &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
