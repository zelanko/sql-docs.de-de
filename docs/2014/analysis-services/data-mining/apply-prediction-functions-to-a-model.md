---
title: Anwenden von Vorhersagefunktionen auf ein Modell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Model Prediction [Analysis Services], selecting mining models
ms.assetid: cf9a97e2-c249-441b-af12-c977c1a91c44
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 41c7c447af3eb7e0f40c10b98be827caa59867e0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66086141"
---
# <a name="apply-prediction-functions-to-a-model"></a>Anwenden von Vorhersagefunktionen auf ein Modell
  Zum Erstellen einer Vorhersageabfrage müssen Sie zunächst das Miningmodell auswählen, auf dem die Abfrage basieren soll. Sie können jedes Miningmodell auswählen, das im aktuellen Projekt vorhanden ist.  
  
 Nachdem Sie ein Modell ausgewählt haben, fügen Sie der Abfrage eine *Vorhersagefunktion* hinzu. Es ist wichtig zu verstehen, dass Vorhersagefunktionen, für viele Zwecke – Ja verwendet werden, Sie können damit Werte Vorhersagen, aber erhalten Sie auch verwandte Statistiken sowie Informationen, die beim Generieren der Vorhersage verwendet wurde. Vorhersagefunktionen können die folgenden Typen von Werten zurückgeben:  
  
-   Den Namen des vorhersagbaren Attributs und den vorhergesagten Wert  
  
-   Statistiken zur Verteilung und der Varianz der vorhergesagten Werte  
  
-   Die Wahrscheinlichkeit eines angegebenen Ergebnisses oder von allen möglichen Ergebnissen  
  
-   Die obersten oder untersten Ergebnisse oder Werte  
  
-   Werte, die einem bestimmten Knoten, Objekt oder Attribut zugeordnet sind  
  
 Sie können eine Vielzahl von Vorhersagefunktionen verwenden. Sie müssen jedoch die Funktion verwenden, die zu dem von Ihnen erstellten Modelltyp passt. Normalerweise hängt diese Auswahl vom Algorithmus ab, der verwendet wurde, um das Modell zu erstellen.  
  
-   Eine Liste der Vorhersagefunktionen, die für fast alle Modelltypen unterstützt werden, finden Sie unter [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).  
  
-   Darüber hinaus unterstützen einzelne Algorithmen eine Vielzahl spezialisierter Funktionen. Wenn Sie beispielsweise auf Grundlage des Microsoft Clustering-Algorithmus ein Miningmodell erstellen, können Sie spezialisierte Vorhersagefunktionen verwenden, um Informationen über die Cluster zu suchen (beispielsweise die Entfernung von einem Datenwert zum Clusterschwerpunkt).  
  
     Beispiele zum Abfragen eines bestimmten Typs von Miningmodell finden Sie im Algorithmusreferenzthema unter [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).  
  
### <a name="choose-a-mining-model-to-use-for-prediction"></a>Auswählen eines Miningmodells für die Vorhersage  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste auf das Modell, und wählen Sie **Vorhersageabfrage erstellen**aus.  
  
     \- oder -  
  
     Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]auf die Registerkarte **Miningmodellvorhersage**und anschließend auf **Modell auswählen** in der Tabelle  **Miningmodell** .  
  
2.  Wählen Sie im Dialogfeld **Miningmodell auswählen** ein Miningmodell aus, und klicken Sie dann auf **OK**.  
  
     Sie können jedes Modell in der aktuellen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank auswählen. Damit eine Abfrage mithilfe eines Modells in einer anderen Datenbank erstellt werden kann, müssen Sie entweder ein neues Abfragefenster im Kontext dieser Datenbank öffnen oder die Projektmappendatei öffnen, die das Modell enthält.  
  
### <a name="add-prediction-functions-to-a-query"></a>Hinzufügen von Vorhersagefunktionen zu einer Abfrage  
  
1.  Konfigurieren Sie im **Generator für Vorhersageabfragen**die für die Vorhersage verwendeten Eingabedaten, und zwar entweder durch das Bereitstellen von Werten im Dialogfeld **SINGLETON-Abfrageeingabe** oder indem Sie einer externen Datenquelle das Modell zuordnen.  
  
     Weitere Informationen finden Sie unter [Auswählen und Zuordnen von Eingabedaten für eine Vorhersageabfrage](choose-and-map-input-data-for-a-prediction-query.md).  
  
    > [!WARNING]  
    >  Es ist nicht erforderlich, dass Sie Eingaben bereitstellen, um Vorhersagen zu generieren. Liegt keine Eingabe vor, gibt der Algorithmus im Allgemeinen den am wahrscheinlichsten vorhergesagten Wert über alle möglichen Eingaben zurück.  
  
2.  Klicken Sie auf die Spalte **Quelle** , und wählen Sie einen Wert aus der Liste aus:  
  
    |||  
    |-|-|  
    |**\<Modellname >**|Aktivieren Sie diese Option, um Werte vom Miningmodell in die Ausgabe einzuschließen. Sie können nur vorhersagbaren Spalten hinzufügen.<br /><br /> Wenn Sie eine Spalte aus dem Modell hinzufügen, ist das zurückgegebene Ergebnis die nicht unterschiedliche Liste der Werte in dieser Spalte.<br /><br /> Die Spalten, die Sie mit dieser Option hinzufügen, sind im SELECT-Teil der resultierenden DMX-Anweisung enthalten.|  
    |**Prediction Function**|Aktivieren Sie diese Option, um eine Liste von Vorhersagefunktionen zu durchsuchen.<br /><br /> Dem SELECT-Teil der resultierenden DMX-Anweisung werden die von Ihnen ausgewählten Werte oder die Funktionen hinzugefügt.<br /><br /> Die Liste der Vorhersagefunktionen wird durch den von Ihnen ausgewählten Modelltyp weder gefiltert noch eingeschränkt. Wenn Sie sich nicht sicher sind, ob die Funktion vom aktuellen Modelltyp unterstützt wird, können Sie demzufolge der Liste einfach die Funktion hinzufügen und anzeigen, ob ein Fehler vorliegt.<br /><br /> Listenelemente, denen $ (z. B. $ADJUSTEDPROBABILITY) vorangestellt werden, stellen Spalten von der geschachtelten Tabelle dar, die ausgegeben wird, wenn Sie die Funktion `PredictHistogram` verwenden. Dies sind Verknüpfungen, mit denen Sie eine einzelne Spalte, aber keine geschachtelte Tabelle zurückgeben können.|  
    |**Benutzerdefinierter Ausdruck**|Aktivieren Sie diese Option, um einen benutzerdefinierten Ausdruck einzugeben und der Ausgabe dann einen Alias zuzuweisen.<br /><br /> Dem SELECT-Teil der resultierenden DMX-Vorhersageabfrage wird der benutzerdefinierte Ausdruck hinzugefügt.<br /><br /> Diese Option ist nützlich, wenn Sie Text für die Ausgabe mit jeder Zeile hinzufügen, VB-Funktionen oder benutzerdefinierte gespeicherte Prozeduren aufrufen möchten.<br /><br /> Informationen zum Verwenden von VBA- und Excel-Funktionen von DMX aus finden Sie unter [VBA-Funktionen in MDX und DAX](/sql/mdx/vba-functions-in-mdx-and-dax).|  
  
3.  Wechseln Sie, nachdem Sie jede Funktion oder jeden Ausdruck hinzugefügt haben, zur DMX-Ansicht, um zu sehen, wie die Funktion in der DMX-Anweisung hinzugefügt wurde.  
  
    > [!WARNING]  
    >  Der Generator für Vorhersageabfragen überprüft die DMX erst, wenn Sie auf **Ergebnisse**klicken. Sie werden öfters feststellen, dass der vom Abfrage-Generator erzeugte Ausdruck kein gültiger DMX-Wert ist. Dies liegt normalerweise an einer Spalte, die sich nicht auf die vorhersagbare Spalte bezieht, oder an dem Versuch, eine Spalte in einer geschachtelten Tabelle vorherzusagen, die eine untergeordnete SELECT-Anweisung erfordert. Hierkönnen Sie zur DMX-Ansicht wechseln und die Anweisung weiterhin bearbeiten.  
  
### <a name="example-create-a-query-on-a-clustering-model"></a>Beispiel: Erstellen Sie eine Abfrage für ein Clusteringmodell  
  
1.  Wenn Sie über kein Clustermodell für das Erstellen dieser Beispielabfrage verfügen, erstellen Sie das Modell [TM_Clustering] mithilfe des [Tutorials zu Data Mining-Grundlagen](../../tutorials/basic-data-mining-tutorial.md).  
  
2.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste auf das Modell, [TM_Clustering]. und wählen Sie **Vorhersageabfrage erstellen**aus.  
  
3.  Klicken Sie im Menü **Miningmodell** auf **SINGLETON-Abfrage**.  
  
4.  Legen Sie im Dialogfeld **SINGLETON-Abfrageeingabe** die folgenden Werte als Eingaben fest:  
  
    -   Geschlecht = M  
  
    -   Arbeitsweg = 8–16 Kilometer (5–10 Meilen)  
  
5.  Wählen Sie im Abfrageraster für **Quelle**„TM_Clustering-Miningmodell“ aus, und fügen Sie die Spalte „[Bike Buyer]“ hinzu.  
  
6.  Für **Quelle**Option **Vorhersagefunktion**, und fügen Sie die Funktion, `Cluster`.  
  
7.  Für **Quelle**Option **Vorhersagefunktion**, fügen Sie die Funktion, `PredictSupport`, und ziehen Sie die modellspalte [Bike Buyer] in der **Kriterium/Argument** Feld. Geben Sie in der Spalte **Alias** die Zeichenfolge **Support** ein.  
  
     Kopieren Sie den Ausdruck, der die Vorhersagefunktion und den Spaltenverweis vom Feld **Kriterium/Argument** darstellt.  
  
8.  Wählen Sie für **Quelle**die Option **Benutzerdefinierter Ausdruck**aus, geben Sie einen Alias ein, und verweisen Sie dann in Excel mit der folgenden Syntax auf die CEILING-Funktion:  
  
    ```  
    Excel![CEILING](<arguments) as <return type>  
    ```  
  
     Fügen Sie den Spaltenverweis als Argument zur Funktion ein.  
  
     Der folgende Ausdruck gibt beispielsweise den CEILING vom Unterstützungswert zurück:  
  
    ```  
    EXCEL!CEILING(PredictSupport([TM_Clustering].[Bike Buyer]),2)  
    ```  
  
     Geben Sie in der Spalte **Alias** die Zeichenfolge CEILING ein.  
  
9. Klicken Sie auf **Zur Abfragetextsicht wechseln** , um die generierte DMX-Anweisung zu überprüfen. Klicken Sie dann auf **Zur Abfrageergebnissicht wechseln** , um die Spaltenausgabe durch die Vorhersageabfrage zu sehen.  
  
     In der folgenden Tabelle werden die erwarteten Ergebnisse angezeigt:  
  
    |Bike Buyer|$Cluster|Alias|CEILING|  
    |----------------|--------------|-------------|-------------|  
    |0|Cluster 8|954|953.948638926372|  
  
 Wenn Sie die anderen Klauseln an anderer Stelle in der Anweisung hinzufügen möchten-z. B., wenn Sie eine WHERE-Klausel hinzufügen möchten – Sie können nicht mithilfe des Rasters; hinzufügen Sie müssen zuerst zur DMX-Ansicht wechseln.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Abfragen](data-mining-queries.md)  
  
  
