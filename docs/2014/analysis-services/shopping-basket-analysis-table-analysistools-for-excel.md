---
title: Warenkorbanalyse (Tabellenanalysetools für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- shopping basket analysis
- mining model, association
- Table Analysis tools
- association [data mining]
- market basket analysis
ms.assetid: ba40cf43-f286-49ad-8316-70f5b11f1dae
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8d5545d6a6d0deca345207ec73a039e7abe841ca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62746503"
---
# <a name="shopping-basket-analysis-table-analysistools-for-excel"></a>Warenkorbanalyse (Tabellenanalysetools für Excel)
  ![Einkaufswagentool](media/tat-shopbskt.gif "Einkaufswagentool")  
  
 Die **Warenkorbanalyse** -Tool hilft Ihnen das Suchen `associations` in Ihren Daten. Eine Zuordnung weist u. U. darauf hin, welche Elemente häufig gleichzeitig gekauft werden. Beim Datamining diese Technik ist eine bekannte Methode genannt *Market Basket-Analysen*verwendet, um das Kaufverhalten von Kunden in sehr großen Datasets zu analysieren. Marktforscher können anhand dieser Informationen Kunden Empfehlungen zu ähnlichen Produkten geben und verbundene Produkte besser vermarkten, indem Sie sie auf Webseiten, in Katalogen oder im Ladenregal in unmittelbarer Nähe zueinander anbieten.  
  
 Um die Warenkorbanalyse zu verwenden, müssen die Elemente, die Sie analysieren möchten, durch eine Transaktions-ID zueinander in Beziehung stehen. Wenn Sie beispielsweise alle Bestellungen, die über eine Website eingehen, analysieren möchten, erhält jede Bestellung eine Bestell- oder Transaktions-ID, die einem oder mehreren gekauften Produkten zugeordnet ist.  
  
 Wenn der Assistent abgeschlossen ist, die Daten analysieren, erstellt es zwei neue Arbeitsblätter, **Warenkorb-Elementpakete** und **Warenkorbempfehlungen**.  
  
 Die **Warenkorb-Elementpakete** Arbeitsblatt enthält eine Liste der Elemente, die häufig in Transaktionen zusammen vorkommen. Diese allgemeinen Gruppierungen heißen *Itemsets*. Das Arbeitsblatt enthält auch Statistiken, wie z. B. *unterstützen* und *lift*, um Ihnen ein Verständnis der Bedeutung der Itemsets. Wenn Preisinformationen verfügbar sind, kann auf dem Arbeitsblatt auch eine Summe aller verbundenen Elemente erstellt werden, um eine Vorstellung vom Gesamtwert der Transaktionen zu bekommen.  
  
 Sie können im Bericht nach Spalten filtern und sortieren. Angenommen, Sie möchten nur die Itemsets mit 2 oder mehr Produkte anzeigen, oder bestellen die Itemsets nach **Durchschnittlicher Korbwert**.  
  
 Die **Warenkorbempfehlungen** Arbeitsblatt verwendet die aus der Analyse abgeleiteten Statistiken zum Erstellen von Regeln zur wie Elemente miteinander verbunden sind. Kann z. B., eine Regel, wenn Kunden Produkt A kaufen, sehr wahrscheinlich auch Produkt b kaufen werden Die Regeln können verwendet werden, um Empfehlungen zu erstellen. Jeder Regel liegen Statistiken zugrunde, mit denen Sie die Aussagekraft der Regel bewerten können, sodass Sie nur dann eine Empfehlung ausgeben, wenn die Regel einen bestimmten Wahrscheinlichkeitsschwellenwert überschreitet.  
  
## <a name="using-the-shopping-basket-analysis-tool"></a>Verwenden des Tools Warenkorbanalyse  
  
1.  Öffnen Sie eine Excel-Tabelle mit geeigneten Daten. Klicken Sie in der Beispielarbeitsmappe auf das Zuordnungs-Arbeitsblatt.  
  
2.  Klicken Sie auf **Warenkorbanalyse**.  
  
3.  In der **Warenkorbanalyse** Dialogfeld Wählen Sie die Spalte, die die Transaktions-ID enthält, und wählen Sie dann die Spalte, enthält die Elemente oder Produkte, die Sie analysieren möchten.  
  
4.  Optional können Sie auch eine Spalte hinzufügen, die Produktwerte enthält.  
  
5.  Klicken Sie auf**erweitert**zum Öffnen der **erweiterte Parametereinstellung** Dialogfeld. Erhöhen Sie den Wert für **minimaler Unterstützungswert** um die Anzahl der Produkte zu reduzieren, die als Itemsets gruppiert werden. Erhöhen Sie die **minimale regelwahrscheinlichkeit** um sehr allgemeine Itemsets herauszufiltern.  
  
### <a name="requirements"></a>Anforderungen  
 Verwenden der **Warenkorbanalyse** -Tool, Ihre Daten müssen in einer Excel-Tabelle gespeichert werden und darf die folgenden Spalten:  
  
-   Spalte mit einer eindeutigen ID für die Transaktion. Bei der ID kann es sich um eine Zahl oder um Text handeln, solange der Wert in jeder Zeile eindeutig ist.  
  
-   Spalte mit dem zu analysierenden Element oder Produkt.  
  
-   Eine optionale numerische Spalte, die den Preis oder den Wert jedes Elements darstellt. In dieser Spalte wird der Wert des Itemsets für jedes Produkt aggregiert, sodass Sie eine Vorstellung vom Gesamtwert einzelner Transaktionen erhalten.  
  
## <a name="how-items-are-associated"></a>Zuordnung von Elementen  
 Die einzelnen Elemente, die Sie analysieren, müssen anhand eines Bezeichners gruppiert werden, der für den Fall, die Transaktion oder die Gelegenheit steht. Sie würden daher diese Transaktions-ID-Spalte, nicht die Kunden-ID oder Produkt-ID als Bezeichner auswählen.  
  
 Wenn das Tool die Produkte in jeder Transaktion überprüft, erstellt es ein Itemset für jede gefundene Elementkombination. Wenn ein Kunde beispielsweise drei Elemente bei einem Besuch kauft, gibt es 7 mögliche Itemsets: Jedes Produkt alleine, jedes Produkt in Kombination mit einem anderen Produkt und die Kombination aller drei Produkte.  
  
> [!NOTE]  
>  Sie können die Itemsets herausfiltern, die nur ein Element enthalten. Diese müssen jedoch vom Tool analysiert werden, um aussagekräftige Statistiken für das Dataset zu erstellen.  
  
 Die Unterstützung für jedes Itemset wird als Anzahl von Kunden berechnet, die ein Itemset kaufen. Wenn in dem gerade genannten Beispiel ein Kunde 3 Elemente mit 7 möglichen Itemsets kauft, hat jedes der 7 Itemsets einen Unterstützungswert von 1. Mit steigender Anzahl von Kunden und steigender Anzahl möglicher Kombinationen dauert auch die Verarbeitung des Berichts wesentlich länger. Einige Itemsets weisen jedoch unter Umständen einen sehr niedrigen Unterstützungswert auf. Sie könnten daher die zum Erstellen des Berichts benötigte Zeit reduzieren, indem Sie die Anzahl der Elemente in jedem Itemset auf 3 oder weniger beschränken. Im Allgemeinen haben größere Itemsets eine wesentlich geringere Unterstützung. Daher ist dieser Kompromiss akzeptabel.  
  
## <a name="specifying-minimum-support-and-rule-probability"></a>Festlegen der minimalen Unterstützung und Regelwahrscheinlichkeit  
 Mit zunehmender Größe des Datasets nimmt auch die Anzahl möglicher Elementgruppierungen und -regeln zu, bis sie schließlich unüberschaubar wird. Sie können jedoch den Umfang an Ergebnissen, die vom Tool ausgegeben werden, steuern, um letztendlich nur die wichtigsten Itemsets und Regeln zu berücksichtigen. Sie legen diese Optionen der **Warenkorb Warenkorb erweiterte Parameter (Dialogfeld)**.  
  
### <a name="minimum-support"></a>Minimale Unterstützung  
 *Minimaler Unterstützungswert* bedeutet, dass die Anzahl der Transaktionen, die für das Itemset als signifikant angesehen zu werden ein bestimmtes Itemset enthalten muss. Sie sind möglicherweise nicht an einem Itemset interessiert, es sei denn es wurde in mindestens 10 unterschiedlichen Transaktionen gekauft. Es gibt zwei Möglichkeiten, den Schwellenwert für die Itemset-Bedeutung steuern, und beide verwenden die **minimaler Unterstützungswert** Parameter.  
  
 **Als absoluter Wert:** Geben Sie eine Zahl, die Anzahl der Transaktionen darstellt, die die Zielelemente enthalten. Wenn Sie beispielsweise 10 eingeben, wird jeder Satz an Elementen eingeschlossen, die in mindestens 10 Warenkörben enthalten sind.  
  
 **Als Prozentsatz:** Geben Sie eine Zahl, die einen Prozentsatz der ganzen Itemset-Auflistung darstellt. Wenn Sie z. B. 10 eingeben, werden alle Itemsets berücksichtigt, und das Ziel-Itemset muss mindestens 10 % der Gesamtanzahl an Itemsets ausmachen. Bei sehr großen Datasets sind Prozentangaben u. U. besser geeignet als Wertangaben, da Sie sich so auf die wichtigsten Elementgruppierungen konzentrieren können.  
  
> [!NOTE]  
>  Beachten Sie, dass die Anzahl der Itemsets sich von der Anzahl der Transaktionen in den Daten unterscheidet. Jede Transaktion kann mehrere Itemsets enthalten. Die meisten Itemsets werden jedoch mehrmals im Dataset wiederholt.  
  
### <a name="rule-probability-and-rule-importance"></a>Regelwahrscheinlichkeit und Regelwichtigkeit  
 Die Wahrscheinlichkeit einer Regel beschreibt, wie wahrscheinlich das Auftreten des Ergebnisses einer Regel ist. Die Regelwahrscheinlichkeit wird anhand der Häufigkeit der Itemsets berechnet, die eine Regel unterstützen. Wenn ein Itemset sehr selten auftritt, hat es eine niedrige Wahrscheinlichkeit.  
  
 Regeln, die eine hohe Wahrscheinlichkeit aufweisen, sind allerdings unter Umständen nicht immer hilfreich. Diese könnten nämlich Itemsets angeben, die häufig gekauft werden und daher keine zusätzliche Werbung benötigen. Mit der Wichtigkeit wird die Nützlichkeit einer Regel gemessen. Manchmal kann eine Regel eine sehr hohe Wahrscheinlichkeit jedoch eine geringe Wichtigkeit haben, da die Vorhersage keine neuen Informationen bietet. Wenn z. B. jedes Itemset einen bestimmten Attributstatus enthält, ist die Regel, die diesen Status vorhersagt, unbedeutend, auch wenn die Wahrscheinlichkeit sehr hoch ist.  
  
 Sie sollten mit diesen Einstellungen experimentieren, um andere Ergebnisse zu erhalten und zu ermitteln, welche Einstellung die besten Regeln ergibt.  
  
## <a name="understanding-the-reports"></a>Grundlegendes zu Berichten  
 Die **Warenkorbanalyse** Tool erstellt zwei komplementäre Berichte. Der erste Bericht, der mit dem Titel **signifikanten Gruppen von während der Analyse bestimmt Elemente**, enthält eine Liste aller Itemsets, die gefunden wurden. Sie können die neuen Tabellentools in Microsoft Excel verwenden, um die Daten zu sortieren, zu filtern und zu durchsuchen.  
  
 Der zweite Bericht, der mit dem Titel **Warenkorbempfehlungen**, erfahren Sie, welche Art von Rückschlüsse basierend auf den im ersten Bericht aufgeführten Itemsets vorgenommen werden kann. Die Liste der Itemsets ist nützlicher, um die Daten zu durchsuchen und zu verstehen, anhand der Regelliste können Sie jedoch Vorhersagen und Empfehlungen treffen.  
  
### <a name="shopping-basket-item-groups-report"></a>Bericht Warenkorb-Elementpakete  
 Dieser Bericht enthält eine Liste aller möglichen Kombinationen von Elementen, die im Dataset gefunden wurden. Wenn Ihre Transaktionsdaten Bestellungen für jeden Auftrag enthält z. B. die **Warenkorbanalyse** Tool berechnet, wie oft das einzelne Element bestellt wurde, und alle Kombinationen für dieses Element mit anderen Elementen berechnet.  
  
 Der Bericht listet die gefundenen Itemsets in der Reihenfolge der Prognosegüte auf. Die Prognosegüte ist eine Bewertung, die die Wichtigkeit des Itemsets kennzeichnet.  
  
|Spalte im Bericht|Ihre Auswertung|  
|----------------------|-----------------------|  
|Elementpaket|Listet die Itemsets oder Kombination von Elementen auf.|  
|Gruppengröße|Anzahl der Elemente im Itemset. Sie können anhand dieses Felds filtern, um nur Elementpaare, einzelne Elemente usw. anzuzeigen.|  
|Support|Anzahl der Fälle, für die diese Kombination aufgetreten ist. Sie können anhand dieser Spalte sortieren, um die am häufigsten verwendeten Itemsets anzuzeigen.|  
|Durchschnittswert|Eine Summe des Werts der Elemente in ausschließlich diesen Itemsets geteilt durch die Unterstützung. Sie können anhand dieser Spalte sortieren und filtern, um Produkte in verschiedenen Preisbereichen anzuzeigen.|  
|Durchschnittlicher Korbwert|Eine Summe der Werte aller Elemente in Bestellungen, die dieses Itemset enthalten, geteilt durch die Unterstützung. Diese Statistik ist vor allem zusammen mit dem durchschnittlichen Wert des Itemsets interessant.|  
|Lift|Eine Bewertung, die angibt, wie bedeutend dieses Itemset im ganzen Dataset ist. Der Lift (auch bezeichnet als Prognosegüte) wird durch die Wahrscheinlichkeit, dass zwei Elemente gemeinsam bestellt werden, geteilt durch die Wahrscheinlichkeit, dass zwei Elemente einzeln auftreten, berechnet. Wenn es eine starke Abhängigkeit zwischen den Elementen gibt, wird die Bewertung der Prognosegüte höher ausfallen.|  
  
### <a name="shopping-basket-rules-report"></a>Bericht Warenkorbempfehlungen  
 Dieser Bericht enthält einen Satz an Regeln, die durch die Analyse der gefundenen Itemsets erstellt wurden. Wenn die Transaktionsdaten ergeben, dass die Produkte A und B häufig gleichzeitig gekauft wurden, erstellt das Warenkorbanalyse-Tool eine Regel, die A vorhersagt, vorausgesetzt B liegt vor, bzw. umgekehrt.  
  
 Eine Regel wird einer Wahrscheinlichkeit, die von den zugrunde liegenden Daten abgeleitet wird, zugeordnet. Diese Wahrscheinlichkeiten sind vor allem für Empfehlungen nützlich. Sie möchten möglicherweise nur die Regeln anzeigen, die basierend auf den vorhandenen Daten mit einer Wahrscheinlichkeit von mindestens 50 % akkurat sind.  
  
 Der Bericht listet die gefundenen Itemsets in der Reihenfolge der Prognosegüte auf. Die Prognosegüte ist eine Bewertung, die die Wichtigkeit des Itemsets kennzeichnet.  
  
|Spalte im Bericht|Ihre Auswertung|  
|----------------------|-----------------------|  
|Vorhandene Elemente|Listet die Elemente auf, die für eine Empfehlung erforderlich sind.<br /><br /> Beim Datamining, diese Elemente sind meist auf die *Links* der der Zuordnungsregel.|  
|Vorhergesagtes Element|Listet das zu empfehlende Element auf.<br /><br /> Beim Datamining, diese Elemente sind meist auf die *rechts* der der Zuordnungsregel.|  
|Probability|Zeigt die Wahrscheinlichkeit an, mit der diese Regel richtig ist.|  
|Support|Gibt die Anzahl von Fällen in vorhandenen Daten an, die diese Regel bestätigen.|  
|Durchschnittlicher Empfehlungswert|Wenn Sie einen Wert für die Elemente im Warenkorb angeben, wird in dieser Spalte der Wert der Vorhersage anhand der Kosten der Elemente berechnet.|  
|Lift|Gibt die Stärke der Abhängigkeit zwischen den Elementen in der ersten Spalte und den Elementen in der zweiten Spalte an. Auch bezeichnet als *Wichtigkeit*.<br /><br /> Ein Lift (auch bezeichnet als Prognosegüte) von 0 bedeutet, dass keine Abhängigkeit vorliegt. Ein positiver Wert bedeutet, dass die Elemente in der ersten Spalte das Element in der zweiten Spalte vorhersagen. Je höher die Zahl, desto stärker die Abhängigkeit.|  
  
## <a name="related-tools"></a>Verwandte Tools  
 Der Data Mining-Client für Excel, bei dem es sich um ein separates Add-In mit erweiterter Data Mining-Funktionalität handelt, umfasst auch einen Assistenten, mit dem eine Zuordnungsanalyse durchgeführt wird. Weitere Informationen finden Sie unter [Assistenten zum Zuordnen von &#40;Data Mining-Client für Excel&#41;](associate-wizard-data-mining-client-for-excel.md).  
  
 Weitere Informationen zum Algorithmus, der für diese Analyse verwendet wird, finden Sie im Thema "Microsoft Association-Algorithmus" in der SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  
