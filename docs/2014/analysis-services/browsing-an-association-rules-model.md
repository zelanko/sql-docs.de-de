---
title: Durchsuchen eine Zuordnung Regeln Modell | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining models, browsing
- mining model, association
- mining models, viewing
- association [data mining]
ms.assetid: faffe208-7a64-4ec6-825f-ecbaa79caff7
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4db0b96fe2520a7d9a7aee82ff8d0a3996b730b8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150010"
---
# <a name="browsing-an-association-rules-model"></a>Durchsuchen eines Association Rules-Modells
  Beim Öffnen einer Zuordnung Modell mit **Durchsuchen**, das Modell wird angezeigt, in einem interaktiven Viewer, ähnlich dem Viewer für Zuordnungsregeln in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  Im Viewer sehen Sie auf einen Blick, welche Elemente untereinander korreliert wurden. Außerdem können Sie Regeln anzeigen, die Sie für Vorhersagen oder Empfehlungen verwenden können.  
  
##  <a name="BKMK_ViewerTabs"></a> Untersuchen des Modells  
 Beim Öffnen eines Miningmodells, das erstellt wurde, mithilfe der [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules-Algorithmus, der **Durchsuchen** Fenster umfasst die folgenden Ansichten, mit der Sie einen anderen Aspekt des Modells untersuchen können so entworfen, dass:  
  
-   [Itemsets](#BKMK_Itemsets)  
  
-   [Regeln](#BKMK_Rules)  
  
-   [Abhängigkeitsnetzwerk](#BKMK_Dependency)  
  
 Notieren Sie die Option auf jeder Registerkarte **langen Namen anzeigen** . Wenn Sie diese Option auswählen, können Sie die Tabelle, aus der das Itemset stammt, anzeigen oder ausblenden. Darüber hinaus können Sie den Namen der Regel oder des Itemsets verkürzen oder verlängern. Diese Option ist insbesondere dann sinnvoll, wenn die Fall- und Attributdaten aus verschiedenen Datenquellen stammen.  
  
 Um mit einem Zuordnungsmodell zu experimentieren, können Sie die Beispieldaten auf der Registerkarte "Zuordnen" der Beispieldatenarbeitsmappe verwenden und ein Zuordnungsmodell mit allen Standardeinstellungen erstellen. Sie können auch ein warenkorbanalysemodell erstellen und öffnen Sie diese mit **Durchsuchen**.  
  
###  <a name="BKMK_Itemsets"></a> Itemsets  
 Die **Itemsets** Registerkarte ist ein guter Ausgangspunkt ein Association-Modell untersuchen. Auf dieser Registerkarte wird eine Liste der Elemente angezeigt, die das Modell als häufig zusammen auftretend identifiziert hat.  
  
 ![Liste der Elemente in einem Zuordnungsmodell](media/dm13-association-itemsets.gif "Liste von Elementen in einem Zuordnungsmodell")  
  
 Das häufigste Beispiel für Itemsets ist ein Warenkorbmodell, bei dem ein Itemset Paare oder Gruppen von Produkten darstellt, die viele Kunden gleichzeitig kaufen. Abhängig davon, wie Sie die Elemente gruppieren und anordnen, könnte das Itemset jedoch auch eine Reihe von Filmen enthalten, die die Kunden in einem bestimmten Zeitraum bestellen, oder Ereignisse, die in der Regel an einem bestimmten Ort stattfinden.  
  
 Ein *Itemset* darf als ein Element auf zwei, drei oder jedoch festgelegten maximalen itemsetgröße für das Modell. Der Viewer zeigt für jedes Itemset, das Itemset an *unterstützen*, *Wahrscheinlichkeit*, und *Größe*. Unterstützung und Wahrscheinlichkeit sind die Hauptstatistiken, um die von einem Zuordnungsmodell generierten Itemsets und Regeln zu sortieren. Diese Werte werden auch zum Berechnen und Beschreiben ihrer Wichtigkeit verwendet.  
  
 **Unterstützung**. Unterstützung gibt die Anzahl von Fällen oder Zeilen von Eingabedaten an, die über dieses Element verfügen. Z. B. wenn ein Itemset über zwei Elemente enthält, die im Warenkorb gefunden Einkaufswagen, die Zahl in die **Unterstützung** Spalte gibt an, wie oft, die Kombination von Elementen in den Quelldaten aufgetreten sind.  
  
 **Größe**. Wenn Sie die Größe eines Itemsets ändern, können Sie die Länge der Listen von Itemsets steuern. Wenn Sie nicht möchten, dass für einzelne Produkte in der Liste angezeigt wird, ändern Sie die Option **Mindestgröße des Itemsets**in 2 oder mehr.  Sie können die Liste durch Erhöhen der Mindestgröße von Itemsets einschränken und sich dadurch auf ganz bestimmte Muster konzentrieren. Dies kann hilfreich sein, wenn Sie mit einem sehr großen Datensatz arbeiten.  
  
 Sie können die Anzahl der durch Ändern der Registerkarte angezeigten Itemsets Filtern die **minimaler Unterstützungswert** und **maximale Zeilenanzahl** Werte. Wenn Sie erhöhen die **minimaler Unterstützungswert** Wert, die Liste weniger Itemsets angezeigt, aber die Itemsets werden häufigeren in den Eingabedaten. Ob entspricht dem als gleichzusetzen ist, die Sie untersuchen können, mit der **Regeln** Registerkarte.  
  
 Beachten Sie, dass das Ändern der Unterstützungswert oder andere Steuerelemente auf der **Itemsets** Registerkarte ändert nur die Elemente, die angezeigt werden und wirkt sich nicht auf das zugrunde liegende Modell. Wenn Sie weniger oder mehr Itemsets generieren oder deren Größe begrenzen möchten, verwenden Sie die Parameter `MINIMUM_SUPPORT` und `MAXIMUM_SUPPORT`, die in der **Algorithmusparameter** (Dialogfeld).  
  
##### <a name="explore-the-itemsets-list"></a>Untersuchen der Itemsets-Liste  
  
1.  Klicken Sie auf die **unterstützen** Spalte sortiert vom höchsten zum niedrigsten Unterstützung. Auf diese Weise können Sie feststellen, welche Elemente die Kunden am häufigsten kaufen.  
  
2.  Geben Sie auf ein bestimmtes Itemset von Interesse sind, aus der Tausenden von möglichen Kombinationen, konzentrieren Text in die **Filteritemset** Feld.  
  
     Eingabe `Gloves`. Wenn Sie den Filter anwenden, wird die Liste aktualisiert, und es werden nur Itemsets angezeigt, die Handschuhe enthalten. Auf diese Weise können Sie sich auf die Transaktionen konzentrieren, bei denen Kunden Handschuhe und einen anderen Artikel gekauft haben.  
  
     Über die Option **Filteritemset** wird auch eine Liste der zuvor verwendeten Filter angezeigt.  
  
3.  Ändern Sie den Wert der **Mindestgröße des Itemsets** herausfiltern, die Kunden, die nur Handschuhe und keine anderen Artikel gekauft haben.  
  
4.  Klicken Sie auf die Dropdownliste für die Option **anzeigen**, um zu steuern, wie die Attribute angezeigt werden:  
  
    -   **Attributnamen und Wert anzeigen**  
  
    -   **Nur Attributwert anzeigen**  
  
    -   **Nur Attributnamen anzeigen**  
  
     Beachten Sie die Änderung des Namens. Bei einem Warenkorbmodell, das basierend auf geschachtelten Tabellen von Produkten erstellt wird, die von mehreren Kunden gekauft wurden, ist der Attributname in der Regel der Produktname. Die Anzeige des Produkts in der Liste ist als `Existing` gekennzeichnet, d. h., der Kunde hat den Artikel gekauft.  
  
     Das Gegenteil von `Existing` lautet `Missing`. Dieses Attribut kann für Untersuchungen mit Data Mining nützlich sein. Nehmen wir beispielsweise an das Itemset A + B ist so beliebt, dass Kunden, die Produkt A gekauft finden, aber nicht Artikel b möchten Sie können zu diesem Zweck verwenden eine Vorhersageabfrage und Abrufen von Transaktionen mit einem, jedoch nicht durch den anderen und weitergehend Analysieren auf diesen. Informationen über das Erstellen von Vorhersageabfragen für zuordnungsmodelle finden Sie unter [Zuordnungsmodellabfragen](data-mining/association-model-query-examples.md) in SQL Server-Onlinedokumentation  
  
5.  Um die Liste der Itemsets, um anzuzeigen, verwenden die neuen Filterkriterien zu erzwingen, können Sie aktivieren oder Deaktivieren der **langen Namen anzeigen** Kontrollkästchen.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Rules"></a> Regeln  
 Die **Regeln** Registerkarte werden Informationen über die Itemsets und ihr relativer Wert kombiniert.  
  
 ![Liste der von einem Zuordnungsmodell erstellten Regeln](media/dm13-association-rules.gif "Liste der von einem Zuordnungsmodell erstellten Regeln")  
  
 *Wahrscheinlichkeit* stellt den Anteil der Fälle im Dataset, die die gewünschte Kombination von Elementen enthalten. Wahrscheinlichkeit ähnelt dem statistischen Konzept des *vertrauen*, und bietet Ihnen die Angabe der wie wahrscheinlich das Ergebnis einer Regel ausgeführt werden soll. Sie können ändern, den Wert der **minimale Wahrscheinlichkeit** in diesem Bereich zum Filtern der Regeln, die angezeigt werden.  
  
 Der Wert für **minimale Wahrscheinlichkeit** , dass Sie anfänglich finden Sie unter ist der Schwellenwert, der vom Algorithmus beim Erstellen des Modells verwendet. Wenn das Modell vollständig ist, können Sie diesen Wert nicht mehr verringern. Sie können ihn jedoch erhöhen, sodass nur die Elemente mit höherer Wahrscheinlichkeit angezeigt werden.  
  
 *Wichtigkeit* dient die Nützlichkeit einer Regel gemessen. Eine sehr häufig verwendete Regel könnte so allgemein sein, dass sie nur wenig Informationswert hat. Je größer die Wichtigkeit ist, umso bedeutender ist die Regel für die Vorhersage des Ergebnisses. In der [Warenkorbanalyse &#40;Tabellenanalysetools für Excel&#41; ](shopping-basket-analysis-table-analysistools-for-excel.md) Tool Wichtigkeit mit dem Preis von Elementen, die die Bündel zu ermitteln, die potenziell am wertvollsten Sales sind kombiniert werden kann.  
  
##### <a name="explore-the-rules-list"></a>Untersuchen der Liste "Regeln"  
  
1.  Klicken Sie auf die Spaltenüberschriften – **Wahrscheinlichkeit**, **Wichtigkeit**, und **Regel** , um festzustellen, wie die Daten geändert.  
  
2.  Verwenden der **Filterregel** Option aus, um Werte einzugeben und konzentrieren sich auf gewünschte Regeln.  
  
     Wenn Sie beispielsweise alle Regeln anzeigen möchten, die vorhersagen, welche Elemente die Kunden höchstwahrscheinlich zusammen mit Handschuhen kaufen, geben Sie im Textfeld "Gloves" ein, und aktualisieren Sie den Bereich.  
  
     Über die Option **Filteritemset** wird auch eine Liste der zuvor verwendeten Filter angezeigt.  
  
3.  So erzwingen die Liste der Regeln mithilfe der Filterkriterien Filterkriterien, können Sie aktivieren oder Deaktivieren der **langen Namen anzeigen** Kontrollkästchen.  
  
4.  Verwenden Sie die Option **anzeigen** um zu steuern, die Regelnamen angezeigt werden.  
  
5.  Legen Sie den Wert für die **maximale Zeilenanzahl** 100 aus, und klicken Sie dann auf **nach Excel kopieren**.  
  
     Die Änderung dieses Werts wirkt sich nicht auf die Datenmenge im Modell aus, sondern legt nur die Anzahl der Zeilen in der Anzeigeliste fest. Diese Option kann bei der Arbeit mit sehr großen Modellen nützlich sein.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Dependency"></a> Abhängigkeitsnetzwerk  
 Die **Abhängigkeitsnetzwerk** Registerkarte ist eine visuelle Karte der Korrelationen zwischen den Elementen. Jedes Oval im Diagramm (bezeichnet als eine *Knoten*) stellt ein Attribut / Wert-Paar dar, z. B. "Vest = Existing" oder "Age = 1-30".  Jede Verbindungslinie zwischen die ovalen (als bezeichnet ein *Edge*) stellt einen Typ von Korrelation dar.  
  
 ![Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell](media/dm13-association-dependencynetwork.gif "abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell")  
  
##### <a name="explore-the-dependency-network"></a>Untersuchen des Abhängigkeitsnetzwerks  
  
1.  Klicken Sie auf die **suchen** Schaltfläche und Verwenden der **Knoten suchen** (Dialogfeld), geben Sie ein Element von Interesse sind.  
  
     Geben Sie beispielsweise "Gloves" ein, und maximieren Sie dann das Diagramm im Fenster, sodass die Ergebnisse leicht ersichtlich sind.  
  
     Der Knoten, der das Element enthält, ist hervorgehoben, während die Pfeile, die auf den Knoten zeigen, eine Regel darstellen, die die Elemente verbindet.  
  
     Die Richtung der Pfeile gibt die Richtung der Regel an. Wenn zum Beispiel ein Kunde, der Handschuhe kauft, höchstwahrscheinlich auch eine Weste erwerben wird, startet der Pfeil am Knoten "Gloves" und endet am Knoten "Vest".  
  
     Um zusätzliche Statistiken über diese Regel erhalten, klicken Sie auf die **Regeln** Registerkarte und eine Regel mit der Beschreibung "Glove - Existing" -> "Steht Ihnen zu – vorhandenen.")  
  
2.  Klicken Sie auf den Schieberegler auf der linken Seite des Viewers, und ziehen Sie ihn.  
  
     Der Schieberegler fungiert als Filter für die Wahrscheinlichkeit der Regel. Wenn Sie den Schieberegler nach unten ziehen, werden nur die stärksten Regeln angezeigt.  
  
3.  Klicken Sie auf **nach Excel kopieren** eine Momentaufnahme des aktuellen Fensters nach Excel kopieren.  
  
     Sie können nicht mit dem Diagramm arbeiten, die Sie in Excel zu kopieren; Wenn Sie ein interaktives Netzwerkdiagramm benötigen, verwenden Sie die [Anzeigen von Data Mining-Modelle in Visio &#40;Data Mining-Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md).  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
## <a name="more-about-association-models"></a>Weitere Informationen zu Zuordnungsmodellen  
 Sie können die **Durchsuchen** Funktion zum Öffnen und Durchsuchen jedes Modell, das mit dem Microsoft Association Rules-Algorithmus erstellt wurde. Hierzu zählen auch Modelle erstellt, mit der [Warenkorbanalyse &#40;Tabellenanalysetools für Excel&#41; ](shopping-basket-analysis-table-analysistools-for-excel.md) tool, in der **Tabellenanalysetools** Menüband, oder im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Wenn Sie ein Zuordnungsregelmodell mit dem Tool Warenkorbanalyse erstellen, werden viele der erweiterten Optionen automatisch konfiguriert.  
  
 Wenn Sie erweiterte Parameter festzulegen oder alter mindestwahrscheinlichkeit und-Unterstützung verwenden möchten die [Assistenten zum Zuordnen von &#40;Data Mining-Client für Excel&#41; ](associate-wizard-data-mining-client-for-excel.md) -Assistenten, oder erstellen Sie Ihre eigene Modell mithilfe der [Modell hinzufügen Struktur &#40;Data Mining-Add-ins für Excel&#41; ](add-model-to-structure-data-mining-add-ins-for-excel.md) modellierungsoption.  
  
-   **Itemsets:** beim Erstellen des Modells können Sie auch steuern, auf die Anzahl der Itemsets, die durch Zuweisen eines Werts zum Parameter MINIMUM_PROBABILITY generiert werden. Dieser Parameter ist im Dialogfeld Algorithmusparameter verfügbar.  
  
-   **Regeln:** der [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules-Algorithmus werden Wahrscheinlichkeitswerte verwendet, um die Anzahl der Regeln zu beschränken, die generiert werden. Sie können die Anzahl der Regeln steuern, indem Sie die Parameter `MINIMUM_PROBABILITY` oder `MINIMUM _IMPORTANCE` festlegen.  
  
 Weitere Informationen zum Konfigurieren erweiterter Parameter finden Sie unter [Data Mining-Algorithmen &#40;SQL Server Data Mining-Add-ins&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  