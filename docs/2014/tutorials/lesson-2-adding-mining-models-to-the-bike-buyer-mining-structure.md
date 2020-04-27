---
title: 'Lektion 2: Hinzufügen von Mining Modellen zur Bike Buyer-Mining Struktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 03fe44c5-6452-4ed0-95f6-9682670c0f52
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: de65fb7a85154f607cd8f266faec4621cdc41476
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63131745"
---
# <a name="lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure"></a>Lektion 2: Hinzufügen von Miningmodellen zur Bike Buyer-Miningstruktur
  In dieser Lektion fügen Sie der Bike Buyer-Mining Struktur, die Sie [Lektion 1: Erstellen der Bike Buyer-Mining Struktur](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)erstellt haben, zwei Mining Modelle hinzu. Diese Miningmodelle ermöglichen es Ihnen, mit einem Modell die Daten zu prüfen und mit einem anderen Vorhersagen zu erstellen.  
  
 Um herauszufinden, wie potenzielle Kunden anhand ihrer Merkmale kategorisiert werden können, erstellen Sie ein Mining Modell, das auf dem [Microsoft Clustering-Algorithmus](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)basiert. In einer späteren Lektion prüfen Sie, wie dieser Algorithmus Cluster von Kunden mit ähnlichen Merkmalen ermittelt. So könnten Sie beispielsweise ermitteln, dass bestimmte Kunden nicht weit voneinander entfernt leben, mit dem Fahrrad zur Arbeit fahren und über einen ähnlichen Bildungsstand verfügen. Sie können diese Cluster dazu verwenden, das Beziehungsgefüge zwischen unterschiedlichen Kunden besser zu verstehen. Mithilfe der gewonnenen Informationen können Sie dann eine Marketingstrategie erstellen, die auf bestimmte Kunden abzielt.  
  
 Um vorherzusagen, ob ein potenzieller Kunde wahrscheinlich ein Fahrrad kaufen wird, erstellen Sie ein Mining Modell, das auf dem [Microsoft Decision Trees-Algorithmus](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)basiert. Dieser Algorithmus analysiert die mit allen potenziellen Kunden verknüpften Informationen und sucht Merkmale, die für die Vorhersage, ob diese Kunden ein Fahrrad kaufen werden, hilfreich sein können. Anschließend vergleicht der Algorithmus die Merkmale von Kunden, die in der Vergangenheit ein Fahrrad gekauft haben, mit den Merkmalen potenzieller Neukunden, um zu bestimmen, wie wahrscheinlich es ist, dass diese potenziellen Neukunden ein Fahrrad kaufen werden.  
  
## <a name="alter-mining-structure-statement"></a>ALTER MINING STRUCTURE-Anweisung  
 Um der Mining Struktur ein Mining Modell hinzuzufügen, verwenden Sie die Anweisung [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) . Der in der Anweisung enthaltene Code umfasst folgende Abschnitte:   
  
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
  
 Weitere Informationen zum Benennen eines Objekts in DMX finden Sie unter Bezeichner [&#40;DMX-&#41;](/sql/dmx/identifiers-dmx).  
  
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
  
 Die letzte Codezeile ist optional und definiert einen Filter, der zum Trainieren und Testen des Modells verwendet wird. Weitere Informationen zum Anwenden von Filtern auf Mining Modelle finden Sie unter [Filter für Mining Modelle &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Hinzufügen eines Entscheidungsstruktur-Miningmodells zur Bike Buyer-Struktur mithilfe des [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus  
  
-   Hinzufügen eines Clustering-Miningmodells zur Bike Buyer-Struktur mithilfe des [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus  
  
-   Da Sie Ergebnisse für alle Fälle anzeigen möchten, fügen Sie noch keinen Filter zu einem Modell hinzu.  
  
## <a name="adding-a-decision-tree-mining-model-to-the-structure"></a>Hinzufügen eines Entscheidungsstruktur-Miningmodells zur Struktur  
 Im ersten Schritt müssen Sie ein Miningmodell auf der Basis des [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus hinzufügen.  
  
#### <a name="to-add-a-decision-tree-mining-model"></a>So fügen Sie ein Entscheidungsstruktur-Miningmodell hinzu  
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX** , um den Abfrage-Editor und eine neue, leere Abfrage zu öffnen.  
  
2.  Kopieren Sie das allgemeine Beispiel der ALTER MINING STRUCTURE-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure name>   
    ```  
  
     Durch:  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining model name>   
    ```  
  
     Durch:  
  
    ```  
    Decision Tree  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining model columns>,  
    ```  
  
     Durch:  
  
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
  
     Durch:  
  
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
  
7.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
8.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `DT_Model.dmx`.  
  
9. Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
## <a name="adding-a-clustering-mining-model-to-the-structure"></a>Hinzufügen eines Clustering-Miningmodells zur Struktur  
 Sie können nun der Bike Buyer-Struktur ein Miningmodell hinzufügen, das auf dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering-Algorithmus basiert. Da das Clustering-Miningmodell alle Spalten verwendet, die in der Miningstruktur definiert sind, können Sie der Struktur das Modell vereinfacht hinzufügen, indem Sie darauf verzichten, die Miningspalten zu definieren.  
  
#### <a name="to-add-a-clustering-mining-model"></a>So fügen Sie ein Clustering-Miningmodell hinzu  
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX** , um den Abfrage-Editor zu öffnen und eine neue, leere Abfrage zu öffnen.  
  
2.  Kopieren Sie das allgemeine Beispiel der ALTER MINING STRUCTURE-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure name>   
    ```  
  
     Durch:  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining model>   
    ```  
  
     Durch:  
  
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
  
     Durch:  
  
    ```  
    USING Microsoft_Clustering  
    ```  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Clustering]  
    USING Microsoft_Clustering   
    ```  
  
7.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
8.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `Clustering_Model.dmx`.  
  
9. Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
 In der nächsten Lektion verarbeiten Sie die Modelle und die Miningstruktur.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 3: Verarbeiten der Bike Buyer-Miningstruktur](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
  
  
