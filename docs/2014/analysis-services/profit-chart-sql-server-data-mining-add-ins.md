---
title: Gewinn Diagramm (SQL Server Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- profit chart
- mining models, charting
- mining models, testing
ms.assetid: 5c902543-4da9-4db3-99d5-4ce04c43d7ef
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 32ee1539c734c549f89d5b3db8ec4add467a72b2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66070588"
---
# <a name="profit-chart-sql-server-data-mining-add-ins"></a>Gewinndiagramm (SQL Server Data Mining-Add-Ins)
  ![Gewinndiagramm (Schaltfläche auf Data Mining-Menüband)](media/dmc-profitchart.gif "Gewinndiagramm (Schaltfläche auf Data Mining-Menüband)")  
  
 Ein Gewinndiagramm zeigt den geschätzten Gewinnanstieg an, der einem Miningmodell zugeordnet ist, um so zu ermitteln, welche Kunden in einem Geschäftsszenario angesprochen werden sollen. Auf der Y-Achse des Diagramms ist der Gewinn dargestellt, während auf der X-Achse der Prozentwert der vom Unternehmen angesprochenen Personen dargestellt ist. Ein typisches Gewinndiagramm zeigt einen Anstieg der Gewinne bis zu einem Wendepunkt an, nach dem die Gewinne abnehmen, wenn mehr Personen angesprochen werden.  
  
## <a name="configuring-the-profit-chart"></a>Konfigurieren des Gewinndiagramms  
 Während im Genauigkeitsdiagramm nur die Wahrscheinlichkeit bewertet wird, mit der Vorhersagen falsch oder richtig sind, werden im Gewinndiagramm Erfahrungswerte aus der realen Welt über die Konsequenzen von Aktionen infolge einer bestimmten Vorhersage mit einbezogen. Dazu werden folgende Faktoren berücksichtigt, die Sie beim Ausführen des Assistenten angeben:  
  
-   **Bevölkerungs**  
  
     Die Anzahl von Fällen im Dataset, die zum Erstellen des Liftdiagramms verwendet wird. Dies ist z. B. die Anzahl von potenziellen Kunden.  
  
-   **Festes Kosten**  
  
     Die festen Kosten, die mit dem Geschäftsproblem verbunden sind. Wenn es sich hier z. B. um eine gezielte Mailingaktion handelt, hängen die Kosten nicht von variablen Werten (z. B. der Anzahl von getätigten Telefonanrufen oder der Anzahl von verschickten Werbesendungen) ab.  
  
-   **Einzelkosten**  
  
     Kosten, die zusätzlich zu den festen Kosten entstehen und den einzelnen Kundenkontakten zugeordnet werden können. Dies wären z. B. Werbesendungen oder Telefonanrufe.  
  
-   **Einzelumsatz**  
  
     Die Höhe des mit einem erfolgreichen Verkauf verbundenen Umsatzes.  
  
## <a name="using-the-profit-chart-wizard"></a>Verwenden des Gewinndiagramm-Assistenten  
 Beim Erstellen eines Gewinndiagramms müssen Sie auf ein bereits vorhandenes Data Mining-Modell verweisen. Sie können Modelle durchsuchen, um nach einem Modell zu suchen, das Ihren Daten entspricht, indem Sie auf **Modelle verwalten** oder auf **Durchsuchen** klicken, um Details zu dem verwendeten Algorithmus und den Spalten im Mining Modell anzuzeigen.  
  
 Weitere Informationen finden Sie unter durch [Suchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) und [Verwalten von Modellen &#40;SQL Server Data Mining-Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md).  
  
#### <a name="to-create-a-profit-chart"></a>So erstellen Sie ein Gewinndiagramm  
  
1.  Wählen Sie ein bereits vorhandenes Modell aus.  
  
2.  Geben Sie die Spalte an, die vorhergesagt werden soll, sowie ggf. den Zielwert.  
  
3.  Wählen Sie die Quelldaten aus. Dies sind die Daten, die Sie in das Modell eingeben, um eine Vorhersage zu erstellen. Es sollte sich dabei nicht um die gleichen Daten handeln, mit denen Sie das Modell erstellt haben.  
  
4.  Ordnen Sie die Spalten in den neuen (Quell-)Daten den Spalten im Data Mining-Modell zu. Wenn sich die Spaltennamen ähneln, werden sie automatisch vom Assistenten zugeordnet.  
  
5.  Geben Sie die für den Assistenten erforderlichen Kosteninformationen ein: feste Kosten, Einzelkosten, Auffüllung und erwartete Einnahmen.  
  
6.  Optional können Sie eine gestaffelte Reihe von Kosten eingeben (Klicken Sie auf die Schaltfläche zum Durchsuchen **(...)** ). Beispielsweise fallen die Kosten für ein Mailing möglicherweise geringer aus, je größer die Anzahl der gesendeten Elemente ist. In diesem Fall können Sie abhängig von der Anzahl der Sendungen unterschiedliche Kosten eingeben. Die Kosten werden dann vom Assistenten für jede Stichprobengröße automatisch angepasst.  
  
7.  Vom Assistenten wird ein Diagramm erstellt, in dem die Kosten-Nutzen-Analyse für das Modell dargestellt wird.  
  
### <a name="requirements"></a>Anforderungen  
 Wenn Sie Vorhersagen für diskrete numerische Werte treffen möchten, müssen Sie den genauen vorherzusagenden Zielwert auswählen.  
  
## <a name="understanding-the-profit-chart"></a>Grundlegendes zum Gewinndiagramm  
 Das Gewinndiagramm enthält eine graue vertikale Linie, die Sie durch Klicken auf eine Stelle des Diagramms verschieben können. In der **Mining Legende** werden eine Bewertung, die richtige Auffüllung und die Vorhersage Wahrscheinlichkeit angezeigt, die mit der Position der grauen Linie im Diagramm verknüpft sind. Wenn Sie mit der grauen Linie im Diagramm den Punkt des höchsten Gewinns auswählen, können Sie über den Wert Vorhersagewahrscheinlichkeit einen Wahrscheinlichkeitsschwellenwert festlegen, ab dem ein Kunde angesprochen wird.  
  
 Wenn beispielsweise die Gewinnkurve ihren höchsten Punkt bei 55 Prozent der Auffüllung erreicht und die zugeordnete Vorhersagewahrscheinlichkeit bei 20 Prozent liegt, bedeutet dies, dass zur Erzielung des Gewinnmaximums nur diejenigen Kunden angesprochen werden sollten, von denen mit einer Wahrscheinlichkeit von 20 Prozent oder mehr eine Antwort erwartet werden kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Validieren von Modellen und Verwenden von Modellen für Vorhersage &#40;Data Mining-Add-Ins für Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
