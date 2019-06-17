---
title: Erstellen von Vorhersagen für ein Sequenzclustermodell (Datamining-Lernprogramm für fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 94a8d4f9-a76a-49c5-9785-917010359511
author: minewiskan
ms.author: owend
manager: kfilee
ms.openlocfilehash: 893067e234d868ae6dde2f93d93bfd50458bfeb2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63217743"
---
# <a name="creating-predictions-on-a-sequence-clustering-model-intermediate-data-mining-tutorial"></a>Erstellen von Vorhersagen für ein Sequenzclustermodell (Data Mining-Lernprogramm für Fortgeschrittene)
  Nachdem Sie das Sequenzclustermodell durch Navigieren sie in der Ereignisanzeige verstanden haben, können Sie Vorhersageabfragen erstellen, mit dem Generator für Vorhersageabfragen auf die **Miningmodellvorhersage** -Registerkarte im Data Mining-Designer. Um eine Vorhersage zu erstellen, wählen Sie zuerst das Sequenzclustermodell und dann die Eingabedaten aus. Sie können eine externe Datenquelle als Eingabe verwenden, oder Sie können eine SINGLETON-Abfrage erstellen und Werte in einem Dialogfeld angeben.  
  
 In dieser Lektion wird davon ausgegangen, dass Sie bereits mit der Verwendung des Generators für Vorhersageabfragen vertraut sind und lernen möchten, wie spezifische Abfragen für ein Sequenzclustermodell erstellt werden. Allgemeine Informationen zur Verwendung von Abfrage-Generator für Vorhersageabfragen finden Sie unter [Data Mining-Abfrageschnittstellen](../../2014/analysis-services/data-mining/data-mining-query-tools.md) oder im Abschnitt des Tutorials Basic Data Mining [Vorhersagen erstellen &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md).  
  
## <a name="creating-predictions-on-the-regional-model"></a>Erstellen von Vorhersagen für das regionale Modell  
 In diesem Szenario erstellen Sie zunächst einige SINGLETON-Vorhersageabfragen, um eine Vorstellung von den regionalen Unterschieden bei Vorhersageabfragen zu erhalten.  
  
#### <a name="to-create-a-singleton-query-on-a-sequence-clustering-model"></a>So erstellen Sie eine SINGLETON-Abfrage für ein Sequenzclustermodell  
  
1.  Klicken Sie auf die **Miningmodellvorhersage** -Registerkarte des Data Mining-Designers.  
  
2.  In der **Miningmodell** wählen Sie im spaltenmenü **Singleton-Abfrage**.  
  
     Die **Miningmodell** Bereich und **Singleton-Abfrageeingabe** Bereich angezeigt werden.  
  
3.  In der **Miningmodell** Bereich, klicken Sie auf **Modell auswählen**. (Sie können diesen Schritt überspringen, wenn der Sequenzclustermodus bereits ausgewählt wurde.)  
  
     Die **Miningmodell auswählen** Dialogfeld wird geöffnet.  
  
4.  Erweitern Sie den Knoten, der die Miningstruktur darstellt **Sequenzcluster mit Region**, und wählen Sie das Modell **Sequenzcluster mit Region**. Klicken Sie auf **OK**. Der Eingabebereich spielt im Moment noch keine Rolle; die Eingaben werden nach Einrichten der Vorhersagefunktionen vorgenommen.  
  
5.  Klicken Sie im Raster auf die leere Zelle unter **Quelle** , und wählen Sie **Vorhersagefunktion.** In der Zelle unter **Feld**Option **PredictSequence**.  
  
    > [!NOTE]  
    >  Sie können auch die **Predict** Funktion. Wenn Sie möchten, wählen Sie die Version des sein Zweck der **Predict** Funktion, die eine Tabellenspalte als Argument akzeptiert...  
  
6.  In der **Miningmodell** Bereich Wählen Sie die geschachtelte Tabelle `v Assoc Seq Line Items`, und ziehen Sie es in das Raster zu den **Kriterium/Argument** Feld für die **PredictSequence** Funktion.  
  
     Ziehen und Ablegen von Tabellen- und Spaltennamen ermöglicht es Ihnen, komplexe Anweisungen ohne Syntaxfehler zu erstellen. Allerdings ersetzt den aktuellen Inhalt der Zelleninhalt einschließlich anderer optionaler Argumente für die **PredictSequence** Funktion. Wenn Sie die anderen Argumente anzeigen möchten, können Sie dem Raster vorübergehend eine zweite Instanz der Funktion als Referenz hinzufügen.  
  
7.  Klicken Sie auf die **Ergebnis** -Schaltfläche in der oberen Ecke des Generators für Vorhersageabfragen.  
  
 Die erwarteten Ergebnisse enthalten eine einzelne Spalte mit der Überschrift **Ausdruck**. Die **Ausdruck** Spalte enthält eine geschachtelte Tabelle mit drei Spalten wie folgt:  
  
|$SEQUENCE|Zeilennummer|Model|  
|---------------|-----------------|-----------|  
|1||Mountain-200|  
  
 Was bedeuten diese Ergebnisse? Denken Sie daran, dass Sie keine Eingaben angegeben haben. Die Vorhersage erfolgt daher auf Basis aller Fälle, und die wahrscheinlichste Gesamtvorhersage wird von Analysis Services zurückgegeben.  
  
### <a name="adding-inputs-to-a-singleton-prediction-query"></a>Hinzufügen von Eingaben zu einer Singleton-Vorhersageabfrage  
 Bislang haben Sie noch keine Eingaben angegeben. In der nächsten Aufgabe verwenden Sie die **Singleton-Abfrageeingabe** Bereich, um einige Eingaben für die Abfrage anzugeben. Zunächst verwenden Sie [Region] als Eingabe für das Clustermodell für regionale Sequenzen, um zu überprüfen, ob die vorhergesagten Sequenzen für alle Regionen gleich sind. Anschließend erfahren Sie, wie Sie die Abfrage bearbeiten und die Wahrscheinlichkeit für die einzelnen Vorhersagen hinzufügen können; außerdem vereinfachen Sie die Ergebnisse, um diese übersichtlicher zu gestalten.  
  
##### <a name="to-generate-predictions-for-a-specific-customer-group"></a>So generieren Sie Vorhersagen für eine bestimmte Kundengruppe  
  
1.  Klicken Sie auf die **Entwurf** -Schaltfläche in der linken oberen Ecke des Generators für Vorhersageabfragen, wechseln zurück zum Raster Erstellen der Abfrage.  
  
2.  In der **Singleton-Abfrageeingabe** im Dialogfeld klicken Sie auf die **Wert** für Feld `Region`, und wählen Sie **"Europa"** .  
  
3.  Klicken Sie auf die **Ergebnis** Schaltfläche, um Vorhersagen für Kunden in Europa anzuzeigen.  
  
4.  Klicken Sie auf die **Entwurf** -Schaltfläche in der linken oberen Ecke des Generators für Vorhersageabfragen, wechseln zurück zum Raster Erstellen der Abfrage.  
  
5.  In der **Singleton-Abfrageeingabe** im Dialogfeld klicken Sie auf die **Wert** für Feld `Region`, und wählen Sie **Nordamerika**.  
  
6.  Klicken Sie auf die **Ergebnis** Schaltfläche, um Vorhersagen für Kunden in Nordamerika anzuzeigen.  
  
### <a name="adding-probabilities-by-using-a-custom-expression"></a>Hinzufügen von Wahrscheinlichkeiten mit einem benutzerdefinierten Ausdruck  
 Das Ausgeben der Wahrscheinlichkeit für die einzelnen Vorhersagen gestaltet sich etwas schwieriger, da die Wahrscheinlichkeit ein Attribut der Vorhersage darstellt und als geschachtelte Tabelle ausgegeben wird. Wenn Sie bereits mit Data Mining-Erweiterungen (DMX) vertraut sind, können Sie einfach die Abfrage ändern und der geschachtelten Tabelle eine untergeordnete SELECT-Anweisung hinzufügen. Sie können jedoch auch eine untergeordnete SELECT-Anweisung im Generator für Vorhersageabfragen erstellen, indem Sie einen benutzerdefinierten Ausdruck hinzufügen.  
  
##### <a name="to-output-probabilities-for-a-predicted-sequence-by-using-a-custom-expression"></a>So geben Sie Wahrscheinlichkeiten für eine vorhergesagte Sequenz mit einem benutzerdefinierten Ausdruck aus  
  
1.  Klicken Sie auf die **Entwurf** -Schaltfläche in der linken oberen Ecke des Generators für Vorhersageabfragen, wechseln zurück zum Raster Erstellen der Abfrage.  
  
2.  Im Raster unter **Quelle**, klicken Sie auf eine neue Zeile ein, und wählen **benutzerdefinierter Ausdruck**.  
  
3.  Lassen Sie das Kontrollkästchen unter **Feld** leer.  
  
4.  Für **Alias**, Typ `t`.  
  
5.  In der **Kriterium/Argument** geben die vollständige untergeordnete select-Anweisung wie im folgenden Codebeispiel gezeigt. Achten Sie darauf, auch die öffnende und die schließende Klammer einzugeben.  
  
    ```  
    (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))  
    ```  
  
6.  Klicken Sie auf die **Ergebnis** Schaltfläche, um Vorhersagen für Kunden in Europa anzuzeigen.  
  
 Das Ergebnis enthält zwei geschachtelte Tabellen: eine Tabelle mit der Vorhersage und eine Tabelle mit der Wahrscheinlichkeit für die Vorhersage. Wenn Sie die Abfrage nicht ausführen können, können Sie zur Abfrageentwurfsansicht wechseln und die vollständige Abfrageanweisung überprüfen. Diese sollte wie folgt lauten:  
  
```  
SELECT  
  PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
  ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
FROM  
  [Sequence Clustering with Region]  
NATURAL PREDICTION JOIN  
(SELECT 'Europe' AS [Region]) AS t  
```  
  
### <a name="working-with-results"></a>Arbeiten mit Ergebnissen  
 Wenn Ihre Ergebnisse eine große Zahl von geschachtelten Tabellen enthalten, können Sie diese vereinfachen, um die Anzeige übersichtlicher zu gestalten. Dazu können Sie die Abfrage manuell ändern und das `FLATTENED`-Schlüsselwort hinzufügen.  
  
##### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a>So vereinfachen Sie geschachtelte Rowsets in einer Vorhersageabfrage  
  
1.  Klicken Sie auf die **Abfrage** Schaltfläche in der Ecke des Generators für Vorhersageabfragen.  
  
     Das Raster ändert sich in einen offenen Bereich, in dem Sie die DMX-Anweisung anzeigen und ändern können, die Sie mit dem Generator für Vorhersageabfragen erstellt haben.  
  
2.  Geben Sie nach dem `SELECT`-Schlüsselwort `FLATTENED` ein.  
  
     Der vollständige Abfragetext sollte wie folgt aussehen:  
  
    ```  
    SELECT FLATTENED  
      PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
      ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
    FROM  
      [Sequence Clustering with Region]  
    NATURAL PREDICTION JOIN  
    (SELECT 'Europe' AS [Region]) AS t  
    ```  
  
3.  Klicken Sie auf die **Ergebnisse** -Schaltfläche in der oberen Ecke des Generators für Vorhersageabfragen.  
  
 Nachdem Sie eine Abfrage manuell bearbeitet haben, werden Sie nicht wieder zur Entwurfsansicht zu wechseln, ohne dass Sie die Änderungen verloren gehen können. Sie können jedoch die DMX-Anweisung, die Sie manuell erstellt haben, als Textdatei speichern und anschließend zur Entwurfsansicht zurückkehren. In diesem Fall wird die Abfrage auf die letzte gültige Version in der Entwurfsansicht zurückgesetzt.  
  
## <a name="creating-predictions-on-the-related-model"></a>Erstellen von Vorhersagen für das verwandte Modell  
 In den vorangegangenen Beispielen wurde die Tabellenspalte für den Fall Region als Eingabe für eine SINGLETON-Vorhersageabfrage verwendet, um zu überprüfen, ob im Modell regionale Unterschiede festzustellen sind. Nach der Untersuchung des Modells sind Sie jedoch zu dem Schluss gekommen, dass die Unterschiede nicht groß genug sind, um eine Anpassung von Produktempfehlungen nach Region zu rechtfertigen. Vielmehr interessieren Sie sich für Vorhersagen über die Elemente, die ein Kunde voraussichtlich wählen wird. In den folgenden Abfragen verwenden Sie daher das Sequenzclustermodell ohne Region, um Empfehlungen für alle Kunden zu generieren.  
  
### <a name="using-nested-table-columns-as-input"></a>Verwenden von geschachtelten Tabellenspalten als Eingabe  
 Zunächst erstellen Sie eine SINGLETON-Vorhersageabfrage, die ein Element als Eingabe akzeptiert und das Element mit der nächsthöheren Wahrscheinlichkeit zurückgibt. Voraussetzung für eine solche Vorhersage ist die Verwendung einer geschachtelten Tabellenspalte als Eingabewert. Dies liegt daran, dass das Attribut für die Vorhersage (Modell) Teil einer geschachtelten Tabelle ist. Analysis Services stellt die **Eingabe für geschachtelte Tabelle** Dialogfeld können Sie ganz einfach erstellen von Vorhersageabfragen für geschachtelte Tabellenattribute mit dem Generator für Vorhersageabfragen.  
  
##### <a name="to-use-a-nested-table-as-input-to-a-prediction"></a>So verwenden Sie eine geschachtelte Tabelle als Eingabe für eine Vorhersage  
  
1.  Klicken Sie auf die **Entwurf** -Schaltfläche in der linken oberen Ecke des Generators für Vorhersageabfragen, wechseln zurück zum Raster Erstellen der Abfrage.  
  
2.  In der **Singleton-Abfrageeingabe** im Dialogfeld klicken Sie auf die **Wert** für Feld `Region`, und wählen Sie die leere Zeile, um die Eingabe für dieses Feld zu löschen.  
  
3.  In der **Singleton-Abfrageeingabe** Dialogfeld klicken Sie auf die **Wert** für Feld `vAssocSeqLineItems`, und klicken Sie dann auf die Schaltfläche (…).  
  
4.  In der **Eingabe für geschachtelte Tabelle** Dialogfeld klicken Sie auf **hinzufügen**.  
  
5.  Klicken Sie in der neuen Zeile auf das Feld unter `Model`, und wählen Sie Touring Tire aus der Liste. Klicken Sie auf **OK**.  
  
6.  Klicken Sie auf die **Ergebnis** Schaltfläche, um die Vorhersagen anzuzeigen.  
  
 Im Modell werden die angegebenen Folgeelemente für alle Kunden empfohlen, die Touring Tire als erstes Element ausgewählt haben. Aus Ihrer Untersuchung des Modells wissen Sie, dass die Produkte Touring Tire und Touring Tire Tube von Kunden häufig zusammen gekauft werden. Die Empfehlungen entsprechen daher den Erwartungen.  
  
|$SEQUENCE|Zeilennummer|Model|  
|---------------|-----------------|-----------|  
|1||Touring Tire Tube|  
|2||Sport-100|  
|3||Long-Sleeve Logo Jersey|  
  
### <a name="creating-a-bulk-prediction-query-using-nested-table-inputs"></a>Erstellen einer Abfrage für Massenvorhersagen mit Eingaben für geschachtelte Tabellen  
 Sie können nun mit dem Modell wie gewünscht Vorhersagen erstellen, die als Grundlage für Empfehlungen dienen können. Als Nächstes erstellen Sie eine Vorhersageabfrage, die einer externen Datenquelle zugeordnet ist. Diese Datenquelle stellt Werte bereit, die aktuelle Produkte darstellen. Da Sie eine Vorhersageabfrage erstellen möchten, die die Customer ID sowie eine Liste der Produkte als Eingabe bereitstellt, fügen Sie die Kundentabelle als Falltabelle hinzu und die Tabelle mit den von Kunden getätigten Käufen als geschachtelte Tabelle. Anschließend fügen Sie wie zuvor Vorhersagefunktionen hinzu, um Empfehlungen zu erstellen.  
  
 Dieses Verfahren wird auch in Lektion 3 zum Erstellen von Vorhersagen für das Market Basket-Szenario verwendet; bei Vorhersagen in einem Sequenzclustermodell ist allerdings auch die Reihenfolge als Eingabe erforderlich.  
  
##### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a>So erstellen Sie eine Vorhersageabfrage mit Eingaben für geschachtelte Tabellen  
  
1.  In der **Miningmodell** wählen Sie im Bereich der Sequence Clustering-Modell, wenn es nicht bereits ausgewählt ist.  
  
2.  In der **Eingabetabelle(n)** Dialogfeld klicken Sie auf **Falltabelle auswählen**.  
  
3.  In der **Tabelle auswählen** , für die Datenquelle, wählen Sie im Dialogfeld Aufträge. In der **Tabellen-/Sichtname** auflisten, wählen Sie vAssocSeqOrders, und klicken Sie dann auf **OK**.  
  
4.  In der **Eingabetabelle(n)** Dialogfeld klicken Sie auf **geschachtelte Tabelle auswählen**.  
  
5.  In der **Tabelle auswählen** im Dialogfeld für **Datenquelle**, wählen Sie Aufträge aus. In der **Tabellen-/Sichtname** auflisten, wählen Sie "vassocseqlineitems", und klicken Sie dann auf **OK**.  
  
     Analysis Services versucht, Beziehungen zu erkennen und automatisch zu erstellen, wenn die Datentypen übereinstimmen und ähnliche Spaltennamen vorliegen. Wenn die Beziehungen, die es erstellt auf falsch festgelegt sind, können Sie mit der rechten Maustaste der Joinlinie und auswählen **Verbindungen ändern** zum Bearbeiten der Spalte zuordnen oder Sie können mit der rechten Maustaste der Joinlinie, und wählen **löschen** auf Entfernen Sie die Beziehung vollständig. In diesem Fall werden die Beziehungen automatisch dem Entwurfsbereich hinzugefügt, da die Tabellen in der Datenquellensicht bereits verbunden waren.  
  
6.  Fügen Sie dem Raster eine neue Zeile hinzu. Für **Quelle**, wählen Sie vassocseqorders als und **Feld**, wählen Sie CustomerKey.  
  
7.  Fügen Sie dem Raster eine neue Zeile hinzu. Für **Quelle**Option **Vorhersagefunktion**, und für **Feld**Option **PredictSequence**.  
  
8.  Ziehen Sie vAssocSeqLineItems in das **Kriterium/Argument** Feld. Klicken Sie am Ende der **Kriterium/Argument** Feld ein, und geben Sie dann die folgenden Argumente: `2`.  
  
     Der vollständige Text im der **Kriterium/Argument** werden sollten: `[Sequence Clustering].[v Assoc Seq Line Items],2`  
  
9. Klicken Sie auf die **Ergebnis** Schaltfläche, um die Vorhersagen für jeden Kunden anzuzeigen.  
  
 Sie haben das Lernprogramm für Sequenzclustermodelle abgeschlossen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie alle Abschnitte in haben die [Data Mining Tutorial für fortgeschrittene &#40;Analysis Services – Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md), der nächste Schritt ist möglicherweise erfahren, wie Sie Data Mining Extensions (DMX)-Anweisungen verwenden, um Modelle zu erstellen und Generieren von Vorhersagen. Weitere Informationen finden Sie unter [erstellen und Abfragen von Data Mining-Modellen mit DMX: Lernprogramme &#40;Analysis Services – Datamining&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md).  
  
 Wenn Sie mit Programmierkonzepten vertraut sind, können Sie Data Mining-Objekte mithilfe von Analysis Management Objects (AMO) auch programmgesteuert bearbeiten. Weitere Informationen finden Sie unter [AMO-Klassen für Data Mining](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes).  
  
## <a name="see-also"></a>Siehe auch  
 [Sequenzclusteringmodellabfragebeispiele](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)   
 [Miningmodellinhalt von Sequence Clustering-Modellen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)  
  
  
