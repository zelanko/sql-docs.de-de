---
title: Genauigkeitsdiagramm (SQL Server Data Mining-Add-ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- mining models, validating
- mining models, charting
- lift chart
- mining models, testing
- lift [data mining]
ms.assetid: 303973b4-71c0-4cfc-b7bc-92218b52509d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 328ce6c6474beb68d14edd26779d868142a29fd0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48136796"
---
# <a name="accuracy-chart-sql-server-data-mining-add-ins"></a>Genauigkeitsdiagramm (SQL Server Data Mining-Add-Ins)
  ![Genauigkeit diagrammschaltfläche im Data Mining-Menüband](media/dmc-accchart.gif "Schaltfläche \"Genauigkeitsdiagramm\" im Data Mining-Menüband")  
  
 Mit einem Genauigkeitsdiagramm können Sie ein Modell auf ein neues Dataset anwenden und anschließend bewerten, wie leistungsfähig das Modell ist. Vom Assistenten erstellte Genauigkeitsdiagramm ist ein *prognosegütediagramm*, d.h. eine Art von Diagramm, das häufig verwendet wird, um die Genauigkeit von Datamining-Modells messen. Bei diesem Genauigkeitsdiagrammtyp handelt es sich um eine grafische Darstellung der Verbesserung, die Sie durch das Verwenden des angegebenen Data Mining-Modells im Vergleich zu Vorhersagen nach dem Zufallsprinzip und dem Idealfall erhalten, dass 100 Prozent der Vorhersagen genau sind. Sie können mehrere Modelle in einem Diagramm vergleichen.  
  
## <a name="example"></a>Beispiel  
 Angenommen, die Marketingabteilung von Adventure Works Cycles möchte eine zielgerichtete Mailingkampagne starten. Aus vergangenen Kampagnen weiß man, dass typischerweise mit einer Antwortquote von 10 Prozent zu rechnen ist. Eine Liste mit 10.000 potenziellen Kunden ist in einer Tabelle in der Datenbank gespeichert. Ausgehend von der typischen Antwortquote ist zu erwarten, dass 1.000 Kunden antworten.  
  
 Da die Werbung jedoch nur an 5.000 Kunden gesendet werden kann, verwendet die Marketingabteilung ein Miningmodell, um die 5.000 Kunden auszuwählen, die am wahrscheinlichsten auf die Werbung reagieren werden.  
  
 Bei einer willkürlichen Auswahl von 5.000 Kunden kann das Unternehmen nur mit 500 positiven Antworten rechnen, da in der Regel nur 10 Prozent der Zielgruppe antworten. Dieses Szenario wird von der Zufallslinie im Prognosegütediagramm dargestellt.  
  
 Wenn die Marketingabteilung für das gezielte Mailing jedoch ein Miningmodell verwendet, könnte sie im Fall eines perfekten Modells damit rechnen, von allen 1.000 kontaktierten Kunden, die vom Modell empfohlen wurden, Antworten zu erhalten. Dieses Szenario wird von der Ideallinie im Prognosegütediagramm dargestellt.  
  
## <a name="using-the-accuracy-chart-wizard"></a>Verwenden des Genauigkeitsdiagramm-Assistenten  
 Beim Erstellen eines Genauigkeitsdiagramms müssen Sie auf eine bereits vorhandene Data Mining-Struktur verweisen. Sie können die Genauigkeit mehrerer Modelle messen, die auf dieser Struktur basieren, sofern sie das Gleiche vorhersagen.  
  
 Wenn Sie nicht sicher sind, welche Strukturen verfügbar sind, können Sie den Server durchsuchen. Weitere Informationen finden Sie unter [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).  
  
#### <a name="to-create-an-accuracy-chart"></a>So erstellen Sie ein Genauigkeitsdiagramm  
  
1.  Klicken Sie auf die **Data Mining-Client** Menüband.  
  
2.  In der **Genauigkeit und Überprüfung** auf **Genauigkeitsdiagramm**.  
  
3.  In der **Struktur oder Modell auswählen** Dialogfeld Wählen Sie das Modell, das Sie auswerten möchten. Klicken Sie auf **Weiter**.  
  
    > [!NOTE]  
    >  Sie müssen ein Modell auswählen, das weitgehend mit den Daten übereinstimmt, die Sie überprüfen möchten.  
  
4.  In der **geben vorherzusagende Spalte und vorherzusagenden Wert** Dialogfeld auf die Spalte, die Sie vorhersagen möchten, und einem Zielwert, falls zutreffend. Klicken Sie auf **Weiter**.  
  
     Im Beispiel oben könnten Sie beispielsweise die Spalte auswählen, die die Kundenreaktion wiedergibt, und den Zielwert als "Wird wahrscheinlich kaufen" festlegen.  
  
    > [!NOTE]  
    >  Für kontinuierliche Werte können Sie keine Vorhersage erstellen. Sie können jedoch die Spalte diskretisieren, indem Sie die Werte in diskrete Wertebereiche aufteilen. Dies müssen Sie tun, bevor Sie das Data Mining-Modell erstellen.  
  
5.  In der **Quelldaten auswählen** Dialogfeld geben die Quelle der Daten, die Sie über das Modell übergeben werden, um eine Vorhersage zu erstellen.  
  
6.  Bei Verwendung eine externe Quelle von Daten und nicht die Testdaten, die mit dem Modell gespeichert sind, in der **Beziehung angeben** Dialogfeld Zuordnung die Spalten in der neuen Datenquelle den Spalten ein, die im Datamining-Modell.  
  
     Wenn sich die Spaltennamen ähneln, werden sie automatisch vom Assistenten zugeordnet. Manche Spalten der Eingabedaten sind möglicherweise irrelevant für die Analyse und können deshalb ignoriert werden. Bestimmte Spalten sind jedoch erforderlich, damit die Eingabe vom Data Mining-Modell verarbeitet werden kann. Bei diesen Spalten handelt es sich möglicherweise um eine Transaktions-ID, den Zielwert oder Spalten, die für die Vorhersage verwendet werden. Wenn Sie eine erforderliche Spalte nicht zuordnen, gibt der Assistent eine Warnmeldung aus.  
  
7.  Klicken Sie auf **Fertig stellen**.  
  
     Der Assistent erstellt einen Bericht, der das Prognosegütediagramm und zugrunde liegende Daten enthält.  
  
### <a name="requirements"></a>Anforderungen  
 Wenn Sie einen diskreten Wert vorhersagen, müssen Sie den Zielwert auswählen, den Sie vorhersagen möchten. Wenn Ihre Daten beispielsweise mit einer Antwort "Ja: Kaufen" als 1 und der Antwort "Nein: Nicht kaufen" als 2 kategorisiert werden, müssen Sie 1 oder 2 als Vorhersagewerte festlegen. Wenn Sie jedoch einen Wertebereich vorhersagen möchten, können Sie nur zwei Werte gleichzeitig vergleichen. Wenn Sie beispielsweise ein Ergebnis über 5 vorhersagen möchten, müssen Sie Ihre Quelldaten möglicherweise neu bezeichnen und ein neues Modell erstellen, in dem die Ergebnisse in zwei Gruppen aufgeteilt werden: größer als 5 und kleiner als 5 Anschließend können Sie die Genauigkeit dieser beiden Gruppen vergleichen.  
  
## <a name="understanding-accuracy"></a>Grundlegendes zur Genauigkeit  
 Sie können zwei Arten von Diagrammen erstellen: ein Diagramm, in dem Sie einen Status der vorhersagbaren Spalte angeben, und eines, in dem Sie den Status nicht angeben.  
  
 Wenn Sie den Status der vorhersagbaren Spalte angeben, stellt die X-Achse des Diagramms den Prozentsatz des Testdatasets dar, das zum Vergleichen der Vorhersagen verwendet wird. Die Y-Achse des Diagramms stellt den Prozentsatz der Werte dar, die für den angegebenen Status vorhergesagt werden.  
  
 Wenn Sie für den Status der vorhersagbaren Spalte nichts angeben, zeigt das Diagramm die Genauigkeit des Modells für alle möglichen Vorhersagen an.  
  
 Weitere Informationen zur Funktionsweise eines Prognosegütediagramms und zur Berechnung der Genauigkeit anhand der zufälligen und idealen Vorhersagezeilen finden Sie im Thema "Prognosegütediagramm" in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Validieren von Modellen und Verwenden von Modellen für Vorhersagen &#40;Data Mining-Add-ins für Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
