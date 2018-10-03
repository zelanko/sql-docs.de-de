---
title: Vorhersagen von Zuordnungen (mittleres Datamining Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 9140c5f2-b340-45a6-9c27-d870d15aafea
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 09084760637464c5e985eeb17762959c8576c5ae
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222804"
---
# <a name="predicting-associations-intermediate-data-mining-tutorial"></a>Vorhersagen von Zuordnungen (Data Mining-Lernprogramm für Fortgeschrittene)
  Im Anschluss an die Verarbeitung der Modelle können Sie anhand der Informationen über Zuordnungen, die im Modell gespeichert sind, Vorhersagen erstellen. In der abschließenden Aufgabe der Lektion lernen Sie, Vorhersageabfragen auf Basis der erstellten Zuordnungsmodelle zu erstellen. In dieser Lektion wird davon ausgegangen, dass Sie mit der Verwendung des Generators für Vorhersageabfragen vertraut sind und lernen möchten, wie Vorhersageabfragen für Zuordnungsmodelle erstellt werden. Weitere Informationen zum Verwenden des Generators für Vorhersageabfragen finden Sie unter [Data Mining-Abfrageschnittstellen](../../2014/analysis-services/data-mining/data-mining-query-tools.md).  
  
## <a name="creating-a-singleton-prediction-query"></a>Erstellen einer SINGLETON-Vorhersageabfrage  
 Vorhersageabfragen für ein Zuordnungsmodell können sehr nützlich sein:  
  
-   Empfehlen Sie einem Kunden Artikel auf der Grundlage früherer oder verwandter Käufe.  
  
-   Suchen Sie verwandte Ereignisse.  
  
-   Identifizieren Sie Beziehungen in oder zwischen Transaktionen.  
  
 Um eine Vorhersageabfrage zu erstellen, wählen Sie zuerst das gewünschte Zuordnungsmodell aus und geben dann die Eingabedaten an. Eingabedaten können aus einer externen Datenquelle wie einer Werteliste stammen, oder Sie können eine SINGLETON-Abfrage erstellen und dabei Werte bereitstellen.  
  
 In diesem Szenario erstellen Sie zunächst einige SINGLETON-Vorhersageabfragen, um eine Vorstellung der Funktionsweise von Vorhersageabfragen zu erhalten. Anschließend erstellen Sie eine Abfrage für Batchvorhersagen, mit der Empfehlungen ausgesprochen werden können, die auf den aktuellen Einkäufen von Kunden basieren.  
  
#### <a name="to-create-a-prediction-query-on-an-association-model"></a>So erstellen Sie eine Vorhersageabfrage für ein Zuordnungsmodell  
  
1.  Klicken Sie auf die **Miningmodellvorhersage** -Registerkarte des Data Mining-Designers.  
  
2.  In der **Miningmodell** Bereich, klicken Sie auf **Modell auswählen**. (Sie können diesen Schritt und den nächsten Schritt überspringen, wenn das richtige Modell bereits ausgewählt wurde.)  
  
3.  In der **Miningmodell auswählen** Dialogfeld erweitern Sie den Knoten, die Miningstruktur darstellt **Zuordnung**, und wählen Sie das Modell **Zuordnung**. Klicken Sie auf **OK**.  
  
     Den Eingabebereich können Sie zunächst ignorieren.  
  
4.  Klicken Sie im Raster auf die leere Zelle unter **Quelle** , und wählen Sie **Vorhersagefunktion.** In der Zelle unter **Feld**Option `PredictAssociation`.  
  
     Sie können auch die **Predict** Funktion, um Zuordnungen vorherzusagen. Wenn Sie möchten, wählen Sie die Version des sein Zweck der **Predict** Funktion, die eine Tabellenspalte als Argument akzeptiert.  
  
5.  In der **Miningmodell** Bereich Wählen Sie die geschachtelte Tabelle `vAssocSeqLineItems`, und ziehen Sie es in das Raster zu den **Kriterium/Argument** Feld für die `PredictAssociation` Funktion.  
  
     Das Ziehen und Ablegen von Tabellen- und Spaltennamen ermöglicht es Ihnen, komplexe Anweisungen ohne Syntaxfehler zu erstellen. Allerdings ersetzt den aktuellen Inhalt der Zelleninhalt einschließlich anderer optionaler Argumente für die `PredictAssociation` Funktion. Wenn Sie die anderen Argumente anzeigen möchten, können Sie dem Raster vorübergehend eine zweite Instanz der Funktion als Referenz hinzufügen.  
  
6.  Klicken Sie auf die **Kriterium/Argument** ein, und geben Sie den folgenden Text nach dem Tabellennamen: `,3`  
  
     Der vollständige Text im der **Kriterium/Argument** Feld sollte wie folgt lauten:  
  
     `[Association].[v Assoc Seq Line Items],3`  
  
7.  Klicken Sie auf die **Ergebnisse** -Schaltfläche in der oberen Ecke des Generators für Vorhersageabfragen.  
  
 Die erwarteten Ergebnisse enthalten eine einzelne Spalte mit der Überschrift **Ausdruck**. Die **Ausdruck** Spalte enthält eine geschachtelte Tabelle mit einer einzelnen Spalte und die folgenden drei Zeilen. Da Sie keinen Eingabewert angegeben haben, stellen die Vorhersagen die wahrscheinlichsten Produktzuordnungen für das gesamte Modell dar.  
  
|Model|  
|-----------|  
|Women's Mountain Shorts|  
|Water Bottle|  
|Touring-3000|  
  
 Als Nächstes verwenden Sie die **Singleton-Abfrageeingabe** Bereich, um ein Produkt als Eingabe für die Abfrage angeben, und zeigen die Produkte an, die am ehesten mit dem Element verknüpft.  
  
#### <a name="to-create-a-singleton-prediction-query-with-nested-table-inputs"></a>So erstellen Sie eine Singleton-Vorhersageabfrage mit Eingaben für geschachtelte Tabellen  
  
1.  Klicken Sie auf die **Entwurf** Schaltfläche in der Ecke des Generators für Vorhersageabfragen, wechseln zurück zum Raster Erstellen der Abfrage.  
  
2.  Auf der **Miningmodell** , wählen Sie im Menü **Singleton-Abfrage**.  
  
3.  In der **Miningmodell** wählen Sie im Dialogfeld die **Zuordnung** Modell.  
  
4.  Klicken Sie im Raster auf die leere Zelle unter **Quelle** , und wählen Sie **Vorhersagefunktion.** In der Zelle unter **Feld**Option `PredictAssociation`.  
  
5.  In der **Miningmodell** Bereich Wählen Sie die geschachtelte Tabelle `vAssocSeqLineItems`, und ziehen Sie es in das Raster zu den **Kriterium/Argument** Feld für die `PredictAssociation` Funktion. Typ `,3` nach dem Namen der geschachtelten Tabelle genau wie in der vorherigen Prozedur.  
  
6.  In der **Singleton-Abfrageeingabe** im Dialogfeld klicken Sie auf die **Wert** -Feld neben **Vassocseqlineitems**, und klicken Sie dann auf die **(...)**  Schaltfläche.  
  
7.  In der **Eingabe für geschachtelte Tabelle** wählen Sie im Dialogfeld `Touring Tire` in die **Schlüsselspalte** , und klicken Sie dann auf **hinzufügen**.  
  
8.  Klicken Sie auf die **Ergebnisse** Schaltfläche.  
  
 Die Ergebnisse zeigen nun die Vorhersagen für Produkte an, die höchstwahrscheinlich Touring Tire zugeordnet sind.  
  
|Model|  
|-----------|  
|Touring Tire Tube|  
|Sport-100|  
|Water Bottle|  
  
 Aus Ihrer Untersuchung des Modells wissen Sie jedoch bereits, dass die Produkte Touring Tire Tube und Touring Tire von Kunden häufig zusammen gekauft werden. Sie möchten vielmehr wissen, welche anderen Produkte Sie diesen Kunden empfehlen können. Sie ändern die Abfrage daher so, dass verwandte Produkte anhand der Elemente vorhergesagt werden, die sich im Einkaufskorb befinden. Außerdem ändern Sie die Abfrage, um die Wahrscheinlichkeit für jedes vorhergesagte Produkt hinzuzufügen.  
  
#### <a name="to-add-inputs-and-probabilities-to-the-singleton-prediction-query"></a>So fügen Sie der Singleton-Vorhersageabfrage Eingaben und Wahrscheinlichkeiten hinzu  
  
1.  Klicken Sie auf die **Entwurf** Schaltfläche in der Ecke des Generators für Vorhersageabfragen, wechseln zurück zum Raster Erstellen der Abfrage.  
  
2.  In der **Singleton-Abfrageeingabe** im Dialogfeld klicken Sie auf die **Wert** -Feld neben **Vassocseqlineitems**, und klicken Sie dann auf die **(...)**  Schaltfläche.  
  
3.  In der **Schlüsselspalte** wählen Sie im Bereich `Touring Tire`, und klicken Sie dann auf **hinzufügen**.  
  
4.  Klicken Sie im Raster auf die leere Zelle unter **Quelle** , und wählen Sie **Vorhersagefunktion.** In der Zelle unter **Feld**Option `PredictAssociation`.  
  
5.  In der **Miningmodell** Bereich Wählen Sie die geschachtelte Tabelle `vAssocSeqLineItems`, und ziehen Sie es in das Raster zu den **Kriterium/Argument** Feld für die `PredictAssociation` Funktion. Typ `,3` nach dem Namen der geschachtelten Tabelle genau wie in der vorherigen Prozedur.  
  
6.  In der **Eingabe für geschachtelte Tabelle** wählen Sie im Dialogfeld `Touring Tire Tube` in die **Schlüsselspalte** , und klicken Sie dann auf **hinzufügen**.  
  
7.  Im Raster in der Zeile für die `PredictAssociation` funktioniert, klicken Sie auf die **Kriterium/Argument** ein, und ändern Sie die Argumente, um das Argument INCLUDE_STATISTICS hinzuzufügen.  
  
     Der vollständige Text im der **Kriterium/Argument** Feld sollte wie folgt lauten:  
  
     `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`  
  
8.  Klicken Sie auf die **Ergebnisse** Schaltfläche.  
  
 Die Ergebnisse in der geschachtelten Tabelle werden geändert, und die Vorhersagen werden mit Unterstützung und Wahrscheinlichkeit angezeigt. Weitere Informationen zum Interpretieren dieser Werte finden Sie unter [Mingingmodellinhalt von Clustermodellen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).  
  
|Model|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291...|0.252...|  
|Water Bottle|2866|0,192...|0.175...|  
|Patchkit|2113|0,142...|0.132|  
  
## <a name="working-with-results"></a>Arbeiten mit Ergebnissen  
 Wenn Ihre Ergebnisse eine große Zahl von geschachtelten Tabellen enthalten, können Sie diese vereinfachen, um die Anzeige übersichtlicher zu gestalten. Dazu können Sie die Abfrage manuell ändern und das `FLATTENED`-Schlüsselwort hinzufügen.  
  
#### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a>So vereinfachen Sie geschachtelte Rowsets in einer Vorhersageabfrage  
  
1.  Klicken Sie auf die **SQL** Schaltfläche in der Ecke des Generators für Vorhersageabfragen.  
  
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
  
3.  Klicken Sie auf die **Ergebnisse** -Schaltfläche in der oberen Ecke des Generators für Vorhersageabfragen.  
  
 Nach dem manuellen Bearbeiten einer Abfrage können Sie nicht mehr zur Entwurfsansicht zurückkehren, ohne dass Ihre Änderungen verloren gehen. Wenn Sie die Abfrage speichern möchten, können Sie die manuell erstellte DMX-Anweisung in eine Textdatei kopieren. Wenn Sie zur Entwurfsansicht zurückkehren, wird die Abfrage auf die letzte gültige Version in der Entwurfsansicht zurückgesetzt.  
  
## <a name="creating-multiple-predictions"></a>Erstellen von mehreren Vorhersagen  
 Angenommen, Sie möchten die besten Vorhersagen für einzelne Kunden auf Basis ihrer vergangenen Käufe erstellen. Als Eingabe für eine solche Vorhersageabfrage können Sie externe Daten wie Tabellen mit der Kunden-ID und den letzten Produktkäufen verwenden. Diese Datentabellen müssen bereits als Analysis Services-Datenquellensichten definiert worden sein, und die Eingabedaten müssen Falltabellen und geschachtelte Tabellen analog zu den Modelltabellen enthalten. Die Tabellen müssen nicht den gleichen Namen, jedoch eine ähnliche Struktur aufweisen. In diesem Lernprogramm verwenden Sie die ursprünglichen Tabellen, die zum Trainieren des Modells verwendet wurden.  
  
#### <a name="to-change-the-input-method-for-the-prediction-query"></a>So ändern Sie die Eingabemethode für die Vorhersageabfrage  
  
1.  In der **Miningmodell** , wählen Sie im Menü **Singleton-Abfrage** in diesem Fall auf das Häkchen zu entfernen.  
  
2.  Es wird eine Warnmeldung angezeigt, die Sie darüber informiert, dass die SINGLETON-Abfrage verloren geht. Klicken Sie auf **Ja**.  
  
     Der Name des eingabedialogfelds ändert sich in **Eingabetabelle(n)**.  
  
 Da Sie eine Vorhersageabfrage erstellen möchten, die die Customer ID sowie eine Liste der Produkte als Eingabe bereitstellt, fügen Sie die Kundentabelle als Falltabelle hinzu und die Tabelle mit den von Kunden getätigten Käufen als geschachtelte Tabelle. Anschließend fügen Sie Vorhersagefunktionen hinzu, um Empfehlungen zu erstellen.  
  
#### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a>So erstellen Sie eine Vorhersageabfrage mit Eingaben für geschachtelte Tabellen  
  
1.  Wählen Sie im Bereich Miningmodell das Modell Association Filtered aus.  
  
2.  In der **Eingabetabelle(n)** Dialogfeld klicken Sie auf **Falltabelle auswählen**.  
  
3.  In der **Tabelle auswählen** im Dialogfeld für **Datenquelle**, wählen Sie AdventureWorksDW2008. In der **Tabellen-/Sichtname** auflisten, wählen Sie vAssocSeqOrders, und klicken Sie dann auf **OK**.  
  
     Die Tabelle vAssocSeqOrders wird dem Bereich hinzugefügt.  
  
4.  In der **Eingabetabelle(n)** Dialogfeld klicken Sie auf **geschachtelte Tabelle auswählen**.  
  
5.  In der **Tabelle auswählen** im Dialogfeld für **Datenquelle**, wählen Sie AdventureWorksDW2008. In der **Tabellen-/Sichtname** auflisten, wählen Sie "vassocseqlineitems", und klicken Sie dann auf **OK**.  
  
     Die Tabelle vAssocSeqLineItems wird dem Bereich hinzugefügt.  
  
6.  In der **geschachtelten Join angeben** (Dialogfeld), ziehen Sie die OrderNumber-Feld aus der Falltabelle und legen Sie es im OrderNumber-Feld in der geschachtelten Tabelle.  
  
     Sie können auch klicken **Beziehung hinzufügen** und die Beziehung zu erstellen, indem Sie Spalten aus einer Liste auswählen.  
  
7.  In der **Beziehung angeben** Dialogfeld Vergewissern Sie sich, dass der OrderNumber-Felder ordnungsgemäß zugeordnet sind, und klicken Sie dann auf **OK**.  
  
8.  Klicken Sie auf **OK** schließen die **geschachtelten Join angeben** Dialogfeld.  
  
     Die Falltabelle und die geschachtelte Tabelle werden im Entwurfsbereich aktualisiert, um die Joins zwischen den externen Datenspalten und den Spalten im Modell anzuzeigen. Wenn fehlerhafte Beziehungen erstellt werden, können Sie mit der rechten Maustaste der Joinlinie und auswählen **Verbindungen ändern** zum Bearbeiten der Spalte zuordnen oder Sie können mit der rechten Maustaste der Joinlinie, und wählen **löschen** So entfernen Sie die Beziehung vollständig.  
  
9. Fügen Sie dem Raster eine neue Zeile hinzu. Für **Quelle**Option **Tabelle "vAssocSeqOrders"**. Für **Feld**, wählen Sie CustomerKey.  
  
10. Fügen Sie dem Raster eine neue Zeile hinzu. Für **Quelle**Option **Tabelle "vAssocSeqOrders"**. Für **Feld**, Region auswählen.  
  
11. Fügen Sie dem Raster eine neue Zeile hinzu. Für **Quelle**Option **Vorhersagefunktion**, und für **Feld**Option `PredictAssociation`.  
  
12. Ziehen Sie vAssocSeqLineItems in das **Kriterium/Argument** im Feld der `PredictAssociation` Zeile. Klicken Sie am Ende der **Kriterium/Argument** Feld ein, und geben Sie dann den folgenden Text: `INCLUDE_STATISTICS,3`  
  
     Der vollständige Text im der **Kriterium/Argument** werden sollten: `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`  
  
13. Klicken Sie auf die **Ergebnis** Schaltfläche, um die Vorhersagen für jeden Kunden anzuzeigen.  
  
 Sie können versuchen, eine ähnliche Vorhersageabfrage für mehrere Modelle zu erstellen, um mögliche Auswirkungen von Filteränderungen auf die Vorhersageergebnisse zu überprüfen. Weitere Informationen zum Erstellen von Vorhersagen und anderen Typen von Abfragen finden Sie unter [Zuordnungsmodellabfragen](../../2014/analysis-services/data-mining/association-model-query-examples.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Mingingmodellinhalt von Clustermodellen &#40;Analysis Services – Datamining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)   
 [PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx)   
 [Erstellen von Vorhersageabfragen mithilfe des Generators für Vorhersageabfragen](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
