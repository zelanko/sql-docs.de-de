---
title: Analysieren Sie die wichtige Einflussfaktoren (Tabellenanalysetools für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- key influencers
- factor analysis
ms.assetid: 54d7b4ce-7b79-407a-985c-aa655ad19280
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: df6622abc3a507d917aefd2a8a5a1bf9505a2622
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66062261"
---
# <a name="analyze-key-influencers-table-analysis-tools-for-excel"></a>Wichtige Einflussfaktoren analysieren (Tabellenanalysetools für Excel)
  ![Schaltfläche "Analysieren wichtige Einflussfaktoren" im Menüband](media/tat-aki.gif "wichtige Einflussfaktoren analysieren-Schaltfläche im Menüband")  
  
 Mit der **wichtige Einflussfaktoren analysieren** -Tool, wählen Sie eine Spalte, die ein zielergebnis enthält, und der Algorithmus bestimmt, welche Faktoren den stärksten Einfluss auf das Ergebnis hatten.  
  
 Im Tool werden neue Datentabellen erstellt, in denen die zu jedem Ergebnis gehörenden Faktoren aufgeführt und die Beziehungswahrscheinlichkeit grafisch dargestellt wird. Sie können die Tabellen nach verschiedenen Faktoren und Ergebnissen filtern, um die Resultate ausführlicher zu prüfen.  
  
 Sie können auch zwei mögliche Ergebnisse auswählen und diese miteinander vergleichen. Beispielsweise können Sie verschiedene Verbrauchergruppen vergleichen, um mögliche Faktoren für die Entscheidungsfindung zu ermitteln.  
  
## <a name="using-the-analyze-key-influencers-tool"></a>Verwenden des Tools Wichtige Einflussfaktoren analysieren  
  
1.  Öffnen Sie eine Excel-Datentabelle.  
  
2.  In **Tabellentools**auf die **analysieren** des Menübands, klicken Sie auf **wichtige Einflussfaktoren analysieren.**  
  
3.  Öffnen Sie die Spalte, die das Ziel der Analyse darstellt.  
  
4.  Klicken Sie optional auf **Spalten für die Analyse auswählen**. In der **erweiterte Spaltenauswahl** Dialogfeld Wählen Sie die Spalten, die am wahrscheinlichsten relevanten Daten enthalten sind. Um Leistung und Genauigkeit zu verbessern, heben Sie die Auswahl von Spalten wie ID oder Name auf, die für die Musteranalyse irrelevant sind. Klicken Sie auf **OK** schließen die **erweiterte Spaltenauswahl** Dialogfeld.  
  
5.  Klicken Sie auf **Ausführen**.  
  
     Die **wichtige Einflussfaktoren analysieren** Tool führt eine Analyse der Daten, die optimalen Einstellungen zu ermitteln, und alle Parameter automatisch festgelegt.  
  
6.  Wenn keine Muster erkannt werden, erstellt der Assistent ein neues Arbeitsblatt, das eine Beschreibung des Problems enthält.  
  
7.  Wenn Muster erkannt werden, erstellt der Assistent auf einem neuen Arbeitsblatt einen Bericht, der die Muster enthält. Der Bericht wird mit dem Namen **wichtige Einflussfaktoren für \<Spalte >**. Sie haben folgende Möglichkeiten, den Bericht anzupassen:  
  
#### <a name="create-a-custom-report"></a>Erstellen eines benutzerdefinierten Berichts  
  
1.  In der **Unterscheidung basierend auf wichtigen Einflussfaktoren** Dialogfeld Wählen Sie die beiden Werte, die Sie vergleichen, indem Sie sie aus auswählen möchten die **Wert 1** und **Wert 2** Dropdown-Listen . Sie können zum Beispiel Käufer und Nicht-Käufer vergleichen.  
  
2.  Klicken Sie auf **Bericht hinzufügen**.  
  
     Im Assistenten wird ein neues Arbeitsblatt erstellt und für jedes Paar von Schlüsselfaktorvergleichen eine Tabelle hinzugefügt.  
  
3.  Wenn Sie Vergleiche abgeschlossen haben, klicken Sie auf **schließen**.  
  
## <a name="understanding-the-key-influencers-report"></a>Grundlegendes zum Bericht der wichtigen Einflussfaktoren  
 Nachdem das Datenmodell erstellt wurde, die **wichtige Einflussfaktoren analysieren** Tool erstellt Berichte, mit denen Sie untersuchen und wichtige Einflussfaktoren verglichen werden soll.  
  
-   Der Bericht auf der linken Seite wird standardmäßig generiert. Außerdem werden hier die stärksten Indikatoren der Ergebnisspalte angezeigt (die abhängige Variable).  
  
-   Der Bericht auf der rechten Seite ist optional. Sie können ihn erstellen, indem Sie zwei bestimmten Ergebniswerte vergleichen. Dieser Bericht vergleicht Käufer und Nicht-Käufer.  
  
-   Beachten Sie, dass für jeden Bericht ein neues Arbeitsblatt hinzugefügt wird, den Sie erstellen. Sie können die Tabellen verschieben, nachdem sie erstellt wurden; sie werden für den Vergleich nebeneinander platziert.  
  
 ![DM13](media/dm13-tat-aki-report.gif "DM13")  
  
 **Relative Auswirkung**  
 Der schattierte Balken im ersten Bericht gibt die Gewichtung der Zuordnung dieses Attributs zu dem Ergebnis an.  
  
 Die Länge des Balkens gibt die Wahrscheinlichkeit an, dass der Faktor zum Ergebnis beiträgt. Je länger der schattierte Balken also ist, desto stärker ist die Verknüpfung.  
  
 **Begünstigt**  
 Im zweiten Bericht werden die Zielwerte, die Sie vergleichen, in zwei Spalten aufgeführt. Die zugehörigen Faktoren werden in absteigender Reihenfolge (in Bezug auf die Zuverlässigkeit) aufgeführt.  
  
-   Die **blaue** Balken zeigt die Attribute, die auf das Ergebnis beitragen, "Nein" (= kein Einkauf).  
  
-   Die **roten** Balken zeigt die Attribute zum Ergebnis beitragen, "Yes" (= ein Fahrrad gekauft haben).  
  
 Die Farben in der schattierten Leiste sind beliebig wählbar. Sie können diese Farben ändern, indem Sie die Optionen für Tabellenentwurf in Excel festlegen.  
  
 In einem Bericht, der zwei Werte miteinander vergleicht, werden die wichtigen Einflussfaktoren im zweiten Bericht nach ihrer Auswirkung auf die Zielwerte sortiert.  
  
 Da alle Diagramme auf Excel-Tabellen basieren, können Sie die Tabellen filtern und sortieren, um sich auf bestimmte Faktoren oder Ergebnisse zu konzentrieren.  
  
## <a name="more-about-the-analyze-key-influencers-tool"></a>Weitere Informationen zum Tool "Wichtige Einflussfaktoren analysieren"  
 Wenn die **wichtige Einflussfaktoren analysieren** Tool analysiert die Daten, die bewirkt Folgendes:  
  
-   Es wird eine Datenstruktur erstellt, in der wichtige Informationen zur Verteilung von Daten gespeichert werden.  
  
-   Erstellt ein Modell mithilfe des Microsoft Naïve Bayes-Algorithmus.  
  
-   Erstellt Vorhersagen, die jede Datenspalte mit dem angegebenen Ergebnis korrelieren.  
  
-   Verwendet das Vertrauensergebnis für jede Vorhersage, um die Faktoren zu identifizieren, die sich beim Erzeugen des Zielergebnisses am meisten ausgewirkt haben.  
  
-   Erstellt einen Bericht, der die wichtigen Einflussfaktoren beschreibt, die nach dem Vertrauensergebnis sortiert sind.  
  
### <a name="requirements"></a>Anforderungen  
 Wenn die Zielspalte kontinuierliche numerische Werte enthält, werden die numerischen Werte vom Tool automatisch in Gruppen unterteilt. Diese Gruppierungen stellen Cluster von Fällen mit ähnlichen Merkmalen dar. Numerische Werte können jedoch nicht in benutzerfreundliche Gruppen aufgeteilt werden. Beispielsweise kann der Bericht enthält eine Gruppierung wie z. B. "\<12.85701", während die Benutzer des Berichts in der Regel Gruppierungen angezeigt, die ganze Zahlen, wie z. B. 10-19, 20-29 und So weiter verwenden möchten.  
  
 Wenn Sie numerische Daten anders gruppieren möchten, müssen Sie die Daten vor der Analyse entsprechend segmentieren. Beispielsweise können Sie die [neu bezeichnen](relabel-sql-server-data-mining-add-ins.md) Tool im Data Mining-Client für Excel verwenden, um eine neue gruppenbezeichnung in einer separaten Spalte erstellen, und klicken Sie dann nur die neue Spalte in der Analyse verwenden.  
  
### <a name="related-tools"></a>Verwandte Tools  
 Die **Data Mining** Menüband bietet erweiterte Tools, einschließlich der Möglichkeit, Datamining-Modelle anpassen.  
  
 Wenn Sie Ihr Modell mithilfe von speichern die **wichtige Einflussfaktoren analysieren** -Tool können Sie Data Mining-Client das Modell durchsuchen und Beziehungen ausführlicher untersuchen. Weitere Informationen finden Sie unter [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md). Sie können mithilfe von Microsoft Office Visio Diagramme erstellen, die Beziehungen als Cluster oder Abhängigkeitsnetzwerke anzeigen. Weitere Informationen finden Sie unter [Problembehandlung Visio Data Mining-Diagramme in &#40;SQL Server Data Mining-Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md).  
  
> [!NOTE]  
>  Die mit den Tabellenanalysetools erstellten Modelle werden gelöscht, wenn Sie das Arbeitsblatt schließen oder die Verbindung mit dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server beenden. Daher können Sie die Modelle nur durchsuchen, solange die Verbindung bestehen bleibt. Sie können die Modelle nicht in Visio rendern, wenn Sie die Verbindung beenden oder das Arbeitsblatt schließen.  
  
 Weitere Informationen zu den vom verwendeten Algorithmus die **wichtige Einflussfaktoren analysieren** finden Sie unter "Microsoft Naive Bayes-Algorithmus" in SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)   
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)  
  
  
