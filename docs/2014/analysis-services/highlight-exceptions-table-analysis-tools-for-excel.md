---
title: Ausnahmen hervorheben (Tabellenanalyse Tools für Excel) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66080755"
---
# <a name="highlight-exceptions-table-analysis-tools-for-excel"></a>Ausnahmen hervorheben (Tabellenanalysetools für Excel)
  ![Ausnahmen hervorheben (Schaltfläche auf Menüband)](media/tat-highlightex.gif "Ausnahmen hervorheben (Schaltfläche auf Menüband)")  
  
 Gelegentlich können Ihre Daten ungewöhnliche Werte enthalten. Als Alter eines Hauseigentümers kann z. B. fünf Jahre angegeben sein. Diese Werte, die oft als *Ausreißer*bezeichnet werden, sind möglicherweise aufgrund eines Dateneingabe Fehlers falsch, oder Sie können auf ungewöhnliche Trends hindeuten. In jedem Fall können Ausnahmen Auswirkungen auf die Qualität Ihrer Analyse haben. Das Tool **Ausnahmen hervorheben** hilft Ihnen beim Auffinden dieser Werte und der Überprüfung auf weitere Aktionen.  
  
 Das Tool **Ausnahmen hervorheben** kann mit dem gesamten Datenbereich in einer Excel-Datentabelle arbeiten, oder Sie können nur wenige Spalten auswählen. Außerdem ist es möglich, einen Schwellenwert zu definieren, der die Datenvariabilität steuert, um mehr oder weniger Ausnahmen zu finden.  
  
 Nach der Analyse des Tools erstellt es ein neues Arbeitsblatt, das einen Zusammenfassungsbericht dazu enthält, wie viele Ausreißer in den einzelnen analysierten Spalten gefunden wurden. Das Tool hebt auch die Ausnahmen in der ursprünglichen Datentabelle hervor. Da mit dem Tool allgemeine Trends analysiert werden, wird möglicherweise festgestellt, dass die meisten Werte in einer Zeile normal sind, und es wird nur eine Zelle in dieser Zeile hervorgehoben. Im obigen Beispiel für Hauseigentümer kann nur die Spalte **Age** hervorgehoben werden.  
  
 Sie können auch den Schwellenwert für die **Ausnahme** im **Zusammenfassungs Bericht**ändern. Dieser Wert gibt die Wahrscheinlichkeit an, mit der eine bestimmte Zelle einen ungewöhnlichen Wert enthält. Wenn Sie diesen Wert erhöhen, werden daher weniger Werte als Ausreißer hervorgehoben. Wenn Sie hingegen den Wert verringern, werden mehr Zellen hervorgehoben.  
  
## <a name="using-the-highlight-exceptions-tool"></a>Verwenden des Tools 'Ausnahmen hervorheben'  
  
1.  Öffnen Sie eine Excel-Tabelle, und klicken Sie auf **Ausnahmen markieren**.  
  
2.  Geben Sie die zu analysierenden Spalten an.  
  
3.  Klicken Sie auf **Ausführen**.  
  
4.  Öffnen Sie das Arbeitsblatt \<mit dem Titel Tabellenname> Ausreißer, um eine Zusammenfassung der gefundenen Ausreißer anzuzeigen.  
  
5.  Um die Anzahl der Highlights zu ändern, klicken Sie in der Zeile **Ausnahme Schwellenwert** des **Berichts Ausnahmen hervorheben**auf die Pfeile nach oben und nach unten.  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Sie können auch Spalten einbeziehen, die keinen falschen Werte enthalten, wenn diese Werte Informationen enthalten, die zum Vorhersagen anderer Zeilen nützlich sein können. Sie sollten jedoch die Auswahl von Spalten aufheben, deren Werte fehlen oder Null sind.  
  
 Da alle ausgewählten Spalten für die Ermittlung eines allgemeinen Musters herangezogen werden, sollten Sie keine Spalten auswählen, die bekanntermaßen ungeeignete Daten enthalten, z. B.:  
  
-   Spalten, die eindeutige Werte wie z. B. IDs enthalten  
  
-   Spalten, die einen hohen Prozentsatz falscher Werte enthalten  
  
-   Spalten mit vielen fehlenden Werten  
  
     Beachten Sie, dass es gelegentlich nützlich sein kann, Eingabespalten einzuschließen, die über viele fehlende Werte verfügen. Beispiel: Wenn der Wert des Adressfelds immer fehlt, wenn der Kunde einen Kauf über einen Einzelhändler tätigt, kann der Data Mining-Algorithmus diese Informationen nutzen, um ähnliche Kunden zu identifizieren. Sie müssen von Fall zu Fall bestimmen, ob Daten fehlen, weil sie weggelassen wurden oder weil der Status "Fehlend" sinnvoll ist.  
  
-   Spalten, die für die Erstellung eines Musters wahrscheinlich nicht nützlich sind. Eine Spalte, die in jeder Zeile den gleichen Wert aufweist, wäre z. B. nicht hilfreich bei der Erstellung von Mustern.  
  
## <a name="understanding-the-highlight-exceptions-report"></a>Grundlegendes zum Bericht 'Ausnahmen hervorheben'  
 Wenn Sie auf **Ausführen**klicken, führt das Tool drei Schritte aus:  
  
-   Es erstellt eine Data Mining-Struktur anhand der aktuellen Daten in der Tabelle.  
  
-   Es erstellt ein neues Data Mining-Modell mithilfe des [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus.  
  
-   Es erstellt eine Vorhersageabfrage anhand der Muster, um zu ermitteln, ob im Arbeitsblatt unwahrscheinliche Werte enthalten sind.  
  
 Der ursprüngliche Wert des Ausnahmeschwellenwerts ist stets 75, d. h. der Algorithmus hat berechnet, dass eine Möglichkeit von 75 Prozent besteht, dass die hervorgehobenen Werte falsch sind. Dieser Schwellenwert wird für die erste Analyse vom Tool automatisch festgelegt. Sie können den Wert jedoch im Bericht ändern.  
  
 Das Tool **Ausnahmen hervorheben** markiert die Zellen in der ursprünglichen Datentabelle, die verdächtig sind. Eine dunkle Hervorhebung bedeutet, dass die Zeile überprüft werden sollte. Eine helle Hervorhebung bedeutet, dass in dieser Zelle ein fehlerverdächtiger Wert gefunden wurde. Wenn Sie den Schwellenwert für die Ausnahmen ändern, ändern sich die hervorgehobenen Werte entsprechend.  
  
 Das Zusammenfassungsdiagramm zeigt die Anzahl der Zellen in jeder Spalte, die über dem Ausnahmeschwellenwert liegen.  
  
## <a name="related-tools"></a>Verwandte Tools  
 Wenn Sie vor dem Data Mining Daten bereinigen oder überprüfen, sollten Sie auch die Funktionen zum Durchsuchen von Daten im Data Mining-Client für Excel ausprobieren. Dieses Add-In enthält erweiterte Tools zum Finden von Ausreißern, Neubezeichnen von Daten oder Anzeigen der Verteilung von Daten. Weitere Informationen zu Tools zum Durchsuchen von Daten im Data Mining-Client für Excel finden Sie unter durch [Suchen und Bereinigen von Daten](exploring-and-cleaning-data.md).  
  
 Das Tool **Ausnahmen hervorheben** verwendet [!INCLUDE[msCoName](../includes/msconame-md.md)] den Clustering-Algorithmus. Ein Clustermodell erkennt Gruppen von Zeilen mit ähnlichen Merkmalen. Der Data Mining-Client für Excel bietet ein Fenster zum **Durchsuchen** , in dem Diagramme und Merkmal Profile verwendet werden, um die durch das Clustering erstellten Data Mining Modelle zu untersuchen. Weitere Informationen zum Durchsuchen des Clustering-Modells, das mit dem Tool **Ausnahmen hervorheben** erstellt wurde, finden Sie unter [Durchsuchen von Modellen (Data Mining-Client für Excel)](highlight-exceptions-table-analysis-tools-for-excel.md).  
  
 Weitere Informationen zum [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus finden Sie im Thema zum Microsoft Clustering-Algorithmus in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  
