---
title: 'Lektion 5: Ausführen von Vorhersageabfragen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0037bd2f-aa2d-464b-bf86-b0210f0438b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a5f4d6dd79f62541e207df688349f694680e2421
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62822312"
---
# <a name="lesson-5-executing-prediction-queries"></a>Lektion 5: Ausführen von Vorhersageabfragen
  In dieser Lektion verwenden Sie die [SELECT FROM \<Model > PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) Form der SELECT-Anweisung zum Erstellen von zwei verschiedene Arten von Vorhersagen auf Grundlage der Entscheidungsstruktur Modellieren Sie erstellt haben, im [ Lektion 2: Hinzufügen von Miningmodellen zur Association-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md). Diese Vorhersagetypen werden weiter unten definiert.  
  
 Singleton-Abfrage  
 Verwenden Sie eine SINGLETON-Abfrage, um Ad-hoc-Werte bereitzustellen, wenn Sie Vorhersagen treffen. Sie können beispielsweise bestimmen, ob ein einzelner Kunde wahrscheinlich ein Fahrradkäufer ist, indem Sie Eingaben wie die Pendelstrecke, die Postleitzahl oder die Anzahl der Kinder des Kunden an die Abfrage übergeben. Die SINGLETON-Abfrage gibt basierend auf diesen Eingaben einen Wert zurück, der angibt, wie wahrscheinlich es ist, dass die Person ein Fahrrad kauft.  
  
 Batchabfrage  
 Verwenden Sie eine Batchabfrage, um zu bestimmen, wer in einer Tabelle möglicher Kunden wahrscheinlich ein Fahrrad kaufen wird. Wenn Sie beispielsweise von der Marketingabteilung eine Liste mit Kunden und Kundenattributen erhalten, können Sie mithilfe einer Batchvorhersage bestimmen, wer wahrscheinlich ein Fahrrad kaufen wird.  
  
 Die [SELECT FROM \<Model > PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) Form der SELECT-Anweisung besteht aus drei Teilen:  
  
-   Einer Liste der Miningmodellspalten und Vorhersagefunktionen, die in den Ergebnissen zurückgegeben werden. Die Ergebnisse können auch Eingabespalten aus den Quelldaten enthalten.  
  
-   Der Quellabfrage, die die zum Erstellen einer Vorhersage verwendeten Daten definiert. In einer Batchabfrage könnte dies beispielsweise eine Kundenliste sein.  
  
-   Einer Zuordnung von Miningmodellspalten und Quelldaten. Wenn diese Namen übereinstimmen, können Sie NATURAL-Syntax verwenden und auf die Spaltenzuordnungen verzichten.  
  
 Mithilfe von Vorhersagefunktionen lässt sich die Abfrage zusätzlich optimieren. Vorhersagefunktionen stellen zusätzliche Informationen bereit, z. B. die Wahrscheinlichkeit des Eintreffens einer Vorhersage; außerdem bieten sie Unterstützung für die Vorhersage im Trainings-Dataset. Weitere Informationen zu Vorhersagefunktionen finden Sie unter [Funktionen &#40;DMX&#41;](/sql/dmx/functions-dmx).  
  
 Die Vorhersagen in diesem Lernprogramm basieren auf der ProspectiveBuyer-Tabelle in der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]-Beispieldatenbank. Die ProspectiveBuyer-Tabelle enthält eine Liste potenzieller Kunden und die Merkmale dieser Kunden. Die Kunden in dieser Tabelle sind von den zum Erstellen des Entscheidungsstruktur-Miningmodells verwendeten Kunden unabhängig.  
  
 Vorhersagen können auch mit dem Generator für Vorhersageabfragen in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] erstellt werden.  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Erstellen einer SINGLETON-Abfrage, um zu ermitteln, ob ein bestimmter Kunde wahrscheinlich ein Fahrrad kaufen wird.  
  
-   Erstellen einer Batchabfrage, um zu bestimmen, wer in einer Tabelle möglicher Kunden wahrscheinlich ein Fahrrad kaufen wird.  
  
## <a name="singleton-query"></a>Singleton-Abfrage  
 Der erste Schritt ist die Verwendung der [SELECT FROM &#60;Modell&#62; PREDICTION JOIN &#40;DMX&#41; ](/sql/dmx/select-from-model-cases-dmx) in einer Singleton-Vorhersageabfrage. Es folgt ein allgemeines Beispiel für die SINGLETON-Anweisung:  
  
```  
SELECT <select list> FROM [<mining model name>]   
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
```  
  
 In der ersten Codezeile werden die Spalten des Miningmodells definiert, das die Abfrage zurückgibt, und der Name des Miningmodells angegeben, mit dem die Vorhersage generiert wurde:  
  
```  
SELECT <select list> FROM [<mining model name>]   
```  
  
 In den nächsten Codezeilen werden die Merkmale des Kunden definiert, die Sie zum Erstellen einer Vorhersage verwenden:  
  
```  
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
ORDER BY <expression>  
```  
  
 Wenn Sie NATURAL PREDICTION JOIN angeben, gleicht der Server den Namen jeder Spalte aus dem Modell mit den Namen der Spalten aus der Eingabe ab. Wenn Spaltennamen nicht übereinstimmen, werden die Spalten ignoriert.  
  
#### <a name="to-create-a-singleton-prediction-query"></a>So erstellen Sie eine SINGLETON-Vorhersageabfrage  
  
1.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das allgemeine Beispiel der SINGLETON-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <select list>   
    ```  
  
     durch:  
  
    ```  
    [Bike Buyer] AS Buyer, PredictHistogram([Bike Buyer]) AS Statistics  
    ```  
  
     Die AS-Anweisung wird verwendet, um einen Alias für von der Abfrage zurückgegebene Spalten zu erstellen. Die [PredictHistogram](/sql/dmx/predicthistogram-dmx) Funktion gibt Statistiken zur Vorhersage, einschließlich der Wahrscheinlichkeit und Unterstützungswert zurück. Weitere Informationen zu den Funktionen, die in einer vorhersageanweisung verwendet werden können, finden Sie unter [Funktionen &#40;DMX&#41;](/sql/dmx/functions-dmx).  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining model>]   
    ```  
  
     durch:  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    (SELECT '<value>' AS [<column name>], ...)  AS t  
    ```  
  
     durch:  
  
    ```  
    (SELECT 35 AS [Age],  
      '5-10 Miles' AS [Commute Distance],  
      '1' AS [House Owner Flag],  
      2 AS [Number Cars Owned],  
      2 AS [Total Children]) AS t  
    ```  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    SELECT  
       [Bike Buyer] AS Buyer,  
       PredictHistogram([Bike Buyer]) AS Statistics  
    FROM  
       [Decision Tree]  
    NATURAL PREDICTION JOIN  
    (SELECT 35 AS [Age],  
       '5-10 Miles' AS [Commute Distance],  
       '1' AS [House Owner Flag],  
       2 AS [Number Cars Owned],  
       2 AS [Total Children]) AS t  
    ```  
  
6.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
7.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `Singleton_Query.dmx`.  
  
8.  Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
     Die Abfrage gibt eine Vorhersage dazu zurück, ob ein Kunde mit den angegebenen Merkmalen ein Fahrrad kaufen wird, und sie stellt statistische Informationen zu der betreffenden Vorhersage zur Verfügung.  
  
## <a name="batch-query"></a>Batchabfrage  
 Der nächste Schritt ist die Verwendung der [SELECT FROM &#60;Modell&#62; PREDICTION JOIN &#40;DMX&#41; ](/sql/dmx/select-from-model-cases-dmx) in einer batchvorhersageabfrage. Das folgende Beispiel ist ein allgemeines Beispiel für eine Batchanweisung:  
  
```  
SELECT TOP <number> <select list>   
FROM [<mining model name>]  
PREDICTION JOIN  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
ON <on clause, mapping,>  
WHERE <where clause, boolean expression,>  
ORDER BY <expression>  
```  
  
 Wie in der SINGLETON-Abfrage definieren die ersten beiden Codezeilen die Spalten aus dem von der Abfrage zurückgegebenen Miningmodell sowie aus dem Namen des zum Generieren der Vorhersage verwendeten Miningmodells. Im oberen Bereich \<Anzahl >-Anweisung gibt an, dass die Abfrage nur zurückgeben wird die Anzahl oder die Ergebnisse anhand des \<Anzahl >.  
  
 Die nächsten Codezeilen definieren die Quelldaten, auf denen die Vorhersagen basieren:  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
```  
  
 Für das Abrufen von Quelldaten stehen Ihnen eine Reihe verschiedener Optionen zur Verfügung, jedoch verwenden Sie in diesem Lernprogramm OPENQUERY. Weitere Informationen zu den verfügbaren Optionen finden Sie unter [ &#60;quelldatenabfrage&#62;](/sql/dmx/source-data-query).  
  
 Die nächste Zeile definiert die Zuordnung zwischen den Quellspalten im Miningmodell und den Spalten in den Quelldaten:  
  
```  
ON <column mappings>  
```  
  
 Die WHERE-Klausel filtert die von der Vorhersageabfrage zurückgegebenen Ergebnisse:  
  
```  
WHERE <where clause, boolean expression,>  
```  
  
 Die letzte und optionale Zeile des Codes gibt die Spalte an, nach der die Ergebnisse sortiert werden:  
  
```  
ORDER BY <expression> [DESC|ASC]  
```  
  
 Verwenden Sie ORDER BY in Kombination mit dem obersten Element \<Anzahl >-Anweisung, um die Ergebnisse zu filtern, die zurückgegeben werden. In dieser Vorhersage geben Sie z. B. die obersten 10 Fahrradkäufer zurück (sortiert nach der Wahrscheinlichkeit, dass die Vorhersage richtig ist). Mithilfe der [DESC|ASC]-Syntax können Sie festlegen, in welcher Reihenfolge die Ergebnisse angezeigt werden.  
  
#### <a name="to-create-a-batch-prediction-query"></a>So erstellen Sie eine Batchvorhersageabfrage  
  
1.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das allgemeine Beispiel der Batchanweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <select list>   
    ```  
  
     durch:  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    ```  
  
     Die TOP 10-Klausel gibt an, dass nur die ersten zehn Ergebnisse von der Abfrage zurückgegeben werden. Mit der ORDER BY-Anweisung in dieser Abfrage werden die Ergebnisse nach der Wahrscheinlichkeit, dass die Vorhersage richtig ist, sortiert. Dies bedeutet, dass nur die zehn Ergebnisse mit der höchsten Wahrscheinlichkeit zurückgegeben werden.  
  
4.  Ersetzen Sie den folgenden Platzhalter:  
  
    ```  
    [<mining model>]   
    ```  
  
     Durch den Namen des Modells:  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  Ersetzen Sie die folgende generische OPENQUERY-Anweisung:  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     Durch eine Anweisung, die auf das aktuelle Adventureworks-Data Warehouse verweist, beispielsweise:  
  
    ```  
    OPENQUERY([Adventure Works DW 2014],  
      'SELECT  
        [LastName],  
        [FirstName],  
        [MaritalStatus],  
        [Gender],  
        [YearlyIncome],  
        [TotalChildren],  
        [NumberChildrenAtHome],  
        [Education],  
        [Occupation],  
        [HouseOwnerFlag],  
        [NumberCarsOwned]  
      FROM  
        [dbo].[ProspectiveBuyer]  
      ') AS t  
    ```  
  
6.  Ersetzen Sie die folgende generische Syntax:  
  
    ```  
    <ON clause, mapping,>   
    WHERE <where clause, boolean expression,>  
    ORDER BY <expression>  
    ```  
  
     Durch die Spaltenzuordnungen, die für dieses Modell und Eingabedataset erforderlich sind:  
  
    ```  
    [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
     Geben Sie `DESC` an, um die Ergebnisse mit der höchsten Wahrscheinlichkeit zuerst aufzulisten.  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    FROM  
      [Decision Tree]  
    PREDICTION JOIN  
      OPENQUERY([Adventure Works DW 2014],  
        'SELECT  
          [LastName],  
          [FirstName],  
          [MaritalStatus],  
          [Gender],  
          [YearlyIncome],  
          [TotalChildren],  
          [NumberChildrenAtHome],  
          [Education],  
          [Occupation],  
          [HouseOwnerFlag],  
          [NumberCarsOwned]  
        FROM  
          [dbo].[ProspectiveBuyer]  
        ') AS t  
    ON  
      [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
7.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
8.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `Batch_Prediction.dmx`.  
  
9. Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
     Die Abfrage gibt eine Tabelle mit Kundennamen zurück, eine Vorhersage dazu, ob jeder Kunde ein Fahrrad kaufen wird, und die Wahrscheinlichkeit des Eintreffens der Vorhersage.  
  
 Dies ist der letzte Schritt im Bike Buyer-Lernprogramm. Sie verfügen jetzt über mehrere Miningmodelle, mit denen Sie Ähnlichkeiten zwischen Ihren Kunden untersuchen und vorhersagen können, ob potenzielle Kunden ein Fahrrad kaufen werden.  
  
 Verwenden von DMX in einem Market Basket-Szenario finden Sie unter [Market Basket DMX-Lernprogramm](../../2014/tutorials/market-basket-dmx-tutorial.md).  
  
  
