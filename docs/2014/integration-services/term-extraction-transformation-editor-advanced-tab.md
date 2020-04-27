---
title: Transformations-Editor für ausdrucksexextraktion (Registerkarte Erweitert) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bc333bae08cd9ec658b6e8050b869d1232dbe629
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66055272"
---
# <a name="term-extraction-transformation-editor-advanced-tab"></a>Transformations-Editor für Ausdrucksextrahierung (Registerkarte Erweitert)
  Auf der Registerkarte **Erweitert** des Dialogfelds **Transformations-Editor für Ausdrucksextrahierung** können Sie Eigenschaften für die Extrahierung angeben, wie z. B. Häufigkeit, Länge und ob Wörter oder Ausdrücke extrahiert werden sollen.  
  
 Weitere Informationen zur Transformation für Ausdrucksextrahierung finden Sie unter [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).  
  
## <a name="options"></a>Optionen  
 **Nomen**  
 Gibt an, dass durch die Transformation nur einzelne Nomen extrahiert werden.  
  
 **Substantiv Phrase**  
 Gibt an, dass durch die Transformation nur nominale Ausdrücke extrahiert werden.  
  
 **Nomen und nominaler Ausdruck**  
 Gibt an, dass durch die Transformation sowohl Nomen als auch nominale Ausdrücke extrahiert werden.  
  
 **Frequency**  
 Gibt an, dass es sich bei dem Ergebnis um die Häufigkeit des Begriffs handelt.  
  
 **TFIDF**  
 Gibt an, dass es sich bei dem Ergebnis um den TFIDF-Wert des Begriffs handelt. Das TFIDF-Ergebnis ist das Produkt von Ausdruckshäufigkeit und umgekehrter Dokumenthäufigkeit, definiert als: TFIDF des Ausdrucks T = (Häufigkeit von T) * log((Anz. Zeilen in der Eingabe)/(Anz. Zeilen mit T))  
  
 **Schwellenwert für Häufigkeit**  
 Gibt in Form eines Zahlenwertes an, wie oft ein Wort oder ein Ausdruck vorkommen muss, bevor die Extrahierung erfolgt. Der Standardwert ist 2.  
  
 **Maximale Ausdruckslänge**  
 Gibt die maximale Länge des Ausdrucks in Worten an. Diese Option bezieht sich nur auf nominale Ausdrücke. Der Standardwert ist 12.  
  
 **Ausdrucksextrahierung mit Unterscheidung nach Groß-/Kleinschreibung verwenden**  
 Gibt an, ob bei der Extrahierung nach Groß-/Kleinschreibung unterschieden wird. Der Standardwert ist `False`.  
  
 **Fehlerausgabe konfigurieren**  
 Geben Sie mit dem Dialogfeld [Fehlerausgabe konfigurieren](../../2014/integration-services/configure-error-output.md) die Fehlerbehandlung für Zeilen an, die Fehler verursachen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformations-Editor für Ausdrucksextrahierung &#40;Registerkarten&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Transformations-Editor für Ausdrucksextrahierung &#40;&#41;Register](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md)   
 [Transformation für Ausdruckssuche](data-flow/transformations/lookup-transformation.md)  
  
  
