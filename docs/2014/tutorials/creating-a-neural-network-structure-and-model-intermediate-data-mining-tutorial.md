---
title: Erstellen einer Struktur des neuronalen Netzwerks und eines Modells (mittleres Datamining Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- DISCRETIZED column
- DiscretizationBuckets property
- DiscretizationMethod property
- EQUAL_AREAS method
ms.assetid: 3f16215c-531e-4ecf-a11f-ee7c6a764463
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6787db165770f944838a312ecd3e0386d161da38
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56037721"
---
# <a name="creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial"></a>Erstellen einer neuronalen Netzwerkstruktur und eines neuronalen Netzwerkmodells (Data Mining-Lernprogramm für Fortgeschrittene)
  Um ein Data Mining-Modell zu erstellen, müssen Sie zuerst mithilfe des Data Mining-Assistenten eine neue Miningstruktur auf Grundlage der neuen Datenquellensicht erstellen. In diesem Task erstellen Sie mit dem Assistenten eine Miningstruktur und zugleich ein zugehöriges Miningmodell auf Grundlage des [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network-Algorithmus.  
  
 Da neuronale Netzwerke äußerst flexibel sind und viele Kombinationen von Eingaben und Ausgaben analysieren können, sollten Sie mit mehreren Methoden der Datenverarbeitung experimentieren, um optimale Ergebnisse zu erhalten. Beispielsweise möchten Sie die Methode anpassen, das numerische Ziel für die Dienstqualität *klassifiziert*, oder gruppiert werden, um bestimmte geschäftsanforderungen zu entsprechen. Hierzu fügen Sie der Miningstruktur eine neue Spalte hinzu, die numerische Daten auf eine andere Weise gruppiert, und erstellen dann ein Modell, das die neue Spalte verwendet. Mithilfe dieser Miningmodelle werden Daten durchsucht.  
  
 Wenn Sie vom neuronalen Netzwerkmodell dann gelernt haben, welche Faktoren sich am stärksten auf Ihre geschäftliche Fragestellung auswirken, erstellen Sie ein separates Modell für die Vorhersage und Bewertung. Sie verwenden hierzu den [!INCLUDE[msCoName](../includes/msconame-md.md)] Logistic Regression-Algorithmus, der auf dem neuronalen Netzwerkmodell basiert, aber für das Suchen nach einer Lösung auf Grundlage von bestimmten Eingaben optimiert ist.  
  
 **Schritte**  
  
 [Erstellen Sie die standardmäßigen Miningstruktur und das Modell](#bkmk_defaul)  
  
 [Verwenden der Diskretisierung zum Klassifizieren der vorhersagbaren Spalte](#bkmk_ColumnCopy)  
  
 [Kopieren Sie die Spalte aus, und Ändern der Diskretisierungsmethode für ein anderes Modell](#bkmk_Alias)  
  
 [Erstellen Sie einen Alias für die vorhersagbare Spalte, damit Modelle verglichen werden können](#bkmk_Alias2)  
  
 [Verarbeiten Sie aller Modelle](#bkmk_SeedProcess)  
  
## Erstellen der Callcenter-Standardstruktur  <a name="bkmk_defaul"></a>  
  
1.  Im Projektmappen-Explorer [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], mit der rechten Maustaste **Miningstrukturen** , und wählen Sie **neue Miningstruktur**.  
  
2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.  
  
3.  Auf der **Definitionsmethode auswählen** überprüfen Sie, ob Seite **aus vorhandener relationaler Datenbank oder Data Warehouse** ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **Erstellen von Data Mining-Struktur** Seite, überprüfen Sie, ob die Option **Miningstruktur mit Miningmodell erstellen** ausgewählt ist.  
  
5.  Klicken Sie auf die Dropdownliste für die Option **welche Datamining-Technik möchten Sie verwenden?**, und wählen Sie dann **Microsoft Neural Networks**.  
  
     Da die logistischen Regressionsmodelle auf den neuronalen Netzwerken basieren, können Sie die gleiche Struktur wiederverwenden und ein neues Miningmodell hinzufügen.  
  
6.  Klicken Sie auf **Weiter**.  
  
     Die **Datenquellensicht auswählen** Seite wird angezeigt.  
  
7.  Klicken Sie unter **verfügbare Datenquellensichten**Option `Call Center`, und klicken Sie auf **Weiter**.  
  
8.  Auf der **Tabellentypen angeben** Seite die **Fall** das Kontrollkästchen neben den **FactCallCenter** Tabelle. Wählen Sie nichts für **DimDate**. Klicken Sie auf **Weiter**.  
  
9. Auf der **Trainingsdaten** Seite **Schlüssel** neben der Spalte **FactCallCenterID.**  
  
10. Wählen Sie die `Predict` und **Eingabe** Kontrollkästchen.  
  
11. Wählen Sie die **Schlüssel**, **Eingabe**, und `Predict` Kontrollkästchen wie in der folgenden Tabelle dargestellt:  
  
    |Tabellen/Spalten|Schlüssel/Eingabe/Vorhersagen|  
    |---------------------|-------------------------|  
    |AutomaticResponses|Eingabe|  
    |AverageTimePerIssue|Eingabe/Vorhersagen|  
    |Aufrufe|Eingabe|  
    |DateKey|Nicht verwenden|  
    |DayOfWeek (TagderWoche)|Eingabe|  
    |FactCallCenterID|Key|  
    |IssuesRaised|Eingabe|  
    |LevelOneOperators|Eingabe/Vorhersagen|  
    |LevelTwoOperators|Eingabe|  
    |Orders|Eingabe/Vorhersagen|  
    |ServiceGrade|Eingabe/Vorhersagen|  
    |Shift|Eingabe|  
    |TotalOperators|Nicht verwenden|  
    |WageType|Eingabe|  
  
     Beachten Sie, dass mehrere vorhersagbare Spalten ausgewählt wurden. Eine der Stärken des Neural Network-Algorithmus besteht in seiner Fähigkeit, alle möglichen Kombinationen von Eingabe- und Ausgabeattributen zu analysieren. Sie nicht empfehlenswert für ein großes DataSet, wie sie die Verarbeitungszeit exponentiell verlängern könnte...  
  
12. Auf der **Inhalt und Datentyp der Spalten angeben** Seite stellen Sie sicher, dass das Raster enthält, die Spalten, Inhaltstypen und Datentypen, wie in der folgenden Tabelle dargestellt, und klicken Sie dann auf **Weiter**.  
  
    |Spalte|Inhaltstyp|Datentypen|  
    |-------------|------------------|----------------|  
    |AutomaticResponses|Continuous|Long|  
    |AverageTimePerIssue|Continuous|Long|  
    |Aufrufe|Continuous|Long|  
    |DayOfWeek (TagderWoche)|Discrete|Textmodus|  
    |FactCallCenterID|Key|Long|  
    |IssuesRaised|Continuous|Long|  
    |LevelOneOperators|Continuous|Long|  
    |LevelTwoOperators|Continuous|Long|  
    |Orders|Continuous|Long|  
    |ServiceGrade|Continuous|Double|  
    |Shift|Discrete|Textmodus|  
    |WageType|Discrete|Textmodus|  
  
13. Auf der **erstellen Tests legen** Seite, deaktivieren Sie im Textfeld für die Option **Prozentsatz der Testdaten**. Klicken Sie auf **Weiter**.  
  
14. Auf der **Abschließen des Assistenten** Seite für die **Miningstrukturname**, Typ `Call Center`.  
  
15. Für die **Miningmodellname**, Typ `Call Center Default NN`, und klicken Sie dann auf **Fertig stellen**.  
  
     Die **Drillthrough zulassen** Feld ist deaktiviert, da Sie Daten mit neuronalen netzwerkmodellen Drillthrough können nicht.  
  
16. Im Projektmappen-Explorer mit der rechten Maustaste des Namens des Datamining-Struktur, die Sie soeben erstellt haben, und wählen **Prozess**.  
  
## <a name="use-discretization-to-bin-the-target-column"></a>Verwenden der Diskretisierung zum Klassifizieren der Zielspalte  
 Wenn Sie ein neuronales Netzwerkmodell erstellen, das über ein numerisches vorhersagbares Attribut verfügt, behandelt der Microsoft Neural Network-Algorithmus das Attribut in der Standardeinstellung als kontinuierliche Zahl. Zum Beispiel ist das ServiceGrade-Attribut eine Zahl, die theoretisch zwischen 0,00 (alle Anrufe werden beantwortet) und 1,00 (alle Anrufer hängen auf) liegt. In diesem Dataset verfügen die Werte über die folgende Verteilung:  
  
 ![Verteilung von Werten für Dienstqualität](../../2014/tutorials/media/skt-service-grade-valuesc.gif "Verteilung von Werten für Dienstqualität")  
  
 Bei der Verarbeitung des Modells könnten die Ausgaben daher anders als erwartet gruppiert werden. Bei Verwendung von clustering Identifizieren der besten Wertegruppen unterteilt der Algorithmus z. B. die Werte in ServiceGrade in Bereiche wie diese: 0.0748051948 - 0.09716216215. Obwohl diese Gruppierung mathematisch korrekt ist, sind solche Bereiche für Geschäftsbenutzer möglicherweise weniger sinnvoll.  
  
 In diesem Schritt werden um das Ergebnis intuitiver, machen Sie die numerischen Werte gruppieren anders und Kopien der numerischen Datenspalte erstellen.  
  
### <a name="how-discretization-works"></a>Funktionsweise der Diskretisierung  
 Analysis Services stellt eine Vielzahl von Methoden zur Klasseneinteilung oder zur Verarbeitung numerischer Daten bereit. In der folgenden Tabelle werden die Unterschiede zwischen den Ergebnissen veranschaulicht, wenn das ServiceGrade-Ausgabeattribut mit drei verschiedenen Methoden verarbeitet wurde:  
  
-   Behandlung als kontinuierliche Zahl.  
  
-   Ermittlung der besten Anordnung von Werten durch Verwendung von Clustering durch den Algorithmus.  
  
-   Angabe, dass die Zahlen durch die Equal Areas-Methode klassifiziert werden.  
  
 Standardmodell (kontinuierlich)  
  
|Value|Alias|  
|-----------|-------------|  
|Missing|0|  
|0.09875|120|  
  
 Klassifiziert durch Clustering  
  
|Value|Alias|  
|-----------|-------------|  
|\< 0.0748051948|34|  
|0.0748051948 - 0.09716216215|27|  
|0.09716216215 - 0.13297297295|39|  
|0.13297297295 - 0.167499999975|10|  
|>= 0.167499999975|10|  
  
 Klassifiziert durch gleiche Bereiche  
  
|Value|Alias|  
|-----------|-------------|  
|\< 0.07|26|  
|0.07 - 0.00|22|  
|0.09 - 0.11|36|  
|>= 0.12|36|  
  
> [!NOTE]  
>  Diese Statistik kann nach der Verarbeitung aller Daten vom Knoten für Randstatistik des Modells abgerufen werden. Weitere Informationen zu den Knoten für randstatistik, finden Sie unter [Mingingmodellinhalt von neuronalen Netzwerkmodellen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md).  
  
 In dieser Tabelle zeigt die Spalte VALUE an, wie die Zahl für ServiceGrade behandelt wurde. Die Spalte SUPPORT zeigt Ihnen, wie viele Fälle über diesen Wert verfügen oder in diesen Bereich fallen.  
  
-   **Verwenden von fortlaufenden Nummern (Standard)**  
  
     Wenn Sie die Standardmethode verwenden, berechnet der Algorithmus Ergebnisse für 120 unterschiedliche Werte, deren Mittelwert 0.09875 ist. Sie können auch die Anzahl der fehlenden Werte sehen.  
  
-   **Klassifizieren durch clustering**  
  
     Wenn Sie den Microsoft Clustering-Algorithmus die optionale Gruppierung von Werten bestimmen lassen, gruppiert der Algorithmus die Werte für ServiceGrade in fünf (5) Bereiche. Die Anzahl von Fällen in jedem Bereich ist nicht gleichmäßig verteilt, wie Sie in der Unterstützungsspalte sehen können.  
  
-   **Klassifizieren durch gleiche Bereiche**  
  
     Wenn Sie diese Methode auswählen, zwingt der Algorithmus die Werte in Buckets gleicher Größe, die dann die Ober- und die Untergrenzen jedes Bereichs ändern. Sie können die Anzahl der Buckets angeben, sollten aber vermeiden, dass ein Bucket zu wenige Werte enthält.  
  
 Weitere Informationen zu klassifizierungsoptionen finden Sie unter [Diskretisierungsmethoden &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md).  
  
 Alternativ, statt die numerischen Werte zu verwenden, können, fügen Sie eine separate abgeleitete Spalte, die die Dienstqualitäten in vordefinierte Zielbereiche, z. B. klassifiziert **bewährte** (ServiceGrade \<= 0,05),  **Zulässige** (0,10 > ServiceGrade > 0,05), und **schlechte** (ServiceGrade > = 0,10).  
  
###  <a name="bkmk_newColumn"></a> Erstellen Sie eine Kopie einer Spalte, und Ändern der Diskretisierungsmethode  
 Sie erstellen eine Kopie der Miningspalte, die das ServiceGrade-Zielattribut enthält und ändern, wie die Nummern gruppiert werden. Sie können mehrere Kopien einer Spalte in einer Miningstruktur erstellen, einschließlich des vorhersagbaren Attributs.  
  
 Für dieses Lernprogramm verwenden Sie die Equal Areas-Methode der Diskretisierung und geben vier Buckets an. Die Gruppierungen, die sich aus dieser Methode ergeben, liegen relativ nah an den Zielwerten, die für Ihre Geschäftsbenutzer von Interesse sind.  
  
####  <a name="bkmk_ColumnCopy"></a> Um eine angepasste Kopie einer Spalte in der Miningstruktur zu erstellen.  
  
1.  Doppelklicken Sie im Projektmappen-Explorer auf die soeben erstellte Miningstruktur.  
  
2.  Klicken Sie auf der Registerkarte Miningstruktur auf **hinzufügen eine Miningstrukturspalte**.  
  
3.  In der **Spalte auswählen** Option ServiceGrade aus der Liste im Dialogfeld **Quellspalte**, klicken Sie dann auf **OK**.  
  
     Der Liste der Miningstrukturspalten wird eine neue Spalte hinzugefügt. In der Standardeinstellung hat die neue Miningspalte den gleichen Namen wie die vorhandene Spalte mit einem numerischen Postfix: z. B. ServiceGrade 1. Sie können den Namen dieser Spalte in einen aussagekräftigeren Namen ändern.  
  
     Geben Sie auch die Diskretisierungsmethode an.  
  
4.  Mit der rechten Maustaste ServiceGrade 1, und wählen Sie **Eigenschaften**.  
  
5.  In der **Eigenschaften** Fenster Suchen der **Namen** -Eigenschaft, und ändern Sie den Namen in **Dienstqualität-Klassifizierung** .  
  
6.  Im angezeigten Dialogfeld können Sie auswählen, ob Sie die gleiche Änderung für die Namen aller zugehörigen Miningmodellspalten übernehmen möchten. Klicken Sie auf **Nein**.  
  
7.  In der **Eigenschaften** Fenster Suchen Sie den Abschnitt **Datentyp** und erweitern Sie ihn bei Bedarf.  
  
8.  Ändern Sie den Wert der Eigenschaft `Content` von `Continuous` auf `Discretized`.  
  
     Die folgenden Eigenschaften sind nun verfügbar. Ändern Sie die Werte der Eigenschaften, wie in der folgenden Tabelle angezeigt:  
  
    |Eigenschaft|Standardwert|Neuer Wert|  
    |--------------|-------------------|---------------|  
    |`DiscretizationMethod`|`Continuous`|`EqualAreas`|  
    |`DiscretizationBucketCount`|Kein Wert|4|  
  
    > [!NOTE]  
    >  Der Standardwert von <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> ist eigentlich 0. Das bedeutet, dass der Algorithmus die optimale Anzahl der Buckets automatisch bestimmt. Geben Sie daher 0 ein, wenn Sie den Wert dieser Eigenschaft auf den Standardwert zurücksetzen möchten.  
  
9. Klicken Sie im Data Mining-Designer auf die **Miningmodelle** Registerkarte.  
  
     Beachten Sie, dass beim Hinzufügen einer Kopie einer Miningstrukturspalte das Verwendungsflag der Kopie automatisch auf `Ignore` festgelegt wird. Wenn Sie einer Miningstruktur eine Spaltenkopie hinzufügen, werden Sie in der Regel nicht die Kopie zusammen mit der ursprünglichen Spalte für eine Analyse verwenden. Denn wenn der Algorithmus eine starke Korrelation zwischen den beiden Spalten feststellt, können andere Beziehungen leicht übersehen werden.  
  
##  <a name="bkmk_NewModel"></a> Fügen Sie der Miningstruktur ein neues Miningmodell hinzu  
 Sie haben nun eine neue Gruppierung für das Zielattribut erstellt und müssen ein neues Miningmodell hinzufügen, das die diskretisierte Spalte verwendet. Wenn dies abgeschlossen ist, verfügt die Callcenter-Miningstruktur über zwei Miningmodelle:  
  
-   Das Miningmodell Callcenterstandard NN behandelt die ServiceGrade-Werte als kontinuierlichen Bereich.  
  
-   Erstellen Sie ein neues Miningmodell Callcenterklassifizierung NN, die als Zielergebnisse die Werte der Spalte ServiceGrade in vier Buckets gleicher Größe verteilt verwendet.  
  
#### <a name="to-add-a-mining-model-based-on-the-new-discretized-column"></a>So fügen Sie ein Miningmodell auf Grundlage der neuen diskretisierten Spalte hinzu  
  
1.  Im Projektmappen-Explorer mit der rechten Maustaste der Miningstruktur, die Sie soeben erstellt haben, und wählen **öffnen**.  
  
2.  Klicken Sie auf die Registerkarte **Miningmodelle** .  
  
3.  Klicken Sie auf **ein verknüpftes Miningmodell erstellen**.  
  
4.  In der **Neues Miningmodell** im Dialogfeld für **Modellname**, Typ `Call Center Binned NN`. In der **Algorithmusname** Dropdownliste **Microsoft Neural Network**.  
  
5.  Suchen Sie in der Liste der Spalten des neuen Miningmodells den Eintrag ServiceGrade, und legen Sie die Verwendung von `Predict` auf `Ignore` fest.  
  
6.  Suchen Sie analog dazu den Eintrag ServiceGrade-Klassifizierung, und legen Sie die Verwendung von `Ignore` auf `Predict` fest.  
  
##  <a name="bkmk_Alias2"></a> Erstellen eines Alias für die Zielspalte  
 In der Regel können Sie keine Miningmodelle vergleichen, die unterschiedliche vorhersagbare Attribute verwenden. Sie können jedoch einen Alias für eine Miningmodellspalte erstellen. Also können Sie die Spalte ServiceGrade-Klassifizierung, in dem Miningmodell umbenennen, sodass er den gleichen Namen wie die ursprüngliche Spalte aufweist. Anschließend können Sie diese beiden Modelle trotz der unterschiedlichen Diskretisierung der Daten in einem Genauigkeitsdiagramm direkt vergleichen.  
  
###  <a name="bkmk_Alias"></a> Um einen Alias für eine Miningstrukturspalte in einem Miningmodell hinzuzufügen.  
  
1.  In der **Miningmodelle** Registerkarte **Struktur**, Eintrag ServiceGrade-Klassifizierung.  
  
     Beachten Sie, dass die **Eigenschaften** Fenster zeigt die Eigenschaften des ScalarMiningStructureColumn-Objekts.  
  
2.  Klicken Sie unter der Spalte ServiceGrade-Klassifizierung NN für das Miningmodell auf die Zelle, die der Spalte ServiceGrade-Klassifizierung entspricht.  
  
     Beachten Sie, die jetzt den **Eigenschaften** Fenster zeigt die Eigenschaften des MiningModelColumn-Objekts.  
  
3.  Suchen Sie die **Namen** -Eigenschaft, und ändern Sie den Wert auf `ServiceGrade`.  
  
4.  Suchen Sie die **Beschreibung** Eigenschaft, und geben **temporärer Spaltenalias**.  
  
     Die **Eigenschaften** Fenster sollte Folgendes enthalten:  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Beschreibung**|Temporärer Spaltenalias|  
    |**ID**|ServiceGrade-Klassifizierung|  
    |**Modellierungsflags**||  
    |**Name**|Service Grade|  
    |**SourceColumn-ID**|Service Grade 1|  
    |**Usage**|Vorhersagen|  
  
5.  Klicken Sie auf eine beliebige Stelle der **Miningmodell** Registerkarte.  
  
     Das Raster wird aktualisiert, um die neue temporäre Spaltenalias `ServiceGrade`, neben der Spaltenverwendung. Das Raster mit der Miningstruktur und zwei Miningmodellen sollte wie folgt aussehen:  
  
    |Struktur|Call Center Default NN|Callcenterklassifizierung NN|  
    |---------------|----------------------------|---------------------------|  
    ||Microsoft Neural Network|Microsoft Neural Network|  
    |AutomaticResponses|Eingabe|Eingabe|  
    |AverageTimePerIssue|Vorhersagen|Vorhersagen|  
    |Aufrufe|Eingabe|Eingabe|  
    |DayOfWeek (TagderWoche)|Eingabe|Eingabe|  
    |FactCallCenterID|Key|Key|  
    |IssuesRaised|Eingabe|Eingabe|  
    |LevelOneOperators|Eingabe|Eingabe|  
    |LevelTwoOperators|Eingabe|Eingabe|  
    |Orders|Eingabe|Eingabe|  
    |ServiceGrade-Klassifizierung|Ignorieren|Vorhersagen (ServiceGrade)|  
    |ServiceGrade|Vorhersagen|Ignorieren|  
    |Shift|Eingabe|Eingabe|  
    |Gesamtzahl Telefonisten|Eingabe|Eingabe|  
    |WageType|Eingabe|Eingabe|  
  
## <a name="process-all-models"></a>Verarbeiten aller Modelle  
 Um abschließend sicherzustellen, dass die erstellten Modelle einfach vergleichbar sind, legen Sie den Parameter für den Zurückhaltungsausgangswert für den Standard und die klassifizierten Modelle fest. Durch das Festlegen eines Ausgangswerts wird sichergestellt, dass in allen Modellen die Verarbeitung der Daten von der gleichen Position aus gestartet wird.  
  
> [!NOTE]  
>  Wenn Sie keinen numerischen Wert für den Ausgangswertparameter angeben, wird dieser in SQL Server Analysis Services anhand des Modellnamens generiert. Da die Modelle immer andere Namen haben, müssen Sie einen Ausgangswert festlegen und so sicherstellen, dass sie die Daten in der gleichen Reihenfolge verarbeiten.  
  
###  <a name="bkmk_SeedProcess"></a> Geben Sie den Ausgangswert und die Modelle verarbeiten  
  
1.  In der **Miningmodell** , mit der rechten Maustaste der Spalte, für das Modell mit dem Namen Callcenter - LR, und wählen Sie **Algorithmusparameter festlegen**.  
  
2.  Klicken Sie in der Zeile für den HOLDOUT_SEED-Parameter, auf die leere Zelle unter **Wert**, und geben `1`. Klicken Sie auf **OK**. Wiederholen Sie diesen Schritt für jedes der Struktur zugeordnete Modell.  
  
    > [!NOTE]  
    >  Welchen Wert Sie als Ausgangswert auswählen, ist gleichgültig, solange für alle verwandten Modelle der gleiche Ausgangswert verwendet wird.  
  
3.  In der **Miningmodelle** , wählen Sie im Menü **Miningstruktur verarbeiten und alle Modelle**. Klicken Sie auf **Ja** , um das aktualisierte Data Mining-Projekt auf dem Server bereitzustellen.  
  
4.  Klicken Sie im Dialogfeld **Miningmodell verarbeiten** auf **Ausführen**.  
  
5.  Klicken Sie auf **Schließen** , um das Dialogfeld **Verarbeitungsstatus** zu schließen, und klicken Sie im Dialogfeld **Miningmodell verarbeiten** erneut auf **Schließen** .  
  
 Nachdem Sie nun die zwei zugehörigen Miningmodelle erstellt haben, durchsuchen Sie die Daten auf ihre Beziehungen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Untersuchen des Callcentermodells &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
  
