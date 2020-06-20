---
title: Tabellenanalyse Tools für Excel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- getting started
ms.assetid: 6d9d1481-18e4-4108-9efa-68152b0940c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7c8610fd3ac9ee92d6e08084c48f14298cb3203f
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940191"
---
# <a name="table-analysis-tools-for-excel"></a>Tabellenanalysetools für Excel
  Die Data Mining Tools auf der Symbolleiste **analysieren** sind die einfachste Möglichkeit, um mit Data Mining zu beginnen. Jedes Tool analysiert automatisch die Verteilung und den Typ der Daten und legt die Parameter fest, um die Gültigkeit der Ergebnisse sicherzustellen. Sie müssen keine Algorithmen auswählen oder komplexe Parameter konfigurieren.  
  
 ![DM](media/dm-tabletoolsanalyze.gif "DM")  
  
 Das Menüband **analysieren** umfasst die folgenden Tools:  
  
 [Wichtige Einflussfaktoren &#40;Tabellenanalyse Tools für Excel analysieren&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 Sie wählen eine Spalte oder einen Ausgabewert von Interesse aus. Anschließend analysiert der Algorithmus alle Eingabedaten, um die Faktoren zu identifizieren, die den größten Einfluss auf das Ziel haben. Optional können Sie einen Bericht erstellen, in dem zwei beliebige Werte miteinander verglichen werden, sodass Sie feststellen können, wie sich die Einflussfaktoren ändern.  
  
 Das Tool **wichtige Einflussfaktoren analysieren** verwendet den Microsoft Naive Bayes-Algorithmus.  
  
 [Erkennen von Kategorien &#40;Tabellenanalyse Tools für Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
 Mit diesem Tool können Sie ein beliebiges Dataset hinzufügen und das Clustering anwenden, um Gruppierungen von Daten zu bestimmen. Es ist nützlich, um Ähnlichkeiten zu suchen und Gruppen zu erstellen, um Sie weiter zu analysieren.  
  
 Das Tool **Kategorien erkennen** verwendet den Microsoft Clustering-Algorithmus.  
  
 [Füllen Sie aus Beispiel &#40;Tabellenanalyse Tools für Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)  
 Dieses Tool unterstützt Sie beim Eingeben fehlender Werte. Sie geben einige Beispiele dafür an, worum es sich bei den fehlenden Werten handeln soll, und das Tool erstellt anhand sämtlicher Daten in der Tabelle Muster. Anschließend werden auf der Grundlage der Muster in den Daten neue Werte empfohlen.  
  
 Das Tool **aus Beispiel füllen** verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Vorhersage &#40;Tabellenanalyse Tools für Excel&#41;](forecast-table-analysis-tools-for-excel.md)  
 Das Tool erfasst Daten, die sich mit der Zeit ändern, und sagt zukünftige Werte vorher.  
  
 Das Tool für die **Vorhersage** verwendet den Microsoft Time Series-Algorithmus.  
  
 [Ausnahmen &#40;Tabellenanalyse Tools für Excel markieren&#41;](highlight-exceptions-table-analysis-tools-for-excel.md)  
 Dieses Tool analysiert Muster in einer Datentabelle und ermittelt Zeilen und Werte, die nicht dem Muster entsprechen. Sie können diese anschließend überprüfen und korrigieren und dann das Modell erneut ausführen oder Werte für spätere Maßnahmen mit Flags versehen.  
  
 Das Tool **Ausnahmen hervorheben** verwendet den Microsoft Clustering-Algorithmus.  
  
 [Zielsuchszenario &#40;Tabellenanalyse Tools für Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)  
 Im **zielsuchtool** geben Sie einen Zielwert an, und das Tool identifiziert die zugrunde liegenden Faktoren, die geändert werden müssen, um dieses Ziel zu erreichen. Wenn Ihnen beispielsweise bekannt ist, dass die Kundenzufriedenheit in Bezug auf Anrufe um 20 % gesteigert werden muss, können Sie das Modell anweisen, die Faktoren vorherzusagen, die zum Erreichen dieses Ziels geändert werden müssen.  
  
 Das Tool zur **Zielsuche** verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Was-wäre-wenn-Szenario &#40;Tabellenanalyse Tools für Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)  
 Das Tool **Was-wäre-wenn-Analyse** ergänzt das Tool zur **Zielsuche** . Bei diesem Tool geben Sie den Wert ein, der geändert werden soll. Das Modell trifft eine Vorhersage, ob die betreffende Änderung zum Erreichen des gewünschten Ergebnisses ausreichend ist. Sie können beispielsweise das Modell anweisen abzuleiten, ob durch den Einsatz eines zusätzlichen Callcenter-Mitarbeiters die Kundenzufriedenheit um einen Punkt steigt.  
  
 Das **Was-wäre-wenn-** Tool verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Vorhersagerechner &#40;Tabellenanalyse Tools für Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 Mit diesem Tool wird ein Modell erstellt, das die Faktoren analysiert, die zum Zielergebnis führen, und anschließend wird ein Ergebnis für alle neuen Eingaben vorhergesagt, basierend auf den von den Daten abgeleiteten Bewertungsregeln. Dieses Tool generiert außerdem ein interaktives Arbeitsblatt für die Entscheidungsfindung, mit dem Sie einfach neue Eingaben bewerten können. Sie können das Bewertungsarbeitsblatt auch ausdrucken und offline nutzen.  
  
 Das **Vorhersagerechner** Tool verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Waren Korb Analyse &#40;Tabellenanalyse für Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)  
 Dieses Tool identifiziert Muster, die bei Cross-Selling oder Up-Selling von Nutzen sein können. Es identifiziert Gruppen von Produkten, die häufig zusammen gekauft werden, und generiert auch Berichte basierend auf dem Preis und den Kosten zugehöriger Produktpakete, um bei der Entscheidungsfindung zu unterstützen.  
  
 Das Tool ist nicht auf die Warenkorbanalyse beschränkt; Sie können es für jedes Problem nutzen, das sich für die Zuordnungsanalyse eignet. Sie können beispielsweise nach häufig zusammen auftretenden Ereignissen, Faktoren für eine Diagnose oder sonstigen potenziellen Ursachen und Ergebnissen suchen.  
  
 Das **waren Korb Analyse** Tool verwendet den Microsoft Association-Algorithmus.  
  
## <a name="requirements-for-the-table-analysis-tools-for-excel"></a>Anforderungen für die Tabellenanalysetools für Excel  
 Wenn Sie die Tabellenanalysetools für Excel verwenden möchten, müssen Sie zuerst eine Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] herstellen. Über diese Verbindung können Sie auf die Data Mining-Algorithmen von Microsoft zugreifen, die zum Analysieren Ihrer Daten verwendet werden. Wenn Sie keinen Zugriff auf eine Instanz haben, empfiehlt es sich, den Administrator zu bitten, eine Instanz zu installieren, die Sie zum Experimentieren mit Data Mining verwenden können. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Um Daten mithilfe des Tabellenanalysetools zu bearbeiten, müssen Sie den Datenbereich, den Sie verwenden möchten, in Excel-Tabellen konvertieren.  
  
 Wenn das Menüband **analysieren** nicht angezeigt wird, klicken Sie zuerst in eine Datentabelle. Das Menü wird erst bei Auswahl einer Datentabelle aktiviert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Client für Excel &#40;SQL Server Data Mining-Add-ins&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)   
 [Problembehandlung bei Visio Data Mining-Diagrammen &#40;SQL Server Data Mining-Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)   
 [Inhalt der Data Mining-Add-Ins für Office](what-s-included-in-the-data-mining-add-ins-for-office.md)  
  
  
