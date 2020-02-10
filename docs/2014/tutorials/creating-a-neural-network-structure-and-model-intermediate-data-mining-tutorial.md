---
title: Erstellen einer Struktur und eines Modells für neuronale Netzwerke (Data Mining-Tutorial für Fortgeschrittene) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62856332"
---
# <a name="creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial"></a>Erstellen einer neuronalen Netzwerkstruktur und eines neuronalen Netzwerkmodells (Data Mining-Lernprogramm für Fortgeschrittene)
  Um ein Data Mining-Modell zu erstellen, müssen Sie zuerst mithilfe des Data Mining-Assistenten eine neue Miningstruktur auf Grundlage der neuen Datenquellensicht erstellen. In diesem Task erstellen Sie mit dem Assistenten eine Miningstruktur und zugleich ein zugehöriges Miningmodell auf Grundlage des [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network-Algorithmus.  
  
 Da neuronale Netzwerke äußerst flexibel sind und viele Kombinationen von Eingaben und Ausgaben analysieren können, sollten Sie mit mehreren Methoden der Datenverarbeitung experimentieren, um optimale Ergebnisse zu erhalten. Beispielsweise möchten Sie möglicherweise die Art und Weise anpassen, in der das numerische Ziel für die Dienst Qualität klassifiziert oder *gruppiert wird,* um bestimmte Geschäftsanforderungen zu erfüllen. Hierzu fügen Sie der Miningstruktur eine neue Spalte hinzu, die numerische Daten auf eine andere Weise gruppiert, und erstellen dann ein Modell, das die neue Spalte verwendet. Mithilfe dieser Miningmodelle werden Daten durchsucht.  
  
 Wenn Sie vom neuronalen Netzwerkmodell dann gelernt haben, welche Faktoren sich am stärksten auf Ihre geschäftliche Fragestellung auswirken, erstellen Sie ein separates Modell für die Vorhersage und Bewertung. Sie verwenden hierzu den [!INCLUDE[msCoName](../includes/msconame-md.md)] Logistic Regression-Algorithmus, der auf dem neuronalen Netzwerkmodell basiert, aber für das Suchen nach einer Lösung auf Grundlage von bestimmten Eingaben optimiert ist.  
  
 **Schritte**  
  
 [Erstellen der standardmäßigen Miningstruktur und des Miningmodells](#bkmk_defaul)  
  
 [Verwenden der Diskretisierung zum Klassifizieren der vorhersagbaren Spalte](#bkmk_ColumnCopy)  
  
 [Kopieren der Spalte und Ändern der Diskretisierungsmethode für ein anderes Modell](#bkmk_Alias)  
  
 [Erstellen eines Alias für die vorhersagbare Spalte, damit Modelle verglichen werden können](#bkmk_Alias2)  
  
 [Alle Modelle verarbeiten](#bkmk_SeedProcess)  
  
## Erstellen der standardmäßigen Callcenter-Struktur<a name="bkmk_defaul"></a>  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Projektmappen-Explorer in mit der rechten Maustaste auf **Mining Strukturen** , und wählen Sie **neue Mining Struktur**aus.  
  
2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.  
  
3.  Überprüfen Sie auf der Seite **Definitions Methode auswählen** , ob **aus vorhandener relationaler Datenbank oder Data Warehouse** ausgewählt ist, und klicken Sie dann auf **weiter**.  
  
4.  Vergewissern Sie sich auf der Seite **Data Mining-Struktur erstellen** , dass die Option **Mining Struktur mit einem Mining Modell erstellen** ausgewählt ist.  
  
5.  Klicken Sie in der Dropdown Liste auf die Option **, welche Data Mining Technik Sie verwenden möchten?**, und wählen Sie dann **Microsoft neuronale Netzwerke**aus.  
  
     Da die logistischen Regressionsmodelle auf den neuronalen Netzwerken basieren, können Sie die gleiche Struktur wiederverwenden und ein neues Miningmodell hinzufügen.  
  
6.  Klicken Sie auf **Weiter**.  
  
     Die Seite **Datenquellen Sicht auswählen** wird angezeigt.  
  
7.  Wählen Sie `Call Center`unter **Verfügbare Datenquellen Sichten**die Option aus, und klicken Sie auf **weiter**.  
  
8.  Aktivieren Sie auf der Seite **Tabellentypen angeben** neben der Tabelle **FactCallCenter** das Kontrollkästchen Groß- **/Kleinschreibung** . Wählen Sie für **DimDate**nichts aus. Klicken Sie auf **Weiter**.  
  
9. Wählen Sie auf der Seite **Trainingsdaten angeben** die Option **Schlüssel** neben der Spalte **FactCallCenterID aus.**  
  
10. Aktivieren Sie `Predict` die **Kontrollkästchen und** .  
  
11. Wählen Sie den **Schlüssel**, die **Eingabe**und `Predict` die Kontrollkästchen aus, wie in der folgenden Tabelle gezeigt:  
  
    |Tabellen/Spalten|Schlüssel/Eingabe/Vorhersagen|  
    |---------------------|-------------------------|  
    |AutomaticResponses|Eingabe|  
    |AverageTimePerIssue|Eingabe/Vorhersagen|  
    |Aufrufe|Eingabe|  
    |DateKey|Nicht verwenden|  
    |DayOfWeek|Eingabe|  
    |FactCallCenterID|Key|  
    |IssuesRaised|Eingabe|  
    |LevelOneOperators|Eingabe/Vorhersagen|  
    |LevelTwoOperators|Eingabe|  
    |Aufträge|Eingabe/Vorhersagen|  
    |ServiceGrade|Eingabe/Vorhersagen|  
    |Shift|Eingabe|  
    |TotalOperators|Nicht verwenden|  
    |WageType|Eingabe|  
  
     Beachten Sie, dass mehrere vorhersagbare Spalten ausgewählt wurden. Eine der Stärken des Neural Network-Algorithmus besteht in seiner Fähigkeit, alle möglichen Kombinationen von Eingabe- und Ausgabeattributen zu analysieren. Dies wäre für ein großes Dataset nicht sinnvoll, da es die Verarbeitungszeit exponentiell erhöhen könnte.  
  
12. Überprüfen Sie auf der Seite **Inhalt und Datentyp der Spalten angeben** , ob das Raster die Spalten, Inhaltstypen und Datentypen enthält, wie in der folgenden Tabelle gezeigt, und klicken Sie dann auf **weiter**.  
  
    |Spalten|Inhaltstyp|Datentypen|  
    |-------------|------------------|----------------|  
    |AutomaticResponses|Fortlaufend|Long|  
    |AverageTimePerIssue|Fortlaufend|Long|  
    |Aufrufe|Fortlaufend|Long|  
    |DayOfWeek|Discrete|Text|  
    |FactCallCenterID|Key|Long|  
    |IssuesRaised|Fortlaufend|Long|  
    |LevelOneOperators|Fortlaufend|Long|  
    |LevelTwoOperators|Fortlaufend|Long|  
    |Aufträge|Fortlaufend|Long|  
    |ServiceGrade|Fortlaufend|Double|  
    |Shift|Discrete|Text|  
    |WageType|Discrete|Text|  
  
13. Deaktivieren Sie auf der Seite **Testsatz erstellen** das Textfeld für die Option **Prozentsatz der zu testenden Daten**. Klicken Sie auf **Weiter**.  
  
14. Geben `Call Center`Sie auf der Seite **Assistenten abschließen** für **Mining Struktur Name den Namen**ein.  
  
15. Geben `Call Center Default NN`Sie für **Mining Modellname den Namen**ein, und klicken Sie dann auf **Fertig**stellen.  
  
     Das Kontrollkästchen **Drillthrough zulassen** ist deaktiviert, da Sie keinen Drillthrough zu Daten mit neuronalen Netzwerkmodellen ausführen können.  
  
16. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf den Namen der soeben erstellten Data Mining Struktur, und wählen Sie **verarbeiten**aus.  
  
## <a name="use-discretization-to-bin-the-target-column"></a>Verwenden der Diskretisierung zum Klassifizieren der Zielspalte  
 Wenn Sie ein neuronales Netzwerkmodell erstellen, das über ein numerisches vorhersagbares Attribut verfügt, behandelt der Microsoft Neural Network-Algorithmus das Attribut in der Standardeinstellung als kontinuierliche Zahl. Zum Beispiel ist das ServiceGrade-Attribut eine Zahl, die theoretisch zwischen 0,00 (alle Anrufe werden beantwortet) und 1,00 (alle Anrufer hängen auf) liegt. In diesem Dataset verfügen die Werte über die folgende Verteilung:  
  
 ![Verteilung der Werte für die Dienstqualität](../../2014/tutorials/media/skt-service-grade-valuesc.gif "Verteilung der Werte für die Dienstqualität")  
  
 Bei der Verarbeitung des Modells könnten die Ausgaben daher anders als erwartet gruppiert werden. Wenn Sie z. b. Clustering verwenden, um die besten Gruppen von Werten zu identifizieren, dividiert der Algorithmus die Werte in Service Grade in Bereiche wie diesen: 0,0748051948-0,09716216215. Obwohl diese Gruppierung mathematisch korrekt ist, sind solche Bereiche für Geschäftsbenutzer möglicherweise weniger sinnvoll.  
  
 Um das Ergebnis intuitiver zu gestalten, Gruppieren Sie die numerischen Werte in diesem Schritt anders, und Sie erstellen Kopien der numerischen Datenspalte.  
  
### <a name="how-discretization-works"></a>Funktionsweise der Diskretisierung  
 Analysis Services stellt eine Vielzahl von Methoden zur Klasseneinteilung oder zur Verarbeitung numerischer Daten bereit. In der folgenden Tabelle werden die Unterschiede zwischen den Ergebnissen veranschaulicht, wenn das ServiceGrade-Ausgabeattribut mit drei verschiedenen Methoden verarbeitet wurde:  
  
-   Behandlung als kontinuierliche Zahl.  
  
-   Ermittlung der besten Anordnung von Werten durch Verwendung von Clustering durch den Algorithmus.  
  
-   Angabe, dass die Zahlen durch die Equal Areas-Methode klassifiziert werden.  
  
 Standardmodell (kontinuierlich)  
  
|VALUE|SUPPORT|  
|-----------|-------------|  
|Missing|0|  
|0,09875|120|  
  
 Klassifiziert durch Clustering  
  
|VALUE|SUPPORT|  
|-----------|-------------|  
|\<0,0748051948|34|  
|0,0748051948-0,09716216215|27|  
|0,09716216215-0.13297297295|11,9|  
|0.13297297295 - 0.167499999975|10|  
|>= 0.167499999975|10|  
  
 Klassifiziert durch gleiche Bereiche  
  
|VALUE|SUPPORT|  
|-----------|-------------|  
|\<0,07|26|  
|0,07-0,00|22|  
|0,09-0,11|36|  
|>= 0,12|36|  
  
> [!NOTE]  
>  Diese Statistik kann nach der Verarbeitung aller Daten vom Knoten für Randstatistik des Modells abgerufen werden. Weitere Informationen zum Knoten für Rand Statistik finden Sie unter [Mining Modell Inhalt von neuronalen Netzwerkmodellen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md).  
  
 In dieser Tabelle zeigt die Spalte VALUE an, wie die Zahl für ServiceGrade behandelt wurde. Die Spalte SUPPORT zeigt Ihnen, wie viele Fälle über diesen Wert verfügen oder in diesen Bereich fallen.  
  
-   **Verwenden von fortlaufenden Nummern (Standard)**  
  
     Wenn Sie die Standardmethode verwenden, berechnet der Algorithmus Ergebnisse für 120 unterschiedliche Werte, deren Mittelwert 0.09875 ist. Sie können auch die Anzahl der fehlenden Werte sehen.  
  
-   **Klassifizieren durch Clustering**  
  
     Wenn Sie den Microsoft Clustering-Algorithmus die optionale Gruppierung von Werten bestimmen lassen, gruppiert der Algorithmus die Werte für ServiceGrade in fünf (5) Bereiche. Die Anzahl von Fällen in jedem Bereich ist nicht gleichmäßig verteilt, wie Sie in der Unterstützungsspalte sehen können.  
  
-   **Klassifizieren durch gleiche Bereiche**  
  
     Wenn Sie diese Methode auswählen, zwingt der Algorithmus die Werte in Buckets gleicher Größe, die dann die Ober- und die Untergrenzen jedes Bereichs ändern. Sie können die Anzahl der Buckets angeben, sollten aber vermeiden, dass ein Bucket zu wenige Werte enthält.  
  
 Weitere Informationen zu Klassifizierungs Optionen finden Sie unter [Diskretisierungsmethoden &#40;Data Mining-&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md).  
  
 Anstatt die numerischen Werte zu verwenden, können Sie alternativ eine separate abgeleitete Spalte hinzufügen, die die Dienst Qualitäten in vordefinierte Zielbereiche klassifiziert, z. b. \< **am besten** (Service Grade = 0,05), **akzeptabel** (0,10 > Service Grade > 0,05) und **schlecht** (Service Grade >= 0,10).  
  
###  <a name="bkmk_newColumn"></a>Erstellen einer Kopie einer Spalte und Ändern der Diskretisierungsmethode  
 Erstellen Sie eine Kopie der Mining Spalte, die das Ziel Attribut "Service Grade" enthält, und ändern Sie die Art und Weise, in der die Zahlen gruppiert werden. Sie können mehrere Kopien einer Spalte in einer Miningstruktur erstellen, einschließlich des vorhersagbaren Attributs.  
  
 Für dieses Lernprogramm verwenden Sie die Equal Areas-Methode der Diskretisierung und geben vier Buckets an. Die Gruppierungen, die sich aus dieser Methode ergeben, liegen relativ nah an den Zielwerten, die für Ihre Geschäftsbenutzer von Interesse sind.  
  
####  <a name="bkmk_ColumnCopy"></a>So erstellen Sie eine angepasste Kopie einer Spalte in der Mining Struktur  
  
1.  Doppelklicken Sie im Projektmappen-Explorer auf die soeben erstellte Miningstruktur.  
  
2.  Klicken Sie auf der Registerkarte Mining Struktur auf **Mining Struktur Spalte hinzufügen**.  
  
3.  Wählen Sie im Dialogfeld **Spalte auswählen** in der Liste in der **Spalte Quelle**den Wert Service Grade aus, und klicken Sie dann auf **OK**.  
  
     Der Liste der Miningstrukturspalten wird eine neue Spalte hinzugefügt. In der Standardeinstellung hat die neue Miningspalte den gleichen Namen wie die vorhandene Spalte mit einem numerischen Postfix: z. B. ServiceGrade 1. Sie können den Namen dieser Spalte in einen aussagekräftigeren Namen ändern.  
  
     Geben Sie auch die Diskretisierungsmethode an.  
  
4.  Klicken Sie mit der rechten Maustaste auf Service Grade 1 und dann auf **Eigenschaften**.  
  
5.  Suchen Sie im Fenster **Eigenschaften** die Eigenschaft **Name** , und ändern Sie den Namen in **Service Grade** klassiert.  
  
6.  Im angezeigten Dialogfeld können Sie auswählen, ob Sie die gleiche Änderung für die Namen aller zugehörigen Miningmodellspalten übernehmen möchten. Klicken Sie auf **Nein**.  
  
7.  Suchen Sie im Fenster **Eigenschaften** nach dem **Datentyp** section, und erweitern Sie ihn bei Bedarf.  
  
8.  Ändern Sie den Wert der Eigenschaft `Content` von `Continuous` auf `Discretized`.  
  
     Die folgenden Eigenschaften sind nun verfügbar. Ändern Sie die Werte der Eigenschaften, wie in der folgenden Tabelle angezeigt:  
  
    |Eigenschaft|Standardwert|Neuer Wert|  
    |--------------|-------------------|---------------|  
    |`DiscretizationMethod`|`Continuous`|`EqualAreas`|  
    |`DiscretizationBucketCount`|Kein Wert|4|  
  
    > [!NOTE]  
    >  Der Standardwert von <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> ist eigentlich 0. Das bedeutet, dass der Algorithmus die optimale Anzahl der Buckets automatisch bestimmt. Geben Sie daher 0 ein, wenn Sie den Wert dieser Eigenschaft auf den Standardwert zurücksetzen möchten.  
  
9. Klicken Sie im Data Mining-Designer auf die Registerkarte **Mining Modelle** .  
  
     Beachten Sie, dass beim Hinzufügen einer Kopie einer Miningstrukturspalte das Verwendungsflag der Kopie automatisch auf `Ignore` festgelegt wird. Wenn Sie einer Miningstruktur eine Spaltenkopie hinzufügen, werden Sie in der Regel nicht die Kopie zusammen mit der ursprünglichen Spalte für eine Analyse verwenden. Denn wenn der Algorithmus eine starke Korrelation zwischen den beiden Spalten feststellt, können andere Beziehungen leicht übersehen werden.  
  
##  <a name="bkmk_NewModel"></a>Hinzufügen eines neuen Mining Modells zur Mining Struktur  
 Sie haben nun eine neue Gruppierung für das Zielattribut erstellt und müssen ein neues Miningmodell hinzufügen, das die diskretisierte Spalte verwendet. Wenn dies abgeschlossen ist, verfügt die Callcenter-Miningstruktur über zwei Miningmodelle:  
  
-   Das Miningmodell Callcenterstandard NN behandelt die ServiceGrade-Werte als kontinuierlichen Bereich.  
  
-   Sie erstellen ein neues Mining Modell, Callcenterklassifizierung NN, das als Ziel Ergebnisse die Werte der Service Grade-Spalte verwendet, die in vier Bucket gleicher Größe verteilt werden.  
  
#### <a name="to-add-a-mining-model-based-on-the-new-discretized-column"></a>So fügen Sie ein Miningmodell auf Grundlage der neuen diskretisierten Spalte hinzu  
  
1.  Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf die Mining Struktur, die Sie soeben erstellt haben, und wählen Sie **Öffnen**aus.  
  
2.  Klicken Sie auf die Registerkarte **Miningmodelle** .  
  
3.  Klicken Sie auf Verknüpftes **Mining Modell erstellen**.  
  
4.  Geben `Call Center Binned NN`Sie im Dialogfeld **Neues Mining Modell** für **Modellname den Namen**ein. Wählen Sie in der Dropdown Liste **Algorithmusname** die Option **Microsoft Neural Network**aus.  
  
5.  Suchen Sie in der Liste der Spalten des neuen Miningmodells den Eintrag ServiceGrade, und legen Sie die Verwendung von `Predict` auf `Ignore` fest.  
  
6.  Suchen Sie analog dazu den Eintrag ServiceGrade-Klassifizierung, und legen Sie die Verwendung von `Ignore` auf `Predict` fest.  
  
##  <a name="bkmk_Alias2"></a>Erstellen eines Alias für die Ziel Spalte  
 In der Regel können Sie keine Miningmodelle vergleichen, die unterschiedliche vorhersagbare Attribute verwenden. Sie können jedoch einen Alias für eine Miningmodellspalte erstellen. Das heißt, Sie können die Spalte Service Grade im Mining Modell umbenennen, sodass Sie den gleichen Namen wie die ursprüngliche Spalte hat. Anschließend können Sie diese beiden Modelle trotz der unterschiedlichen Diskretisierung der Daten in einem Genauigkeitsdiagramm direkt vergleichen.  
  
###  <a name="bkmk_Alias"></a>So fügen Sie einen Alias für eine Mining Struktur Spalte in einem Mining Modell hinzu  
  
1.  Wählen Sie auf der Registerkarte **Mining Modelle** unter **Struktur**die Option Service Grade klassiert aus.  
  
     Beachten Sie, dass im **Eigenschaften** Fenster die Eigenschaften des Objekts "scalarminingstructure" angezeigt werden.  
  
2.  Klicken Sie unter der Spalte ServiceGrade-Klassifizierung NN für das Miningmodell auf die Zelle, die der Spalte ServiceGrade-Klassifizierung entspricht.  
  
     Beachten Sie, dass im **Eigenschaften** Fenster nun die Eigenschaften für das Objekt MiningModelColumn angezeigt werden.  
  
3.  Suchen Sie die Eigenschaft **Name** , und ändern Sie den `ServiceGrade`Wert in.  
  
4.  Suchen Sie die Eigenschaft **Beschreibung** , und geben Sie **Temporärer Spaltenalias**ein  
  
     Das Fenster **Eigenschaften** sollte die folgenden Informationen enthalten:  
  
    |Eigenschaft|value|  
    |--------------|-----------|  
    |**Beschreibung**|Temporärer Spaltenalias|  
    |**id**|Klassierte Service Grade|  
    |**Modellierungsflags**||  
    |**Name**|Service Grade|  
    |**SourceColumn-ID**|Service Grade 1|  
    |**Verwendung**|Vorhersagen|  
  
5.  Klicken Sie auf die Registerkarte **Mining Modell** .  
  
     Das Raster wird aktualisiert, um den neuen temporären Spaltenalias `ServiceGrade`neben der Spalten Verwendung anzuzeigen. Das Raster mit der Miningstruktur und zwei Miningmodellen sollte wie folgt aussehen:  
  
    |Struktur|Call Center Default NN|Callcenterklassifizierung NN|  
    |---------------|----------------------------|---------------------------|  
    ||Microsoft Neural Network|Microsoft Neural Network|  
    |AutomaticResponses|Eingabe|Eingabe|  
    |AverageTimePerIssue|Vorhersagen|Vorhersagen|  
    |Aufrufe|Eingabe|Eingabe|  
    |DayOfWeek|Eingabe|Eingabe|  
    |FactCallCenterID|Key|Key|  
    |IssuesRaised|Eingabe|Eingabe|  
    |LevelOneOperators|Eingabe|Eingabe|  
    |LevelTwoOperators|Eingabe|Eingabe|  
    |Aufträge|Eingabe|Eingabe|  
    |ServiceGrade-Klassifizierung|Ignorieren|Vorhersagen (ServiceGrade)|  
    |ServiceGrade|Vorhersagen|Ignorieren|  
    |Shift|Eingabe|Eingabe|  
    |Gesamtzahl Telefonisten|Eingabe|Eingabe|  
    |WageType|Eingabe|Eingabe|  
  
## <a name="process-all-models"></a>Verarbeiten aller Modelle  
 Um abschließend sicherzustellen, dass die erstellten Modelle einfach vergleichbar sind, legen Sie den Parameter für den Zurückhaltungsausgangswert für den Standard und die klassifizierten Modelle fest. Durch das Festlegen eines Ausgangswerts wird sichergestellt, dass in allen Modellen die Verarbeitung der Daten von der gleichen Position aus gestartet wird.  
  
> [!NOTE]  
>  Wenn Sie keinen numerischen Wert für den Ausgangswertparameter angeben, wird dieser in SQL Server Analysis Services anhand des Modellnamens generiert. Da die Modelle immer andere Namen haben, müssen Sie einen Ausgangswert festlegen und so sicherstellen, dass sie die Daten in der gleichen Reihenfolge verarbeiten.  
  
###  <a name="bkmk_SeedProcess"></a>So geben Sie den Seed an und verarbeiten die Modelle  
  
1.  Klicken Sie auf der Registerkarte **Mining Modell** mit der rechten Maustaste auf die Spalte für das Modell "Callcenter-LR", und wählen Sie **Algorithmusparameter festlegen**aus.  
  
2.  Klicken Sie in der Zeile für den HOLDOUT_SEED-Parameter auf die leere Zelle unter **Wert**, `1`und geben Sie ein. Klicken Sie auf **OK**. Wiederholen Sie diesen Schritt für jedes der Struktur zugeordnete Modell.  
  
    > [!NOTE]  
    >  Welchen Wert Sie als Ausgangswert auswählen, ist gleichgültig, solange für alle verwandten Modelle der gleiche Ausgangswert verwendet wird.  
  
3.  Wählen Sie im Menü **Mining Modelle** die Option **Mining Struktur und alle Modelle verarbeiten**aus. Klicken Sie auf **Ja** , um das aktualisierte Data Mining-Projekt auf dem Server bereitzustellen.  
  
4.  Klicken Sie im Dialogfeld **Miningmodell verarbeiten** auf **Ausführen**.  
  
5.  Klicken Sie auf **Schließen** , um das Dialogfeld **Verarbeitungsstatus** zu schließen, und klicken Sie im Dialogfeld **Miningmodell verarbeiten** erneut auf **Schließen** .  
  
 Nachdem Sie nun die zwei zugehörigen Miningmodelle erstellt haben, durchsuchen Sie die Daten auf ihre Beziehungen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Untersuchen des Callcentermodells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Strukturen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
  
