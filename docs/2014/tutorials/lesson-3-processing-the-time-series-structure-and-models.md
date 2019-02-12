---
title: 'Lektion 3: Verarbeiten von Time Series-Struktur und Modelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 493d27c9836eb765c655eba5bbb004e4d48cde40
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56026271"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a>Lektion 3: Verarbeiten von Time Series-Struktur und Modelle
  In dieser Lektion verwenden Sie die [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx) -Anweisung verarbeitet die Zeitreihe, Miningstrukturen und Miningmodelle, die Sie erstellt haben.  
  
 Wenn Sie eine Miningstruktur verarbeiten, liest [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Quelldaten und erstellt die Strukturen, die Miningmodelle unterstützen. Nachdem Sie ein Miningmodell und eine Struktur erstellt haben, müssen Sie diese immer zunächst verarbeiten. Wenn Sie die Miningstruktur bei Verwendung der INSERT INTO-Anweisung angegeben, wird die Miningstruktur zusammen mit allen zugehörigen Miningmodellen von der Struktur verarbeitet.  
  
 Wenn Sie einer Miningstruktur, die bereits verarbeitet wurde, ein Miningmodell hinzufügen, können Sie nur das neue Miningmodell mithilfe der `INSERT INTO MINING MODEL`-Anweisung unter Verwendung von vorhandenen Daten verarbeiten.  
  
 Weitere Informationen zum Verarbeiten von Miningmodellen finden Sie unter [Verarbeitung von Anforderungen und Überlegungen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
## <a name="insert-into-statement"></a>INSERT INTO-Anweisung  
 Verwenden Sie zum Trainieren der Zeitreihen-Miningstruktur und alle ihr zugeordneten Miningmodelle die [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx) Anweisung. Der in der Anweisung enthaltene Code umfasst folgende Abschnitte.   
  
-   Identifizieren der Miningstruktur  
  
-   Auflisten der Spalten in der Miningstruktur  
  
-   Definieren der Trainingsdaten  
  
 Das folgende Beispiel ist ein allgemeines Beispiel für die `INSERT INTO`-Anweisung:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY (<source data definition>)  
```  
  
 Die erste Codezeile identifiziert die Miningstruktur, die Sie trainieren werden:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 Die nächsten Codezeilen geben die Spalten an, die durch die Miningstruktur definiert werden. Sie müssen jede Spalte in der Miningstruktur auflisten, und jede Spalte muss einer in den Quellabfragedaten enthaltenen Spalte zugeordnet werden.  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 Die letzten Codezeilen definieren die Daten, die zum Trainieren der Miningstruktur verwendet werden.  
  
```  
OPENQUERY (<source data definition>)  
```  
  
 In dieser Lektion verwenden Sie `OPENQUERY` zum Definieren der Quelldaten. Weitere Informationen zu anderen Methoden zur Definition einer Abfrage für die Quelldaten finden Sie unter [ &#60;quelldatenabfrage&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgende Aufgabe aus:  
  
-   Verarbeiten der Miningstruktur Forecasting_MIXED_Structure  
  
-   Verarbeiten der verwandten Miningmodelle Forecasting_MIXED, Forecasting_ARIMA und Forecasting_ARTXP  
  
## <a name="processing-the-time-series-mining-structure"></a>Verarbeiten der Zeitreihen-Miningstruktur  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a>So verarbeiten Sie die Miningstruktur sowie verwandte Miningmodelle mithilfe von INSERT INTO  
  
1.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das Standardbeispiel der INSERT INTO-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining structure>]  
    ```  
  
     durch:  
  
    ```  
    Forecasting_MIXED_Structure  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure columns>  
    ```  
  
     durch:  
  
    ```  
    [ReportingDate],  
    [ModelRegion]   
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    OPENQUERY(<source data definition>)  
    ```  
  
     durch:  
  
    ```  
    OPENQUERY([Adventure Works DW 2008R2],'SELECT [ReportingDate], [ModelRegion], [Quantity], [Amount]  
    FROM vTimeSeries ORDER BY [ReportingDate]')  
    ```  
  
     Die Quellabfrage verweist auf die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Datenquelle, die im Beispielprojekt definiert. Diese Datenquelle wird verwendet, um auf die vTimeSeries-Sicht zuzugreifen. Diese Sicht enthält die Quelldaten, die zum Trainieren des Miningmodells verwendet werden. Wenn Sie nicht mit diesem Projekt oder diesen Sichten vertraut sind, finden Sie unter[Lektion 2: Erstellen eines Planungserstellungsszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    INSERT INTO MINING STRUCTURE [Forecasting_MIXED_Structure]  
    (  
       [ReportingDate],[ModelRegion],[Quantity],[Amount])  
    )  
    OPENQUERY(  
    [Adventure Works DW 2008R2],  
    'SELECT [ReportingDate],[ModelRegion],[Quantity],[Amount] FROM vTimeSeries ORDER BY [ReportingDate]'  
    )   
    ```  
  
6.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
7.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `ProcessForecastingAll.dmx`.  
  
8.  Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
 Nachdem die Abfrage ausgeführt wurde, können Sie Vorhersagen mit den verarbeiteten Miningmodellen erstellen. In der nächsten Lektion erstellen Sie mehrere Vorhersagen auf Grundlage der Miningmodelle, die Sie erstellt haben.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 4: Erstellen von Zeitreihenvorhersagen mit DMX](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Anforderungen und Überlegungen zur Verarbeitung &#40;Datamining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)   
 [&#60;quelldatenabfrage&#62;](/sql/dmx/source-data-query)   
 [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery)  
  
  
