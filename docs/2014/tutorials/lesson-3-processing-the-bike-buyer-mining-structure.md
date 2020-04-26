---
title: 'Lektion 3: Verarbeiten der Bike Buyer-Mining Struktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e748c2cd-339d-4e82-82f1-be2d0fc41b61
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2e3f85016b32884b9a6b809e28d20d9985f97cd9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62655801"
---
# <a name="lesson-3-processing-the-bike-buyer-mining-structure"></a>Lektion 3: Verarbeiten der Bike Buyer-Miningstruktur
  In dieser Lektion verwenden Sie die INSERT INTO-Anweisung und die vTargetMail-Sicht aus der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Beispieldatenbank, um die Mining Strukturen und Mining Modelle zu verarbeiten, die Sie in [Lektion 1: Erstellen der Bike Buyer-Mining Struktur](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md) und [Lektion 2: Hinzufügen von Mining Modellen zur Bike Buyer-Mining Struktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)erstellt haben.  
  
 Wenn Sie eine Miningstruktur verarbeiten, liest [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Quelldaten und erstellt die Strukturen, die Miningmodelle unterstützen. Wenn Sie ein Miningmodell verarbeiten, werden die von der Miningstruktur definierten Daten über den von Ihnen ausgewählten Data Mining-Algorithmus übergeben. Der Algorithmus sucht nach Trends und Mustern und speichert diese Informationen dann im Miningmodell. Aus diesem Grund enthält das Miningmodell nicht die tatsächlichen Quelldaten, sondern die vom Algorithmus ermittelten Informationen. Weitere Informationen zum Verarbeiten von Mining Modellen finden Sie unter [Verarbeiten von Anforderungen und Überlegungen &#40;Data Mining-&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
 Sie müssen eine Miningstruktur nur dann erneut verarbeiten, wenn Sie eine Strukturspalte oder die Quelldaten ändern. Wenn Sie einer Miningstruktur, die bereits verarbeitet wurde, ein Miningmodell hinzufügen, können Sie das neue Miningmodell mithilfe der INSERT INTO MINING MODEL-Anweisung trainieren.  
  
## <a name="train-structure-template"></a>Trainieren der Strukturvorlage  
 Um die Mining Struktur und die zugehörigen Mining Modelle zu trainieren, verwenden Sie die [INSERT INTO-Anweisung &#40;DMX-&#41;](/sql/dmx/insert-into-dmx) . Der in der Anweisung enthaltene Code umfasst folgende Abschnitte:   
  
-   Identifizieren der Miningstruktur  
  
-   Auflisten der Spalten in der Miningstruktur  
  
-   Definieren der Trainingsdaten  
  
 Es folgt ein allgemeines Beispiel für die INSERT INTO-Anweisung:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 Die erste Codezeile identifiziert die Miningstruktur, die Sie trainieren werden:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 Die nächste Codezeile gibt die Spalten an, die durch die Miningstruktur definiert sind. Sie müssen jede Spalte in der Miningstruktur auflisten, und jede Spalte muss einer in den Quellabfragedaten enthaltenen Spalte zugeordnet werden.  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 Die letzte Codezeile definiert die Daten, die zum Trainieren der Miningstruktur verwendet werden.  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 In dieser Lektion verwenden Sie `OPENQUERY` zum Definieren der Quelldaten. Weitere Informationen zu anderen Methoden zum Definieren der Quell Abfrage finden Sie unter [&#60;Quelldaten Abfrage&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgende Aufgabe aus:  
  
-   Verarbeiten der Bike Buyer-Miningstruktur  
  
## <a name="processing-the-predictive-mining-structure"></a>Verarbeiten der Vorhersageminingstruktur  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>So verarbeiten Sie die Miningstruktur mithilfe von INSERT INTO  
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das Standardbeispiel der INSERT INTO-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining structure name>]   
    ```  
  
     Durch:  
  
    ```  
    Bike Buyer  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure columns>  
    ```  
  
     Durch:  
  
    ```  
    [Customer Key],  
    [Age],  
    [Bike Buyer],  
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
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     Durch:  
  
    ```  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
     Die OPENQUERY-Anweisung verweist auf die [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]-Datenquelle, um auf die vTargetMail-Sicht zuzugreifen. Die Sicht enthält die Quelldaten, die zum Trainieren der Miningmodelle verwendet werden.  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    INSERT INTO MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key],  
       [Age],  
       [Bike Buyer],  
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
    )  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
6.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
7.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `Process Bike Buyer Structure.dmx`.  
  
8.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
 In der nächsten Lektion untersuchen Sie Miningmodellinhalte, die Sie der Miningstruktur in dieser Lektion hinzugefügt haben.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 4: Durchsuchen des Bike Buyer-Miningmodells](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
  
  
