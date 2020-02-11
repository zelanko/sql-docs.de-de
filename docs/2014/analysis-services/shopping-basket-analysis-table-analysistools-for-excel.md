---
title: Waren Korb Analyse (Tabellenanalyse für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: 3dadc054a3f9927c09e9e236044dd5ddee7f3a9a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66068676"
---
# <a name="shopping-basket-analysis-table-analysistools-for-excel"></a>Warenkorbanalyse (Tabellenanalysetools für Excel)
  ![Einkaufswagentool](media/tat-shopbskt.gif "Einkaufswagentool")  
  
 Das **waren Korb Analyse** Tool hilft Ihnen bei `associations` der Suche in Ihren Daten. Eine Zuordnung weist u. U. darauf hin, welche Elemente häufig gleichzeitig gekauft werden. In Data Mining handelt es sich bei dieser Technik um eine bekannte Methode, die als *Market Basket-Analyse*bezeichnet wird und die zur Analyse des Kaufverhaltens von Kunden in sehr großen Datasets verwendet wird. Marktforscher können anhand dieser Informationen Kunden Empfehlungen zu ähnlichen Produkten geben und verbundene Produkte besser vermarkten, indem Sie sie auf Webseiten, in Katalogen oder im Ladenregal in unmittelbarer Nähe zueinander anbieten.  
  
 Um die Warenkorbanalyse zu verwenden, müssen die Elemente, die Sie analysieren möchten, durch eine Transaktions-ID zueinander in Beziehung stehen. Wenn Sie beispielsweise alle Bestellungen, die über eine Website eingehen, analysieren möchten, erhält jede Bestellung eine Bestell- oder Transaktions-ID, die einem oder mehreren gekauften Produkten zugeordnet ist.  
  
 Wenn der Assistent die Analyse der Daten abgeschlossen hat, werden zwei neue Arbeitsblätter erstellt: waren **Korb Elementgruppen** und **waren Korb Regeln**.  
  
 Das Arbeitsblatt für **waren Korb Elementgruppen** enthält eine Liste der Elemente, die häufig in Transaktionen angezeigt werden. Diese allgemeinen Gruppierungen werden als *Itemsets*bezeichnet. Das Arbeitsblatt enthält auch Statistiken, z. b. *Support* und *Lift*, damit Sie die Bedeutung des Itemsets besser nachvollziehen können. Wenn Preisinformationen verfügbar sind, kann auf dem Arbeitsblatt auch eine Summe aller verbundenen Elemente erstellt werden, um eine Vorstellung vom Gesamtwert der Transaktionen zu bekommen.  
  
 Sie können im Bericht nach Spalten filtern und sortieren. Beispielsweise können Sie nur die Itemsets mit zwei oder mehr Produkten anzeigen oder die Itemsets nach **durchschnittlichem Warenkorbwert**anordnen.  
  
 Das Arbeitsblatt für **waren Korb Regeln** verwendet die aus der Analyse abgeleiteten Statistiken, um Regeln zur Beziehung zwischen Elementen zu erstellen. Eine Regel könnte z. B. lauten, dass Kunden, die Produkt a kaufen, sehr wahrscheinlich Produkt B kaufen. Die Regeln können verwendet werden, um Empfehlungen zu erstellen. Jeder Regel liegen Statistiken zugrunde, mit denen Sie die Aussagekraft der Regel bewerten können, sodass Sie nur dann eine Empfehlung ausgeben, wenn die Regel einen bestimmten Wahrscheinlichkeitsschwellenwert überschreitet.  
  
## <a name="using-the-shopping-basket-analysis-tool"></a>Verwenden des Tools Warenkorbanalyse  
  
1.  Öffnen Sie eine Excel-Tabelle mit geeigneten Daten. Klicken Sie in der Beispielarbeitsmappe auf das Zuordnungs-Arbeitsblatt.  
  
2.  Klicken Sie auf **waren Korb Analyse**.  
  
3.  Wählen Sie im Dialogfeld **waren Korb Analyse** die Spalte aus, die die Transaktions-ID enthält, und wählen Sie dann die Spalte aus, die die zu analysierenden Elemente bzw. Produkte enthält.  
  
4.  Optional können Sie auch eine Spalte hinzufügen, die Produktwerte enthält.  
  
5.  Klicken Sie auf**erweitert**, um das Dialogfeld **Erweiterte Parametereinstellung** zu öffnen. Erhöhen Sie den Wert für den **minimalen Support** , um die Anzahl von Produkten zu reduzieren, die als Itemsets gruppiert sind. Erhöhen Sie die **minimale Regel Wahrscheinlichkeit** , um sehr häufig verwendeter Itemsets herauszufiltern.  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Um das **waren Korb Analyse** Tool zu verwenden, müssen die Daten in einer Excel-Tabelle gespeichert werden und die folgenden Spalten enthalten:  
  
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
 Mit zunehmender Größe des Datasets nimmt auch die Anzahl möglicher Elementgruppierungen und -regeln zu, bis sie schließlich unüberschaubar wird. Sie können jedoch den Umfang an Ergebnissen, die vom Tool ausgegeben werden, steuern, um letztendlich nur die wichtigsten Itemsets und Regeln zu berücksichtigen. Diese Optionen legen Sie im **Dialog Feld Erweiterte Parameter für waren Korb**fest.  
  
### <a name="minimum-support"></a>Minimale Unterstützung  
 *Mindestunterstützung* bedeutet, dass die Anzahl von Transaktionen, die ein bestimmtes Itemset enthalten müssen, für das Itemset als signifikant angesehen werden muss. Sie sind möglicherweise nicht an einem Itemset interessiert, es sei denn es wurde in mindestens 10 unterschiedlichen Transaktionen gekauft. Es gibt zwei Möglichkeiten, den Schwellenwert für die Itemset-Bedeutung zu steuern, und beide verwenden den **minimalen Unterstützungs** Parameter.  
  
 **Als absoluter Wert:** Geben Sie eine Zahl ein, die die Anzahl der Transaktionen darstellt, die die Ziel Elemente enthalten. Wenn Sie beispielsweise 10 eingeben, wird jeder Satz an Elementen eingeschlossen, die in mindestens 10 Warenkörben enthalten sind.  
  
 **Als Prozentsatz:** Geben Sie eine Zahl ein, die einen Prozentsatz der gesamten Itemsets-Auflistung darstellt. Wenn Sie z. B. 10 eingeben, werden alle Itemsets berücksichtigt, und das Ziel-Itemset muss mindestens 10 % der Gesamtanzahl an Itemsets ausmachen. Bei sehr großen Datasets sind Prozentangaben u. U. besser geeignet als Wertangaben, da Sie sich so auf die wichtigsten Elementgruppierungen konzentrieren können.  
  
> [!NOTE]  
>  Beachten Sie, dass die Anzahl der Itemsets sich von der Anzahl der Transaktionen in den Daten unterscheidet. Jede Transaktion kann mehrere Itemsets enthalten. Die meisten Itemsets werden jedoch mehrmals im Dataset wiederholt.  
  
### <a name="rule-probability-and-rule-importance"></a>Regelwahrscheinlichkeit und Regelwichtigkeit  
 Die Wahrscheinlichkeit einer Regel beschreibt, wie wahrscheinlich das Auftreten des Ergebnisses einer Regel ist. Die Regelwahrscheinlichkeit wird anhand der Häufigkeit der Itemsets berechnet, die eine Regel unterstützen. Wenn ein Itemset sehr selten auftritt, hat es eine niedrige Wahrscheinlichkeit.  
  
 Regeln, die eine hohe Wahrscheinlichkeit aufweisen, sind allerdings unter Umständen nicht immer hilfreich. Diese könnten nämlich Itemsets angeben, die häufig gekauft werden und daher keine zusätzliche Werbung benötigen. Mit der Wichtigkeit wird die Nützlichkeit einer Regel gemessen. Manchmal kann eine Regel eine sehr hohe Wahrscheinlichkeit jedoch eine geringe Wichtigkeit haben, da die Vorhersage keine neuen Informationen bietet. Wenn z. B. jedes Itemset einen bestimmten Attributstatus enthält, ist die Regel, die diesen Status vorhersagt, unbedeutend, auch wenn die Wahrscheinlichkeit sehr hoch ist.  
  
 Sie sollten mit diesen Einstellungen experimentieren, um andere Ergebnisse zu erhalten und zu ermitteln, welche Einstellung die besten Regeln ergibt.  
  
## <a name="understanding-the-reports"></a>Grundlegendes zu Berichten  
 Das Tool **waren Korb Analyse** erstellt zwei ergänzende Berichte. Der erste Bericht mit dem Titel **bedeutende Gruppen von Elementen, die während der Analyse identifiziert**werden, enthält eine Liste aller gefundenen Itemsets. Sie können die neuen Tabellentools in Microsoft Excel verwenden, um die Daten zu sortieren, zu filtern und zu durchsuchen.  
  
 Der zweite Bericht mit dem Titel waren **Korb Regeln**gibt Aufschluss darüber, welche Art von Rückschlüsse basierend auf den im ersten Bericht aufgeführten Itemsets vorgenommen werden können. Die Liste der Itemsets ist nützlicher, um die Daten zu durchsuchen und zu verstehen, anhand der Regelliste können Sie jedoch Vorhersagen und Empfehlungen treffen.  
  
### <a name="shopping-basket-item-groups-report"></a>Bericht Warenkorb-Elementpakete  
 Dieser Bericht enthält eine Liste aller möglichen Kombinationen von Elementen, die im Dataset gefunden wurden. Wenn Ihre Transaktionsdaten z. b. Aufträge enthalten, berechnet das **waren Korb Analyse** -Tool für jede Bestellung, wie oft das einzelne Element sortiert wurde, und berechnet dann alle Kombinationen dieses Elements mit anderen Elementen.  
  
 Der Bericht listet die gefundenen Itemsets in der Reihenfolge der Prognosegüte auf. Die Prognosegüte ist eine Bewertung, die die Wichtigkeit des Itemsets kennzeichnet.  
  
|Spalte im Bericht|Was Sie Ihnen mitteilt|  
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
  
|Spalte im Bericht|Was Sie Ihnen mitteilt|  
|----------------------|-----------------------|  
|Vorhandene Elemente|Listet die Elemente auf, die für eine Empfehlung erforderlich sind.<br /><br /> In Data Mining werden diese Elemente auf der *linken Seite* der Zuordnungs Regel angezeigt.|  
|Vorhergesagtes Element|Listet das zu empfehlende Element auf.<br /><br /> In Data Mining werden diese Elemente auf der *rechten Seite* der Zuordnungs Regel angezeigt.|  
|Probability|Zeigt die Wahrscheinlichkeit an, mit der diese Regel richtig ist.|  
|Support|Gibt die Anzahl von Fällen in vorhandenen Daten an, die diese Regel bestätigen.|  
|Durchschnittlicher Empfehlungswert|Wenn Sie einen Wert für die Elemente im Warenkorb angeben, wird in dieser Spalte der Wert der Vorhersage anhand der Kosten der Elemente berechnet.|  
|Lift|Gibt die Stärke der Abhängigkeit zwischen den Elementen in der ersten Spalte und den Elementen in der zweiten Spalte an. Wird auch als *Wichtigkeit*bezeichnet.<br /><br /> Ein Lift (auch bezeichnet als Prognosegüte) von 0 bedeutet, dass keine Abhängigkeit vorliegt. Ein positiver Wert bedeutet, dass die Elemente in der ersten Spalte das Element in der zweiten Spalte vorhersagen. Je höher die Zahl, desto stärker die Abhängigkeit.|  
  
## <a name="related-tools"></a>Verwandte Tools  
 Der Data Mining-Client für Excel, bei dem es sich um ein separates Add-In mit erweiterter Data Mining-Funktionalität handelt, umfasst auch einen Assistenten, mit dem eine Zuordnungsanalyse durchgeführt wird. Weitere Informationen finden Sie unter [Zuordnen des Assistenten &#40;Data Mining-Client für Excel&#41;](associate-wizard-data-mining-client-for-excel.md).  
  
 Weitere Informationen zum Algorithmus, der für diese Analyse verwendet wird, finden Sie im Thema "Microsoft Association-Algorithmus" in der SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  
