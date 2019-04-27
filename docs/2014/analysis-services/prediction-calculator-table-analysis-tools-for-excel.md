---
title: Vorhersagerechner (Tabellenanalysetools für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining model, regression
- Table Analysis tools
- scorecard
- logistic regression
- prediction calculator
ms.assetid: 8bb8c318-e85f-4fd6-b32b-4cdfb13ca1b5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 330e302d1832f8ec5c3e76f961e4e68cf16726af
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62748872"
---
# <a name="prediction-calculator-table-analysis-tools-for-excel"></a>Vorhersagerechner (Tabellenanalysetools für Excel)
  ![Vorhersagerechnertool](media/tat-predcal.gif "Tool Vorhersagerechner")  
  
 Die **Vorhersagerechner** Tool können Sie eine Scorecard erstellen, die verwendet werden können, um neue Daten analysieren und zu Optionen und Risiken bewerten. Für, wenn Sie z. B. Vergangenheitsdaten und demografische Daten zu Kunden, die **Vorhersagerechner** Tool kann Ihnen bei zwei wichtigen Aufgaben helfen:  
  
-   Generieren einer zugrunde liegenden Analyse der demografischen Daten, des Kaufverhaltens und verschiedener anderer Faktoren.  
  
-   Erstellen einer Arbeitsscorecard, mit der Sie die Elemente auswerten und Empfehlungen für neue Produkt- oder Serviceangebote abgeben können.  
  
 Der Assistent erstellt darüber hinaus ein Arbeitsblatt, in dem sämtliche zugrunde liegende Berechnungen gespeichert sind. Auf diese Weise können Sie mit dem Modell interagieren und feststellen, welche Auswirkungen unterschiedliche Eingabewerte auf das Endergebnis haben.  
  
 Wenn Sie dies auswählen, kann der Assistent auch eine gedruckte Version des Arbeitsblatts erstellen, die Sie für Bewertungen unabhängig vom Computer verwenden können. Sie können mit dem Modell nicht so interagieren wie auf dem Computer mit der Excel-Arbeitsmappe, aber die gedruckte Version bietet alle Berechnungen, die Sie benötigen, um Werte einzugeben und das Endergebnis zu berechnen.  
  
## <a name="using-the-prediction-calculator-tool"></a>Verwenden des Tools Vorhersagerechner  
  
1.  Öffnen Sie eine Excel-Tabelle mit den zu analysierenden Daten.  
  
2.  Klicken Sie auf **Vorhersagerechner** auf die **analysieren** Registerkarte.  
  
3.  In der **Vorhersagerechner** im Dialogfeld für das Ziel die Spalte auswählen, die Sie vorhersagen möchten beispielsweise das Kaufverhalten,.  
  
4.  Geben Sie den Zielwert an. Wenn der Wert numerisch ist, verwenden Sie die Option **im Bereich**, und geben Sie dann die minimalen und maximalen Werte für den gewünschten Bereich. Wenn der Wert diskret ist, wählen Sie die **genau** aus, und wählen Sie den Wert aus der Dropdownliste aus.  
  
5.  Klicken Sie auf **wählen Sie Spalten, die zu analysierende**.  
  
6.  In der **erweiterte Spaltenauswahl** klicken Sie im Dialogfeld Spalten auswählen, die nützliche Informationen enthalten. Entfernen Sie alle Spalten, die für die Analyse nicht relevant sind. Klicken Sie auf **OK**.  
  
     Um eine Verzerrung der Ergebnisse zu vermeiden, sollten Sie auch die Spalten entfernen, die doppelte Informationen enthalten. Wenn Sie beispielsweise eine Spalte Einkommen haben, die numerische Daten enthält, und eine Spalte Einkommensgruppe, die die Bezeichnungen Hoch, Mittel und Niedrig enthält, sollten Sie nicht beide Spalten in dasselbe Modell aufnehmen. Stattdessen könnten Sie ein separates Modell für jede Spalte erstellen.  
  
7.  In der **Ausgabeoptionen** wählen Sie im Abschnitt **operativer Rechner** um die Analyse und die Scorecard in einer Excel-Arbeitsmappe zu erstellen. Wählen Sie **druckoptimierter Rechner** erstellen die Analyse und generieren auch einen Bericht, der gedruckt und für manuelle Bewertungen verwendet werden kann.  
  
8.  Klicken Sie auf **Ausführen**.  
  
     Das Tool erstellt neue Arbeitsblätter, die die Berichte und die Scorecards enthalten.  
  
### <a name="requirements"></a>Anforderungen  
 Die **Vorhersagerechner** Tool verwendet den Microsoft Logistic Regression-Algorithmus, der diskrete Werte als auch diskretisierten und kontinuierlichen numerischen Daten arbeiten kann.  
  
## <a name="understanding-the-scoring-reports"></a>Grundlegendes zu den Bewertungsberichten  
 Wenn Sie beide Ausgabeoptionen aktivieren, erstellt der Vorhersagerechner die folgenden drei neuen Arbeitsblätter in der aktuellen Arbeitsmappe:  
  
-   Ein **Vorhersagebericht**, enthält die Ergebnisse der Analyse mit interaktiven Tabellen und Diagramme, mit denen Sie experimentieren mit Interaktionen und gewinnen.  
  
-   Eine interaktive **Vorhersagerechner** , mit dem Sie die Bewertungen zu erstellen.  
  
-   Ein **druckbaren Rechner** mit Anweisungen und Koeffizienten für die Bewertung.  
  
-   In diesem Abschnitt werden die Informationen in den einzelnen Berichten und die Verwendung der verschiedenen Berichtsoptionen beschrieben.  
  
### <a name="prediction-report-with-graphs"></a>Vorhersagebericht mit Diagrammen  
 Der erste vorhersagebericht heißt **Rechner Vorhersagebericht für die \<Zielstatus > der \<Zielattribut >**. Er enthält aus der Analyse abgeleitete Tabellen und Faktoren sowie Tools, mit denen Sie die finanziellen Auswirkungen einer bestimmten Analyse bewerten können.  
  
#### <a name="table-for-specifying-costs-and-profits"></a>Tabelle zum Angeben von Kosten und Gewinnen  
 Das erste Tool dieses Berichts befindet sich oben links im Bericht. Es ist eine Tabelle, in der Sie die Kosten und Gewinne angeben können, die mit der richtigen und falschen Vorhersage eines Werts verbunden sind.  Diese Kosten und Gewinne sind erforderlich, um für den Rechner den optimalen Ergebnisschwellenwert zu berechnen.  
  
|Element|Beschreibung und Beispiel|  
|----------|-----------------------------|  
|Falsch positive Kosten|Die Kosten der Annahme, dass das Modell richtigerweise ein positives Ergebnis vorhergesagt, wobei die Vorhersage eigentlich falsch ist.<br /><br /> Beispielsweise sagt das Modell vorher, dass ein Kunde etwas kaufen wird. Basierend darauf erarbeiten Sie eine Kampagne, die auf den Kunden ausgerichtet ist. Sie könnten die Kosten für Kundenkontakte hier eingeben.|  
|Falsch negative Kosten|Die Kosten der Annahme, dass das Modell richtigerweise ein negatives Ergebnis vorhergesagt, wobei die Vorhersage eigentlich falsch ist.<br /><br /> Beispielsweise kann das Modell vorhersagen, dass ältere Kunden eher keine Fahrräder kaufen. Sie stellen aber fest, dass das Modell verzerrt war und dass Sie deshalb die Gelegenheit verpasst haben, sich an ältere Kunden zu wenden. Sie könnten hier Kosten der entgangenen Gelegenheit angeben.|  
|Richtig positiver Gewinn|Der Gewinn eines richtig vorhergesagten positiven Ergebnisses. Wenn Sie beispielsweise bei einer Verkaufsaktion die richtigen Kunden ansprechen und Kundenkontakte entstehen, würden Sie hier den Gewinn pro Kunde eingeben.|  
|Richtig negativer Gewinn|Der Gewinn eines richtig vorhergesagten negativen Ergebnisses.<br /><br /> Wenn Sie beispielsweise die Kunden, die angesprochen werden sollten, richtig bestimmen können, könnten Sie hier die Zahl X als Werbeaufwand pro Kunde angeben.|  
  
#### <a name="chart-for-viewing-maximum-profit"></a>Diagramm zum Anzeigen des maximalen Gewinns  
 Bei der Eingabe von Werten in die Tabelle werden die entsprechenden Diagramme automatisch aktualisiert, damit Sie sehen können, wo für das aktuelle Modell der optimale Punkt zur Maximierung des Gewinns ist. Das Liniendiagramm rechts neben dieser Tabelle zeigt den Gewinn für verschiedene Ergebnisschwellenwerte an. Der Gewinn wird anhand der Zahlen für Gewinn und Kosten geschätzt, die Sie in die Tabelle eingeben, und basierend auf den Vorhersagen und Wahrscheinlichkeiten des Modells.  
  
 Z. B. If, in der oberen linken Tabelle, die Zelle für **vorgeschlagener Schwellenwert zum Maximieren des Gewinns** zeigt dem Wert 500, das Diagramm auf der rechten Seite 500 als der höchste Punkt im Liniendiagramm angezeigt. Dieser Wert 500 bedeutet, dass Sie zur Maximierung der Gewinne die ersten 500 Empfehlungen des Miningmodells, sortiert nach Wahrscheinlichkeit, verwenden sollten.  
  
#### <a name="table-listing-scores-for-each-attribute-and-value"></a>Tabelle mit den Ergebnissen für jedes Attribut und jeden Wert  
 Die Tabelle unten links im Bericht zeigt eine detaillierte Analyse der gefundenen Werte sowie die Auswirkungen der Werte auf das Ergebnis. Sie können die Werte nicht in dieser Tabelle ändern. Sie werden angezeigt, um Ihnen beim Verständnis der Vorhersage zu helfen.  
  
 Die folgende Tabelle zeigt ein Beispiel der Ergebnisse, wenn es das Ziel ist, dass ein Kunde ein Fahrrad kauft. In der Tabelle wird jede Eingabespalte aufgeführt, die im Modell verwendet wurde, unabhängig davon, ob die Eingabe das Modell beeinflusst hat. In der Tabelle werden auch die diskreten Werte und die diskretisierten Werte aufgelistet, wenn die Eingabespalte kontinuierliche numerische Daten enthält.  
  
 Die Werte in der **Relative Auswirkung** Spalte werden als Prozentsätze dargestellte Wahrscheinlichkeiten. Die Zelle wird schattiert, um die Auswirkung dieses Werts auf die Ergebnisse grafisch darzustellen.  
  
|Attribut|Wert|Relative Auswirkung|  
|---------------|-----------|---------------------|  
|Marital Status|Verheiratet|0|  
|Marital Status|Single|71|  
|Geschlecht|Female|13|  
|Geschlecht|Male|0|  
  
 Sie können diese Faktoren wie folgt interpretieren:  
  
-   Verheiratet zu sein beeinflusst die Wahrscheinlichkeit nicht, dass der Kunde ein Fahrrad kauft.  
  
-   Ledig zu sein ist jedoch ein starker Indikator (70 Prozent) dafür, dass der Kunde wahrscheinlich ein Fahrrad kauft.  
  
-   Das Geschlecht des Kunden hat nur geringe Auswirkungen (13 %) auf das vorhergesagte Kaufverhalten im Hinblick auf Fahrräder, wenn der Kunde eine Frau ist. Ist der Kunde ein Mann, hat das Geschlecht gar keine Auswirkungen auf dieses Verhalten.  
  
#### <a name="chart-of-cumulative-misclassification-cost"></a>Diagramm der kumulativen Kosten der falschen Klassifizierung  
 Das Flächendiagramm unten rechts im Bericht zeigt die kumulativen Kosten der falschen Klassifizierung für verschiedene Ergebnisschwellenwerte an. Dieses Diagramm nutzt außerdem die Zahlen für Kosten und Gewinne, die Sie als falsch und richtig positive Werte und als falsch und richtig negative Werte eingegeben haben.  
  
 Anders als das Diagramm oben rechts im Bericht, das die Maximierung des Gewinns zum Schwerpunkt hat, werden in dieses Diagramm auch die Kosten einer falschen Vorhersage eingearbeitet. Dieses Diagramm ist beispielsweise zur Vorbeugung sehr nützlich, wenn die Kosten einer falschen Entscheidung beträchtlich höher sind als die Kosten einer richtigen Annahme.  
  
 Obwohl das erste Diagramm vorschlägt, dass Sie Ihre Gewinne maximieren können, indem Sie die ersten 500 vom Modell vorhergesagten Kunden erreichen, könnten Sie sich beispielsweise nach einem Blick auf dieses zweite Diagramm entscheiden, dass die Kosten zu hoch sind, wenn diese Kunden fälschlicherweise angesprochen werden. Sie entschließen sich deshalb dazu, die Marketingkampagne auf die ersten 400 Kunden zu beschränken.  
  
### <a name="interactive-prediction-calculator"></a>Interaktiver Vorhersagerechner  
 Das zweite, vom Tool Vorhersagerechner erstellte Arbeitsblatt heißt **Vorhersagerechner für den \<Zielstatus > der \<Zielattribut >**. Es ist ein interaktives Arbeitsblatt, mit dem Sie einzelne Ergebnisse berechnen können. Da dieses Arbeitsblatt im Modell gespeicherte Muster und Statistiken nutzt, können Sie mit unterschiedlichen Werten experimentieren und deren Auswirkungen auf das vorhergesagte Ergebnis ermitteln. Dieser Bericht weist auch zwei Abschnitte auf: Einer ist interaktiv, und einer dient als Referenz.  
  
#### <a name="first-table"></a>Erste Tabelle  
 Sie können auswählen, oder geben Sie einen neuen Wert in der **Wert** -Spalte der Tabelle zu sehen, wie sich die Änderung des Werts auf das Ergebnis auswirkt.  
  
 Wenn der Bericht beispielsweise die folgenden Werte enthält, können Sie den Wert für Autos auf 1 reduzieren und dann auf 0, um festzustellen, wie sich dies auf das Kaufverhalten der Kunden auswirkt. Wenn Sie den Wert der ändern **Autos** 0 ist, ändert sich die Vorhersage unten auf "true".  
  
|Attribut|Wert|Relative Auswirkung|  
|---------------|-----------|---------------------|  
|Marital Status|Verheiratet|0|  
|Geschlecht|Male|0|  
|Income|39050 - 71062|117|  
|Children|0|157|  
|Education|Bachelor|22|  
|Occupation|Skilled Manual|33|  
|Wohneigentum|Ja|8|  
|Autos|2|50|  
|Commute Distance|0-1 Meilen|99|  
|Region|North America|0|  
|Age|37 - 46|5|  
|Total||491|  
|Vorhersage für 'Ja'||FALSE|  
  
 Wenn Sie in den neuen Wert eingeben, ändert sich das Ergebnis in der Zelle Vorhersage für ' Ja ', auf "true", und die **Relative Auswirkung** Bewertungen für die verschiedenen Attribute werden ebenfalls aktualisiert.  
  
> [!NOTE]  
>  Auch wenn Sie nur einen Wert ändern, beispielsweise die Anzahl der Autos, können sich die Werte und Auswirkungen anderer Attribute ebenfalls ändern. Der Grund dafür ist, dass Data Mining-Modelle häufig komplexe Beziehungen zwischen Daten finden. Die Änderung einer Variablen kann dann unvorhergesehene Auswirkungen haben. Deshalb empfehlen wir, mithilfe des interaktiven Vorhersagerechners mit unterschiedlichen Werten zu experimentieren. Sie können auch das Miningmodell durchsuchen, damit Sie die Interaktionen besser verstehen. Weitere Informationen finden Sie unter [Modelle Durchsuchen](prediction-calculator-table-analysis-tools-for-excel.md).  
  
#### <a name="score-breakdown"></a>Ergebnisaufschlüsselung  
 In dieser Tabelle sind die einzelnen Ergebnisse für jeden Zustand der Eingabespalten und die relative Auswirkung auf die Ergebnisse dargestellt. Diese Tabelle ist statisch und dient nur als Referenz.  
  
### <a name="printable-prediction-calculator"></a>Druckbarer Vorhersagerechner  
 Das dritte, vom Tool Vorhersagerechner erstellte Arbeitsblatt heißt **PrintablePrediction Rechner für die \<Zielstatus > der \<Zielattribut >**. Die Scorecard ist zum Drucken vorgesehen, sodass Sie manuell Ergebnisse berechnen können, wenn Sie nicht am Computer sind.  
  
##### <a name="to-print-and-use-the-scoring-report-generated-by-the-prediction-calculator"></a>So drucken und verwenden Sie den vom Vorhersagerechner generierten Bewertungsbericht  
  
1.  Klicken Sie auf der Registerkarte "mit dem Titel" **Druckbarer Vorhersagerechner für \<Attribut >**.  
  
2.  Wählen Sie im Excel-Datei, **Seitenansicht**.  
  
3.  Ändern Sie die Seitenausrichtung, die Ränder und andere Druckoptionen, bis die Scorecard wie gewünscht auf die Seite passt.  
  
     Diese Scorecard ist nicht dynamisch und in keiner Weise mit dem Modell verbunden. Sie können also Spalten oder Zeilen verschieben, und dies hat keine Auswirkungen auf die zugrunde liegenden Daten.  
  
4.  Drucken Sie die Scorecard.  
  
5.  Wählen Sie für jedes Attribut nur einen Wert aus. Für den Wert Sie auswählen, setzen ein Häkchen im Feld, und Schreiben Sie die entsprechende Anzahl in der **Bewertung** Spalte.  
  
6.  Geben Sie möglichst viele Attribute an, um Genauigkeit sicherzustellen.  
  
7.  Berechnet die Summe der Ergebnisse für jedes Attribut, und geben Sie diese Zahl in die **insgesamt** Zeile.  
  
8.  Konvertieren Sie das Ergebnis in ein vorhergesagtes Ergebnis anhand der Kriterien, die auf dem Blatt gedruckt unmittelbar nach der **insgesamt** Zeile.  
  
## <a name="related-tools"></a>Verwandte Tools  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] stellt den Microsoft Logistic Regression-Algorithmus zur Verwendung für diese Art von Analyse bereit. Wenn Sie bereits mit der logistischen Regression vertraut sind, können Sie problemlos logistische regressionsmodelle erstellen, mit der **erweitert** Möglichkeit, Data Mining-Client für Excel. Weitere Informationen finden Sie unter [erweiterte Modellierung &#40;Data Mining-Add-ins für Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md). Weitere Informationen zu den Optionen und Parametern für logistische regressionsmodelle finden Sie im Thema "Microsoft Logistic Regression-Algorithmus" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  
