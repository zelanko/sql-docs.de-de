---
title: Wichtige Einflussfaktoren analysieren (Tabellenanalyse Tools für Excel) | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66062261"
---
# <a name="analyze-key-influencers-table-analysis-tools-for-excel"></a>Wichtige Einflussfaktoren analysieren (Tabellenanalysetools für Excel)
  ![Schaltfläche "Wichtige Einflussfaktoren analysieren" in Menüband](media/tat-aki.gif "Schaltfläche "Wichtige Einflussfaktoren analysieren" in Menüband")  
  
 Mit dem Tool **wichtige Einflussfaktoren analysieren** wählen Sie eine Spalte aus, die ein Zielergebnis enthält, und der Algorithmus bestimmt, welche Faktoren den stärksten Einfluss auf das Ergebnis hatten.  
  
 Im Tool werden neue Datentabellen erstellt, in denen die zu jedem Ergebnis gehörenden Faktoren aufgeführt und die Beziehungswahrscheinlichkeit grafisch dargestellt wird. Sie können die Tabellen nach verschiedenen Faktoren und Ergebnissen filtern, um die Resultate ausführlicher zu prüfen.  
  
 Sie können auch zwei mögliche Ergebnisse auswählen und diese miteinander vergleichen. Beispielsweise können Sie verschiedene Verbrauchergruppen vergleichen, um mögliche Faktoren für die Entscheidungsfindung zu ermitteln.  
  
## <a name="using-the-analyze-key-influencers-tool"></a>Verwenden des Tools Wichtige Einflussfaktoren analysieren  
  
1.  Öffnen Sie eine Excel-Datentabelle.  
  
2.  Klicken Sie in **Tabellen Tools**auf dem Menüband **analysieren** auf **wichtige Einflussfaktoren analysieren.**  
  
3.  Öffnen Sie die Spalte, die das Ziel der Analyse darstellt.  
  
4.  Klicken Sie optional auf **Spalten auswählen, die für die Analyse verwendet werden sollen**. Wählen Sie im Dialogfeld **Erweiterte Spaltenauswahl** die Spalten aus, die am wahrscheinlichsten relevante Daten enthalten. Um Leistung und Genauigkeit zu verbessern, heben Sie die Auswahl von Spalten wie ID oder Name auf, die für die Musteranalyse irrelevant sind. Klicken Sie auf **OK** , um das Dialogfeld **Erweiterte Spaltenauswahl** zu schließen.  
  
5.  Klicken Sie auf **Ausführen**.  
  
     Das Tool **wichtige Einflussfaktoren analysieren** führt eine Analyse der Daten durch, um die optimalen Einstellungen zu ermitteln, und legt alle Parameter automatisch fest.  
  
6.  Wenn keine Muster erkannt werden, erstellt der Assistent ein neues Arbeitsblatt, das eine Beschreibung des Problems enthält.  
  
7.  Wenn Muster erkannt werden, erstellt der Assistent auf einem neuen Arbeitsblatt einen Bericht, der die Muster enthält. Der Bericht heißt **wichtige Einflussfaktoren \<für die Spalten>**. Sie haben folgende Möglichkeiten, den Bericht anzupassen:  
  
#### <a name="create-a-custom-report"></a>Erstellen eines benutzerdefinierten Berichts  
  
1.  Wählen Sie **in der** Dropdown Liste Wert 1 und Wert 2 die zwei zu vergleichenden Werte in der Dropdown Liste **Wert 1** und **Wert 2** aus. Sie können zum Beispiel Käufer und Nicht-Käufer vergleichen.  
  
2.  Klicken Sie auf **Bericht hinzufügen**.  
  
     Im Assistenten wird ein neues Arbeitsblatt erstellt und für jedes Paar von Schlüsselfaktorvergleichen eine Tabelle hinzugefügt.  
  
3.  Wenn Sie die Vergleiche abgeschlossen haben, klicken Sie auf **Schließen**.  
  
## <a name="understanding-the-key-influencers-report"></a>Grundlegendes zum Bericht der wichtigen Einflussfaktoren  
 Nachdem das Datenmodell erstellt wurde, erstellt das Tool **wichtige Einflussfaktoren analysieren** Berichte, die Ihnen helfen, wichtige Einflussfaktoren zu untersuchen und zu vergleichen.  
  
-   Der Bericht auf der linken Seite wird standardmäßig generiert. Außerdem werden hier die stärksten Indikatoren der Ergebnisspalte angezeigt (die abhängige Variable).  
  
-   Der Bericht auf der rechten Seite ist optional. Sie können ihn erstellen, indem Sie zwei bestimmten Ergebniswerte vergleichen. Dieser Bericht vergleicht Käufer und Nicht-Käufer.  
  
-   Beachten Sie, dass für jeden Bericht ein neues Arbeitsblatt hinzugefügt wird, den Sie erstellen. Sie können die Tabellen verschieben, nachdem sie erstellt wurden; sie werden für den Vergleich nebeneinander platziert.  
  
 ![DM13](media/dm13-tat-aki-report.gif "DM13")  
  
 **Relative Auswirkung**  
 Der schattierte Balken im ersten Bericht gibt die Gewichtung der Zuordnung dieses Attributs zu dem Ergebnis an.  
  
 Die Länge des Balkens gibt die Wahrscheinlichkeit an, dass der Faktor zum Ergebnis beiträgt. Je länger der schattierte Balken also ist, desto stärker ist die Verknüpfung.  
  
 **Begünstigt**  
 Im zweiten Bericht werden die Zielwerte, die Sie vergleichen, in zwei Spalten aufgeführt. Die zugehörigen Faktoren werden in absteigender Reihenfolge (in Bezug auf die Zuverlässigkeit) aufgeführt.  
  
-   Der **blaue** Balken zeigt Attribute an, die zum Ergebnis beitragen, "No" (= nicht gekauft).  
  
-   Der **Rote** Balken zeigt Attribute an, die zum Ergebnis beitragen, "yes" (= ein Fahrrad gekauft).  
  
 Die Farben in der schattierten Leiste sind beliebig wählbar. Sie können diese Farben ändern, indem Sie die Optionen für Tabellenentwurf in Excel festlegen.  
  
 In einem Bericht, der zwei Werte miteinander vergleicht, werden die wichtigen Einflussfaktoren im zweiten Bericht nach ihrer Auswirkung auf die Zielwerte sortiert.  
  
 Da alle Diagramme auf Excel-Tabellen basieren, können Sie die Tabellen filtern und sortieren, um sich auf bestimmte Faktoren oder Ergebnisse zu konzentrieren.  
  
## <a name="more-about-the-analyze-key-influencers-tool"></a>Weitere Informationen zum Tool "Wichtige Einflussfaktoren analysieren"  
 Wenn das Tool **wichtige Einflussfaktoren analysieren** die Daten analysiert, werden folgende Aktionen durchführt:  
  
-   Es wird eine Datenstruktur erstellt, in der wichtige Informationen zur Verteilung von Daten gespeichert werden.  
  
-   Erstellt ein Modell mithilfe des Microsoft Naïve Bayes-Algorithmus.  
  
-   Erstellt Vorhersagen, die jede Datenspalte mit dem angegebenen Ergebnis korrelieren.  
  
-   Verwendet das Vertrauensergebnis für jede Vorhersage, um die Faktoren zu identifizieren, die sich beim Erzeugen des Zielergebnisses am meisten ausgewirkt haben.  
  
-   Erstellt einen Bericht, der die wichtigen Einflussfaktoren beschreibt, die nach dem Vertrauensergebnis sortiert sind.  
  
### <a name="requirements"></a>Anforderungen  
 Wenn die Zielspalte kontinuierliche numerische Werte enthält, werden die numerischen Werte vom Tool automatisch in Gruppen unterteilt. Diese Gruppierungen stellen Cluster von Fällen mit ähnlichen Merkmalen dar. Numerische Werte können jedoch nicht in benutzerfreundliche Gruppen aufgeteilt werden. Der Bericht kann z. b. eine Gruppierung wie z.\<b. "12,85701" enthalten, während Berichts Benutzer in der Regel Gruppierungen mit ganzen Zahlen, wie z. b. 10-19, 20-29 usw., sehen.  
  
 Wenn Sie numerische Daten anders gruppieren möchten, müssen Sie die Daten vor der Analyse entsprechend segmentieren. Beispielsweise können Sie [das Tool neu](relabel-sql-server-data-mining-add-ins.md) bezeichnen im Data Mining-Client für Excel verwenden, um eine neue Gruppierungs Bezeichnung in einer separaten Spalte zu erstellen, und dann nur diese neue Spalte in der Analyse verwenden.  
  
### <a name="related-tools"></a>Verwandte Tools  
 Das **Data Mining** -Menüband bietet erweiterte Tools, einschließlich der Möglichkeit zum Anpassen von Data Mining Modellen.  
  
 Wenn Sie das Modell mit dem Tool **wichtige Einflussfaktoren analysieren** speichern, können Sie den Data Mining-Client verwenden, um das Modell zu durchsuchen und die Beziehungen ausführlicher zu untersuchen. Weitere Informationen finden Sie unter durch [Suchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md). Sie können mithilfe von Microsoft Office Visio Diagramme erstellen, die Beziehungen als Cluster oder Abhängigkeitsnetzwerke anzeigen. Weitere Informationen finden Sie unter [Problembehandlung für Visio Data Mining-Diagramme &#40;SQL Server Data Mining-Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md).  
  
> [!NOTE]  
>  Die mit den Tabellenanalysetools erstellten Modelle werden gelöscht, wenn Sie das Arbeitsblatt schließen oder die Verbindung mit dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server beenden. Daher können Sie die Modelle nur durchsuchen, solange die Verbindung bestehen bleibt. Sie können die Modelle nicht in Visio rendern, wenn Sie die Verbindung beenden oder das Arbeitsblatt schließen.  
  
 Weitere Informationen zum Algorithmus, der vom Tool **wichtige Einflussfaktoren analysieren** verwendet wird, finden Sie unter "Microsoft Naive Bayes-Algorithmus" in SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenanalyse Tools für Excel](table-analysis-tools-for-excel.md)   
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)  
  
  
