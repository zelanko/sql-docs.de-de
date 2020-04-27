---
title: 'Lektion 2: Hinzufügen von Mining Modellen zur Zeitreihen-Mining Struktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 75c2a74b-21ce-44fb-a26b-68be4c685c12
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ae0bb91fafb53c0c077a4e0d82558b550d0e6070
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62855720"
---
# <a name="lesson-2-adding-mining-models-to-the-time-series-mining-structure"></a>Lektion 2: Hinzufügen von Miningmodellen zur Miningstruktur für Zeitreihen
  In dieser Lektion fügen Sie der Mining Struktur, die Sie soeben in [Lektion 1: Erstellen eines Zeitreihen-Mining Modells und einer Mining Struktur](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)erstellt haben, ein neues Mining Modell hinzu.  
  
## <a name="alter-mining-structure-statement"></a>ALTER MINING STRUCTURE-Anweisung  
 Um einer vorhandenen Mining Struktur ein neues Mining Modell hinzuzufügen, verwenden Sie die Anweisung [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) . Der in der Anweisung enthaltene Code umfasst folgende Abschnitte:   
  
-   Identifizieren der Miningstruktur  
  
-   Benennen des Miningmodells  
  
-   Definieren der Schlüsselspalte  
  
-   Definieren der vorhersagbaren Spalten  
  
-   Angeben von Algorithmus- und Parameteränderungen  
  
 Es folgt ein allgemeines Beispiel für die ALTER MINING STRUCTURE-Anweisung:  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
   ([<key columns>],  
    <mining model columns>  
   )  
USING <algorithm name>([<algorithm parameters>])  
[WITH DRILLTHROUGH]  
```  
  
 Die erste Codezeile identifiziert die vorhandene Miningstruktur, der die Miningmodelle hinzugefügt werden:  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 Die nächste Codezeile benennt das Miningmodell, das zur Miningstruktur hinzugefügt wird:  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 Weitere Informationen zum Benennen eines Objekts in DMX finden Sie unter Bezeichner [&#40;DMX-&#41;](/sql/dmx/identifiers-dmx).  
  
 Die nächsten Codezeilen definieren Spalten der Miningstruktur, die vom Miningmodell verwendet werden:  
  
```  
[<key columns>],  
<mining model columns>  
```  
  
 Sie können nur Spalten verwenden, die bereits in der Miningstruktur vorhanden sind; außerdem muss die erste Spalte in der Liste die Schlüsselspalte der Miningstruktur sein.  
  
 Die nächste Codezeile definiert den Miningalgorithmus, der das Miningmodell sowie die Algorithmusparameter generiert, die Sie für den Algorithmus festlegen können. Außerdem wird angegeben, ob ein Drilldown für das Miningmodell möglich ist, um Detaildaten in den Trainingsfällen anzuzeigen:  
  
```  
USING <algorithm name>([<algorithm parameters>])  
WITH DRILLTHROUGH  
```  
  
 Weitere Informationen zu den Algorithmusparametern, die Sie anpassen können, finden Sie unter [Technische Referenz für den Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md).  
  
 Mithilfe der folgenden Syntax können Sie angeben, dass eine Spalte des Miningmodells für Vorhersagen verwendet werden soll:  
  
```  
<mining model column> PREDICT  
```  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Hinzufügen eines neuen Zeitreihen-Miningmodells zur Struktur  
  
-   Ändern der Algorithmusparameter zur Verwendung anderer Analyse- und Vorhersagemethoden  
  
## <a name="adding-an-arima-time-series-model-to-the-structure"></a>Hinzufügen eines ARIMA-Zeitreihenmodells zur Struktur  
 Im ersten Schritt fügen Sie der bestehenden Struktur ein neues &lt;legacyBold&gt;Forecasting&lt;/legacyBold&gt;-Miningmodell hinzu. Zeitreihen-Miningmodelle werden vom [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus standardmäßig mit den Algorithmen ARIMA und ARTXP erstellt, und die Ergebnisse werden kombiniert. Sie können jedoch auch angeben, dass nur ein Algorithmus verwendet wird, oder Sie können die exakte Kombination der Algorithmen festlegen. In diesem Schritt fügen Sie ein neues Modell hinzu, das nur den ARIMA-Algorithmus verwendet. Dieser Algorithmus ist für die langfristige Vorhersage optimiert.  
  
#### <a name="to-add-an-arima-time-series-mining-model"></a>So fügen Sie ein ARIMA-Zeitreihen-Miningmodell hinzu  
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX** , um den Abfrage-Editor und eine neue, leere Abfrage zu öffnen.  
  
2.  Kopieren Sie das allgemeine Beispiel der ALTER MINING STRUCTURE-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure name>   
    ```  
  
     Durch:  
  
    ```  
    [Forecasting_MIXED_Structure]  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining model name>   
    ```  
  
     Durch:  
  
    ```  
    Forecasting_ARIMA  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    <key columns>,  
    ```  
  
     Durch:  
  
    ```  
    [ReportingDate],  
    [ModelRegion]  
    ```  
  
     Eine Wiederholung von Datentypen oder Inhaltstypinformationen, die in der CREATE MINING MODEL-Anweisung bereitgestellt wurden, ist nicht erforderlich. Diese Informationen sind bereits in der Miningstruktur gespeichert.  
  
6.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining model columns>  
    ```  
  
     Durch:  
  
    ```  
    ([Quantity] PREDICT,  
    [Amount] PREDICT  
    )  
    ```  
  
7.  Ersetzen Sie Folgendes:  
  
    ```  
    USING <algorithm name>([<algorithm parameters>])   
    [WITH DRILLTHROUGH]  
    ```  
  
     Durch:  
  
    ```  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
     Die resultierende Anweisung sollte wie folgt aussehen:  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARIMA]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARIMA')  
    WITH DRILLTHROUGH  
    ```  
  
8.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
9. Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `Forecasting_ARIMA.dmx`.  
  
10. Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
## <a name="adding-an-artxp-time-series-model-to-the-structure"></a>Hinzufügen eines ARTXP-Zeitreihenmodells zur Struktur  
 Der ARTXP-Algorithmus ist der Standardalgorithmus für Zeitreihen in SQL Server 2005 und wurde für kurzfristige Vorhersagen optimiert. Um Vorhersagen mit allen drei Algorithmen für Zeitreihen zu vergleichen, fügen Sie ein weiteres Modell auf Basis des ARTXP-Algorithmus hinzu.  
  
#### <a name="to-add-an-artxp-time-series-mining-model"></a>So fügen Sie ein ARTXP-Zeitreihen-Miningmodell hinzu  
  
1.  Kopieren Sie den folgenden Code in ein leeres Abfragefenster.  
  
     Sie müssen nur den Namen des neuen Miningmodells sowie den Wert des FORECAST_METHOD-Parameters ändern; weitere Änderungen sind nicht erforderlich.  
  
    ```  
    ALTER MINING STRUCTURE [Forecasting_MIXED_Structure]  
    ADD MINING MODEL [Forecasting_ARTXP]  
       (  
       ([ReportingDate],  
        [ModelRegion],  
        ([Quantity] PREDICT,  
        [Amount] PREDICT  
       )   
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = .08, FORECAST_METHOD = 'ARTXP')  
    WITH DRILLTHROUGH  
    ```  
  
2.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
3.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `Forecasting_ARTXP.dmx`.  
  
4.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
 In der nächsten Lektion verarbeiten Sie alle Modelle und die Miningstruktur.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 3: Verarbeiten der Zeitreihenstruktur und -modelle](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)   
 [Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
