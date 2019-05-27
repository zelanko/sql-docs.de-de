---
title: Markieren von Ausnahmen (Tabellenanalysetools für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- highlight exceptions
ms.assetid: d90a12f8-7bc3-4fdb-95a1-7c89058f0d9a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 18bf54b7b97598c6c61d7e282ad5791d926cc25a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66080755"
---
# <a name="highlight-exceptions-table-analysis-tools-for-excel"></a>Ausnahmen hervorheben (Tabellenanalysetools für Excel)
  ![Markieren Sie die Schaltfläche im Menüband Ausnahmen](media/tat-highlightex.gif "Ausnahmen hervorheben-Schaltfläche im Menüband")  
  
 Gelegentlich können Ihre Daten ungewöhnliche Werte enthalten. Als Alter eines Hauseigentümers kann z. B. fünf Jahre angegeben sein. Diese Werte, die häufig aufgerufen *Ausreißer*, möglicherweise aufgrund eines falschen oder sie können darauf hinweisen, ungewöhnliche Trends darstellen. In jedem Fall können Ausnahmen Auswirkungen auf die Qualität Ihrer Analyse haben. Die **Ausnahmen hervorheben** Tool können Sie diese Werte finden und zu überprüfen, um weitere Aktionen.  
  
 Die **Ausnahmen hervorheben** Tool kann mit den gesamten Bereich der Daten in einer Excel-Datentabelle arbeiten oder Sie können nur wenige Spalten auswählen. Außerdem ist es möglich, einen Schwellenwert zu definieren, der die Datenvariabilität steuert, um mehr oder weniger Ausnahmen zu finden.  
  
 Nach der Analyse des Tools erstellt es ein neues Arbeitsblatt, das einen Zusammenfassungsbericht dazu enthält, wie viele Ausreißer in den einzelnen analysierten Spalten gefunden wurden. Das Tool hebt auch die Ausnahmen in der ursprünglichen Datentabelle hervor. Da mit dem Tool allgemeine Trends analysiert werden, wird möglicherweise festgestellt, dass die meisten Werte in einer Zeile normal sind, und es wird nur eine Zelle in dieser Zeile hervorgehoben. Im Beispiel oben kann nur Hauseigentümer der **Alter** hervorgehoben werden kann.  
  
 Sie können auch ändern, die **ausnahmeschwellenwert** Wert in der **Zusammenfassungsbericht**. Dieser Wert gibt die Wahrscheinlichkeit an, mit der eine bestimmte Zelle einen ungewöhnlichen Wert enthält. Wenn Sie diesen Wert erhöhen, werden daher weniger Werte als Ausreißer hervorgehoben. Wenn Sie hingegen den Wert verringern, werden mehr Zellen hervorgehoben.  
  
## <a name="using-the-highlight-exceptions-tool"></a>Verwenden des Tools 'Ausnahmen hervorheben'  
  
1.  Öffnen Sie eine Excel-Tabelle, und klicken Sie auf **Ausnahmen hervorheben**.  
  
2.  Geben Sie die zu analysierenden Spalten an.  
  
3.  Klicken Sie auf **Ausführen**.  
  
4.  Öffnen Sie das Arbeitsblatt mit dem Titel \<Tabellenname > Ausreißer, um eine Zusammenfassung der Ausreißer anzuzeigen, die gefunden wurden.  
  
5.  Um die Anzahl der Hervorhebungen ändern möchten, klicken Sie auf den Pfeil nach oben und unten weisenden Pfeil in der **Ausnahmeschwellenwert** Zeile die **Ausnahmenbericht markieren**.  
  
### <a name="requirements"></a>Anforderungen  
 Sie können auch Spalten einbeziehen, die keinen falschen Werte enthalten, wenn diese Werte Informationen enthalten, die zum Vorhersagen anderer Zeilen nützlich sein können. Sie sollten jedoch die Auswahl von Spalten aufheben, deren Werte fehlen oder Null sind.  
  
 Da alle ausgewählten Spalten für die Ermittlung eines allgemeinen Musters herangezogen werden, sollten Sie keine Spalten auswählen, die bekanntermaßen ungeeignete Daten enthalten, z. B.:  
  
-   Spalten, die eindeutige Werte wie z. B. IDs enthalten  
  
-   Spalten, die einen hohen Prozentsatz falscher Werte enthalten  
  
-   Spalten mit vielen fehlenden Werten  
  
     Beachten Sie, dass es gelegentlich nützlich sein kann, Eingabespalten einzuschließen, die über viele fehlende Werte verfügen. Beispiel: Wenn der Wert des Adressfelds immer fehlt, wenn der Kunde einen Kauf über einen Einzelhändler tätigt, kann der Data Mining-Algorithmus diese Informationen nutzen, um ähnliche Kunden zu identifizieren. Sie müssen von Fall zu Fall bestimmen, ob Daten fehlen, weil sie weggelassen wurden oder weil der Status "Fehlend" sinnvoll ist.  
  
-   Spalten, die für die Erstellung eines Musters wahrscheinlich nicht nützlich sind. Eine Spalte, die in jeder Zeile den gleichen Wert aufweist, wäre z. B. nicht hilfreich bei der Erstellung von Mustern.  
  
## <a name="understanding-the-highlight-exceptions-report"></a>Grundlegendes zum Bericht 'Ausnahmen hervorheben'  
 Beim Klicken auf **ausführen**, das Tool führt drei Aufgaben:  
  
-   Es erstellt eine Data Mining-Struktur anhand der aktuellen Daten in der Tabelle.  
  
-   Es erstellt ein neues Data Mining-Modell mithilfe des [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus.  
  
-   Es erstellt eine Vorhersageabfrage anhand der Muster, um zu ermitteln, ob im Arbeitsblatt unwahrscheinliche Werte enthalten sind.  
  
 Der ursprüngliche Wert des Ausnahmeschwellenwerts ist stets 75, d. h. der Algorithmus hat berechnet, dass eine Möglichkeit von 75 Prozent besteht, dass die hervorgehobenen Werte falsch sind. Dieser Schwellenwert wird für die erste Analyse vom Tool automatisch festgelegt. Sie können den Wert jedoch im Bericht ändern.  
  
 Die **Ausnahmen hervorheben** Tool markiert den Zellen in der ursprünglichen Datentabelle, die sich nicht sicher sind. Eine dunkle Hervorhebung bedeutet, dass die Zeile überprüft werden sollte. Eine helle Hervorhebung bedeutet, dass in dieser Zelle ein fehlerverdächtiger Wert gefunden wurde. Wenn Sie den Schwellenwert für die Ausnahmen ändern, ändern sich die hervorgehobenen Werte entsprechend.  
  
 Das Zusammenfassungsdiagramm zeigt die Anzahl der Zellen in jeder Spalte, die über dem Ausnahmeschwellenwert liegen.  
  
## <a name="related-tools"></a>Verwandte Tools  
 Wenn Sie vor dem Data Mining Daten bereinigen oder überprüfen, sollten Sie auch die Funktionen zum Durchsuchen von Daten im Data Mining-Client für Excel ausprobieren. Dieses Add-In enthält erweiterte Tools zum Finden von Ausreißern, Neubezeichnen von Daten oder Anzeigen der Verteilung von Daten. Weitere Informationen zu den Tools zum zum Durchsuchen von Daten in Data Mining-Client für Excel finden Sie unter [Exploring und Bereinigen von Daten](exploring-and-cleaning-data.md).  
  
 Die **Ausnahmen hervorheben** tool verwendet die [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus. Ein Clustermodell erkennt Gruppen von Zeilen mit ähnlichen Merkmalen. Data Mining-Client für Excel stellt eine **Durchsuchen** Fenster, das Diagrammen und merkmalprofilen verwendet werden, um mit clustering erstellt die Datamining-Modelle zu untersuchen. Informationen zum Navigieren im clustering-Modells erstellt, indem die **Ausnahmen hervorheben** finden Sie unter [Modell durchsuchen (Data Mining-Client für Excel)](highlight-exceptions-table-analysis-tools-for-excel.md).  
  
 Weitere Informationen zum [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus finden Sie im Thema zum Microsoft Clustering-Algorithmus in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  
