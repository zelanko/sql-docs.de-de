---
title: Durchsuchen eines Zuordnungs Regel Modells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: 30ff9705949be3fb9bf99d985d0db1aa17d93ab1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66088469"
---
# <a name="browsing-an-association-rules-model"></a>Durchsuchen eines Association Rules-Modells
  Wenn Sie ein Zuordnungs Modell mithilfe von **Durchsuchen**öffnen, wird das Modell in einem interaktiven Viewer angezeigt, der dem Association Rules [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Viewer in ähnelt.  Im Viewer sehen Sie auf einen Blick, welche Elemente untereinander korreliert wurden. Außerdem können Sie Regeln anzeigen, die Sie für Vorhersagen oder Empfehlungen verwenden können.  
  
##  <a name="explore-the-model"></a><a name="BKMK_ViewerTabs"></a>Untersuchen des Modells  
 Wenn Sie ein Mining Modell öffnen, das mithilfe des [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules-Algorithmus erstellt wurde, enthält das Fenster **Durchsuchen** die folgenden Sichten, mit denen Sie einen anderen Aspekt des Modells untersuchen können:  
  
-   [Itemsets](#BKMK_Itemsets)  
  
-   [Regeln](#BKMK_Rules)  
  
-   [Abhängigkeitsnetzwerk](#BKMK_Dependency)  
  
 Notieren Sie sich die Option auf den einzelnen Registerkarten, **langen Namen anzeigen** . Wenn Sie diese Option auswählen, können Sie die Tabelle, aus der das Itemset stammt, anzeigen oder ausblenden. Darüber hinaus können Sie den Namen der Regel oder des Itemsets verkürzen oder verlängern. Diese Option ist insbesondere dann sinnvoll, wenn die Fall- und Attributdaten aus verschiedenen Datenquellen stammen.  
  
 Um mit einem Zuordnungsmodell zu experimentieren, können Sie die Beispieldaten auf der Registerkarte "Zuordnen" der Beispieldatenarbeitsmappe verwenden und ein Zuordnungsmodell mit allen Standardeinstellungen erstellen. Sie können auch ein Einkaufskorb Analysemodell erstellen und es mithilfe von **Durchsuchen**öffnen.  
  
###  <a name="itemsets"></a><a name="BKMK_Itemsets"></a>Itemsets  
 Die Registerkarte **Itemsets** ist ein guter Ausgangspunkt für das Untersuchen eines Zuordnungs Modells. Auf dieser Registerkarte wird eine Liste der Elemente angezeigt, die das Modell als häufig zusammen auftretend identifiziert hat.  
  
 ![Liste der Elemente in einem Zuordnungsmodell](media/dm13-association-itemsets.gif "Liste der Elemente in einem Zuordnungsmodell")  
  
 Das häufigste Beispiel für Itemsets ist ein Warenkorbmodell, bei dem ein Itemset Paare oder Gruppen von Produkten darstellt, die viele Kunden gleichzeitig kaufen. Abhängig davon, wie Sie die Elemente gruppieren und anordnen, könnte das Itemset jedoch auch eine Reihe von Filmen enthalten, die die Kunden in einem bestimmten Zeitraum bestellen, oder Ereignisse, die in der Regel an einem bestimmten Ort stattfinden.  
  
 Ein *Itemset* kann nur bis zu zwei Elemente enthalten, die als maximale Itemsetgröße für das Modell festgelegt sind. Für jedes Itemset zeigt der Viewer die *Unterstützung*, *Wahrscheinlichkeit*und *Größe*des Itemsets an. Unterstützung und Wahrscheinlichkeit sind die Hauptstatistiken, um die von einem Zuordnungsmodell generierten Itemsets und Regeln zu sortieren. Diese Werte werden auch zum Berechnen und Beschreiben ihrer Wichtigkeit verwendet.  
  
 **Unterstützung**von. Unterstützung gibt die Anzahl von Fällen oder Zeilen von Eingabedaten an, die über dieses Element verfügen. Wenn ein Itemset beispielsweise zwei Elemente enthält, die in einem Warenkorb gefunden werden, gibt die Zahl in der Spalte **Support** an, wie oft diese Kombination von Elementen in den Quelldaten aufgetreten ist.  
  
 **Größe**. Wenn Sie die Größe eines Itemsets ändern, können Sie die Länge der Listen von Itemsets steuern. Wenn Sie in der Liste keine einzelnen Produkte anzeigen möchten, ändern Sie die Option **minimale Itemsetgröße in mindestens**2.  Sie können die Liste durch Erhöhen der Mindestgröße von Itemsets einschränken und sich dadurch auf ganz bestimmte Muster konzentrieren. Dies kann hilfreich sein, wenn Sie mit einem sehr großen Datensatz arbeiten.  
  
 Sie können die Anzahl der Itemsets filtern, die auf der Registerkarte angezeigt werden, indem Sie die Werte für **minimale Unterstützung** und **Maximale Zeilen** Anzahl ändern. Wenn Sie den **minimalen Unterstützungs** Wert erhöhen, werden in der Liste weniger Itemsets angezeigt, aber die Itemsets sind die gängigeren Werte in den Eingabedaten. Ob Common das gleiche ist wie wichtig, ist eine andere Frage, die Sie auf der Registerkarte **Regeln** durchsuchen können.  
  
 Beachten Sie, dass beim Ändern des Unterstützungs Werts oder anderer Steuerelemente auf der Registerkarte **Itemsets** nur die angezeigten Elemente geändert werden und das zugrunde liegende Modell nicht beeinträchtigt wird. Wenn Sie weniger oder mehr Itemsets generieren oder die Größe begrenzen möchten, sollten Sie die Parameter `MINIMUM_SUPPORT` und `MAXIMUM_SUPPORT`verwenden, die im Dialogfeld **Algorithmusparameter** verfügbar sind.  
  
##### <a name="explore-the-itemsets-list"></a>Untersuchen der Itemsets-Liste  
  
1.  Klicken Sie auf die Spalte **Support** , um nach dem niedrigsten Support zu sortieren. Auf diese Weise können Sie feststellen, welche Elemente die Kunden am häufigsten kaufen.  
  
2.  Um sich auf ein bestimmtes Itemset zu konzentrieren, das von den vielen tausend Kombinationen möglich ist, geben Sie im Feld **Filteritemset** einen Text ein.  
  
     Hier haben wir `Gloves`typisiert. Wenn Sie den Filter anwenden, wird die Liste aktualisiert, und es werden nur Itemsets angezeigt, die Handschuhe enthalten. Auf diese Weise können Sie sich auf die Transaktionen konzentrieren, bei denen Kunden Handschuhe und einen anderen Artikel gekauft haben.  
  
     Über die Option **Filteritemset** wird auch eine Liste der zuvor verwendeten Filter angezeigt.  
  
3.  Ändern Sie den Wert für **minimale Itemsetgröße** , um die Kunden herauszufiltern, die nur Handschuhe und keine anderen Elemente gekauft haben.  
  
4.  Klicken Sie auf die Dropdown Liste für die Option **anzeigen**, um zu steuern, wie die Attribute angezeigt werden:  
  
    -   **Attributnamen und Wert anzeigen**  
  
    -   **Nur Attributwert anzeigen**  
  
    -   **Nur Attributnamen anzeigen**  
  
     Beachten Sie die Änderung des Namens. Bei einem Warenkorbmodell, das basierend auf geschachtelten Tabellen von Produkten erstellt wird, die von mehreren Kunden gekauft wurden, ist der Attributname in der Regel der Produktname. Die Anzeige des Produkts in der Liste ist als `Existing` gekennzeichnet, d. h., der Kunde hat den Artikel gekauft.  
  
     Das Gegenteil von `Existing` lautet `Missing`. Dieses Attribut kann für Untersuchungen mit Data Mining nützlich sein. Angenommen, das Itemset A + B ist so sehr beliebt, dass Sie Kunden suchen möchten, die Artikel A, aber nicht Element B gekauft haben. Hierzu können Sie eine Vorhersage Abfrage verwenden und die Transaktionen mit einem, aber nicht mit dem anderen abrufen und weitere Analysen durchführen. Weitere Informationen zum Erstellen von Vorhersage Abfragen für Zuordnungs Modelle finden Sie unter Beispiele für Zuordnungs [Modell Abfragen](data-mining/association-model-query-examples.md) in SQL Server-Onlinedokumentation  
  
5.  Wenn Sie erzwingen möchten, dass die Liste der Itemsets mithilfe der neuen Filterkriterien erneut angezeigt wird, können Sie das Kontrollkästchen **langen Namen anzeigen** aktivieren bzw. deaktivieren.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
###  <a name="rules"></a><a name="BKMK_Rules"></a>Werks  
 Auf der Registerkarte **Regeln** werden Informationen zu den Itemsets und deren relativer Wert kombiniert.  
  
 ![Liste der von einem Zuordnungsmodell erstellten Regeln](media/dm13-association-rules.gif "Liste der von einem Zuordnungsmodell erstellten Regeln")  
  
 *Wahrscheinlichkeit* stellt den Bruchteil der Fälle im DataSet dar, die die Ziel Kombination der Elemente enthalten. Die Wahrscheinlichkeit ähnelt dem statistischen *Vertrauens*Konzept und gibt Aufschluss darüber, wie wahrscheinlich das Ergebnis einer Regel auftreten kann. Sie können den Wert der **minimalen Wahrscheinlichkeit** in diesem Bereich ändern, um die angezeigten Regeln zu filtern.  
  
 Der Wert für die **Minimale Wahrscheinlichkeit** , der anfänglich angezeigt wird, ist der Schwellenwert, der vom Algorithmus beim Aufbau des Modells verwendet wurde. Nachdem das Modell fertig ist, können Sie diesen Wert nicht mehr verringern, aber Sie können ihn erhöhen, um nur die höheren Wahrscheinlichkeits Elemente anzuzeigen.  
  
 Die *Wichtigkeit* ist so konzipiert, dass die Nützlichkeit einer Regel gemessen wird. Eine sehr häufig verwendete Regel könnte so allgemein sein, dass sie nur wenig Informationswert hat. Je größer die Wichtigkeit ist, umso bedeutender ist die Regel für die Vorhersage des Ergebnisses. Im [waren Korb Analyse &#40;Tabelle analysistool für Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) Tool kann die Wichtigkeit mit dem Preis von Elementen kombiniert werden, um die Bündel zu ermitteln, die in Bezug auf den Vertrieb potenziell besonders wertvoll sind.  
  
##### <a name="explore-the-rules-list"></a>Untersuchen der Liste "Regeln"  
  
1.  Klicken Sie auf die Spaltenüberschriften- **Wahrscheinlichkeit**, **Wichtigkeit**und **Regel** , um zu sehen, wie sich die Daten ändern.  
  
2.  Verwenden Sie die Option **Filter Regel** , um Werte einzugeben, und konzentrieren Sie sich auf die Ziel Regeln.  
  
     Wenn Sie z. b. alle Regeln anzeigen möchten, die Vorhersagen, welche Kunden wahrscheinlich zusammen mit Handschuhen kaufen, geben Sie "Handschuhe" in das Textfeld ein, und aktualisieren Sie den Bereich.  
  
     Über die Option **Filteritemset** wird auch eine Liste der zuvor verwendeten Filter angezeigt.  
  
3.  Wenn Sie erzwingen möchten, dass die Liste der Regeln mithilfe der Filterkriterien erneut angezeigt wird, können Sie das Kontrollkästchen **langen Namen anzeigen** aktivieren bzw. deaktivieren.  
  
4.  Verwenden Sie die Option **anzeigen** , um die Art und Weise zu steuern, wie Regel Namen angezeigt werden.  
  
5.  Legen Sie den Wert für die Option **Maximale Zeilen** Anzahl auf 100 fest, und klicken Sie dann auf **in Excel kopieren**.  
  
     Beachten Sie, dass sich das Ändern dieses Werts nicht auf die Datenmenge im Modell auswirkt. Er steuert lediglich die Anzahl der Zeilen in der Anzeigeliste. Diese Option kann bei der Arbeit mit sehr großen Modellen nützlich sein.  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
###  <a name="dependency-network"></a><a name="BKMK_Dependency"></a>Abhängigkeits Netzwerk  
 Die Registerkarte **Abhängigkeits Netzwerk** ist eine visuelle Zuordnung der Korrelationen zwischen Elementen. Jedes Oval im Diagramm (als *Knoten*bezeichnet) stellt ein Attribut-Wert-Paar dar, z. b. "Vest = vorhandenes" oder "Age = 1-30".  Jede Zeile, die die ovale (als *Edge*bezeichnet) verbindet, stellt einen Korrelationstyp dar.  
  
 ![Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell](media/dm13-association-dependencynetwork.gif "Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell")  
  
##### <a name="explore-the-dependency-network"></a>Untersuchen des Abhängigkeitsnetzwerks  
  
1.  Klicken Sie auf die Schaltfläche **Suchen** , und verwenden Sie das Dialogfeld **Knoten suchen** , um ein interessantes Element einzugeben.  
  
     Geben Sie z. b. "Handschuhe" ein, und maximieren Sie das Diagramm im Fenster, damit Sie die Ergebnisse problemlos sehen können.  
  
     Der Knoten, der das Element enthält, ist hervorgehoben, während die Pfeile, die auf den Knoten zeigen, eine Regel darstellen, die die Elemente verbindet.  
  
     Die Richtung der Pfeile gibt die Richtung der Regel an. Wenn z. b. ein Benutzer, der Handschuhe kauft, wahrscheinlich auch eine Weste kaufen wird, startet der Pfeil vom "Hand Schuh Knoten" und endet dann mit dem Knoten "Vest".  
  
     Um zusätzliche Statistiken zu dieser Regel zu erhalten, klicken Sie auf die Registerkarte **Regeln** , und suchen Sie nach einer Regel mit der Beschreibung "Glove-vorhanden"-> "Vest-vorhandene".)  
  
2.  Klicken Sie auf den Schieberegler auf der linken Seite des Viewers, und ziehen Sie ihn.  
  
     Der Schieberegler fungiert als Filter für die Wahrscheinlichkeit der Regel. Wenn Sie den Schieberegler nach unten ziehen, werden nur die stärksten Regeln angezeigt.  
  
3.  Klicken Sie auf **nach Excel kopieren** , um eine Momentaufnahme des aktuellen Fensters nach Excel zu kopieren.  
  
     Sie können nicht mit dem Diagramm arbeiten, das Sie in Excel kopieren. Wenn Sie ein interaktives Netzwerkdiagramm benötigen, verwenden Sie das [Anzeigen von Data Mining-Modellen in Visio &#40;Data Mining-Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md).  
  
 [Zurück zum Anfang](#BKMK_ViewerTabs)  
  
## <a name="more-about-association-models"></a>Weitere Informationen zu Zuordnungs Modellen  
 Mithilfe der Funktion " **Durchsuchen** " können Sie alle Modelle öffnen und untersuchen, die mithilfe des Microsoft Association Rules-Algorithmus erstellt wurden. Dies schließt Modelle ein, die mithilfe der [waren Korb Analyse &#40;Tabelle analysistool für Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) Tool, im Menüband **Tabellenanalyse Tools** oder [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]in erstellt wurden.  
  
 Wenn Sie ein Zuordnungsregelmodell mit dem Tool Warenkorbanalyse erstellen, werden viele der erweiterten Optionen automatisch konfiguriert.  
  
 Wenn Sie erweiterte Parameter festlegen oder minimale Wahrscheinlichkeit und Unterstützung ändern möchten, verwenden Sie den Assistenten zum [Verknüpfen von Assistenten &#40;Data Mining-Client für Excel&#41;](associate-wizard-data-mining-client-for-excel.md) , oder erstellen Sie ein eigenes Modell mithilfe der Option [Modell zu Struktur hinzufügen &#40;Data Mining-Add-Ins für Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md) Modeling.  
  
-   **Itemsets:** Wenn Sie das Modell erstellen, können Sie auch die Anzahl der Itemsets steuern, die generiert werden, indem Sie dem MINIMUM_PROBABILITY-Parameter einen Wert zuweisen. Dieser Parameter ist im Dialogfeld Algorithmusparameter verfügbar.  
  
-   **Regeln:** Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules-Algorithmus verwendet Wahrscheinlichkeitswerte, um die Anzahl der generierten Regeln einzuschränken. Sie können die Anzahl der Regeln steuern, indem Sie die Parameter `MINIMUM_PROBABILITY` oder `MINIMUM _IMPORTANCE` festlegen.  
  
 Weitere Informationen zum Konfigurieren erweiterter Parameter finden [Sie unter Data Mining-Algorithmen &#40;SQL Server Data Mining-Add-ins&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
