---
title: 'Lektion 3: Verarbeiten der Market Basket-Miningstruktur | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 095a043f-cf6f-45bb-a021-ae4e1b535c65
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cc4ea28876fa0b52577f0d78e357a3cb1fe0a9bf
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312668"
---
# <a name="lesson-3-processing-the-market-basket-mining-structure"></a>Lektion 3: Verarbeiten der Market Basket-Miningstruktur
  In dieser Lektion verwenden Sie die [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx) -Anweisung und vAssocSeqLineItems sowie vAssocSeqOrders aus der [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Beispieldatenbank beim Verarbeiten der Miningstrukturen und Mining-Modelle, die Sie erstellt [Lektion 1: Erstellen der Market Basket-Miningstruktur](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md) und [Lektion 2: Hinzufügen von Miningmodellen zur der Market Basket-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).  
  
 Wenn Sie eine Miningstruktur verarbeiten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] liest die Quelldaten und erstellt die Strukturen, die die Miningmodelle unterstützen. Wenn Sie ein Miningmodell verarbeiten, werden die von der Miningstruktur definierten Daten über die Datamining-Algorithmus übergeben, die Sie ausgewählt haben. Der Algorithmus sucht nach Trends und Mustern und speichert diese Informationen dann im Miningmodell. Aus diesem Grund enthält das Miningmodell nicht die tatsächlichen Quelldaten, sondern die vom Algorithmus ermittelten Informationen. Weitere Informationen zum Verarbeiten von Miningmodellen finden Sie unter [Verarbeitung von Anforderungen und Überlegungen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
 Sie müssen eine Miningstruktur nur erneut verarbeiten, wenn Sie eine Strukturspalte oder die Quelldaten ändern. Wenn Sie einer Miningstruktur, die bereits verarbeitet wurde, ein Miningmodell hinzufügen, können Sie das neue Miningmodell mithilfe der `INSERT INTO MINING MODEL`-Anweisung für die vorhandenen Daten trainieren.  
  
 Da die Market Basket-Miningstruktur eine geschachtelte Tabelle enthält, müssen Sie die zu trainierenden Miningspalten mithilfe der Struktur der geschachtelten Tabelle definieren und mithilfe des `SHAPE`-Befehls die Abfragen definieren, die die Trainingsdaten aus den Quelltabellen extrahieren.  
  
## <a name="insert-into-statement"></a>INSERT INTO-Anweisung  
 Trainieren der Market Basket-Miningstruktur und ihre zugeordneten Mining-Modelle verwenden die [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx) Anweisung. Der in der Anweisung enthaltene Code umfasst folgende Abschnitte.   
  
-   Identifizieren der Miningstruktur  
  
-   Auflisten der Spalten in der Miningstruktur  
  
-   Definieren der Trainingsdaten mithilfe von `SHAPE`  
  
 Folgender Ausdruck ist ein allgemeines Beispiel der `INSERT INTO` Anweisung:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],'<nested SELECT statement>')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 Die erste Codezeile identifiziert die Miningstruktur, die Sie trainieren werden:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 Die nächsten Codezeilen geben die Spalten an, die durch die Miningstruktur definiert werden. Sie müssen jede Spalte in der Miningstruktur auflisten, und jede Spalte muss einer in den Quellabfragedaten enthaltenen Spalte zugeordnet werden. Sie können `SKIP` verwenden, um Spalten zu ignorieren, die in den Quelldaten, jedoch nicht in der Miningstruktur vorhanden sind. Weitere Informationen zur Verwendung von `SKIP`, finden Sie unter [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx).  
  
```  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
```  
  
 Die letzten Codezeilen definieren die Daten, die zum Trainieren der Miningstruktur verwendet werden. Da die Quelldaten auf zwei Tabellen verteilt sind, verwenden Sie `SHAPE`, um die Tabellen miteinander in Beziehung zu setzen.  
  
```  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],''<nested SELECT statement>'')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 In dieser Lektion verwenden Sie `OPENQUERY` zum Definieren der Quelldaten. Informationen zu anderen Methoden definieren Sie eine Abfrage für die Quelldaten finden Sie unter [ &#60;quelldatenabfrage&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgende Aufgabe aus:  
  
-   Verarbeiten der Market Basket-Miningstruktur  
  
## <a name="processing-the-market-basket-mining-structure"></a>Verarbeiten der Market Basket-Miningstruktur  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>So verarbeiten Sie die Miningstruktur mithilfe von INSERT INTO  
  
1.  In **Objektexplorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das Standardbeispiel der INSERT INTO-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining structure>]  
    ```  
  
     durch:  
  
    ```  
    Market Basket  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure columns>  
    [<nested table>]  
    ( SKIP, <skipped column> )  
    ```  
  
     durch:  
  
    ```  
    [OrderNumber],  
    [Products]   
    (SKIP, [Model])  
    ```  
  
     In der Anweisung verweist `Products` auf die von der SHAPE-Anweisung definierte Products-Tabelle. `SKIP` wird verwendet, um die Model-Spalte zu ignorieren, die in den Quelldaten als Schlüssel existiert, aber nicht von der Miningstruktur verwendet wird.  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    SHAPE {  
      OPENQUERY([<datasource>],'<SELECT statement>') }  
    APPEND  
    (   
      {OPENQUERY([<datasource>],'<nested SELECT statement>')  
    }  
    RELATE [<case key>] TO [<foreign key>]  
    ) AS [<nested table>]  
    ```  
  
     durch:  
  
    ```  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
     Die Quellabfrage verweist auf die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] in definierte Datenquelle die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Beispielprojekt. Sie verwendet diese Datenquelle für den Zugriff auf die Sichten vAssocSeqLineItems und vAssocSeqOrders. Diese Sichten enthalten die Quelldaten, die zum Trainieren des Miningmodells verwendet werden. Wenn Sie dieses Projekt oder diesen Sichten nicht erstellt haben, finden Sie unter [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).  
  
     Im `SHAPE`-Befehl verwenden Sie `OPENQUERY`, um zwei Abfragen zu definieren. Die erste Abfrage definiert die übergeordnete Tabelle und die zweite Abfrage definiert die geschachtelte Tabelle. Die zwei Tabellen werden mithilfe der OrderNumber-Spalte, die in beiden Tabellen vorhanden ist, miteinander in Beziehung gesetzt.  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    INSERT INTO MINING STRUCTURE [Market Basket]  
    (  
       [OrderNumber],[Products] (SKIP, [Model])  
    )  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
6.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
7.  In der **speichern unter** (Dialogfeld), suchen Sie den entsprechenden Ordner, und nennen Sie die Datei `Process Market Basket.dmx`.  
  
8.  Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
 Nachdem die Abfrage ausgeführt wurde, werden die gefundenen Muster und Itemsets sowie die Zuordnungen angezeigt, außerdem können Sie nach Itemset, Wahrscheinlichkeit oder Wichtigkeit filtern. So zeigen Sie diese Informationen in an [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]mit der rechten Maustaste auf den Namen des Datenmodells, und klicken Sie dann auf **Durchsuchen**.  
  
 In der nächsten Lektion erstellen Sie mehrere Vorhersagen auf der Basis des Miningmodells, das Sie der Market Basket-Struktur hinzugefügt haben.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 4: Ausführen von Warenkorbvorhersagen](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
  
  
