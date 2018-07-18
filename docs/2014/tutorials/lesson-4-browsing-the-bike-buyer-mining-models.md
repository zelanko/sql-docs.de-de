---
title: 'Lektion 4: Durchsuchen der Bike Buyer-Miningmodells | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8de3c500-f881-42da-a096-b6c03300d58d
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5866ebce4673033bf9be78b81bb65ad705dd331a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278176"
---
# <a name="lesson-4-browsing-the-bike-buyer-mining-models"></a>Lektion 4: Durchsuchen des Bike Buyer-Miningmodells
  In dieser Lektion verwenden Sie die [SELECT (DMX)](/sql/dmx/select-dmx) Anweisung zum Untersuchen des Inhalts in der Decision Tree- und clustering-Miningmodelle modelliert, die Sie im erstellten [Lektion 2: Hinzufügen von Miningmodellen, Bike Buyer-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).  
  
 Die in einem Miningmodell enthaltenen Spalten entsprechen nicht den Spalten, die durch die Miningstruktur definiert werden; stattdessen handelt es sich um eine bestimmte Gruppe von Spalten, die die vom Algorithmus ermittelten Tendenzen und Muster beschreiben. Diese Miningmodellspalten werden beschrieben, der [DMSCHEMA_MINING_MODEL_CONTENT-Rowset](../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md) -Schemarowsets. Beispielsweise enthält die MODEL_NAME-Spalte im Schemarowset für den Inhalt den Namen des Miningmodells. Für ein Clustering-Miningmodell enthält die NODE_CAPTION-Spalte den Namen des jeweiligen Clusters und die NODE_DESCRIPTION-Spalte eine Beschreibung der Merkmale des jeweiligen Clusters. Sie können diese Spalten durchsuchen, indem Sie mit der SELECT FROM \<Modell >. Inhalt in DMX-Anweisung. Sie können diese Anweisung auch verwenden, um die zum Erstellen des Miningmodells verwendeten Daten zu durchsuchen. Drillthrough muss in der Miningstruktur aktiviert sein, um diese Anweisung verwenden zu können. Weitere Informationen zur Anweisung finden Sie unter [SELECT FROM &#60;Modell&#62;. Fällen &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).  
  
 Sie können auch alle Statuswerte einer diskreten Spalte zurückgeben, indem Sie die SELECT DISTINCT-Anweisung verwenden. Wenn Sie diesen Vorgang beispielsweise für eine Geschlechterspalte durchführen, gibt die Abfrage `male` und `female` zurück.  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Durchsuchen des Inhalts der Miningmodelle  
  
-   Zurückgeben der Fälle aus den Quelldaten, die zum Trainieren der Miningmodelle verwendet wurden  
  
-   Prüfen der verschiedenen Status, die für eine bestimmte diskrete Spalte zur Verfügung stehen  
  
## <a name="returning-the-content-of-a-mining-model"></a>Zurückgeben des Inhalts eines Miningmodells  
 In dieser Lektion verwenden Sie die [SELECT FROM &#60;Modell&#62;. Inhalt &#40;DMX&#41; ](/sql/dmx/select-from-model-dimension-content-dmx) Anweisung, um den Inhalt des Clusteringmodells zurückzugeben.  
  
 Im folgenden ist ein allgemeines Beispiel der SELECT FROM \<Modell >. CONTENT-Anweisung:  
  
```  
SELECT <select list> FROM [<mining model>].CONTENT  
WHERE <where clause>  
```  
  
 Die erste Codezeile definiert die vom Inhalt des Miningmodells zurückzugebenden Spalten und das Miningmodell, dem sie zugeordnet sind:  
  
```  
SELECT <select list> FROM [<mining model].CONTENT  
```  
  
 Die .CONTENT-Klausel neben dem Namen des Miningmodells gibt an, dass Inhalt aus dem Miningmodell zurückgegeben werden soll. Weitere Informationen zu den Spalten im Miningmodell enthalten sind, finden Sie unter [DMSCHEMA_MINING_MODEL_CONTENT-Rowset](../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md).  
  
 Optional können Sie die letzte Codezeile zum Filtern der von der Anweisung zurückgegebenen Ergebnisse verwenden:  
  
```  
WHERE <where clause>  
```  
  
 Wenn Sie beispielsweise die Ergebnisse der Abfrage auf die Cluster beschränken möchten, die eine hohe Anzahl von Fällen enthalten, können Sie der SELECT-Anweisung die folgende WHERE-Klausel hinzufügen:  
  
```  
WHERE NODE_SUPPORT > 100  
```  
  
 Weitere Informationen zum Verwenden von WHERE-Anweisung finden Sie unter [wählen &#40;DMX&#41;](/sql/dmx/select-dmx).  
  
#### <a name="to-return-the-content-of-the-clustering-mining-model"></a>So geben Sie den Inhalt des Clustering-Miningmodells zurück  
  
1.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das allgemeine Beispiel der SELECT FROM \<Modell >. CONTENT-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <select list>   
    ```  
  
     durch:  
  
    ```  
    *  
    ```  
  
     Sie können auch ersetzen * mit einer Liste aller Spalten in der [DMSCHEMA_MINING_MODEL_CONTENT-Rowset](../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md).  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining model>]   
    ```  
  
     durch:  
  
    ```  
    [Clustering]  
    ```  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    SELECT * FROM [Clustering].CONTENT  
    ```  
  
5.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
6.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `SELECT_CONTENT.dmx`.  
  
7.  Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
     Die Abfrage gibt den Inhalt des Miningmodells zurück.  
  
## <a name="use-drillthrough"></a>Verwenden von Drillthrough  
 Im nächsten Schritt verwenden Sie die Drillthroughanweisung, um eine Stichprobe der Fälle zurückzugeben, die zum Trainieren des Decision Tree-Miningmodells verwendet wurden. In dieser Lektion verwenden Sie die [SELECT FROM &#60;Modell&#62;. Fällen &#40;DMX&#41; ](/sql/dmx/select-from-model-content-dmx) Anweisung, um den Inhalt des Decision Tree-Modell zurückzugeben.  
  
 Im folgenden ist ein allgemeines Beispiel der SELECT FROM \<Modell >. CASES-Anweisung:  
  
```  
SELECT <select list>   
FROM [<mining model>].CASES  
WHERE IsInNode('<node id>')  
```  
  
 Die erste Codezeile definiert die aus den Quelldaten zurückzugebenden Spalten sowie das Miningmodell, in dem sie enthalten sind:  
  
```  
SELECT <select list> FROM [<mining model>].CASES  
```  
  
 Die .CASES-Klausel gibt an, dass Sie eine Drillthroughabfrage durchführen. Um Drillthrough verwenden zu können, müssen Sie beim Erstellen des Miningmodells Drillthrough aktivieren.  
  
 Die letzte Codezeile ist optional und gibt den Knoten des Miningmodells an, aus dem Sie Fälle anfordern:  
  
```  
WHERE IsInNode('<node id>')  
```  
  
 Weitere Informationen zum Verwenden von WHERE-Anweisung mit IsInNode finden Sie unter [SELECT FROM &#60;Modell&#62;. Fällen &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).  
  
#### <a name="to-return-the-cases-that-were-used-to-train-the-mining-model"></a>So geben Sie die Fälle zurück, die zum Trainieren des Miningmodells verwendet wurden  
  
1.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das allgemeine Beispiel der SELECT FROM \<Modell >. CASES-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <select list>   
    ```  
  
     durch:  
  
    ```  
    *  
    ```  
  
     Sie können * auch durch eine Liste mit beliebigen Spalten aus den Quelldaten ersetzen (z. B. [Bike Buyer]).  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining model>]   
    ```  
  
     durch:  
  
    ```  
    [Decision Tree]  
    ```  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    SELECT *   
    FROM [Decision Tree].CASES  
    ```  
  
5.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
6.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `SELECT_DRILLTHROUGH.dmx`.  
  
7.  Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
     Die Abfrage gibt die Quelldaten zurück, die zum Trainieren des Decision Tree-Miningmodells verwendet wurden.  
  
## <a name="return-the-states-of-a-discrete-mining-model-column"></a>Zurückgeben der Status einer diskreten Miningmodellspalte  
 Im nächsten Schritt verwenden Sie die SELECT DISTINCT-Anweisung, um die möglichen verschiedenen Status in der angegebenen Miningmodellspalte zurückzugeben.  
  
 Die folgende Zeile ist ein allgemeines Beispiel für die SELECT DISTINCT-Anweisung:  
  
```  
SELECT DISTINCT [<column>]   
FROM [<mining model>]  
```  
  
 Die erste Codezeile definiert die Miningmodellspalten, für die die Status zurückgegeben werden:  
  
```  
SELECT DISTINCT [<column>]   
```  
  
 Sie müssen DISTINCT einschließen, damit alle Status der Spalte zurückgegeben werden. Wenn Sie DISTINCT nicht angeben, wird die Anweisung zu einer Abkürzung für eine Vorhersage und gibt den wahrscheinlichsten Status der angegebenen Spalte zurück. Weitere Informationen finden Sie unter [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).  
  
#### <a name="to-return-the-states-of-a-discrete-column"></a>So geben Sie die Status einer diskreten Spalte zurück  
  
1.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das allgemeine Beispiel der SELECT-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    [<column,name>   
    ```  
  
     durch:  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining model>]   
    ```  
  
     durch:  
  
    ```  
    [Decision Tree]  
    ```  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    SELECT DISTINCT [Bike Buyer]   
    FROM [Decision Tree]  
    ```  
  
5.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
6.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `SELECT_DISCRETE.dmx`.  
  
7.  Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
     Die Abfrage gibt die möglichen Status der Bike Buyer-Spalte zurück.  
  
 In der nächsten Lektion sagen Sie mithilfe des Decision Tree-Miningmodells vorher, ob potenzielle Kunden ein Fahrrad kaufen werden.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 5: Ausführen von Vorhersageabfragen](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
  
  
