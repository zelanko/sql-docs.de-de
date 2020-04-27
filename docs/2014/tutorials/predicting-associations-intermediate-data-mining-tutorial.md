---
title: Vorhersagen von Zuordnungen (Data Mining-Tutorial für Fortgeschrittene) Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9140c5f2-b340-45a6-9c27-d870d15aafea
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bee5ca4ded1b2fd5cbda0712cb766c825b9d0318
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62472845"
---
# <a name="predicting-associations-intermediate-data-mining-tutorial"></a>Vorhersagen von Zuordnungen (Data Mining-Lernprogramm für Fortgeschrittene)
  Im Anschluss an die Verarbeitung der Modelle können Sie anhand der Informationen über Zuordnungen, die im Modell gespeichert sind, Vorhersagen erstellen. In der abschließenden Aufgabe der Lektion lernen Sie, Vorhersageabfragen auf Basis der erstellten Zuordnungsmodelle zu erstellen. In dieser Lektion wird davon ausgegangen, dass Sie mit der Verwendung des Generators für Vorhersageabfragen vertraut sind und lernen möchten, wie Vorhersageabfragen für Zuordnungsmodelle erstellt werden. Weitere Informationen zur Verwendung von Vorhersage Abfrage-Generator finden Sie unter [Data Mining-Abfrageschnittstellen](../../2014/analysis-services/data-mining/data-mining-query-tools.md).  
  
## <a name="creating-a-singleton-prediction-query"></a>Erstellen einer SINGLETON-Vorhersageabfrage  
 Vorhersageabfragen für ein Zuordnungsmodell können sehr nützlich sein:  
  
-   Empfehlen Sie einem Kunden Artikel auf der Grundlage früherer oder verwandter Käufe.  
  
-   Suchen Sie verwandte Ereignisse.  
  
-   Identifizieren Sie Beziehungen in oder zwischen Transaktionen.  
  
 Um eine Vorhersageabfrage zu erstellen, wählen Sie zuerst das gewünschte Zuordnungsmodell aus und geben dann die Eingabedaten an. Eingabedaten können aus einer externen Datenquelle wie einer Werteliste stammen, oder Sie können eine SINGLETON-Abfrage erstellen und dabei Werte bereitstellen.  
  
 In diesem Szenario erstellen Sie zunächst einige SINGLETON-Vorhersageabfragen, um eine Vorstellung der Funktionsweise von Vorhersageabfragen zu erhalten. Anschließend erstellen Sie eine Abfrage für Batchvorhersagen, mit der Empfehlungen ausgesprochen werden können, die auf den aktuellen Einkäufen von Kunden basieren.  
  
#### <a name="to-create-a-prediction-query-on-an-association-model"></a>So erstellen Sie eine Vorhersageabfrage für ein Zuordnungsmodell  
  
1.  Klicken Sie im Data Mining-Designer auf die Registerkarte **Mining Modellvorhersage** .  
  
2.  Klicken Sie im Bereich **Mining Modell** auf **Modell auswählen**. (Sie können diesen Schritt und den nächsten Schritt überspringen, wenn das richtige Modell bereits ausgewählt wurde.)  
  
3.  Erweitern Sie im Dialogfeld **Mining Modell auswählen** den **Knoten, der die Mining Struktur Zuordnung**darstellt, und wählen Sie die **Modell Zuordnung**aus. Klicken Sie auf **OK**.  
  
     Den Eingabebereich können Sie zunächst ignorieren.  
  
4.  Klicken Sie im Raster unter **Quelle** auf die leere Zelle, und wählen Sie **Vorhersagefunktion aus.** Wählen Sie `PredictAssociation`in der Zelle unter **Feld**den Wert aus.  
  
     Sie können auch die **Vorhersage** Funktion verwenden, um Zuordnungen vorherzusagen. Wenn Sie dies tun, achten Sie darauf, dass Sie die Version der **Vorhersage** Funktion auswählen, die eine Tabellenspalte als Argument annimmt.  
  
5.  Wählen Sie im Bereich **Mining Modell** die Tabelle `vAssocSeqLineItems`aus, und ziehen Sie Sie in das Raster, in das Feld **Kriterium/Argument** für die `PredictAssociation` Funktion.  
  
     Das Ziehen und Ablegen von Tabellen- und Spaltennamen ermöglicht es Ihnen, komplexe Anweisungen ohne Syntaxfehler zu erstellen. Allerdings ersetzt Sie den aktuellen Inhalt der Zelle, die andere optionale Argumente für die `PredictAssociation` Funktion enthält. Wenn Sie die anderen Argumente anzeigen möchten, können Sie dem Raster vorübergehend eine zweite Instanz der Funktion als Referenz hinzufügen.  
  
6.  Klicken Sie auf das Feld **Kriterium/Argument** , und geben Sie den folgenden Text nach dem Tabellennamen ein:`,3`  
  
     Der vollständige Text im Feld **Kriterium/Argument** sollte wie folgt lauten:  
  
     `[Association].[v Assoc Seq Line Items],3`  
  
7.  Klicken Sie in der oberen Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **Ergebnisse** .  
  
 Die erwarteten Ergebnisse enthalten eine einzelne Spalte mit dem Überschriften **Ausdruck**. Die Spalte **Ausdruck** enthält eine Tabelle mit einer einzelnen Spalte und den folgenden drei Zeilen. Da Sie keinen Eingabewert angegeben haben, stellen die Vorhersagen die wahrscheinlichsten Produktzuordnungen für das gesamte Modell dar.  
  
|Modell|  
|-----------|  
|Women's Mountain Shorts|  
|Water Bottle|  
|Touring-3000|  
  
 Im nächsten Schritt verwenden Sie den **Eingabebereich SINGLETON-Abfrage** , um ein Produkt als Eingabe für die Abfrage anzugeben, und Sie können die Produkte anzeigen, die diesem Element am wahrscheinlichsten zugeordnet sind.  
  
#### <a name="to-create-a-singleton-prediction-query-with-nested-table-inputs"></a>So erstellen Sie eine Singleton-Vorhersageabfrage mit Eingaben für geschachtelte Tabellen  
  
1.  Klicken Sie in der Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **Entwurf** , um zum Raster für die Abfrage Erstellung zurückzukehren.  
  
2.  Wählen Sie im Menü **Mining Modell** die Option **Singleton-Abfrage**aus.  
  
3.  Wählen **Sie im Dialog** Feld **Mining Modell** das Zuordnungs Modell aus.  
  
4.  Klicken Sie im Raster unter **Quelle** auf die leere Zelle, und wählen Sie **Vorhersagefunktion aus.** Wählen Sie `PredictAssociation`in der Zelle unter **Feld**den Wert aus.  
  
5.  Wählen Sie im Bereich **Mining Modell** die Tabelle `vAssocSeqLineItems`aus, und ziehen Sie Sie in das Raster, in das Feld **Kriterium/Argument** für die `PredictAssociation` Funktion. Geben `,3` Sie nach dem Namen der Tabellen Tabelle wie in der vorherigen Prozedur ein.  
  
6.  Klicken Sie im Dialogfeld **Singleton-Abfrage Eingabe** auf das Feld **Wert** neben **vAssoc-Zeilen Elemente**, und klicken Sie dann auf die Schaltfläche **(...)** .  
  
7.  Wählen `Touring Tire` Sie im Dialogfeld **Eingabe der eingefügten Tabelle** im Bereich **Schlüssel Spalte** aus, und klicken Sie dann auf **Hinzufügen**.  
  
8.  Klicken Sie auf die Schaltfläche **Ergebnisse** .  
  
 Die Ergebnisse zeigen nun die Vorhersagen für Produkte an, die höchstwahrscheinlich Touring Tire zugeordnet sind.  
  
|Modell|  
|-----------|  
|Touring Tire Tube|  
|Sport-100|  
|Water Bottle|  
  
 Aus Ihrer Untersuchung des Modells wissen Sie jedoch bereits, dass die Produkte Touring Tire Tube und Touring Tire von Kunden häufig zusammen gekauft werden. Sie möchten vielmehr wissen, welche anderen Produkte Sie diesen Kunden empfehlen können. Sie ändern die Abfrage daher so, dass verwandte Produkte anhand der Elemente vorhergesagt werden, die sich im Einkaufskorb befinden. Außerdem ändern Sie die Abfrage, um die Wahrscheinlichkeit für jedes vorhergesagte Produkt hinzuzufügen.  
  
#### <a name="to-add-inputs-and-probabilities-to-the-singleton-prediction-query"></a>So fügen Sie der Singleton-Vorhersageabfrage Eingaben und Wahrscheinlichkeiten hinzu  
  
1.  Klicken Sie in der Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **Entwurf** , um zum Raster für die Abfrage Erstellung zurückzukehren.  
  
2.  Klicken Sie im Dialogfeld **Singleton-Abfrage Eingabe** auf das Feld **Wert** neben **vAssoc-Zeilen Elemente**, und klicken Sie dann auf die Schaltfläche **(...)** .  
  
3.  Wählen Sie `Touring Tire`im Bereich **Schlüssel Spalte** die Option aus, und klicken Sie dann auf **Hinzufügen**.  
  
4.  Klicken Sie im Raster unter **Quelle** auf die leere Zelle, und wählen Sie **Vorhersagefunktion aus.** Wählen Sie `PredictAssociation`in der Zelle unter **Feld**den Wert aus.  
  
5.  Wählen Sie im Bereich **Mining Modell** die Tabelle `vAssocSeqLineItems`aus, und ziehen Sie Sie in das Raster, in das Feld **Kriterium/Argument** für die `PredictAssociation` Funktion. Geben `,3` Sie nach dem Namen der Tabellen Tabelle wie in der vorherigen Prozedur ein.  
  
6.  Wählen `Touring Tire Tube` Sie im Dialogfeld **Eingabe der eingefügten Tabelle** im Bereich **Schlüssel Spalte** aus, und klicken Sie dann auf **Hinzufügen**.  
  
7.  Klicken Sie im Raster in der Zeile für die `PredictAssociation` Funktion auf das Feld **Kriterium/Argument** , und ändern Sie die Argumente, um das Argument INCLUDE_STATISTICS hinzuzufügen.  
  
     Der vollständige Text im Feld **Kriterium/Argument** sollte wie folgt lauten:  
  
     `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`  
  
8.  Klicken Sie auf die Schaltfläche **Ergebnisse** .  
  
 Die Ergebnisse in der geschachtelten Tabelle werden geändert, und die Vorhersagen werden mit Unterstützung und Wahrscheinlichkeit angezeigt. Weitere Informationen zum Interpretieren dieser Werte finden Sie unter [Mining Modell Inhalt von Zuordnungs Modellen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).  
  
|Modell|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0,291...|0,252...|  
|Water Bottle|2866|0,192...|0,175...|  
|Patchkit|2113|0,142...|0,132|  
  
## <a name="working-with-results"></a>Arbeiten mit Ergebnissen  
 Wenn Ihre Ergebnisse eine große Zahl von geschachtelten Tabellen enthalten, können Sie diese vereinfachen, um die Anzeige übersichtlicher zu gestalten. Dazu können Sie die Abfrage manuell ändern und das `FLATTENED`-Schlüsselwort hinzufügen.  
  
#### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a>So vereinfachen Sie geschachtelte Rowsets in einer Vorhersageabfrage  
  
1.  Klicken Sie in der Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **SQL** .  
  
     Das Raster ändert sich in einen offenen Bereich, in dem Sie die DMX-Anweisung anzeigen und ändern können, die Sie mit dem Generator für Vorhersageabfragen erstellt haben.  
  
2.  Geben Sie nach dem `SELECT`-Schlüsselwort `FLATTENED` ein.  
  
     Der vollständige Text der Abfrage sollte wie folgt lauten:  
  
    ```  
    SELECT FLATTENED  
      PredictAssociation([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,3)  
    FROM  
      [Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Touring Tire' AS [Model]  
      UNION SELECT 'Touring Tire Tube' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
    ```  
  
3.  Klicken Sie in der oberen Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **Ergebnisse** .  
  
 Nach dem manuellen Bearbeiten einer Abfrage können Sie nicht mehr zur Entwurfsansicht zurückkehren, ohne dass Ihre Änderungen verloren gehen. Wenn Sie die Abfrage speichern möchten, können Sie die manuell erstellte DMX-Anweisung in eine Textdatei kopieren. Wenn Sie zur Entwurfsansicht zurückkehren, wird die Abfrage auf die letzte gültige Version in der Entwurfsansicht zurückgesetzt.  
  
## <a name="creating-multiple-predictions"></a>Erstellen von mehreren Vorhersagen  
 Angenommen, Sie möchten die besten Vorhersagen für einzelne Kunden auf Basis ihrer vergangenen Käufe erstellen. Als Eingabe für eine solche Vorhersageabfrage können Sie externe Daten wie Tabellen mit der Kunden-ID und den letzten Produktkäufen verwenden. Diese Datentabellen müssen bereits als Analysis Services-Datenquellensichten definiert worden sein, und die Eingabedaten müssen Falltabellen und geschachtelte Tabellen analog zu den Modelltabellen enthalten. Die Tabellen müssen nicht den gleichen Namen, jedoch eine ähnliche Struktur aufweisen. In diesem Lernprogramm verwenden Sie die ursprünglichen Tabellen, die zum Trainieren des Modells verwendet wurden.  
  
#### <a name="to-change-the-input-method-for-the-prediction-query"></a>So ändern Sie die Eingabemethode für die Vorhersageabfrage  
  
1.  Wählen Sie im Menü **Mining Modell** erneut **Singleton-Abfrage** aus, um das Häkchen zu löschen.  
  
2.  Es wird eine Warnmeldung angezeigt, die Sie darüber informiert, dass die SINGLETON-Abfrage verloren geht. Klicken Sie auf **Ja**.  
  
     Der Name des Eingabe Dialogfelds ändert sich in **Eingabe Tabelle (n) auswählen**.  
  
 Da Sie eine Vorhersageabfrage erstellen möchten, die die Customer ID sowie eine Liste der Produkte als Eingabe bereitstellt, fügen Sie die Kundentabelle als Falltabelle hinzu und die Tabelle mit den von Kunden getätigten Käufen als geschachtelte Tabelle. Anschließend fügen Sie Vorhersagefunktionen hinzu, um Empfehlungen zu erstellen.  
  
#### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a>So erstellen Sie eine Vorhersageabfrage mit Eingaben für geschachtelte Tabellen  
  
1.  Wählen Sie im Bereich Miningmodell das Modell Association Filtered aus.  
  
2.  Klicken Sie im Dialogfeld **Eingabe Tabelle (n) auswählen** auf **Fall Tabelle auswählen**.  
  
3.  Wählen Sie im Dialogfeld **Tabelle auswählen** für **Datenquelle**die Option AdventureWorksDW2008 aus. Wählen Sie in der Liste **Tabellen-/Sichtname** den Eintrag vassocsqorders aus, und klicken Sie dann auf **OK**.  
  
     Die Tabelle vAssocSeqOrders wird dem Bereich hinzugefügt.  
  
4.  Klicken Sie im Dialogfeld **Eingabe Tabelle (n) auswählen** auf **Tabelle auswählen**.  
  
5.  Wählen Sie im Dialogfeld **Tabelle auswählen** für **Datenquelle**die Option AdventureWorksDW2008 aus. Wählen Sie in der Liste **Tabellen-/Sichtname** den Eintrag vassocsetqlineitems aus, und klicken Sie dann auf **OK**.  
  
     Die Tabelle vAssocSeqLineItems wird dem Bereich hinzugefügt.  
  
6.  Ziehen Sie im Dialogfeld für den verknüpften **Join angeben** das Feld OrderNumber aus der Fall Tabelle, und legen Sie es auf dem Feld OrderNumber in der Tabelle in der Tabelle ab.  
  
     Sie können auch auf **Beziehung hinzufügen** klicken und die Beziehung erstellen, indem Sie Spalten aus einer Liste auswählen.  
  
7.  Überprüfen Sie im Dialogfeld **Beziehung angeben** , ob die Felder OrderNumber ordnungsgemäß zugeordnet sind, und klicken Sie dann auf **OK**.  
  
8.  Klicken Sie auf **OK** , um das Dialogfeld verknüpften **Join angeben** zu schließen.  
  
     Die Falltabelle und die geschachtelte Tabelle werden im Entwurfsbereich aktualisiert, um die Joins zwischen den externen Datenspalten und den Spalten im Modell anzuzeigen. Wenn die Beziehungen falsch sind, klicken Sie mit der rechten Maustaste auf die Joinlinie, und wählen Sie **Verbindungen ändern** aus, um die Spalten Zuordnung zu bearbeiten. Sie können auch mit der rechten Maustaste auf die Joinlinie klicken und **Löschen** auswählen, um die Beziehung vollständig zu entfernen  
  
9. Fügen Sie dem Raster eine neue Zeile hinzu. Wählen Sie für **Quelle**die Option **vassocabqorders-Tabelle**aus. Wählen Sie für **Feld**die Option CustomerKey aus.  
  
10. Fügen Sie dem Raster eine neue Zeile hinzu. Wählen Sie für **Quelle**die Option **vassocabqorders-Tabelle**aus. Wählen Sie für **Feld**die Option Region aus.  
  
11. Fügen Sie dem Raster eine neue Zeile hinzu. Wählen Sie für **Quelle**die Option **Vorhersagefunktion**aus, und `PredictAssociation`wählen Sie für **Feld**aus.  
  
12. Ziehen Sie vassoccot qlineitems in das Feld **Kriterium/Argument** der `PredictAssociation` Zeile. Klicken Sie am Ende des Felds **Kriterium/Argument** , und geben Sie dann den folgenden Text ein:`INCLUDE_STATISTICS,3`  
  
     Der vollständige Text im Feld **Kriterium/Argument** sollte wie folgt lauten:`[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`  
  
13. Klicken Sie auf die Schaltfläche **Ergebnis** , um die Vorhersagen für jeden Kunden anzuzeigen.  
  
 Sie können versuchen, eine ähnliche Vorhersageabfrage für mehrere Modelle zu erstellen, um mögliche Auswirkungen von Filteränderungen auf die Vorhersageergebnisse zu überprüfen. Weitere Informationen zum Erstellen von Vorhersagen und anderen Abfrage Typen finden Sie unter Beispiele für Zuordnungs [Modell Abfragen](../../2014/analysis-services/data-mining/association-model-query-examples.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Modell Inhalt von Zuordnungs Modellen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)   
 [Prätassociation &#40;DMX-&#41;](/sql/dmx/predictassociation-dmx)   
 [erstellt eine Vorhersage mithilfe des Generators für Vorhersageabfragen](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
