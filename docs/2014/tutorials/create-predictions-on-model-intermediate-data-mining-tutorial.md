---
title: Erstellen von Vorhersagen für ein Sequence Clustering-Modell (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63217743"
---
# <a name="creating-predictions-on-a-sequence-clustering-model-intermediate-data-mining-tutorial"></a>Erstellen von Vorhersagen für ein Sequenzclustermodell (Data Mining-Lernprogramm für Fortgeschrittene)
  Nachdem Sie das Sequence Clustering-Modell besser verstanden haben, indem Sie es im Viewer durchsuchen, können Sie Vorhersage Abfragen erstellen, indem Sie Vorhersage Abfrage-Generator auf der Registerkarte **Mining Modellvorhersage** im Data Mining-Designer verwenden. Um eine Vorhersage zu erstellen, wählen Sie zuerst das Sequenzclustermodell und dann die Eingabedaten aus. Sie können eine externe Datenquelle als Eingabe verwenden, oder Sie können eine SINGLETON-Abfrage erstellen und Werte in einem Dialogfeld angeben.  
  
 In dieser Lektion wird davon ausgegangen, dass Sie bereits mit der Verwendung des Generators für Vorhersageabfragen vertraut sind und lernen möchten, wie spezifische Abfragen für ein Sequenzclustermodell erstellt werden. Allgemeine Informationen zur Verwendung von Vorhersage Abfrage-Generator finden Sie unter [Data Mining-Abfrageschnittstellen](../../2014/analysis-services/data-mining/data-mining-query-tools.md) oder im Abschnitt des Lernprogramms zu Data Mining-Grundlagen, [Erstellen von Vorhersagen &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md).  
  
## <a name="creating-predictions-on-the-regional-model"></a>Erstellen von Vorhersagen für das regionale Modell  
 In diesem Szenario erstellen Sie zunächst einige SINGLETON-Vorhersageabfragen, um eine Vorstellung von den regionalen Unterschieden bei Vorhersageabfragen zu erhalten.  
  
#### <a name="to-create-a-singleton-query-on-a-sequence-clustering-model"></a>So erstellen Sie eine SINGLETON-Abfrage für ein Sequenzclustermodell  
  
1.  Klicken Sie im Data Mining-Designer auf die Registerkarte **Mining Modellvorhersage** .  
  
2.  Wählen Sie im Menü **Mining Modell** Spalte die Option **Singleton-Abfrage**aus.  
  
     Der Bereich **Mining Modell** und der **Eingabebereich SINGLETON-Abfrage** werden angezeigt.  
  
3.  Klicken Sie im Bereich **Mining Modell** auf **Modell auswählen**. (Sie können diesen Schritt überspringen, wenn der Sequenzclustermodus bereits ausgewählt wurde.)  
  
     Das Dialogfeld **Mining Modell auswählen** wird geöffnet.  
  
4.  Erweitern Sie den Knoten, der die Mining Struktur **Sequence Clustering with Region**darstellt, und wählen Sie das Modell **Sequence Clustering with Region**aus. Klicken Sie auf **OK**. Der Eingabebereich spielt im Moment noch keine Rolle; die Eingaben werden nach Einrichten der Vorhersagefunktionen vorgenommen.  
  
5.  Klicken Sie im Raster unter **Quelle** auf die leere Zelle, und wählen Sie **Vorhersagefunktion aus.** Wählen Sie in der Zelle unter **Feld**die Option **prätsequenzsequenz**aus.  
  
    > [!NOTE]  
    >  Sie können auch die **Vorhersage** Funktion verwenden. Wenn Sie dies tun, achten Sie darauf, dass Sie die Version der **Vorhersage** Funktion auswählen, die eine Tabellenspalte als Argument annimmt.  
  
6.  Wählen Sie im Bereich **Mining Modell** die Tabelle `v Assoc Seq Line Items`aus, und ziehen Sie Sie in das Raster, um das Feld **Kriterium/Argument** für die Funktion " **vorhersagesequence** " zu markieren.  
  
     Durchziehen und Ablegen von Tabellen-und Spaltennamen können Sie komplexe Anweisungen ohne Syntax Fehler erstellen. Allerdings ersetzt Sie den aktuellen Inhalt der Zelle, die andere optionale Argumente für die **prätsequence** -Funktion enthält. Wenn Sie die anderen Argumente anzeigen möchten, können Sie dem Raster vorübergehend eine zweite Instanz der Funktion als Referenz hinzufügen.  
  
7.  Klicken Sie in der oberen Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **Ergebnis** .  
  
 Die erwarteten Ergebnisse enthalten eine einzelne Spalte mit dem Überschriften **Ausdruck**. Die Spalte **Ausdruck** enthält eine Tabelle mit drei Spalten wie folgt:  
  
|$SEQUENCE|Zeilennummer|Modell|  
|---------------|-----------------|-----------|  
|1||Mountain-200|  
  
 Was bedeuten diese Ergebnisse? Denken Sie daran, dass Sie keine Eingaben angegeben haben. Die Vorhersage erfolgt daher auf Basis aller Fälle, und die wahrscheinlichste Gesamtvorhersage wird von Analysis Services zurückgegeben.  
  
### <a name="adding-inputs-to-a-singleton-prediction-query"></a>Hinzufügen von Eingaben zu einer Singleton-Vorhersageabfrage  
 Bislang haben Sie noch keine Eingaben angegeben. In der nächsten Aufgabe verwenden Sie den Bereich **Singleton-Abfrage Eingabe** , um einige Eingaben für die Abfrage anzugeben. Zunächst verwenden Sie [Region] als Eingabe für das Clustermodell für regionale Sequenzen, um zu überprüfen, ob die vorhergesagten Sequenzen für alle Regionen gleich sind. Anschließend erfahren Sie, wie Sie die Abfrage bearbeiten und die Wahrscheinlichkeit für die einzelnen Vorhersagen hinzufügen können; außerdem vereinfachen Sie die Ergebnisse, um diese übersichtlicher zu gestalten.  
  
##### <a name="to-generate-predictions-for-a-specific-customer-group"></a>So generieren Sie Vorhersagen für eine bestimmte Kundengruppe  
  
1.  Klicken Sie in der linken oberen Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **Entwurf** , um zum Raster für die Abfrage Erstellung zurückzukehren.  
  
2.  Klicken Sie im Dialogfeld **Singleton-Abfrage Eingabe** auf **** das Feld Wert `Region`für, und wählen Sie **Europa**aus.  
  
3.  Klicken Sie auf die Schaltfläche **Ergebnis** , um Vorhersagen für Kunden in Europa anzuzeigen.  
  
4.  Klicken Sie in der linken oberen Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **Entwurf** , um zum Raster für die Abfrage Erstellung zurückzukehren.  
  
5.  Klicken Sie im Dialogfeld **Singleton-Abfrage Eingabe** auf **** das Feld Wert `Region`für, und wählen Sie **Nordamerika**aus.  
  
6.  Klicken Sie auf die Schaltfläche **Ergebnis** , um Vorhersagen für Kunden in Nordamerika anzuzeigen.  
  
### <a name="adding-probabilities-by-using-a-custom-expression"></a>Hinzufügen von Wahrscheinlichkeiten mit einem benutzerdefinierten Ausdruck  
 Das Ausgeben der Wahrscheinlichkeit für die einzelnen Vorhersagen gestaltet sich etwas schwieriger, da die Wahrscheinlichkeit ein Attribut der Vorhersage darstellt und als geschachtelte Tabelle ausgegeben wird. Wenn Sie bereits mit Data Mining-Erweiterungen (DMX) vertraut sind, können Sie einfach die Abfrage ändern und der geschachtelten Tabelle eine untergeordnete SELECT-Anweisung hinzufügen. Sie können jedoch auch eine untergeordnete SELECT-Anweisung im Generator für Vorhersageabfragen erstellen, indem Sie einen benutzerdefinierten Ausdruck hinzufügen.  
  
##### <a name="to-output-probabilities-for-a-predicted-sequence-by-using-a-custom-expression"></a>So geben Sie Wahrscheinlichkeiten für eine vorhergesagte Sequenz mit einem benutzerdefinierten Ausdruck aus  
  
1.  Klicken Sie in der linken oberen Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **Entwurf** , um zum Raster für die Abfrage Erstellung zurückzukehren.  
  
2.  Klicken Sie im Raster unter **Quelle**auf eine neue Zeile, und wählen Sie **Benutzerdefinierter Ausdruck**aus.  
  
3.  Lassen Sie das **Feld** leer.  
  
4.  Geben **** `t`Sie als Alias ein.  
  
5.  Geben Sie im Feld **Kriterium/Argument** die gesamte untergeordnete SELECT-Anweisung ein, wie im folgenden Codebeispiel gezeigt. Achten Sie darauf, auch die öffnende und die schließende Klammer einzugeben.  
  
    ```  
    (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))  
    ```  
  
6.  Klicken Sie auf die Schaltfläche **Ergebnis** , um Vorhersagen für Kunden in Europa anzuzeigen.  
  
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
  
1.  Klicken Sie in der Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **Abfrage** .  
  
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
  
3.  Klicken Sie in der oberen Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **Ergebnisse** .  
  
 Nachdem Sie eine Abfrage manuell bearbeitet haben, können Sie nicht wieder zu Designansicht wechseln, ohne die Änderungen zu verlieren. Sie können jedoch die DMX-Anweisung, die Sie manuell erstellt haben, als Textdatei speichern und anschließend zur Entwurfsansicht zurückkehren. In diesem Fall wird die Abfrage auf die letzte gültige Version in der Entwurfsansicht zurückgesetzt.  
  
## <a name="creating-predictions-on-the-related-model"></a>Erstellen von Vorhersagen für das verwandte Modell  
 In den vorangegangenen Beispielen wurde die Tabellenspalte für den Fall Region als Eingabe für eine SINGLETON-Vorhersageabfrage verwendet, um zu überprüfen, ob im Modell regionale Unterschiede festzustellen sind. Nach der Untersuchung des Modells sind Sie jedoch zu dem Schluss gekommen, dass die Unterschiede nicht groß genug sind, um eine Anpassung von Produktempfehlungen nach Region zu rechtfertigen. Vielmehr interessieren Sie sich für Vorhersagen über die Elemente, die ein Kunde voraussichtlich wählen wird. In den folgenden Abfragen verwenden Sie daher das Sequenzclustermodell ohne Region, um Empfehlungen für alle Kunden zu generieren.  
  
### <a name="using-nested-table-columns-as-input"></a>Verwenden von geschachtelten Tabellenspalten als Eingabe  
 Zunächst erstellen Sie eine SINGLETON-Vorhersageabfrage, die ein Element als Eingabe akzeptiert und das Element mit der nächsthöheren Wahrscheinlichkeit zurückgibt. Voraussetzung für eine solche Vorhersage ist die Verwendung einer geschachtelten Tabellenspalte als Eingabewert. Dies liegt daran, dass das Attribut für die Vorhersage (Modell) Teil einer geschachtelten Tabelle ist. Analysis Services stellt das Eingabe Dialogfeld der **eingefügten Tabelle** bereit, mit dem Sie mithilfe der Vorhersage Abfrage-Generator problemlos Vorhersage Abfragen für Tabellen Attribute erstellen können.  
  
##### <a name="to-use-a-nested-table-as-input-to-a-prediction"></a>So verwenden Sie eine geschachtelte Tabelle als Eingabe für eine Vorhersage  
  
1.  Klicken Sie in der linken oberen Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **Entwurf** , um zum Raster für die Abfrage Erstellung zurückzukehren.  
  
2.  Klicken Sie im Dialogfeld **Singleton-Abfrage Eingabe** auf **** das Feld Wert `Region`für, und wählen Sie die leere Zeile aus, um die Eingabe für dieses Feld zu löschen.  
  
3.  Klicken Sie im Dialogfeld **Singleton-Abfrage Eingabe** auf **** das Feld Wert `vAssocSeqLineItems`für, und klicken Sie dann auf die Schaltfläche (...).  
  
4.  Klicken Sie im Dialogfeld **Eingabe der eingefügten Tabelle** auf **Hinzufügen**.  
  
5.  Klicken Sie in der neuen Zeile auf das Feld `Model`unter, und wählen Sie Touring Tire in der Liste aus. Klicken Sie auf **OK**.  
  
6.  Klicken Sie auf die Schaltfläche **Ergebnis** , um die Vorhersagen anzuzeigen.  
  
 Im Modell werden die angegebenen Folgeelemente für alle Kunden empfohlen, die Touring Tire als erstes Element ausgewählt haben. Aus Ihrer Untersuchung des Modells wissen Sie, dass die Produkte Touring Tire und Touring Tire Tube von Kunden häufig zusammen gekauft werden. Die Empfehlungen entsprechen daher den Erwartungen.  
  
|$SEQUENCE|Zeilennummer|Modell|  
|---------------|-----------------|-----------|  
|1||Touring Tire Tube|  
|2||Sport-100|  
|3||Long-Sleeve Logo Jersey|  
  
### <a name="creating-a-bulk-prediction-query-using-nested-table-inputs"></a>Erstellen einer Abfrage für Massenvorhersagen mit Eingaben für geschachtelte Tabellen  
 Sie können nun mit dem Modell wie gewünscht Vorhersagen erstellen, die als Grundlage für Empfehlungen dienen können. Als Nächstes erstellen Sie eine Vorhersageabfrage, die einer externen Datenquelle zugeordnet ist. Diese Datenquelle stellt Werte bereit, die aktuelle Produkte darstellen. Da Sie eine Vorhersageabfrage erstellen möchten, die die Customer ID sowie eine Liste der Produkte als Eingabe bereitstellt, fügen Sie die Kundentabelle als Falltabelle hinzu und die Tabelle mit den von Kunden getätigten Käufen als geschachtelte Tabelle. Anschließend fügen Sie wie zuvor Vorhersagefunktionen hinzu, um Empfehlungen zu erstellen.  
  
 Dieses Verfahren wird auch in Lektion 3 zum Erstellen von Vorhersagen für das Market Basket-Szenario verwendet; bei Vorhersagen in einem Sequenzclustermodell ist allerdings auch die Reihenfolge als Eingabe erforderlich.  
  
##### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a>So erstellen Sie eine Vorhersageabfrage mit Eingaben für geschachtelte Tabellen  
  
1.  Wählen Sie im Bereich **Mining Modell** das Sequence Clustering-Modell aus, falls es nicht bereits ausgewählt ist.  
  
2.  Klicken Sie im Dialogfeld **Eingabe Tabelle (n) auswählen** auf **Fall Tabelle auswählen**.  
  
3.  Wählen Sie im Dialogfeld **Tabelle auswählen** für Datenquelle die Option Aufträge aus. Wählen Sie in der Liste **Tabellen-/Sichtname** den Eintrag vassocsqorders aus, und klicken Sie dann auf **OK**.  
  
4.  Klicken Sie im Dialogfeld **Eingabe Tabelle (n) auswählen** auf **Tabelle auswählen**.  
  
5.  Wählen Sie im Dialogfeld **Tabelle auswählen** für **Datenquelle**die Option Aufträge aus. Wählen Sie in der Liste **Tabellen-/Sichtname** den Eintrag vassocsetqlineitems aus, und klicken Sie dann auf **OK**.  
  
     Analysis Services versucht, Beziehungen zu erkennen und automatisch zu erstellen, wenn die Datentypen übereinstimmen und ähnliche Spaltennamen vorliegen. Wenn die erstellten Beziehungen falsch sind, können Sie mit der rechten Maustaste auf die Joinlinie klicken und **Verbindungen ändern** auswählen, um die Spalten Zuordnung zu bearbeiten, oder Sie können mit der rechten Maustaste auf die Joinlinie klicken und **Löschen** auswählen, um die Beziehung vollständig zu entfernen. In diesem Fall werden die Beziehungen automatisch dem Entwurfsbereich hinzugefügt, da die Tabellen in der Datenquellensicht bereits verbunden waren.  
  
6.  Fügen Sie dem Raster eine neue Zeile hinzu. Wählen Sie als **Quelle**die Option vassocabqorders aus, und wählen Sie für **Feld**die Option CustomerKey aus.  
  
7.  Fügen Sie dem Raster eine neue Zeile hinzu. Wählen Sie für **Quelle**die Option **Vorhersagefunktion**aus, und wählen Sie für **Feld**die Option **vorhersag Sequenz**aus.  
  
8.  Ziehen Sie vassoccot qlineitems in das Feld **Kriterium/Argument** . Klicken Sie am Ende des Felds **Kriterium/Argument** , und geben Sie dann die folgenden Argumente `2`ein:.  
  
     Der vollständige Text im Feld **Kriterium/Argument** sollte wie folgt lauten:`[Sequence Clustering].[v Assoc Seq Line Items],2`  
  
9. Klicken Sie auf die Schaltfläche **Ergebnis** , um die Vorhersagen für jeden Kunden anzuzeigen.  
  
 Sie haben das Lernprogramm für Sequenzclustermodelle abgeschlossen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie alle Abschnitte im Data Mining-Lernprogramm für fort [geschrittene &#40;Analysis Services Data Mining-&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)fertiggestellt haben, können Sie im nächsten Schritt erfahren, wie Sie DMX-Anweisungen (Data Mining Extensions) zum Erstellen von Modellen und Generieren von Vorhersagen verwenden. Weitere Informationen finden Sie unter [Erstellen und Abfragen von Data Mining-Modellen mit DMX: Tutorials &#40;Analysis Services Data Mining-&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md).  
  
 Wenn Sie mit Programmierkonzepten vertraut sind, können Sie Data Mining-Objekte mithilfe von Analysis Management Objects (AMO) auch programmgesteuert bearbeiten. Weitere Informationen finden Sie unter [AMO-Klassen für Data Mining](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sequence Clustering-Modell Abfrage Beispiele](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)   
 [Mining Modell Inhalt von Sequence Clustering-Modellen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)  
  
  
