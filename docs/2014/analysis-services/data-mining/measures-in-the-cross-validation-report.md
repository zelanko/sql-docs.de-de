---
title: Measures in der übergreifenden Überprüfungsbericht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
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
ms.openlocfilehash: df327dbf712e82100ea0edb3c2943ade9d6e1b87
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120730"
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
|Clustering|Auf Clustermodelle anwendbare Measures:<br /><br /> **Fallwahrscheinlichkeit**: dieses Measure gibt normalerweise an, wie wahrscheinlich es, die ein Fall einem bestimmten Cluster angehört. <br />                      Bei der Kreuzvalidierung werden die Ergebnisse addiert und dann durch die Anzahl der Fälle dividiert, sodass das Ergebnis in diesem Fall einer durchschnittlichen Fallwahrscheinlichkeit entspricht.|  
|Klassifizierung|Auf klassifizierungsmodelle anwendbare Measures:<br /><br /> **Richtig positiv**/<br />                      **WAHR negativ**/ **falsch Positive**/ **falsch Positive**: Anzahl der Zeilen oder Werte in der Partition, in denen der vorhergesagte Status den Zielstatus übereinstimmt, und die vorhersagewahrscheinlichkeit ist größer als der angegebene Schwellenwert. Fälle mit fehlenden Werten für das Zielattribut ausgeschlossen werden, kann also die Anzahl aller Werte nicht bis hinzufügen|  
||**Erfolg/Misserfolg**: Anzahl der Zeilen oder Werte in der Partition, in denen der vorhergesagte Status mit den Zielstatus übereinstimmt und der vorhersagewahrscheinlichkeitswert größer als 0 ist.|  
|Wahrscheinlichkeit|Wahrscheinlichkeitsmeasures gelten für mehrere Modelltypen:<br /><br /> **Heben Sie**: das Verhältnis der tatsächlichen vorhersagewahrscheinlichkeit zur randwahrscheinlichkeit in den Testfällen. Zeilen mit fehlenden Werten für das Zielattribut werden ausgeschlossen. Dieses Measure gibt normalerweise den Grad an, um den sich die Wahrscheinlichkeit des Zielergebnisses verbessert, wenn das Modell verwendet wird.<br /><br /> **Wurzel des mittleren quadratischen Fehler**: Quadratwurzel des mittleren Fehlers für alle partitionsfälle geteilt durch die Anzahl der Fälle in der Partition ohne die Zeilen mit fehlenden Werten für das Zielattribut. RMSE ist eine bekannte Schätzfunktion für Vorhersagemodelle. Im Ergebnis werden die Restwerte für jeden Fall gemittelt, wodurch sich ein einzelner Indikator für den Modellfehler ergibt.<br /><br /> **Logarithmisches Ergebnis**: der Logarithmus der tatsächlichen Wahrscheinlichkeit für jeden Fall, summiert und dann dividiert durch die Anzahl der Zeilen im Eingabedataset, ohne die Zeilen mit fehlenden Werten für das Zielattribut. Da die Wahrscheinlichkeit als Dezimalbruch dargestellt wird, sind logarithmische Ergebnisse immer negative Zahlen. Eine Zahl, die näher bei 0 liegt, ist ein besseres Ergebnis. Während Rohergebnisse sehr unregelmäßige oder verfälschte Verteilungen aufweisen können, ist ein logarithmisches Ergebnis einem Prozentwert ähnlich.|  
|Schätzung|Measures, die nur auf schätzungsmodelle angewendet, die ein kontinuierliches numerisches Attribut Vorhersagen:<br /><br /> **Wurzel des mittleren quadratischen Fehler**: durchschnittliche Abweichung, wenn der vorhergesagte Wert mit dem Istwert verglichen wird. RMSE ist eine bekannte Schätzfunktion für Vorhersagemodelle. Im Ergebnis werden die Restwerte für jeden Fall gemittelt, wodurch sich ein einzelner Indikator für den Modellfehler ergibt.<br /><br /> **Mittlerer absoluter Fehler**: durchschnittliche Abweichung, wenn vorhergesagte Werte mit Istwerten, berechnet als Mittelwert der absoluten Summe der Fehler verglichen werden. Mithilfe des mittleren absoluten Fehlers lässt sich einfacher verdeutlichen, wie nahe die Vorhersagen und die Istwerte insgesamt beieinander liegen. Ein kleineres Ergebnis bedeutet, dass die Vorhersagen genauer waren.<br /><br /> **Logarithmisches Ergebnis**: der Logarithmus der tatsächlichen Wahrscheinlichkeit für jeden Fall, summiert und dann dividiert durch die Anzahl der Zeilen im Eingabedataset, ohne die Zeilen mit fehlenden Werten für das Zielattribut. Da die Wahrscheinlichkeit als Dezimalbruch dargestellt wird, sind logarithmische Ergebnisse immer negative Zahlen. Eine Zahl, die näher bei 0 liegt, ist ein besseres Ergebnis. Während Rohergebnisse sehr unregelmäßige oder verfälschte Verteilungen aufweisen können, ist ein logarithmisches Ergebnis einem Prozentwert ähnlich.|  
|Aggregate|Aggregierte Measures geben einen Überblick über die Abweichung in den Ergebnissen für jede Partition:<br /><br /> **Bedeutet, dass**: Mittelwert der Partitionswerte für ein bestimmtes Measure-Werte.<br /><br /> **Standardabweichung**: Durchschnitt der Abweichung vom Mittelwert für ein bestimmtes Measure für alle Partitionen in einem Modell. Bei der Kreuzvalidierung impliziert ein höherer Wert für dieses Ergebnis eine erhebliche Variation zwischen den Folds.|  
  
## <a name="see-also"></a>Siehe auch  
 [Tests und Überprüfung &#40;Datamining&#41;](testing-and-validation-data-mining.md)  
  
  
