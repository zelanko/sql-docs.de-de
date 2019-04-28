---
title: Erkennen von Kategorien (Tabellenanalysetools für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- clustering [data mining]
- mining model, decision tree
- category detection
ms.assetid: 3c7e9ebb-d0c9-498e-a9ba-cc13eaa43520
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 572c331cb5f9a88ee78cb26544772b126405c02c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62732256"
---
# <a name="detect-categories-table-analysis-tools-for-excel"></a>Kategorien erkennen (Tabellenanalysetool für Excel)
  ![Kategorien-Schaltfläche im Menüband erkennen](media/tat-detectcat.gif "Kategorien erkennen-Schaltfläche im Menüband")  
  
 Die **Kategorien erkennen** Tool sucht automatisch Zeilen in einer Tabelle, die ähnliche Merkmale aufweisen.  
  
 Bei Abschluss des Tools wird ein Bericht erstellt, in dem die gefundenen Kategorien zusammen mit ihren charakteristischen Merkmalen aufgeführt werden. Standardmäßig wird der Datentabelle, die die vorgeschlagene Kategorie enthält, für jede Zeile Ihrer Daten eine neue Spalte hinzugefügt. Sie können die Kategorien dann überprüfen und umbenennen.  
  
## <a name="using-the-detect-categories-tool"></a>Verwenden des Tools Kategorien erkennen  
  
1.  Öffnen Sie eine Excel-Tabelle.  
  
2.  Klicken Sie auf **Kategorien erkennen**.  
  
3.  Geben Sie die in der Analyse zu verwendenden Spalten an. Sie können die Auswahl von Spalten, die andere Werte aufweisen, wie Personennamen oder Datensatz-IDs, aufheben, wenn diese Spalten für die Analyse nicht nützlich sind.  
  
4.  Geben Sie optional die maximale Anzahl der zu erstellenden Kategorien an. Standardmäßig werden vom Tool so viele Kategorien automatisch erstellt, wie von ihm gefunden werden.  
  
5.  Klicken Sie auf **Ausführen**.  
  
6.  Es wird ein neues Arbeitsblatt mit dem Namen Kategoriebericht vom Tool erstellt, in dem die Kategorien und deren Merkmale aufgelistet sind.  
  
 Weitere Informationen zur Vorgehensweise beim Angeben von Optionen für das Tool finden Sie unter [erkennt das Dialogfeld Kategorien (Tabellenanalysetools für Excel)](detect-categories-table-analysis-tools-for-excel.md).  
  
## <a name="understanding-the-categories-report"></a>Grundlegendes zum Kategoriebericht  
 Die **Kategoriebericht** enthält die beiden Tabellen **Kategorieliste** und **Kategoriemerkmale**, und ein **Kategorieprofile** Diagramm.  
  
### <a name="category-list"></a>Kategorieliste  
 In der ersten Tabelle sind die Kategorien aufgeführt, die gefunden wurden. Die **Zeilenanzahl** Spalte gibt an, wie viele Datenzeilen jeder Kategorie zugewiesen wurden.  
  
 Im Modell werden temporäre Namen für jede Kategorie erstellt, die Kategorien können aber nach Bedarf umbenannt werden. Z. B. im folgenden Beispiel ist die erste Kategorie wurde umbenannt **Low Income**, denn dies war, dass das oberste Attribut des Clusters.  
  
 ![vom Tool Kategorien erkennen erstellten Bericht](media/dm13-tat-detectcat-report1.gif "vom Tool Kategorien erkennen erstellten Bericht")  
  
 Sobald Sie die neue Bezeichnung eingeben, wird die Änderung an alle anderen Diagramme sowie an die Kategorieliste weitergegeben, die im Quelldatenarbeitsblatt hinzugefügt wird.  
  
### <a name="category-characteristics"></a>Kategoriemerkmale  
 Der zweiten Tabelle **Kategoriemerkmale**, zeigt die Details über die Zusammensetzung jeder Kategorie. Klicken Sie auf die **Filter** Schaltfläche am oberen Rand der **Kategorie** Spalte, um den Fokus auf einer oder wenigen Kategorien angezeigt.  
  
 ![vom Tool Kategorien erkennen erstellten Bericht](media/dm13-tat-detectcat-report2.gif "vom Tool Kategorien erkennen erstellten Bericht")  
  
 Die Schattierung in der Spalte **Relative Wichtigkeit**, gibt an, wie wichtig eine Kombination aus Attribut und Wert als Unterscheidungsmerkmal ist. Je länger der Balken, desto wahrscheinlicher ist es, dass das Attribut für seine Kategorie stark repräsentativ ist.  
  
### <a name="categories-profile-chart"></a>Kategorieprofildiagramm  
 Das endgültige Diagramm in die **Kategoriebericht** Arbeitsblatt **Kategorieprofile**, ist ein interaktives **PivotChart** , Sie verwenden können, neu anordnen und Ausblenden von Feldern, nach Werten zu filtern , und die Darstellung des Diagramms anpassen.  
  
 Excel 2013 bietet jetzt **Diagrammformate** und **Diagrammelemente** Steuerelemente in der Entwurfsoberfläche, die zur Verbesserung des diagrammentwurfs zu erleichtern.  
  
 ![vom Tool Kategorien erkennen erstellten Bericht](media/dm13-tat-detectcat-report3.gif "vom Tool Kategorien erkennen erstellten Bericht")  
  
## <a name="requirements"></a>Anforderungen  
 Die **Kategorien erkennen** Tool verfügt über keine Anforderungen hinsichtlich der Menge oder den Typ der Daten.  
  
> [!NOTE]  
>  Bei Verwendung der **Kategorien erkennen** -Tool, erstellt er eine neue Spalte namens Kategorie, in der ursprünglichen Datentabelle. Wenn Sie diese Spalte in der Datentabelle belassen, beeinflusst sie möglicherweise die Ergebnisse von anschließend durchgeführten Data Mining-Vorgängen. Erstellen Sie daher eine Kopie der Datentabelle ohne die Spalte Kategorie, um sicherzustellen, dass diese Spalte sich nicht auf andere Vorgänge auswirkt, bevor Sie andere Data Mining-Tools verwenden.  
  
## <a name="related-tools"></a>Verwandte Tools  
 Wenn die **Kategorien erkennen** Tool analysiert die Daten, die es erstellt ein Datamining-Struktur und die Datamining-Modell mithilfe der [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus.  
  
 Nach der Erstellung von Datamining-Modells mithilfe der **wichtige Einflussfaktoren analysieren** -Tool können Sie Data Mining-Client für Excel das Modell durchsuchen und Beziehungen ausführlicher untersuchen. Der Data Mining-Client für Excel stellt ein separates Add-In mit erweiterter Data Mining-Funktionalität dar. Weitere Informationen finden Sie unter [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).  
  
 Weitere Informationen zum Verwenden der datenmodellierungsfunktionen im Data Mining-Client für Excel finden Sie unter [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md).  
  
 Weitere Informationen zu den vom verwendeten Algorithmus die **Kategorien erkennen** finden Sie unter dem Thema "Microsoft Clustering-Algorithmus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  
