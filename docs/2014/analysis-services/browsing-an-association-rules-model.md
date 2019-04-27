---
title: Durchsuchen eine Zuordnung Modell Regeln | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining model, association
- mining models, viewing
- association [data mining]
ms.assetid: faffe208-7a64-4ec6-825f-ecbaa79caff7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1259cc627ef53d8f5a201e42772a9dba390824cc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62664401"
---
# <a name="browsing-an-association-rules-model"></a>Durchsuchen eines Association Rules-Modells
  Beim Öffnen einer Zuordnung Modell mit **Durchsuchen**, das Modell wird angezeigt, in einem interaktiven Viewer, ähnelt dem Viewer für Zuordnungsregeln in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  Im Viewer sehen Sie auf einen Blick, welche Elemente untereinander korreliert wurden. Außerdem können Sie Regeln anzeigen, die Sie für Vorhersagen oder Empfehlungen verwenden können.  
  
##  <a name="BKMK_ViewerTabs"></a> Durchsuchen des Modells  
 Beim Öffnen eines Mining-Modells, das erstellt wurde, mithilfe der [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules-Algorithmus die **Durchsuchen** Fenster enthält die folgenden Ansichten, die jeweils einen anderen Aspekt des Modells untersuchen zu können:  
  
-   [Itemsets](#BKMK_Itemsets)  
  
-   [Regeln](#BKMK_Rules)  
  
-   [Abhängigkeitsnetzwerk](#BKMK_Dependency)  
  
 Notieren Sie sich die Option auf jeder Registerkarte, **langen Namen anzeigen** . Wenn Sie diese Option auswählen, können Sie die Tabelle, aus der das Itemset stammt, anzeigen oder ausblenden. Darüber hinaus können Sie den Namen der Regel oder des Itemsets verkürzen oder verlängern. Diese Option ist insbesondere dann sinnvoll, wenn die Fall- und Attributdaten aus verschiedenen Datenquellen stammen.  
  
 Um mit einem Zuordnungsmodell zu experimentieren, können Sie die Beispieldaten auf der Registerkarte "Zuordnen" der Beispieldatenarbeitsmappe verwenden und ein Zuordnungsmodell mit allen Standardeinstellungen erstellen. Sie können auch ein warenkorbanalysemodell erstellen und öffnen Sie diese mit **Durchsuchen**.  
  
###  <a name="BKMK_Itemsets"></a> Itemsets  
 Die **Itemsets** Registerkarte ist ein guter Ausgangspunkt zu untersuchen, ein Association-Modell. Auf dieser Registerkarte wird eine Liste der Elemente angezeigt, die das Modell als häufig zusammen auftretend identifiziert hat.  
  
 ![Liste der Elemente in einem Zuordnungsmodell](media/dm13-association-itemsets.gif "Liste von Elementen in einem Zuordnungsmodell")  
  
 Das häufigste Beispiel für Itemsets ist ein Warenkorbmodell, bei dem ein Itemset Paare oder Gruppen von Produkten darstellt, die viele Kunden gleichzeitig kaufen. Abhängig davon, wie Sie die Elemente gruppieren und anordnen, könnte das Itemset jedoch auch eine Reihe von Filmen enthalten, die die Kunden in einem bestimmten Zeitraum bestellen, oder Ereignisse, die in der Regel an einem bestimmten Ort stattfinden.  
  
 Ein *Itemset* darf nur ein Element, das zwei, drei, oder aber festgelegten maximalen itemsetgröße für das Modell. Für jedes Itemset, zeigt der Viewer die Itemsets *unterstützen*, *Wahrscheinlichkeit*, und *Größe*. Unterstützung und Wahrscheinlichkeit sind die Hauptstatistiken, um die von einem Zuordnungsmodell generierten Itemsets und Regeln zu sortieren. Diese Werte werden auch zum Berechnen und Beschreiben ihrer Wichtigkeit verwendet.  
  
 **Unterstützung**. Unterstützung gibt die Anzahl von Fällen oder Zeilen von Eingabedaten an, die über dieses Element verfügen. Z. B. wenn ein Itemset über zwei Elemente enthält, die in einem Einkaufswagen befinden Einkaufswagen, die Zahl in die **Unterstützung** Spalte gibt an, wie viele Male, die Kombination von Elementen in den Quelldaten aufgetreten sind.  
  
 **Größe**. Wenn Sie die Größe eines Itemsets ändern, können Sie die Länge der Listen von Itemsets steuern. Wenn Sie nicht möchten, dass für einzelne Produkte in der Liste angezeigt wird, ändern Sie die Option **Mindestgröße des Itemsets**in 2 oder mehr.  Sie können die Liste durch Erhöhen der Mindestgröße von Itemsets einschränken und sich dadurch auf ganz bestimmte Muster konzentrieren. Dies kann hilfreich sein, wenn Sie mit einem sehr großen Datensatz arbeiten.  
  
 Sie können filtern, die Anzahl der Itemsets, die auf der Registerkarte, indem Sie ändern angezeigt werden die **minimaler Unterstützungswert** und **maximale Zeilenanzahl** Werte. Wenn Sie erhöhen die **minimaler Unterstützungswert** Wert, die Liste weniger Itemsets angezeigt, aber die Itemsets werden den häufigeren Problemen gehören, in den Eingabedaten. Ob entspricht dem genauso wichtig ist eine weitere Frage, die Sie untersuchen können, mit der **Regeln** Registerkarte.  
  
 Beachten Sie, dass Änderungen der Unterstützungswert oder andere Steuerelemente auf der **Itemsets** Registerkarte ändert nur die Elemente, die angezeigt werden, und wirkt sich nicht auf das zugrunde liegende Modell. Wenn Sie weniger oder mehr Itemsets generieren oder deren Größe begrenzen möchten, verwenden Sie die Parameter `MINIMUM_SUPPORT` und `MAXIMUM_SUPPORT`, verfügbar in der **Algorithmusparameter** Dialogfeld.  
  
##### <a name="explore-the-itemsets-list"></a>Untersuchen der Itemsets-Liste  
  
1.  Klicken Sie auf die **unterstützen** Spalte sortiert vom höchsten zum niedrigsten Unterstützung. Auf diese Weise können Sie feststellen, welche Elemente die Kunden am häufigsten kaufen.  
  
2.  Für die sich auf ein bestimmtes Itemset von Interesse sind, aus den Tausenden von möglichen Kombinationen, geben Sie Text in die **Filteritemset** Feld.  
  
     Eingabe `Gloves`. Wenn Sie den Filter anwenden, wird die Liste aktualisiert, und es werden nur Itemsets angezeigt, die Handschuhe enthalten. Auf diese Weise können Sie sich auf die Transaktionen konzentrieren, bei denen Kunden Handschuhe und einen anderen Artikel gekauft haben.  
  
     Über die Option **Filteritemset** wird auch eine Liste der zuvor verwendeten Filter angezeigt.  
  
3.  Ändern Sie den Wert der **Mindestgröße des Itemsets** um Kunden zu filtern, die nur Handschuhe und keine anderen Artikel gekauft haben.  
  
4.  Klicken Sie auf die Dropdownliste für die Option **anzeigen**steuern, wie die Attribute angezeigt werden:  
  
    -   **Attributnamen und Wert anzeigen**  
  
    -   **Nur Attributwert anzeigen**  
  
    -   **Nur Attributnamen anzeigen**  
  
     Beachten Sie die Änderung des Namens. Bei einem Warenkorbmodell, das basierend auf geschachtelten Tabellen von Produkten erstellt wird, die von mehreren Kunden gekauft wurden, ist der Attributname in der Regel der Produktname. Die Anzeige des Produkts in der Liste ist als `Existing` gekennzeichnet, d. h., der Kunde hat den Artikel gekauft.  
  
     Das Gegenteil von `Existing` lautet `Missing`. Dieses Attribut kann für Untersuchungen mit Data Mining nützlich sein. Nehmen wir beispielsweise an das Itemset A + B ist so beliebt, dass Sie verwenden möchten, finden Kunden, die Produkt A gekauft, aber nicht Artikel B. Sie können zu diesem Zweck verwenden eine Abfrage und Abrufen von Transaktionen mit einer, aber nicht in der anderen, und diese weitergehend Analysieren auf diesen. Weitere Informationen über das Erstellen von Vorhersageabfragen für zuordnungsmodelle finden Sie unter [Zuordnungsmodellabfragen](data-mining/association-model-query-examples.md) in SQL Server-Onlinedokumentation  
  
5.  Um die Liste der Itemsets, um die erneute Anzeige mit den neuen Filterkriterien zu erzwingen, können Sie aktivieren oder Deaktivieren der **langen Namen anzeigen** Kontrollkästchen.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Rules"></a> Regeln  
 Die **Regeln** Registerkarte werden Informationen über die Itemsets und ihr relativer Wert kombiniert.  
  
 ![Liste der von einem Zuordnungsmodell erstellten Regeln](media/dm13-association-rules.gif "Liste der von einem Zuordnungsmodell erstellten Regeln")  
  
 *Wahrscheinlichkeit* stellt den Anteil der Fälle im Dataset, die die gewünschte Kombination von Elementen enthalten. Wahrscheinlichkeit ähnelt dem statistischen Konzept des *vertrauen*, und bietet Ihnen ein Überblick über die wie wahrscheinlich das Ergebnis einer Regel ausgeführt werden soll. Sie können den Wert der ändern **minimale Wahrscheinlichkeit** in diesem Bereich zum Filtern der Regeln, die angezeigt werden.  
  
 Der Wert für **minimale Wahrscheinlichkeit** am Anfang unter ist der Schwellenwert, der vom Algorithmus beim Erstellen des Modells verwendet. Nachdem das Modell vollständig ist, kann können Sie nicht diesen Wert verringern, aber erhöht werden, um nur die Elemente mit höherer Wahrscheinlichkeit angezeigt.  
  
 *Wichtigkeit* wurde entwickelt, um die Nützlichkeit einer Regel zu messen. Eine sehr häufig verwendete Regel könnte so allgemein sein, dass sie nur wenig Informationswert hat. Je größer die Wichtigkeit ist, umso bedeutender ist die Regel für die Vorhersage des Ergebnisses. In der [Warenkorbanalyse &#40;Tabellenanalysetools für Excel&#41; ](shopping-basket-analysis-table-analysistools-for-excel.md) Tool Wichtigkeit kann kombiniert werden, mit dem Preis von Elementen, die die Bündel zu ermitteln, die im Hinblick auf Verkäufe möglicherweise besonders hilfreich sind.  
  
##### <a name="explore-the-rules-list"></a>Untersuchen der Liste "Regeln"  
  
1.  Klicken Sie auf die Spalte Überschriften - **Wahrscheinlichkeit**, **Wichtigkeit**, und **Regel** : um festzustellen, wie die Daten geändert.  
  
2.  Verwenden der **Filterregel** Option Geben Sie Werte aus, und konzentrieren Sie sich auf gewünschte Regeln.  
  
     Beispielsweise wenn Sie alle Regeln anzuzeigen, die Vorhersagen, welche Kunden wahrscheinlich zusammen mit Handschuhen kaufen möchten, geben Sie im Textfeld "Gloves", und aktualisieren Sie den Bereich.  
  
     Über die Option **Filteritemset** wird auch eine Liste der zuvor verwendeten Filter angezeigt.  
  
3.  Erzwingen Sie die Liste der Regeln mithilfe der Filterkriterien Filterkriterien, können Sie aktivieren oder Deaktivieren der **langen Namen anzeigen** Kontrollkästchen.  
  
4.  Verwenden Sie die Option **anzeigen** steuern, wie die Regelnamen angezeigt werden.  
  
5.  Legen Sie den Wert für die **maximale Zeilenanzahl** auf 100 aus, und klicken Sie dann auf **nach Excel kopieren**.  
  
     Beachten Sie, dass durch Ändern dieses Werts keine Auswirkungen auf die Menge der Daten im Modell nicht. Es steuert lediglich die Anzahl der Zeilen in der Anzeigeliste. Diese Option kann bei der Arbeit mit sehr großen Modellen nützlich sein.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Dependency"></a> Abhängigkeitsnetzwerk  
 Die **Abhängigkeitsnetzwerk** Registerkarte ist eine visuelle Karte der Korrelationen zwischen den Elementen. Jedes Oval im Diagramm (bezeichnet als eine *Knoten*) stellt ein Attribut / Wert-Paar dar, z. B. "Vest = Existing" oder "Age = 1-30".  Jede Zeile zwischen den ovalen (als bezeichnet ein *Edge*) stellt einen Typ der Korrelation.  
  
 ![Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell](media/dm13-association-dependencynetwork.gif "abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell")  
  
##### <a name="explore-the-dependency-network"></a>Untersuchen des Abhängigkeitsnetzwerks  
  
1.  Klicken Sie auf die **finden** und legen Sie mit der **Knoten suchen** Dialogfeld Geben Sie ein Element von Interesse sind.  
  
     Geben Sie z. B. "Gloves" ein, und Maximieren Sie das Diagramm im Fenster, damit Sie die Ergebnisse leicht erkennen können.  
  
     Der Knoten, der das Element enthält, ist hervorgehoben, während die Pfeile, die auf den Knoten zeigen, eine Regel darstellen, die die Elemente verbindet.  
  
     Die Richtung der Pfeile gibt die Richtung der Regel an. Wenn eine Person, die Handschuhe kauft auch eine Weste erwerben wahrscheinlich ist, wird der Pfeil z. B. aus dem Knoten "Glove" starten und beenden auf dem Knoten "Vest".  
  
     Um zusätzliche Statistiken über diese Regel zu erhalten, klicken Sie auf die **Regeln** Registerkarte und suchen Sie nach einer Regel mit der Beschreibung "Glove - vorhandenen" -> "Steht Ihnen zu - vorhandene.")  
  
2.  Klicken Sie auf den Schieberegler auf der linken Seite des Viewers, und ziehen Sie ihn.  
  
     Der Schieberegler fungiert als Filter für die Wahrscheinlichkeit der Regel. Wenn Sie den Schieberegler nach unten ziehen, werden nur die stärksten Regeln angezeigt.  
  
3.  Klicken Sie auf **nach Excel kopieren** eine Momentaufnahme des aktuellen Fensters nach Excel kopieren.  
  
     Sie können nicht mit dem Diagramm zu arbeiten, die Sie in Excel kopieren; Wenn Sie ein interaktives Netzwerkdiagramm benötigen, verwenden Sie die [Anzeigen von Data Mining-Modellen in Visio &#40;Data Mining-Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md).  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
## <a name="more-about-association-models"></a>Weitere Informationen zu Zuordnungsmodellen  
 Sie können die **Durchsuchen** Feature zum Öffnen und Durchsuchen ein Modell, das mit dem Microsoft Association Rules-Algorithmus erstellt wurde. Hierzu zählen auch Modelle erstellt, mit der [Warenkorbanalyse &#40;Tabellenanalysetools für Excel&#41; ](shopping-basket-analysis-table-analysistools-for-excel.md) tool in der **Tabellenanalysetools** Menüband oder im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Wenn Sie ein Zuordnungsregelmodell mit dem Tool Warenkorbanalyse erstellen, werden viele der erweiterten Optionen automatisch konfiguriert.  
  
 Wenn Sie erweiterte Parameter festzulegen oder alter mindestwahrscheinlichkeit und-Unterstützung, verwenden möchten die [Assistenten zum Zuordnen von &#40;Data Mining-Client für Excel&#41; ](associate-wizard-data-mining-client-for-excel.md) -Assistenten, oder erstellen Sie Ihr eigenes Modell mit den [Modell hinzufügen Struktur &#40;Data Mining-Add-ins für Excel&#41; ](add-model-to-structure-data-mining-add-ins-for-excel.md) modellierungsoption.  
  
-   **Itemsets:** Wenn Sie das Modell erstellen, können Sie auch die Anzahl der Itemsets steuern, die durch das Zuweisen eines Werts zum Parameter MINIMUM_PROBABILITY generiert werden. Dieser Parameter ist im Dialogfeld Algorithmusparameter verfügbar.  
  
-   **Regeln:** Die [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules-Algorithmus werden Wahrscheinlichkeitswerte verwendet, um die Anzahl der Regeln zu beschränken, die generiert werden. Sie können die Anzahl der Regeln steuern, indem Sie die Parameter `MINIMUM_PROBABILITY` oder `MINIMUM _IMPORTANCE` festlegen.  
  
 Weitere Informationen zum Konfigurieren erweiterter Parameter finden Sie unter [Data Mining-Algorithmen &#40;SQL Server Data Mining-Add-ins&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
