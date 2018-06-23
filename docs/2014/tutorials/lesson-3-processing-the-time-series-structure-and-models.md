---
title: 'Lektion 3: Verarbeiten der Zeitreihenstruktur und-Modelle | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 652d88a0c977b45f6c1628020ae4e6fd8fae4ad9
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312648"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a>Lektion 3: Verarbeiten der Zeitreihenstruktur und -modelle
  In dieser Lektion verwenden Sie die [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx) -Anweisung verarbeitet die Zeitreihe, Miningstrukturen und Miningmodelle, die Sie erstellt haben.  
  
 Wenn Sie eine Miningstruktur verarbeiten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] liest die Quelldaten und erstellt die Strukturen, die die Miningmodelle unterstützen. Nachdem Sie ein Miningmodell und eine Struktur erstellt haben, müssen Sie diese immer zunächst verarbeiten. Wenn Sie die Miningstruktur bei Verwendung der INSERT INTO-Anweisung angegeben, wird die Miningstruktur zusammen mit allen zugehörigen Miningmodellen von der Struktur verarbeitet.  
  
 Wenn Sie einer Miningstruktur, die bereits verarbeitet wurde, ein Miningmodell hinzufügen, können Sie nur das neue Miningmodell mithilfe der `INSERT INTO MINING MODEL`-Anweisung unter Verwendung von vorhandenen Daten verarbeiten.  
  
 Weitere Informationen zum Verarbeiten von Miningmodellen finden Sie unter [Verarbeitung von Anforderungen und Überlegungen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
## <a name="insert-into-statement"></a>INSERT INTO-Anweisung  
 Trainieren der Zeitreihen-Miningstruktur und alle ihr zugeordneten Miningmodelle verwenden die [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx) Anweisung. Der in der Anweisung enthaltene Code umfasst folgende Abschnitte.   
  
-   Identifizieren der Miningstruktur  
  
-   Auflisten der Spalten in der Miningstruktur  
  
-   Definieren der Trainingsdaten  
  
 Folgender Ausdruck ist ein allgemeines Beispiel der `INSERT INTO` Anweisung:  
  
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
  
 In dieser Lektion verwenden Sie `OPENQUERY` zum Definieren der Quelldaten. Weitere Informationen zu anderen Methoden der Definition einer Abfrage für die Quelldaten, finden Sie unter [ &#60;quelldatenabfrage&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgende Aufgabe aus:  
  
-   Verarbeiten der Miningstruktur Forecasting_MIXED_Structure  
  
-   Verarbeiten der verwandten Miningmodelle Forecasting_MIXED, Forecasting_ARIMA und Forecasting_ARTXP  
  
## <a name="processing-the-time-series-mining-structure"></a>Verarbeiten der Zeitreihen-Miningstruktur  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a>So verarbeiten Sie die Miningstruktur sowie verwandte Miningmodelle mithilfe von INSERT INTO  
  
1.  In **Objektexplorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
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
  
     Die Quellabfrage verweist auf die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Datenquelle, die im Beispielprojekt definiert. Diese Datenquelle wird verwendet, um auf die vTimeSeries-Sicht zuzugreifen. Diese Sicht enthält die Quelldaten, die zum Trainieren des Miningmodells verwendet werden. Wenn Sie nicht mit diesem Projekt oder diesen Sichten vertraut sind, finden Sie unter[Lektion 2: erstellen eine Forecasting-Szenarios &#40;Mining-Lernprogramm für fortgeschrittene Data&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).  
  
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
  
7.  In der **speichern unter** (Dialogfeld), suchen Sie den entsprechenden Ordner, und nennen Sie die Datei `ProcessForecastingAll.dmx`.  
  
8.  Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
 Nachdem die Abfrage ausgeführt wurde, können Sie Vorhersagen mit den verarbeiteten Miningmodellen erstellen. In der nächsten Lektion erstellen Sie mehrere Vorhersagen auf Grundlage der Miningmodelle, die Sie erstellt haben.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 4: Erstellen von Zeitreihenvorhersagen mit DMX](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Anforderungen und Überlegungen zur Verarbeitung &#40;Datamining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)   
 [&#60;quelldatenabfrage&#62;](/sql/dmx/source-data-query)   
 [OPENQUERY &AMP;#40;DMX&AMP;#41;](/sql/dmx/source-data-query-openquery)  
  
  
