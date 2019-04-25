---
title: Tabellenanalysetools für Excel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- getting started
ms.assetid: 6d9d1481-18e4-4108-9efa-68152b0940c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 596bc66152f36c25169e4a089644042d25f8c13b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62757906"
---
# <a name="table-analysis-tools-for-excel"></a>Tabellenanalysetools für Excel
  Die Datamining-Tools in der **analysieren** Symbolleiste sind die einfachste Möglichkeit, erste Schritte mit Datamining. Jedes Tool analysiert automatisch die Verteilung und den Typ der Daten und legt die Parameter fest, um die Gültigkeit der Ergebnisse sicherzustellen. Sie müssen keine Algorithmen auswählen oder komplexe Parameter konfigurieren.  
  
 ![DM](media/dm-tabletoolsanalyze.gif "DM")  
  
 Die **analysieren** -Menüband umfasst die folgenden Tools:  
  
 [Wichtige Einflussfaktoren analysieren &#40;Tabellenanalysetools für Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 Sie wählen eine Spalte oder einen Ausgabewert von Interesse aus. Anschließend analysiert der Algorithmus alle Eingabedaten, um die Faktoren zu identifizieren, die den größten Einfluss auf das Ziel haben. Optional können Sie einen Bericht erstellen, in dem zwei beliebige Werte miteinander verglichen werden, sodass Sie feststellen können, wie sich die Einflussfaktoren ändern.  
  
 Die **wichtige Einflussfaktoren analysieren** Tool wird der Microsoft Naïve Bayes-Algorithmus verwendet.  
  
 [Kategorien erkennen &#40;Tabellenanalysetools für Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
 Mit diesem Tool können Sie ein beliebiges Dataset hinzufügen und das Clustering anwenden, um Gruppierungen von Daten zu bestimmen. Es ist nützlich zum Ermitteln von ähnlichkeiten sowie zum Erstellen von Gruppen, weiter zu analysieren.  
  
 Die **Kategorien erkennen** Tool verwendet den Microsoft Clustering-Algorithmus.  
  
 [Aus Beispiel füllen &#40;Tabellenanalysetools für Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)  
 Dieses Tool unterstützt Sie beim Eingeben fehlender Werte. Sie geben einige Beispiele dafür an, worum es sich bei den fehlenden Werten handeln soll, und das Tool erstellt anhand sämtlicher Daten in der Tabelle Muster. Anschließend werden auf der Grundlage der Muster in den Daten neue Werte empfohlen.  
  
 Die **aus Beispiel füllen** Tool verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Prognostizieren &#40;Tabellenanalysetools für Excel&#41;](forecast-table-analysis-tools-for-excel.md)  
 Das Tool erfasst Daten, die sich mit der Zeit ändern, und sagt zukünftige Werte vorher.  
  
 Die **prognostizieren** Tool wird der Microsoft Time Series-Algorithmus verwendet.  
  
 [Ausnahmen hervorheben &#40;Tabellenanalysetools für Excel&#41;](highlight-exceptions-table-analysis-tools-for-excel.md)  
 Dieses Tool analysiert Muster in einer Datentabelle und ermittelt Zeilen und Werte, die dem Muster nicht entsprechen. Sie können diese anschließend überprüfen und korrigieren und dann das Modell erneut ausführen oder Werte für spätere Maßnahmen mit Flags versehen.  
  
 Die **Ausnahmen hervorheben** Tool verwendet den Microsoft Clustering-Algorithmus.  
  
 [Zielsucheszenario &#40;Tabellenanalysetools für Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)  
 In der **Zielsuche** -Tool, Sie geben Sie einen Zielwert und das Tool identifiziert die zugrunde liegenden Faktoren, die geändert werden müssen, damit dieses Ziel erreicht. Wenn Ihnen beispielsweise bekannt ist, dass die Kundenzufriedenheit in Bezug auf Anrufe um 20 % gesteigert werden muss, können Sie das Modell anweisen, die Faktoren vorherzusagen, die zum Erreichen dieses Ziels geändert werden müssen.  
  
 Die **Zielsuche** Tool verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Was-Wenn-Szenario &#40;Tabellenanalysetools für Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)  
 Die **Datenquellenwerte Analysis** tool ergänzt die **Zielsuche** Tool. Bei diesem Tool geben Sie den Wert ein, der geändert werden soll. Das Modell trifft eine Vorhersage, ob die betreffende Änderung zum Erreichen des gewünschten Ergebnisses ausreichend ist. Sie können beispielsweise das Modell anweisen abzuleiten, ob durch den Einsatz eines zusätzlichen Callcenter-Mitarbeiters die Kundenzufriedenheit um einen Punkt steigt.  
  
 Die **What-If** Tool verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Vorhersagerechner &#40;Tabellenanalysetools für Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 Mit diesem Tool wird ein Modell erstellt, das die Faktoren analysiert, die zum Zielergebnis führen, und anschließend wird ein Ergebnis für alle neuen Eingaben vorhergesagt, basierend auf den von den Daten abgeleiteten Bewertungsregeln. Dieses Tool generiert außerdem ein interaktives Arbeitsblatt für die Entscheidungsfindung, mit dem Sie einfach neue Eingaben bewerten können. Sie können das Bewertungsarbeitsblatt auch ausdrucken und offline nutzen.  
  
 Die **Vorhersagerechner** Tool verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Warenkorbanalyse &#40;Tabelle AnalysisTools für Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)  
 Dieses Tool identifiziert Muster, die bei Cross-Selling oder Up-Selling von Nutzen sein können. Es identifiziert Gruppen von Produkten, die häufig zusammen gekauft werden, und generiert auch Berichte basierend auf dem Preis und den Kosten zugehöriger Produktpakete, um bei der Entscheidungsfindung zu unterstützen.  
  
 Das Tool ist nicht auf die Warenkorbanalyse beschränkt; Sie können es für jedes Problem nutzen, das sich für die Zuordnungsanalyse eignet. Sie können beispielsweise nach häufig zusammen auftretenden Ereignissen, Faktoren für eine Diagnose oder sonstigen potenziellen Ursachen und Ergebnissen suchen.  
  
 Die **Warenkorbanalyse** Tool verwendet den Microsoft Association-Algorithmus.  
  
## <a name="requirements-for-the-table-analysis-tools-for-excel"></a>Anforderungen für die Tabellenanalysetools für Excel  
 Wenn Sie die Tabellenanalysetools für Excel verwenden möchten, müssen Sie zuerst eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] herstellen. Über diese Verbindung können Sie auf die Data Mining-Algorithmen von Microsoft zugreifen, die zum Analysieren Ihrer Daten verwendet werden. Wenn Sie keinen Zugriff auf eine Instanz haben, empfiehlt es sich, den Administrator zu bitten, eine Instanz zu installieren, die Sie zum Experimentieren mit Data Mining verwenden können. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Um Daten mithilfe des Tabellenanalysetools zu bearbeiten, müssen Sie den Datenbereich, den Sie verwenden möchten, in Excel-Tabellen konvertieren.  
  
 Wenn Sie nicht sehen können die **analysieren** des Menübands, klicken Sie zunächst in eine Datentabelle auf. Das Menü wird erst bei Auswahl einer Datentabelle aktiviert.  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Client für Excel &#40;SQL Server Data Mining-Add-ins&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)   
 [Problembehandlung für Data Mining-Diagramme in Visio &#40;SQL Server Data Mining-Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)   
 [Inhalt der Data Mining-Add-Ins für Office](what-s-included-in-the-data-mining-add-ins-for-office.md)  
  
  
