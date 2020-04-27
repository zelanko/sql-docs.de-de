---
title: Measures im Kreuz Validierungsbericht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- root mean square error [data mining]
- cross-validation [data mining]
- mean absolute error [data mining]
- log score [data mining]
- likelihood [data mining]
ms.assetid: a07b1665-7f72-4266-82a4-43a91ae2571d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 30f8daab91172863ba18c6b75529063555b61afc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66084159"
---
# <a name="measures-in-the-cross-validation-report"></a>Measures im Kreuzvalidierungsbericht
  Während der Kreuzvalidierung werden die Daten in einer Miningstruktur von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in mehrere Querschnitte unterteilt. Anschließend werden die Struktur und zugeordnete Miningmodelle iterativ getestet. Auf Grundlage dieser Analyse wird eine Reihe standardmäßiger Genauigkeitsmeasures für die Struktur und jedes Modell ausgegeben.  
  
 Der Bericht enthält einige grundlegende Informationen über die Anzahl der Folds in den Daten sowie die Menge der Daten in jeder Aufteilung sowie einen Satz allgemeiner Metriken zur Beschreibung der Datenverteilung. Sie können die Zuverlässigkeit der Struktur oder des Modells bewerten, indem Sie die allgemeinen Metriken für jeden Querschnitt vergleichen.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] wird auch ein Satz detaillierter Measures für Miningmodelle angezeigt. Diese Measures hängen vom Modelltyp und dem Typ des analysierten Attributs ab, beispielsweise davon, ob es sich um ein diskretes oder kontinuierliches Attribut handelt.  
  
 Dieser Abschnitt enthält eine Liste der im **Kreuzvalidierungsbericht** aufgeführten Measures sowie Erläuterungen zu deren Bedeutung. Ausführliche Informationen zur Berechnung der einzelnen Measures finden Sie unter [Kreuzvalidierungsformeln](cross-validation-formulas.md).  
  
## <a name="list-of-measures-in-the-cross-validation-report"></a>Liste der Measures im Kreuzvalidierungsbericht  
 In der folgenden Tabelle sind die Measures aufgelistet, die im Kreuzvalidierungsbericht angezeigt werden. Die Measures werden nach dem *Testtyp*gruppiert, der in der linken Spalte der folgenden Tabelle angegeben ist. In der rechten Spalte ist der Name des Measures, so wie im Bericht angezeigt, und eine kurze Erläuterung zu dessen Bedeutung enthalten.  
  
|Testtyp|Measures und Beschreibungen|  
|---------------|-------------------------------|  
|Clustering|Measures, die für Clustering-Modelle gelten:<br /><br /> **Fall Wahrscheinlichkeit**: dieses Measure gibt normalerweise an, wie wahrscheinlich es ist, dass ein Fall zu einem bestimmten Cluster gehört. <br />                      Bei der Kreuzvalidierung werden die Ergebnisse addiert und dann durch die Anzahl der Fälle dividiert, sodass das Ergebnis in diesem Fall einer durchschnittlichen Fallwahrscheinlichkeit entspricht.|  
|Klassifizierung|Measures, die für Klassifizierungs Modelle gelten:<br /><br /> **True positiv**/<br />                      **True negative**/ **falsch positive**/ **falsch positiv**: Anzahl der Zeilen oder Werte in der Partition, bei der der vorhergesagte Status mit dem Ziel Status übereinstimmt, und die Vorhersage Wahrscheinlichkeit ist größer als der angegebene Schwellenwert. Fälle mit fehlenden Werten für das Ziel Attribut werden ausgeschlossen, was bedeutet, dass die Anzahl aller Werte möglicherweise nicht addiert wird.|  
||**Pass/Fail**: Anzahl der Zeilen oder Werte in der Partition, in denen der vorhergesagte Status mit dem Ziel Status übereinstimmt und der Vorhersage Wahrscheinlichkeitswert größer als 0 ist.|  
|Wahrscheinlichkeit|Wahrscheinlichkeits Measures gelten für mehrere Modelltypen:<br /><br /> **Lift**: das Verhältnis der tatsächlichen Vorhersage Wahrscheinlichkeit zur Rand Wahrscheinlichkeit in den Testfällen. Zeilen mit fehlenden Werten für das Zielattribut werden ausgeschlossen. Dieses Measure gibt normalerweise den Grad an, um den sich die Wahrscheinlichkeit des Zielergebnisses verbessert, wenn das Modell verwendet wird.<br /><br /> **Wurzel des mittleren quadratischen Fehlers**: Quadratwurzel des mittleren Fehlers für alle Partitions Fälle, dividiert durch die Anzahl der Fälle in der Partition, ohne die Zeilen mit fehlenden Werten für das Ziel Attribut. RMSE ist eine bekannte Schätzfunktion für Vorhersagemodelle. Im Ergebnis werden die Restwerte für jeden Fall gemittelt, wodurch sich ein einzelner Indikator für den Modellfehler ergibt.<br /><br /> **Log Score**: der Logarithmus der tatsächlichen Wahrscheinlichkeit für jeden Fall, summiert und dann dividiert durch die Anzahl der Zeilen im Eingabe DataSet, ohne die Zeilen mit fehlenden Werten für das Ziel Attribut. Da die Wahrscheinlichkeit als Dezimalbruch dargestellt wird, sind logarithmische Ergebnisse immer negative Zahlen. Eine Zahl, die näher bei 0 liegt, ist ein besseres Ergebnis. Während Rohergebnisse sehr unregelmäßige oder verfälschte Verteilungen aufweisen können, ist ein logarithmisches Ergebnis einem Prozentwert ähnlich.|  
|Schätzung|Measures, die nur auf schätzungs Modelle angewendet werden, die ein kontinuierliches numerisches Attribut Vorhersagen:<br /><br /> **Wurzel des mittleren quadratischen Fehlers**: Durchschnittlicher Fehler, wenn der vorhergesagte Wert mit dem tatsächlichen Wert verglichen wird. RMSE ist eine bekannte Schätzfunktion für Vorhersagemodelle. Im Ergebnis werden die Restwerte für jeden Fall gemittelt, wodurch sich ein einzelner Indikator für den Modellfehler ergibt.<br /><br /> **Mittelwert absoluter Fehler**: Durchschnittlicher Fehler, wenn vorhergesagte Werte mit den tatsächlichen Werten verglichen werden, berechnet als Mittelwert der absoluten Summe der Fehler. Mithilfe des mittleren absoluten Fehlers lässt sich einfacher verdeutlichen, wie nahe die Vorhersagen und die Istwerte insgesamt beieinander liegen. Ein kleineres Ergebnis bedeutet, dass die Vorhersagen genauer waren.<br /><br /> **Log Score**: der Logarithmus der tatsächlichen Wahrscheinlichkeit für jeden Fall, summiert und dann dividiert durch die Anzahl der Zeilen im Eingabe DataSet, ohne die Zeilen mit fehlenden Werten für das Ziel Attribut. Da die Wahrscheinlichkeit als Dezimalbruch dargestellt wird, sind logarithmische Ergebnisse immer negative Zahlen. Eine Zahl, die näher bei 0 liegt, ist ein besseres Ergebnis. Während Rohergebnisse sehr unregelmäßige oder verfälschte Verteilungen aufweisen können, ist ein logarithmisches Ergebnis einem Prozentwert ähnlich.|  
|Aggregate|Aggregat Measures geben Aufschluss über die Varianz in den Ergebnissen für jede Partition:<br /><br /> **Mittelwert**: Durchschnitt der Partitionswerte für ein bestimmtes Measure.<br /><br /> **Standard Abweichung**: Durchschnitt der Abweichung vom Mittelwert für ein bestimmtes Measure für alle Partitionen in einem Modell. Bei der Kreuzvalidierung impliziert ein höherer Wert für dieses Ergebnis eine erhebliche Variation zwischen den Folds.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tests und Überprüfung &#40;Data Mining&#41;](testing-and-validation-data-mining.md)  
  
  
