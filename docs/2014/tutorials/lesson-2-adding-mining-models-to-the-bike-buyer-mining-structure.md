---
title: 'Lektion 2: Hinzufügen von Miningmodellen auf die Bike Buyer-Miningstruktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 03fe44c5-6452-4ed0-95f6-9682670c0f52
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c4191d74e2c9a9e4e84bf87bfd0137a241407d6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222610"
---
# <a name="lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure"></a>Lektion 2: Hinzufügen von Miningmodellen zur Bike Buyer-Miningstruktur
  In dieser Lektion fügen Sie zwei Miningmodelle der Bike Buyer-Miningstruktur, die Sie erstellt [Lektion 1: Erstellen der Bike Buyer-Miningstruktur](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md). Diese Miningmodelle ermöglichen es Ihnen, mit einem Modell die Daten zu prüfen und mit einem anderen Vorhersagen zu erstellen.  
  
 Untersuchen, wie potenzielle Kunden nach ihren Merkmalen kategorisiert werden können, erstellen Sie ein Miningmodell auf Basis der [Microsoft Clustering-Algorithmus](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md). In einer späteren Lektion prüfen Sie, wie dieser Algorithmus Cluster von Kunden mit ähnlichen Merkmalen ermittelt. So könnten Sie beispielsweise ermitteln, dass bestimmte Kunden nicht weit voneinander entfernt leben, mit dem Fahrrad zur Arbeit fahren und über einen ähnlichen Bildungsstand verfügen. Sie können diese Cluster dazu verwenden, das Beziehungsgefüge zwischen unterschiedlichen Kunden besser zu verstehen. Mithilfe der gewonnenen Informationen können Sie dann eine Marketingstrategie erstellen, die auf bestimmte Kunden abzielt.  
  
 Um vorherzusagen, ob ein potenzieller Kunde wahrscheinlich ein Fahrrad kaufen, erstellen Sie ein Miningmodell auf Basis der [Microsoft Decision Trees-Algorithmus](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md). Dieser Algorithmus analysiert die mit allen potenziellen Kunden verknüpften Informationen und sucht Merkmale, die für die Vorhersage, ob diese Kunden ein Fahrrad kaufen werden, hilfreich sein können. Anschließend vergleicht der Algorithmus die Merkmale von Kunden, die in der Vergangenheit ein Fahrrad gekauft haben, mit den Merkmalen potenzieller Neukunden, um zu bestimmen, wie wahrscheinlich es ist, dass diese potenziellen Neukunden ein Fahrrad kaufen werden.  
  
## <a name="alter-mining-structure-statement"></a>ALTER MINING STRUCTURE-Anweisung  
 Um der Miningstruktur ein Miningmodell hinzuzufügen, verwenden Sie die [ALTER MINING STRUCTURE &#40;DMX&#41;] ((~/dmx/alter-mining-structure-dmx.md)-Anweisung. Der in der Anweisung enthaltene Code umfasst folgende Abschnitte:   
  
-   Identifizieren der Miningstruktur  
  
-   Benennen des Miningmodells  
  
-   Definieren der Schlüsselspalte  
  
-   Definieren der Eingabespalten und vorhersagbaren Spalten  
  
-   Identifizieren der Algorithmus- und Parameteränderungen  
  
 Es folgt ein allgemeines Beispiel für die ALTER MINING MODEL-Anweisung:  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
(  
    [<key column>],  
    <mining model columns>,  
) USING <algorithm name>( <algorithm parameters> )  
WITH FILTER (<expression>)  
```  
  
 Die erste Codezeile identifiziert die vorhandene Miningstruktur, der die Miningmodelle hinzugefügt werden:  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 Die nächste Codezeile benennt das Miningmodell, das zur Miningstruktur hinzugefügt wird:  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 Informationen zum Benennen eines Objekts in DMX finden Sie unter [Bezeichner &#40;DMX&#41;](/sql/dmx/identifiers-dmx).  
  
 Die nächsten Codezeilen definieren Spalten der Miningstruktur, die vom Miningmodell verwendet werden:  
  
```  
[<key column>],  
<mining model columns>  
```  
  
 Sie können nur Spalten verwenden, die bereits in der Miningstruktur vorhanden sind; außerdem muss die erste Spalte in der Liste die Schlüsselspalte der Miningstruktur sein.  
  
 Die nächste Codezeile definiert den Miningalgorithmus, der das Miningmodell generiert, und die Algorithmusparameter, die Sie für den Algorithmus festlegen können:  
  
```  
) USING <algorithm name>( <algorithm parameters> )  
```  
  
 Weitere Informationen zu den Algorithmusparametern, die Sie anpassen können, finden Sie unter [Microsoft Decision Trees-Algorithmus](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md) und [Microsoft Clustering-Algorithmus](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md).  
  
 Mithilfe der folgenden Syntax können Sie angeben, dass eine Spalte des Miningmodells für Vorhersagen verwendet werden soll:  
  
```  
<mining model column> PREDICT  
```  
  
 Die letzte Codezeile ist optional und definiert einen Filter, der zum Trainieren und Testen des Modells verwendet wird. Weitere Informationen zum Anwenden von Filtern für Miningmodelle finden Sie unter [Filter für Miningmodelle &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Fügen Sie ein Entscheidungsstruktur-Miningmodells zur Bike Buyer-Struktur mithilfe der [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus  
  
-   Fügen Sie ein clustering-Miningmodells zur Bike Buyer-Struktur mithilfe der [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus  
  
-   Da Sie Ergebnisse für alle Fälle anzeigen möchten, fügen Sie noch keinen Filter zu einem Modell hinzu.  
  
## <a name="adding-a-decision-tree-mining-model-to-the-structure"></a>Hinzufügen eines Entscheidungsstruktur-Miningmodells zur Struktur  
 Der erste Schritt ist zum Hinzufügen eines Miningmodells basierend auf den [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus.  
  
#### <a name="to-add-a-decision-tree-mining-model"></a>So fügen Sie ein Entscheidungsstruktur-Miningmodell hinzu  
  
1.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX** zu Abfrage-Editor und eine neue, leere Abfrage zu öffnen.  
  
2.  Kopieren Sie das allgemeine Beispiel der ALTER MINING STRUCTURE-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure name>   
    ```  
  
     durch:  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining model name>   
    ```  
  
     durch:  
  
    ```  
    Decision Tree  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining model columns>,  
    ```  
  
     durch:  
  
    ```  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ```  
  
     In diesem Fall wurde die `[Bike Buyer]`-Spalte als die PREDICT-Spalte angegeben.  
  
6.  Ersetzen Sie Folgendes:  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )   
    ```  
  
     durch:  
  
    ```  
    Using Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
     Mithilfe der WITH DRILLTHROUGH-Anweisung können Sie die Fälle auswerten, die zum Erstellen des Miningmodells verwendet wurden.  
  
     Die resultierende Anweisung sollte wie folgt aussehen:  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Decision Tree]  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ) USING Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
7.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
8.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `DT_Model.dmx`.  
  
9. Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
## <a name="adding-a-clustering-mining-model-to-the-structure"></a>Hinzufügen eines Clustering-Miningmodells zur Struktur  
 Sie können nun der Bike Buyer-Struktur ein Miningmodell hinzufügen, das auf dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus basiert. Da das Clustering-Miningmodell alle Spalten verwendet, die in der Miningstruktur definiert sind, können Sie der Struktur das Modell vereinfacht hinzufügen, indem Sie darauf verzichten, die Miningspalten zu definieren.  
  
#### <a name="to-add-a-clustering-mining-model"></a>So fügen Sie ein Clustering-Miningmodell hinzu  
  
1.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX** zum Öffnen von Abfrage-Editor wird geöffnet und eine neue, leere Abfrage.  
  
2.  Kopieren Sie das allgemeine Beispiel der ALTER MINING STRUCTURE-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure name>   
    ```  
  
     durch:  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining model>   
    ```  
  
     durch:  
  
    ```  
    Clustering Model  
    ```  
  
5.  Löschen Sie Folgendes:  
  
    ```  
    (  
        [<key column>],  
        <mining model columns>,  
    )  
    ```  
  
6.  Ersetzen Sie Folgendes:  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )  
    ```  
  
     durch:  
  
    ```  
    USING Microsoft_Clustering  
    ```  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Clustering]  
    USING Microsoft_Clustering   
    ```  
  
7.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
8.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `Clustering_Model.dmx`.  
  
9. Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
 In der nächsten Lektion verarbeiten Sie die Modelle und die Miningstruktur.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 3: Verarbeiten der Bike Buyer-Miningstruktur](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
  
  
