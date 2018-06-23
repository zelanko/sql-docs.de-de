---
title: 'Lektion 3: Verarbeiten der Bike Buyer-Miningstruktur | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e748c2cd-339d-4e82-82f1-be2d0fc41b61
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ae7d871f4695d4109866a6a25979936116838d17
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312638"
---
# <a name="lesson-3-processing-the-bike-buyer-mining-structure"></a>Lektion 3: Verarbeiten der Bike Buyer-Miningstruktur
  In dieser Lektion verwenden Sie die INSERT INTO-Anweisung und die vTargetMail-Sicht aus der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Beispieldatenbank zum Verarbeiten von Miningstrukturen und Miningmodelle, die Sie in erstellt [Lektion 1: Erstellen der Bike Buyer-Miningstruktur](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md) und [Lektion 2: Hinzufügen von Miningmodellen zur Bike Buyer-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).  
  
 Wenn Sie eine Miningstruktur verarbeiten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] liest die Quelldaten und erstellt die Strukturen, die die Miningmodelle unterstützen. Wenn Sie ein Miningmodell verarbeiten, werden die von der Miningstruktur definierten Daten über den von Ihnen ausgewählten Data Mining-Algorithmus übergeben. Der Algorithmus sucht nach Trends und Mustern und speichert diese Informationen dann im Miningmodell. Aus diesem Grund enthält das Miningmodell nicht die tatsächlichen Quelldaten, sondern die vom Algorithmus ermittelten Informationen. Weitere Informationen zum Verarbeiten von Miningmodellen finden Sie unter [Verarbeitung von Anforderungen und Überlegungen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
 Sie müssen eine Miningstruktur nur dann erneut verarbeiten, wenn Sie eine Strukturspalte oder die Quelldaten ändern. Wenn Sie einer Miningstruktur, die bereits verarbeitet wurde, ein Miningmodell hinzufügen, können Sie das neue Miningmodell mithilfe der INSERT INTO MINING MODEL-Anweisung trainieren.  
  
## <a name="train-structure-template"></a>Trainieren der Strukturvorlage  
 Um die Miningstruktur und ihre zugeordneten Mining-Modelle zu trainieren, verwenden Sie die [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx) Anweisung. Der in der Anweisung enthaltene Code umfasst folgende Abschnitte:   
  
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
  
 In dieser Lektion verwenden Sie `OPENQUERY` zum Definieren der Quelldaten. Informationen zu anderen Methoden definieren, die Quellabfrage finden Sie unter [ &#60;quelldatenabfrage&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgende Aufgabe aus:  
  
-   Verarbeiten der Bike Buyer-Miningstruktur  
  
## <a name="processing-the-predictive-mining-structure"></a>Verarbeiten der Vorhersageminingstruktur  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>So verarbeiten Sie die Miningstruktur mithilfe von INSERT INTO  
  
1.  In **Objektexplorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das Standardbeispiel der INSERT INTO-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining structure name>]   
    ```  
  
     durch:  
  
    ```  
    Bike Buyer  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure columns>  
    ```  
  
     durch:  
  
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
  
     durch:  
  
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
  
6.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
7.  In der **speichern unter** (Dialogfeld), suchen Sie den entsprechenden Ordner, und nennen Sie die Datei `Process Bike Buyer Structure.dmx`.  
  
8.  Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
 In der nächsten Lektion untersuchen Sie Miningmodellinhalte, die Sie der Miningstruktur in dieser Lektion hinzugefügt haben.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 4: Durchsuchen des Bike Buyer-Miningmodells](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
  
  
