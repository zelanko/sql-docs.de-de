---
title: 'Lektion 4: Durchsuchen der Bike Buyer-Mining Modelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8de3c500-f881-42da-a096-b6c03300d58d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 709df371d840d4b24e420b4fcd08750fd31e8075
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63070889"
---
# <a name="lesson-4-browsing-the-bike-buyer-mining-models"></a>Lektion 4: Durchsuchen des Bike Buyer-Miningmodells
  In dieser Lektion verwenden Sie die SELECT-Anweisung [(DMX)](/sql/dmx/select-dmx) zum Durchsuchen des Inhalts in den Entscheidungsstruktur-und Clustering-Mining Modellen, die Sie in [Lektion 2: Hinzufügen von Mining Modellen zur Vorhersage Mining Struktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)erstellt haben.  
  
 Die in einem Miningmodell enthaltenen Spalten entsprechen nicht den Spalten, die durch die Miningstruktur definiert werden; stattdessen handelt es sich um eine bestimmte Gruppe von Spalten, die die vom Algorithmus ermittelten Tendenzen und Muster beschreiben. Diese Mining Modell Spalten werden im [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset) -Schemarowset beschrieben. Beispielsweise enthält die MODEL_NAME-Spalte im Schemarowset für den Inhalt den Namen des Miningmodells. Für ein Clustering-Miningmodell enthält die NODE_CAPTION-Spalte den Namen des jeweiligen Clusters und die NODE_DESCRIPTION-Spalte eine Beschreibung der Merkmale des jeweiligen Clusters. Sie können diese Spalten durchsuchen, indem Sie die \<> Select from Model verwenden. Die Content-Anweisung in DMX. Sie können diese Anweisung auch verwenden, um die zum Erstellen des Miningmodells verwendeten Daten zu durchsuchen. Drillthrough muss in der Miningstruktur aktiviert sein, um diese Anweisung verwenden zu können. Weitere Informationen zur-Anweisung finden Sie unter [Select from &#60;Model&#62;. Fälle &#40;DMX-&#41;](/sql/dmx/select-from-model-content-dmx).  
  
 Sie können auch alle Statuswerte einer diskreten Spalte zurückgeben, indem Sie die SELECT DISTINCT-Anweisung verwenden. Wenn Sie diesen Vorgang beispielsweise für eine Geschlechterspalte durchführen, gibt die Abfrage `male` und `female` zurück.  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Durchsuchen des Inhalts der Miningmodelle  
  
-   Zurückgeben der Fälle aus den Quelldaten, die zum Trainieren der Miningmodelle verwendet wurden  
  
-   Prüfen der verschiedenen Status, die für eine bestimmte diskrete Spalte zur Verfügung stehen  
  
## <a name="returning-the-content-of-a-mining-model"></a>Zurückgeben des Inhalts eines Miningmodells  
 In dieser Lektion verwenden Sie das [&#62; Select from &#60;Model. Inhalt &#40;DMX-&#41;](/sql/dmx/select-from-model-dimension-content-dmx) Anweisung, um den Inhalt des Clustering-Modells zurückzugeben.  
  
 Im folgenden finden Sie ein allgemeines Beispiel für die SELECT \<from Model->. Inhalts Anweisung:  
  
```  
SELECT <select list> FROM [<mining model>].CONTENT  
WHERE <where clause>  
```  
  
 Die erste Codezeile definiert die vom Inhalt des Miningmodells zurückzugebenden Spalten und das Miningmodell, dem sie zugeordnet sind:  
  
```  
SELECT <select list> FROM [<mining model].CONTENT  
```  
  
 Die .CONTENT-Klausel neben dem Namen des Miningmodells gibt an, dass Inhalt aus dem Miningmodell zurückgegeben werden soll. Weitere Informationen zu den Spalten, die im Mining Modell enthalten sind, finden Sie unter [DMSCHEMA_MINING_MODEL_CONTENT-Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).  
  
 Optional können Sie die letzte Codezeile zum Filtern der von der Anweisung zurückgegebenen Ergebnisse verwenden:  
  
```  
WHERE <where clause>  
```  
  
 Wenn Sie beispielsweise die Ergebnisse der Abfrage auf die Cluster beschränken möchten, die eine hohe Anzahl von Fällen enthalten, können Sie der SELECT-Anweisung die folgende WHERE-Klausel hinzufügen:  
  
```  
WHERE NODE_SUPPORT > 100  
```  
  
 Weitere Informationen zum Verwenden der WHERE-Anweisung finden [Sie unter SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).  
  
#### <a name="to-return-the-content-of-the-clustering-mining-model"></a>So geben Sie den Inhalt des Clustering-Miningmodells zurück  
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das allgemeine Beispiel der SELECT FROM \<Model->. Inhalts Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <select list>   
    ```  
  
     durch:  
  
    ```  
    *  
    ```  
  
     Sie können * auch durch eine Liste aller Spalten ersetzen, die im [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)enthalten sind.  
  
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
  
5.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
6.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `SELECT_CONTENT.dmx`.  
  
7.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
     Die Abfrage gibt den Inhalt des Miningmodells zurück.  
  
## <a name="use-drillthrough"></a>Verwenden von Drillthrough  
 Im nächsten Schritt verwenden Sie die Drillthroughanweisung, um eine Stichprobe der Fälle zurückzugeben, die zum Trainieren des Decision Tree-Miningmodells verwendet wurden. In dieser Lektion verwenden Sie das [&#62; Select from &#60;Model. Fälle &#40;DMX-&#41;](/sql/dmx/select-from-model-content-dmx) Anweisung, um den Inhalt des Entscheidungsstruktur Modells zurückzugeben.  
  
 Im folgenden finden Sie ein allgemeines Beispiel für die SELECT \<from Model->. Cases-Anweisung:  
  
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
  
 Weitere Informationen zum Verwenden der WHERE-Anweisung mit IsInNode finden [Sie unter Select from &#60;Model&#62;. Fälle &#40;DMX-&#41;](/sql/dmx/select-from-model-content-dmx).  
  
#### <a name="to-return-the-cases-that-were-used-to-train-the-mining-model"></a>So geben Sie die Fälle zurück, die zum Trainieren des Miningmodells verwendet wurden  
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das allgemeine Beispiel der SELECT FROM \<Model->. Cases-Anweisung in die leere Abfrage.  
  
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
  
5.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
6.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `SELECT_DRILLTHROUGH.dmx`.  
  
7.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
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
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
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
  
5.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
6.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `SELECT_DISCRETE.dmx`.  
  
7.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
     Die Abfrage gibt die möglichen Status der Bike Buyer-Spalte zurück.  
  
 In der nächsten Lektion sagen Sie mithilfe des Decision Tree-Miningmodells vorher, ob potenzielle Kunden ein Fahrrad kaufen werden.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 5: Ausführen von Vorhersageabfragen](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
  
  
