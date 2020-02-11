---
title: Gewinn Diagramm (Analysis Services-Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy, charting
- revenue, estimating
- benefits, estimating
- charts [Analysis Services]
- profit charts [Analysis Services]
ms.assetid: 760ee051-6fd8-48e3-8d2e-82db3ab45e45
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1a64eacb1219e239ad894d9922db5a5032ed525b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66083092"
---
# <a name="profit-chart-analysis-services---data-mining"></a>Gewinndiagramm (Analysis Services – Data Mining)
  Ein Gewinndiagramm zeigt die geschätzte Gewinnsteigerung an, die sich aus der Verwendung eines Miningmodells ergibt. Nehmen wir beispielsweise an, dass Ihr Modell vorhersagt, welche Kunden ein Unternehmen in einem Geschäftsszenario kontaktieren sollte. In diesem Fall würden Sie dem Gewinndiagramm Informationen hinzufügen, wie hoch die Kosten einer solchen zielgerichteten Mailingkampagne sind. Das fertige Diagramm enthält die geschätzte Gewinnsteigerung, die darauf basiert, dass die Kunden gezielt und nicht nach dem Zufallsprinzip angesprochen werden.  
  
## <a name="build-a-profit-chart"></a>Erstellen eines Gewinndiagramms  
 Ein Gewinndiagramm ist mit einem Prognosegütediagramm vergleichbar. Zunächst erstellen Sie ein Prognosegütediagramm und fügen dann die Kosten- und Gewinninformationen hinzu.  
  
 Um ein Gewinndiagramm erstellen zu können, müssen Sie bereits über ein vorhandenes Modell verfügen.  
  
 In diesem Beispiel verwenden wir das Entscheidungsstrukturmodell für zielgerichtete Mailings ("Targeted Mailing"). Das Modell ermittelt die Kunden, die mit höherer Wahrscheinlichkeit ein Fahrrad kaufen werden. Sie können das **Gewinndiagramm** verwenden, um die Anzahl der Kunden zu ermitteln, die mit dem Ziel der Gewinnmaximierung selektiv angesprochen werden sollten.  
  
 Wenn Sie nicht über das Beispielmodell verfügen, können Sie es mit dem Lernprogramm zu [Data Mining-Grundlagen](../../tutorials/basic-data-mining-tutorial.md)erstellen.  
  
1.  Öffnen Sie den Generator für Mininggenauigkeitsdiagramme.  
  
    -   Klicken Sie in SQL Server Management Studio mit der rechten Maustaste auf das Modell, und wählen Sie **Prognosegütediagramm anzeigen**aus.  
  
    -   Öffnen Sie in SQL Server Data Tools das Projekt, in dem Sie das Modell erstellt haben, und klicken Sie auf die Registerkarte **Mininggenauigkeitsdiagramm** .  
  
2.  Wählen Sie auf der Registerkarte **Eingabeauswahl** erst das Modell und dann den vorhersagbaren Attributwert aus.  
  
     In diesem Szenario interessieren Sie sich ausschließlich für die Gewinnsteigerung, die sich aus einem präzise vorhergesagten Wert ergibt, und zwar [Bike Buyer] =1.  
  
     In anderen Szenarien könnte es aber auch interessant sein, falsche Werte (negative Kosten) präzise vorherzusagen. Falsch-positive Werte bei einem medizinischen Diagnosetest können beispielsweise erhebliche Kosten verursachen. Diese müssen bei der Schätzung der Gewinnsteigerung genauso wie die Kosten falsch-negativer Ergebnisse berücksichtigt werden. In einem solchen Szenario würden Sie keinen bestimmten Wert angeben, sondern sämtliche Ergebnisse messen.  
  
3.  Wählen Sie ein Dataset für Testzwecke aus. In diesem Beispiel wählen Sie das Testdataset ("Testing") aus.  
  
4.  Klicken Sie dann auf die Registerkarte **Prognosegütediagramm** .  
  
     Ein Prognosegütediagramm wird automatisch generiert.  
  
5.  Um dieses Diagramm in ein Gewinndiagramm zu ändern, wählen Sie aus der Liste **Diagrammtyp** die Option **Gewinndiagramm** aus.  
  
6.  Sobald Sie ein Gewinndiagramm als Diagrammtyp auswählen, wird automatisch das Dialogfeld **Gewinndiagrammeinstellungen** geöffnet.  
  
     In diesem Dialogfeld können Sie Kosten und Nutzen einer Targeted Mailing-Kampagne angeben. Für das in diesen Beispielen gezeigte Diagramm wurden die folgenden Werte verwendet:  
  
    |Einstellung|value|Kommentare|  
    |-------------|-----------|--------------|  
    |**Bevölkerungs**|20.000|Festlegen des Werts für die gesamte Zielpopulation<br /><br /> Die Datenbank kann zahlreiche Kunden umfassen. Da Sie die Versandkosten jedoch eindämmen möchten, sprechen Sie gezielt die 20.000 Kunden an, bei denen am wahrscheinlichsten mit einer Antwort zu rechnen ist. Sie können diese Liste abrufen, indem Sie eine Vorhersageabfrage ausführen und diese nach den Wahrscheinlichkeitsangaben des Vorhersagemodells sortieren.|  
    |**Festes Kosten**|500|Geben Sie die einmaligen Kosten ein, die mit einer zielgerichteten Mailingkampagne für 20.000 Kunden verbunden sind. Darunter fallen beispielsweise Druckkosten oder der Kostenaufwand für die Vorbereitung der E-Mail-Kampagne.|  
    |**Einzelkosten**|3|Geben Sie die Kosten für die Targeted Mailing-Kampagne pro Einheit ein.<br /><br /> Dieser Betrag wird mit einer Zahl kleiner oder gleich 20.000 multipliziert, je nachdem, wie viele Kunden vom Modell als potenzielle Kunden vorhergesagt werden.|  
    |**Umsatz pro Einzelperson**|400|Geben Sie einen Wert für die bei einem erfolgreichen Ergebnis zu erwartenden Gewinne oder Einkünfte ein. In diesem Fall gehen wir davon aus, dass das Versenden eines Katalogs den Kauf von Zubehör oder Fahrrädern im Mittelwert von $400 ergibt.<br /><br /> Dieser Betrag wird zum Projizieren des Gesamtgewinns bei Fällen mit einer hohen Wahrscheinlichkeit verwendet.|  
  
7.  Nachdem Sie die erforderlichen Parameter festgelegt haben, klicken Sie auf **OK**.  
  
8.  Das Diagramm wird aktualisiert, um die Gewinnkurve anzuzeigen.  
  
## <a name="understanding-the-profit-chart"></a>Grundlegendes zum Gewinndiagramm  
 Im Folgenden ist ein auf diesen Parametern basierendes Diagramm dargestellt. Auf der Y-Achse des Diagramms ist der Gewinn dargestellt, während auf der X-Achse der prozentuale Anteil der Kunden dargestellt wird, die im Rahmen der Mailingkampagne gezielt angesprochen wurden.  
  
 Wie hier ersichtlich, kann ein Gewinndiagramm zum Vergleichen mehrerer Modelle verwendet werden, solange alle das gleiche diskrete Attribut vorhersagen.  
  
 ![ein Gewinndiagramm mit einem Vergleich von drei Modellen](../media/dm14-profitchartupdated.gif "ein Gewinndiagramm mit einem Vergleich von drei Modellen")  
  
 Beachten Sie die graue vertikale Linie im Diagramm. Wenn Sie auf die Linie klicken und sie ziehen, wird in der QuickInfo der Prozentsatz der Zielpopulation angezeigt, der der Kurve an diesem Punkt zugrunde liegt.  
  
 Während Sie die Linie ziehen, wird die **Mininglegende** ebenfalls aktualisiert, um den Prozentwert, eine Gewinnauswertung und die Vorhersagewahrscheinlichkeit für den Populationsprozentsatz an der vertikalen grauen Linie anzuzeigen.  
  
 Wenn Sie anhand dieses Modells beispielsweise ermitteln möchten, an welche Kunden Sie gezielt Werbematerialien schicken sollten, können Sie sich auf 25 % der Population festlegen. Diese 25 % werden nach der Vorhersagewahrscheinlichkeit ausgewählt. Der Bereich unter der Gewinnkurve des Diagramms ist jedoch zwischen 40 und 70 Prozent am größten. Das deutet darauf hin, dass Sie den Gewinn maximieren können, wenn Sie mehr Kunden gezielt ansprechen. Das trifft auch dann zu, wenn insgesamt nur ein kleinerer Gesamtprozentsatz antwortet.  
  
## <a name="saving-charts"></a>Speichern von Diagrammen  
 Beim Erstellen eines Genauigkeits- oder Gewinndiagramms werden keine Objekte auf dem Server erstellt. Stattdessen werden Abfragen für ein vorhandenes Modell ausgeführt und die Ergebnisse im Viewer gerendert. Um die Ergebnisse zu speichern, müssen Sie entweder das Diagramm oder die Ergebnisse in Excel bzw. ein anderes Dateiformat kopieren.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Die folgenden Themen enthalten weitere Informationen zum Erstellen und Verwenden von Genauigkeitsdiagrammen.  
  
|Themen|Links|  
|------------|-----------|  
|Bietet eine exemplarische Vorgehensweise zum Erstellen eines Prognosegütediagramms für das Targeted Mailing-Modell.|[Lernprogramm zu Data Mining-Grundlagen](../../tutorials/basic-data-mining-tutorial.md)<br /><br /> [Testen der Genauigkeit mit Lift Charts &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)|  
|Erläutert verwandte Diagrammtypen.|[Lift Chart &#40;Analysis Services-Data Mining-&#41;](lift-chart-analysis-services-data-mining.md)<br /><br /> [Klassifizierungs Matrix &#40;Analysis Services Data Mining-&#41;](classification-matrix-analysis-services-data-mining.md)<br /><br /> [Punkt Diagramm &#40;Analysis Services-Data Mining-&#41;](scatter-plot-analysis-services-data-mining.md)|  
|Beschreibt die Kreuzvalidierung für Miningmodelle und Miningstrukturen.|[Übergreifende Überprüfung &#40;Analysis Services Data Mining-&#41;](cross-validation-analysis-services-data-mining.md)|  
|Beschreibt Schritte zum Erstellen von Prognosegütediagrammen und anderen Genauigkeitsdiagrammen.|[Test-und validierungsaufgaben und Anleitungen &#40;Data Mining-&#41;](testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Testen und validieren &#40;Data Mining-&#41;](testing-and-validation-data-mining.md)   
 [Testen der Genauigkeit mit Lift Charts &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
  
