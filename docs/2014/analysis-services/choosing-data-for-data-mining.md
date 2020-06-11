---
title: Auswählen von Daten für Data Mining | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content type [data mining]
- nested tables
- key [data mining]
- continuous values
- key sequence [data mining]
- table data type
- key time [data mining]
- discrete values
- discretized
ms.assetid: 7c72d80e-913c-4bbe-b258-444294a78838
author: minewiskan
ms.author: owend
ms.openlocfilehash: 589a1f64a3bed5455f8004e51f6cddf84e83fec5
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527586"
---
# <a name="choosing-data-for-data-mining"></a>Auswählen von Daten für das Data Mining
  Wenn Sie Data Mining starten, Fragen Sie sich möglicherweise, wie viele Daten benötigt werden. oder "gibt es spezielle Anforderungen, die ich bei der Bereinigung oder Formatierung meiner Daten kennen muss?"  
  
 Neueinsteiger im Bereich Data Mining stoßen insbesondere im Zusammenhang mit Excel-Daten häufig auf Probleme. Beispielsweise, wenn sie Daten innerhalb von Spalten konsistent formatieren, fehlende Werte bereinigen oder Zahlen klassifizieren müssen. In diesem Abschnitt sind die Datenanforderungen für bestimmte Modellarten aufgeführt.  
  
 [Auswählen von Daten](#bkmk_ChoosingData)  
  
 [Allgemeine Datenprobleme](#bkmk_CommonDataProblems)  
  
 [Sonstige Datenanforderungen](#bkmk_OtherRequirements)  
  
##  <a name="choosing-data"></a><a name="bkmk_ChoosingData"></a>Auswählen von Daten  
 Die Auswahl der zu analysierenden Daten ist möglicherweise der wichtigste Schritt im Data Mining-Prozess, sogar wichtiger als die Auswahl eines Algorithmus. Der Grund hierfür ist, dass sich Data Mining im Allgemeinen nicht auf eine Hypothese, sondern auf Daten stützt. Im Unterschied zur herkömmlichen statistischen Modellierung, bei der Variablen im voraus ausgewählt und getestet werden, ermittelt das Data Mining auf der Basis der Daten neue Korrelationen (es kann jedoch vorkommen, dass überhaupt keine Muster gefunden werden). Qualität und Menge der Daten können erhebliche Auswirkungen auf die Ergebnisse haben.  
  
 Die folgenden grundsätzlichen Regeln sollten beachtet werden:  
  
-   Nutzen Sie so viele bereinigte Daten wie möglich.  
  
-   Führen Sie eine Datenprofilerstellung aus, bevor Sie ein Modell ausprobieren. Ein grundlegendes Verständnis der Daten ist erforderlich, damit Sie eine Bedeutung daraus ableiten können. Mindestanforderungen:  
  
    1.  Verwenden Sie die Add-In-Tools, um die Maximal- und Minimalwerte, die gängigsten Werte und die Durchschnittswerte zu suchen.  
  
    2.  Ergänzen Sie fehlende Werte. Die Add-Ins (sowie einige Algorithmen) stellen Tools zum Einfügen fehlender Werte bereit.  
  
    3.  Korrigieren Sie nach Möglichkeit fehlerhafte Daten. Data Mining-Projekte sind häufig der Auslöser für neue Initiativen zur Verbesserung der Datenqualität.  
  
-   Versuchen Sie, ein Testmodell zu erstellen und auf diese Weise Datenprobleme zu ermitteln. Möglicherweise stellen Sie bei der Untersuchung der Ergebnisse fest, dass sich Umsatzprognosen aufgrund einer fehlerhaften Währungsumrechnung auf anomale Daten stützen.  
  
-   Versuchen Sie, die Daten in andere Formate umzuwandeln, oder ordnen Sie die Zahlen Buckets zu. Muster ergeben sich häufig bei der Transformation der Daten.  
  
     Beispielsweise kann der Wochentag Einfluss auf den Servicelevel in einem Callcenter nehmen. Das lässt sich jedoch nur erkennen, wenn Sie nicht ausschließlich datetime-Werte verwenden. Wenn Sie Vorhersagen in einem 10-Tage-Zyklus anstatt wöchentlich oder täglich generieren, erzielen Sie eine bessere Vorhersagequalität.  
  
-   Ordnen Sie die Zahlen entsprechenden Containern zu, um die Anzahl der möglichen Analysewerte zu reduzieren.  
  
-   Erstellen Sie mehrere Versionen der Daten, und generieren Sie mehrere Modelle.  
  
 Weitere Tipps zum auswählen, ändern und Überprüfen von Daten finden Sie unter [Checkliste der Vorbereitung für das Data Mining](checklist-of-preparation-for-data-mining.md).  
  
### <a name="how-much-data-do-i-need"></a>Wie viele Daten benötige ich?  
 Als Faustregel gilt, dass eine Anzahl von 50-100 Datenzeilen bei den einfachsten Modelltypen und Szenarien nicht unterschritten werden darf. Wenn Sie beispielsweise ein einzelnes Attribut mithilfe eines Naive Bayes-Modells vorhersagen und das Dataset wohl geformt ist, lässt sich mit 50-100 Datenzeilen bereits eine ziemlich genaue Vorhersage treffen.  
  
 Bei Zuordnungs Modellen benötigen Sie in der Regel viel mehr Daten. eine Tausendstel Zeilen reichen möglicherweise nicht aus, wenn Sie viele Attribute analysieren, z. b. Zuordnungen zwischen Produkten. Wenn das Dataset zu groß oder zu klein ist, erzielen Sie in einigen Fällen bessere Ergebnisse, indem Sie Zeilen in Kategorien unterteilen. Anstatt die Zuordnungen zwischen einzelnen Produkten zu analysieren, könnten Sie die Produkte z. B. kategorisieren.  
  
 Wenn Sie über ein Dataset in der richtigen Größe verfügen, sollten Sie sich stärker auf die Datenqualität konzentrieren, anstatt laufend weitere Daten hinzuzufügen. An einem bestimmten Punkt sind alle statistisch aussagekräftigen Muster ermittelt, und das Hinzufügen weiterer Daten bringt keine zusätzlichen Vorteile. Im Gegenteil kann eine größere Datenmenge in einigen Fällen zu unbeabsichtigten Korrelationen führen.  
  
### <a name="discrete-vs-continuous-numbers"></a>Diskrete und fortlaufende Zahlen  
 Eine *diskrete* Spalte enthält eine endliche Anzahl von Werten. So wird beispielsweise Text immer als diskreter Wert behandelt.  
  
 Diskrete Werte zeichnen sich durch einige wichtige Merkmale aus. Wenn Sie Zahlen beispielsweise als diskret behandeln, weisen die Zahlen keine Reihenfolge auf, sodass Sie keine Mittelwerte oder Summen bilden können. Ortsvorwahlen sind ein anschauliches Beispiel für diskrete numerische Daten, die für mathematische Berechnungen niemals infrage kommen würden.  
  
 Diskrete Werte werden gelegentlich als kategoriale Werte bezeichnet, da Sie anhand dieser Werte eine Datenmenge gruppieren können, während dies bei Zahlen in einer unbegrenzten Reihe nicht möglich ist.  
  
 Sie können auch entscheiden, dass Zahlen als diskrete Werte behandelt werden, wenn die Werte eindeutig voneinander getrennt und Bruchzahlen nicht möglich bzw. nicht hilfreich sind.  
  
 *Kontinuierliche* numerische Daten können eine unendliche Anzahl von Bruch Werten enthalten. Eine Einkommensspalte stellt ein Beispiel für eine kontinuierliche Attributspalte dar. Wenn Sie eine Spalte als numerisch festlegen, muss jeder Wert in dieser Spalte eine Zahl sein (mit Ausnahme von NULL-Werten). Beachten Sie, dass in Excel Zeitstempel und sonstige Datum-Uhrzeit-Darstellungen, die in einen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datentyp konvertierbar sind, berücksichtigt werden können.  
  
 **Konvertieren von Zahlen in Kategorievariablen**  
  
 Dass eine Spalte Zahlen enthält, bedeutet nicht, dass sie als kontinuierliche Zahlen zu behandeln sind. Die *Diskretisierung* bietet viele Vorteile für die Analyse. Einer davon besteht darin, dass das Problemfeld reduziert wird. Ein weiterer Vorteil ist, dass Zahlen nicht immer die geeignete Methode sind, um ein Ergebnis auszudrücken.  
  
 So kann beispielsweise die Anzahl der Kinder pro Familie als kontinuierlicher oder als diskreter Wert behandelt werden. Da es nicht möglich ist, dass in einer Familie 2,5 Kinder leben, und Familien mit 3 oder mehr Kindern deutliche Unterschiede zu Familien mit 2 Kindern aufweisen, erzielen Sie u. U. bessere Ergebnisse, wenn Sie diese Zahl als Kategorie behandeln. Wenn Sie jedoch ein Regressionsmodell erstellen oder aus einem anderen Grund einen Mittelwert (z. B. 1,357 Kinder pro Haushalt) benötigen, würden Sie einen Datentyp mit kontinuierlichen Zahlen verwenden.  
  
 Es ist nicht möglich, ein Miningmodell mit kontinuierlichen Daten zu erstellen und die Spalte zu einem späteren Zeitpunkt als diskret zu behandeln. Die beiden Datasets müssen unterschiedlich verarbeitet werden und werden im Back-End -System als separate Miningstrukturen behandelt. Wenn Sie unsicher sind, wie die Daten behandelt werden sollen, sollten Sie separate Modelle erstellen, von denen die Daten unterschiedlich verarbeitet werden. Das ist ein guter Ansatz, um Daten aus unterschiedlichen Blickwinkeln zu betrachten und ggf. unterschiedliche Ergebnisse zu vergleichen.  
  
 **Konvertieren von Zahlen in Text**  
  
 Häufig werden Werte, die diskret sein sollten (z. B. Männlich und Weiblich) als numerische Daten dargestellt, wobei die Bezeichnungen 1 und 2 zur Anwendung kommen. Normalerweise wird diese Codierung zur Vereinfachung von Dateneingaben oder zum Einsparen von Speicherplatz durchgeführt. Sie kann jedoch auch zu Mehrdeutigkeit bezüglich der Art oder der Bedeutung der Werte führen. Zudem entstehen bei der Verschiebung der Daten zwischen Anwendungen möglicherweise Fehler bei der Konvertierung des Datentyps, da diskrete Werte als Zahlen gespeichert werden. Die Werte werden in diesem Fall berechnet oder als kontinuierliche Werte behandelt. Um das zu vermeiden, sollten Sie die numerischen Bezeichnungen vor dem Data Mining in diskrete Textbezeichnungen zurückkonvertieren.  
  
 **Klassifizieren von Zahlen**  
  
 Obwohl alle Zahlen im Prinzip unendlich sind und daher kontinuierlich sind, ist es beim Modellieren von Informationen möglicherweise effektiver, die verfügbaren Werte zu *diskretisieren* *oder zu* klassifizieren.  
  
 Zum Klassifzieren von Daten stehen Ihnen zahlreiche Möglichkeiten zur Verfügung:  
  
-   Geben Sie eine endliche Anzahl von Buckets an, und lassen Sie den Algorithmus die Werte in Buckets einsortieren.  
  
-   Nehmen Sie eine Vorgruppierung vor, indem Sie Gruppierungen erstellen, die eine geschäftliche Bedeutung aufweisen oder leichter verarbeitet werden können. Bei einem solchen Ansatz entgeht Ihnen oft die tatsächliche Verteilung der Werte, die Bereiche sind jedoch für die Benutzer lesbarer.  
  
-   Die optimale Anzahl der Buckets und die Verteilung der Werte können durch den Algorithmus bestimmt werden. Dies ist die Standardeinstellung in den meisten Tools, aber Sie können diese Standardeinstellungen in den Assistenten für die **Data Mining** -Symbolleiste überschreiben.  
  
-   Annähern der Werte an einen zentralen Mittelwert oder repräsentativen Wert.  
  
##  <a name="common-data-problems"></a><a name="bkmk_CommonDataProblems"></a>Häufige Daten Probleme  
  
### <a name="excel-number-formats"></a>Excel-Zahlenformate  
 Excel ist ein einfach zu verwendende Tool, da es sich um einen forout-Vorgang handelt. Wenn Sie jedoch nach Mustern suchen und Korrelationen analysieren, müssen Sie für die Daten eine bestimmte Struktur bzw. Einschränkungen festlegen.  
  
 Wenn Sie numerische Daten in [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel importieren, werden die Zahlen standardmäßig in einem Dezimalformat mit zwei Dezimalstellen gespeichert. Wenn dies kein geeignetes Zahlenformat ist, sollten Sie ein anderes numerisches Format verwenden oder die Anzahl der Dezimalstellen ändern.  
  
 Eine Möglichkeit besteht darin, das [Tool neu](relabel-sql-server-data-mining-add-ins.md) bezeichnen zu verwenden, um die Art und Weise zu ändern, in der Zahlen angezeigt oder gruppiert werden.  
  
 Wenn Ihre Daten jedoch zu komplex sind, um mit dem Tool " **Relabel** " zu verarbeiten, können Sie die numerischen Funktionen in Excel verwenden, um Ihre Daten in diskrete Bereiche zu konvertieren, das Ergebnis in einer separaten Spalte zu speichern und dann die diskretisierte Spalte für die Klassifizierung zu verwenden.  
  
 Wenn Sie beispielsweise die Ergebnisse eines Rennens analysieren und die Läufer nach der Ankunftszeit in Minuten gruppieren möchten, können Sie auf die nächste Minute aufrunden und den gerundeten Wert in einer neuen Spalte speichern. Sie können auch nur den Minutenwert extrahieren, indem Sie die `MINUTE`-Funktion verwenden, und diesen Wert anschließend in eine neue Spalte zur Verwendung in der Analyse speichern.  
  
### <a name="discretizing-numbers-and-dates-in-excel"></a>Diskretisieren von Zahlen und Datumsangaben in Excel  
 Standardmäßig werden numerische Daten in Excel als Daten vom Typ `Double` gespeichert. Datums- und Uhrzeitangaben werden ebenfalls in einem numerischen Format gespeichert. Wenn das Diskretisieren von Zahlen oder Datumsangaben für das Data Mining erforderlich ist, sollten Sie vor dem Generieren Ihres Data Mining-Modells neue Spalten hinzufügen oder Datumsangaben und Zahlen in ein anderes Format konvertieren.  
  
### <a name="scientific-number-formats"></a>Wissenschaftliche Zahlenformate  
 Die Data Mining-Tools geben Wahrscheinlichkeiten oft in wissenschaftlicher Schreibweise aus, um Zahlen darzustellen, die sehr groß oder sehr klein sind. Wenn Sie mit der wissenschaftlichen Schreibweise nicht vertraut sind, können Sie diese Zahlen in einem anderen Format anzeigen, indem Sie das Zellformat ändern.  
  
##### <a name="to-change-scientific-notation-to-a-decimal-numeric-format"></a>So ändern Sie die wissenschaftliche Schreibweise in ein numerisches Dezimalformat  
  
1.  Markieren Sie in der Excel-Datentabelle die Spalte oder Zelle, die die Zahl in wissenschaftlicher Schreibweise enthält.  
  
2.  Klicken Sie mit der rechten Maustaste, und wählen Sie im Kontextmenü **Zellen formatieren** aus.  
  
3.  Wählen Sie in der Liste **Kategorie** die Option **Zahl**aus.  
  
4.  Erhöhen Sie die Anzahl der Dezimalstellen. Eine Wahrscheinlichkeit, die in wissenschaftlicher Schreibweise dargestellt wird, ist im Allgemeinen sehr klein.  
  
     Nur die Anzeige der Zahl wird geändert, nicht der zugrunde liegende Wert.  
  
### <a name="working-with-dates-and-times"></a>Arbeiten mit Datums- und Uhrzeitangaben  
 Wenn Datumsangaben in einer Excel-Tabelle vorliegen und Sie die Spalte entweder als Eingabe oder für die Vorhersage verwenden, erhalten Sie möglicherweise unerwartete Ergebnisse, je nachdem, wie die Datums- bzw. Uhrzeitangaben formatiert sind. Wenn Sie z. b. **Kategorien erkennen** oder **klassifizieren** und eine Spalte einschließen, die Datumsangaben enthält, werden die Datumsangaben als Zahlen mit vielen Dezimalstellen kategorisiert. Dies ist kein Fehler, sondern eine genaue Darstellung der zugrunde liegenden Daten. Der Data Mining-Algorithmus arbeitet mit dem zugrunde liegenden Speicherformat, nicht dem Anzeigeformat.  
  
 Wenn Sie Schwierigkeiten bei der Arbeit mit Datumswerten haben und Sie Datumswerte mit solch allgemein gebräuchlichen Gruppierungen wie Monat oder Tag analysieren möchten, können Sie die DATE-Funktionen in Excel verwenden, um das Jahr, den Monat oder den Tag in einer separaten Spalte zu extrahieren und diese Spalte stattdessen für die Klassifizierung zu verwenden.  
  
##  <a name="other-data-requirements"></a><a name="bkmk_OtherRequirements"></a>Weitere Datenanforderungen  
  
### <a name="requirements-by-algorithm-type"></a>Anforderungen nach Algorithmustyp  
 Einige in den Add-Ins verwendete Algorithmen erfordern bestimmte Daten- oder Inhaltstypen für die Modellerstellung.  
  
 **Naïve Bayes-Modelle**  
  
-   Beispielsweise kann der [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes-Algorithmus keine kontinuierlichen Spalten als Eingabe verarbeiten. Das bedeutet, dass Sie Zahlen entweder klassifizieren oder − falls die Anzahl der Werte überschaubar ist − als diskrete Werte behandeln müssen.  
  
-   Zudem unterstützt dieser Modelltyp keine Vorhersage kontinuierlicher Werte. Wenn Sie also eine kontinuierliche Zahl, wie z. B. das Einkommen, vorhersagen möchten, sollten Sie die Werte zuerst in sinnvolle Bereiche unterteilen. Wenn Sie nicht sicher sind, welche Bereiche sinnvoll sind, können Sie anhand des Clusteringalgorithmus Zahlengruppierungen in den Daten identifizieren.  
  
-   Wenn Sie einen Assistenten verwenden, der auf diesem Algorithmus basiert (z. b. die [Analyse wichtiger Einflussfaktoren &#40;Tabellenanalyse Tools für Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)), werden Spalten, die fortlaufend sind, vom Assistenten klassifiziert.  
  
-   Wenn Sie mithilfe der Option [Erweiterte Modellierung &#40;Data Mining-Add-Ins für Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md) ein Naive Bayes-Modell erstellen, werden Zahlen Spalten aus dem Modell entfernt. Wenn Sie dies vermeiden möchten, verwenden Sie das Tool [Relabel &#40;SQL Server Data Mining-Add-ins&#41;](relabel-sql-server-data-mining-add-ins.md) , um eine neue Spalte mit klassierten Werten zu erstellen.  
  
 **Clusteringmodelle**  
  
-   Die clusteringtools ([Cluster-Assistent &#40;Data Mining-Add-Ins für Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) und [Erkennen von Kategorien &#40;Tabellenanalyse Tools für Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)) können auch keine kontinuierlichen Zahlen verwenden  
  
-   Beide Tools bieten Ihnen die Möglichkeit, die Anzahl der Ausgabekategorien in den Ergebnissen auszuwählen. Wenn Sie jedoch angeben möchten, wie Werte in den einzelnen Spalten gruppiert werden, sollten Sie eine neue Spalte mit der gewünschten Gruppierung erstellen.  
  
 **Vorhersagemodelle**  
  
-   Alle Planungstools erfordern, dass Sie eine kontinuierliche Zahl vorhersagen. Sie können keine Vorhersage auf der Basis von Zahlen treffen, die als Text gespeichert wurden.  
  
-   Wenn Ihre Daten Zahlenspalten enthalten, die den falschen Datentyp aufweisen, können Sie mithilfe von Excel- oder PowerPivot-Funktionen eine Kopie der Spalte anlegen, die dann den richtigen numerischen Datentyp aufweist. Achten Sie in diesem Fall darauf, die Kopie der Spalte, die Zahlen im Textformat enthält, zu entfernen. So vermeiden Sie doppelte Werte.  
  
-   Wenn Sie ein Punktdiagramm eines Regressionsmodells erstellen möchten, müssen die Eingabevariablen ebenfalls kontinuierlichen Zahlen entsprechen, die einen geeigneten Datentyp aufweisen.  
  
### <a name="using-content-types-to-make-better-models"></a>Erstellen effizienterer Modelle mithilfe von Inhaltstypen  
 Ein *Inhaltstyp* ist eine Eigenschaft, die Sie auf eine Spalte anwenden, um anzugeben, wie die Spaltendaten vom Modell verwendet werden sollen. Der Algorithmus kann den Inhaltstyp beim Ausführen der Analyse als Anweisung oder Hinweis interpretieren.  
  
 Wenn sich z. B. die Zahlen in einer Spalte in bestimmten Abständen wiederholen, mit denen die Wochentage angegeben werden, können Sie den Inhaltstyp dieser Spalte als `Cyclical` angeben.  
  
 Sie müssen sich keine Gedanken über Inhaltstypen machen, wenn Sie die Assistenten und Tools verwenden, die in diesen Add-ins bereitgestellt werden. Wenn Sie jedoch die Option [Modell zu Struktur &#40;Data Mining-Add-Ins für Excel&#41;Modellierung hinzufügen](add-model-to-structure-data-mining-add-ins-for-excel.md) verwenden, um vorhandenen Daten ein neues Modell hinzuzufügen, erhalten Sie möglicherweise einen Fehler im Zusammenhang mit Inhaltstypen.  
  
 Dies ist darauf zurückzuführen, dass einige Modelltypen eine bestimmte Art von Daten (z. B. einen Timestamp) erfordern. Die Tools verarbeiten diese Spalten entsprechend den jeweiligen Anforderungen und fügen zudem eine Inhaltstypeigenschaft hinzu. Wenn Sie die Daten mit einem vollkommen anderen Algorithmus erneut verwenden, müssen Sie deshalb ggf. den Datentyp oder den Inhaltstyp ändern.  
  
 In der folgenden Liste werden die Inhaltstypen beschrieben, die Sie beim Data Mining verwenden. Außerdem erfahren Sie hier, von welchen Datentypen die einzelnen Inhaltstypen unterstützt werden.  
  
 `Discrete`  
 Die Spalte enthält eine endliche Anzahl von Werten, wobei sich die Werte nicht durch eine kontinuierliche Größe unterscheiden. Eine Spalte mit der Angabe des Geschlechts ist ein Beispiel für eine typische diskrete Attributspalte, da die Daten eine bestimmte Anzahl von Kategorien darstellen.  
  
 Der Inhaltstyp `Discrete` kann mit allen Datentypen verwendet werden.  
  
 `Continuous`  
 Diese Spalte enthält Werte, die numerische Daten auf einer Skala darstellen, die Zwischenwerte zulässt. Eine kontinuierliche Spalte stellt skalierbare Messdaten dar, und die Daten können eine unendliche Anzahl von Teilwerten enthalten. Eine Temperaturspalte stellt ein Beispiel für eine kontinuierliche Attributspalte dar.  
  
 Der Inhaltstyp `Continuous` kann mit den folgenden Datentypen verwendet werden: `Date`, `Double` und `Long`.  
  
 `Discretized`  
 Diese Spalte enthält Werte, die Wertegruppen darstellen, die von einer kontinuierlichen Spalte abgeleitet sind. Die bucketwerte werden als **geordnete** und diskrete Werte behandelt.  
  
 Der Inhaltstyp `Discretized` kann mit den folgenden Datentypen verwendet werden: `Date`, `Double`, `Long`.  
  
 **Schlüssel**  
 Diese Spalte identifiziert eine Zeile eindeutig.  
  
 In der Regel ist die Schlüsselspalte ein numerischer Bezeichner oder ein Textbezeichner, der nur für das Verfolgen von Datensätzen und nicht für die Analyse genutzt werden sollte. Ausnahmen sind Zeitreihenschlüssel und Sequenzschlüssel.  
  
 **Schlüssel für die Schlüssel Tabelle** werden nur verwendet, wenn Sie Daten aus einer externen Datenquelle erhalten, die als [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenquellen Sicht definiert wurde. Weitere Informationen zu den Tabellen finden Sie unter [https://msdn.microsoft.com/library/ms175659.aspx](https://msdn.microsoft.com/library/ms175659.aspx) :  
  
 Dieser Inhaltstyp kann mit den folgenden Datentypen verwendet werden: `Date`, `Double`, `Long` und `Text`.  
  
 **Key Sequence**  
 Die Spalte enthält Werte, die eine Folge von Ereignissen darstellen. Die Werte sind sortiert, aber die Abstände zwischen den Werte müssen nicht gleich groß sein.  
  
 Dieser Inhaltstyp wird von folgenden Datentypen unterstützt: `Double`, `Long`, `Text` und `Date`.  
  
 **Key Time**  
 Die Spalte enthält Werte, die sortiert sind und eine Zeitskala darstellen. Sie können den Key Time-Inhaltstyp nur verwenden, wenn das Modell ein Zeitreihenmodell oder ein Sequenzclustermodell ist.  
  
 Dieser Inhaltstyp wird von den folgenden Datentypen unterstützt: `Double`, `Long` und `Date`.  
  
 **Tabelle**  
 Dieser Inhaltstyp wird ebenfalls nur verwendet, wenn Daten aus einer externen Datenquelle abgerufen werden, die als [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquellensicht definiert wurde.  
  
 Dies bedeutet, dass jede Datenzeile tatsächlich eine geschachtelte Datentabelle mit mindestens einer Spalte und mindestens einer Zeile enthält.  
  
 Die Tabellen sind sehr praktisch, aber Sie können Sie nur mit den [erweiterten Modellierungs &#40;Data Mining-Add-Ins für Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md) Modellierungs Optionen verwenden. Beispielsweise enthält die Beispiel Daten für den Assistenten zum [Zuordnen von Assistenten &#40;Data Mining-Client für Excel&#41;](associate-wizard-data-mining-client-for-excel.md) und die [waren Korb Analyse &#40;Table Analyzer for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) Tool Daten, die aus einer Tabelle mit einer Tabelle vereinfacht wurden.  

  
  
