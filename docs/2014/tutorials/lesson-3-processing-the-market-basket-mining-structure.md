---
title: 'Lektion 3: Verarbeiten der Market Basket-Mining Struktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 095a043f-cf6f-45bb-a021-ae4e1b535c65
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ce2c2e6944d524a38edc331d2cd128ca7cf7d419
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62653853"
---
# <a name="lesson-3-processing-the-market-basket-mining-structure"></a>Lektion 3: Verarbeiten der Market Basket-Miningstruktur
  In dieser Lektion verwenden Sie die [INSERT INTO-Anweisung &#40;DMX-&#41;](/sql/dmx/insert-into-dmx) und die vassoccot qlineitems und vAssoc/qorders aus [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] der-Beispieldatenbank, um die Mining Strukturen und Mining Modelle zu verarbeiten, die Sie in [Lektion 1: Erstellen der Market Basket-Mining Struktur](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md) und [Lektion 2: Hinzufügen von Mining Modellen zur Market Basket-Mining Struktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)erstellen  
  
 Wenn Sie eine Miningstruktur verarbeiten, liest [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Quelldaten und erstellt die Strukturen, die Miningmodelle unterstützen. Wenn Sie ein Mining Modell verarbeiten, werden die Daten, die von der Mining Struktur definiert werden, über den Data Mining Algorithmus, den Sie ausgewählt haben, übermittelt. Der Algorithmus sucht nach Trends und Mustern und speichert diese Informationen dann im Miningmodell. Aus diesem Grund enthält das Miningmodell nicht die tatsächlichen Quelldaten, sondern die vom Algorithmus ermittelten Informationen. Weitere Informationen zum Verarbeiten von Mining Modellen finden Sie unter [Verarbeiten von Anforderungen und Überlegungen &#40;Data Mining-&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
 Sie müssen eine Miningstruktur nur erneut verarbeiten, wenn Sie eine Strukturspalte oder die Quelldaten ändern. Wenn Sie einer Miningstruktur, die bereits verarbeitet wurde, ein Miningmodell hinzufügen, können Sie das neue Miningmodell mithilfe der `INSERT INTO MINING MODEL`-Anweisung für die vorhandenen Daten trainieren.  
  
 Da die Market Basket-Miningstruktur eine geschachtelte Tabelle enthält, müssen Sie die zu trainierenden Miningspalten mithilfe der Struktur der geschachtelten Tabelle definieren und mithilfe des `SHAPE`-Befehls die Abfragen definieren, die die Trainingsdaten aus den Quelltabellen extrahieren.  
  
## <a name="insert-into-statement"></a>INSERT INTO-Anweisung  
 Um die Market Basket-Mining Struktur und die zugehörigen Mining Modelle zu trainieren, verwenden Sie die [INSERT INTO-Anweisung &#40;DMX-&#41;](/sql/dmx/insert-into-dmx) . Der in der Anweisung enthaltene Code umfasst folgende Abschnitte.   
  
-   Identifizieren der Miningstruktur  
  
-   Auflisten der Spalten in der Miningstruktur  
  
-   Definieren der Trainingsdaten mithilfe von `SHAPE`  
  
 Das folgende Beispiel ist ein allgemeines Beispiel für die `INSERT INTO`-Anweisung:  
  
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
  
 Die nächsten Codezeilen geben die Spalten an, die durch die Miningstruktur definiert werden. Sie müssen jede Spalte in der Miningstruktur auflisten, und jede Spalte muss einer in den Quellabfragedaten enthaltenen Spalte zugeordnet werden. Sie können `SKIP` verwenden, um Spalten zu ignorieren, die in den Quelldaten, jedoch nicht in der Miningstruktur vorhanden sind. Weitere Informationen zum verwenden `SKIP`von finden Sie unter [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx).  
  
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
  
 In dieser Lektion verwenden Sie `OPENQUERY` zum Definieren der Quelldaten. Weitere Informationen zu anderen Methoden zum Definieren einer Abfrage für die Quelldaten finden Sie unter [&#60;Quelldaten Abfrage&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgende Aufgabe aus:  
  
-   Verarbeiten der Market Basket-Mining Struktur  
  
## <a name="processing-the-market-basket-mining-structure"></a>Verarbeiten der Market Basket-Miningstruktur  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>So verarbeiten Sie die Miningstruktur mithilfe von INSERT INTO  
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das Standardbeispiel der INSERT INTO-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining structure>]  
    ```  
  
     Durch:  
  
    ```  
    Market Basket  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure columns>  
    [<nested table>]  
    ( SKIP, <skipped column> )  
    ```  
  
     Durch:  
  
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
  
     Durch:  
  
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
  
     Die Quell Abfrage verweist auf [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] die im [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Beispiel Projekt definierte Datenquelle. Sie verwendet diese Datenquelle für den Zugriff auf die Sichten vAssocSeqLineItems und vAssocSeqOrders. Diese Sichten enthalten die Quelldaten, die zum Trainieren des Miningmodells verwendet werden. Wenn Sie dieses Projekt oder diese Sichten nicht erstellt haben, finden Sie weitere Informationen unter [Tutorial zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md).  
  
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
  
6.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
7.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `Process Market Basket.dmx`.  
  
8.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
 Nachdem die Abfrage ausgeführt wurde, werden die gefundenen Muster und Itemsets sowie die Zuordnungen angezeigt, außerdem können Sie nach Itemset, Wahrscheinlichkeit oder Wichtigkeit filtern. Um diese Informationen anzuzeigen, klicken [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]Sie in mit der rechten Maustaste auf den Namen des Datenmodells, und klicken Sie dann auf **Durchsuchen**.  
  
 In der nächsten Lektion erstellen Sie mehrere Vorhersagen auf der Basis des Miningmodells, das Sie der Market Basket-Struktur hinzugefügt haben.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 4: Ausführen von Warenkorbvorhersagen](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
  
  
