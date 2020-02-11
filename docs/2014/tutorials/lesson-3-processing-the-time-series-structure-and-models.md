---
title: 'Lektion 3: Verarbeiten der Zeitreihen Struktur und-Modelle | Microsoft-Dokumentation'
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63042876"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a>Lektion 3: Verarbeiten der Zeitreihenstruktur und -modelle
  In dieser Lektion verwenden Sie die [INSERT INTO-Anweisung &#40;DMX-&#41;](/sql/dmx/insert-into-dmx) , um die von Ihnen erstellten Zeitreihen-Mining Strukturen und Mining Modelle zu verarbeiten.  
  
 Wenn Sie eine Miningstruktur verarbeiten, liest [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die Quelldaten und erstellt die Strukturen, die Miningmodelle unterstützen. Nachdem Sie ein Miningmodell und eine Struktur erstellt haben, müssen Sie diese immer zunächst verarbeiten. Wenn Sie die Miningstruktur bei Verwendung der INSERT INTO-Anweisung angegeben, wird die Miningstruktur zusammen mit allen zugehörigen Miningmodellen von der Struktur verarbeitet.  
  
 Wenn Sie einer Miningstruktur, die bereits verarbeitet wurde, ein Miningmodell hinzufügen, können Sie nur das neue Miningmodell mithilfe der `INSERT INTO MINING MODEL`-Anweisung unter Verwendung von vorhandenen Daten verarbeiten.  
  
 Weitere Informationen zum Verarbeiten von Mining Modellen finden Sie unter [Verarbeiten von Anforderungen und Überlegungen &#40;Data Mining-&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
## <a name="insert-into-statement"></a>INSERT INTO-Anweisung  
 Um die Zeitreihen-Mining Struktur und alle zugehörigen Mining Modelle zu trainieren, verwenden Sie die [INSERT INTO-Anweisung &#40;DMX-&#41;](/sql/dmx/insert-into-dmx) . Der in der Anweisung enthaltene Code umfasst folgende Abschnitte.   
  
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
  
 In dieser Lektion verwenden Sie `OPENQUERY` zum Definieren der Quelldaten. Weitere Informationen zu anderen Methoden zum Definieren einer Abfrage für die Quelldaten finden Sie unter [&#60;Quelldaten Abfrage&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgende Aufgabe aus:  
  
-   Verarbeiten der Miningstruktur Forecasting_MIXED_Structure  
  
-   Verarbeiten der verwandten Miningmodelle Forecasting_MIXED, Forecasting_ARIMA und Forecasting_ARTXP  
  
## <a name="processing-the-time-series-mining-structure"></a>Verarbeiten der Zeitreihen-Miningstruktur  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a>So verarbeiten Sie die Miningstruktur sowie verwandte Miningmodelle mithilfe von INSERT INTO  
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
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
  
     Die Quell Abfrage verweist auf [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] die Datenquelle, die im Beispiel Projekt "IntermediateTutorial" definiert ist. Diese Datenquelle wird verwendet, um auf die vTimeSeries-Sicht zuzugreifen. Diese Sicht enthält die Quelldaten, die zum Trainieren des Miningmodells verwendet werden. Wenn Sie mit diesem Projekt oder diesen Sichten nicht vertraut sind, finden Sie weitere Informationen unter[Lektion 2: Erstellung eines Planungs Szenarios &#40;Data Mining ](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)-Lernprogramm für fortgeschrittene&#41;.  
  
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
  
6.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
7.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `ProcessForecastingAll.dmx`.  
  
8.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
 Nachdem die Abfrage ausgeführt wurde, können Sie Vorhersagen mit den verarbeiteten Miningmodellen erstellen. In der nächsten Lektion erstellen Sie mehrere Vorhersagen auf Grundlage der Miningmodelle, die Sie erstellt haben.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 4: Erstellen von Zeitreihenvorhersagen mit DMX](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verarbeitungsanforderungen und Überlegungen &#40;Data Mining-&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)   
 [&#60;Quelldaten Abfrage&#62;](/sql/dmx/source-data-query)   
 [OPENQUERY-&#40;DMX-&#41;](/sql/dmx/source-data-query-openquery)  
  
  
