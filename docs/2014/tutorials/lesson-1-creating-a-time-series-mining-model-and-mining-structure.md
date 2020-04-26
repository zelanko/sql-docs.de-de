---
title: 'Lektion 1: Erstellen eines Zeitreihen-Mining Modells und einer Mining Struktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b201f2b8-9ab5-425b-9ff3-fe321a60a7b7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2513bc3837dd224f6561eb0015ced538ea3add8c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62678451"
---
# <a name="lesson-1-creating-a-time-series-mining-model-and-mining-structure"></a>Lektion 1: Erstellen eines Miningmodells und einer Miningstruktur für eine Zeitreihe
  In dieser Lektion erstellen Sie ein Miningmodell, mit dem Sie auf Basis von Vergangenheitsdaten Werte für einen Zeitraum vorhersagen können. Beim Erstellen des Modells wird die zugrunde liegende Struktur automatisch generiert und kann als Basis für weitere Miningmodelle verwendet werden.  
  
 In dieser Lektion wird davon ausgegangen, dass Sie mit Forecasting-Modellen sowie mit den Anforderungen des Microsoft Time Series-Algorithmus vertraut sind. Weitere Informationen finden Sie unter [Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md).  
  
## <a name="create-mining-model-statement"></a>Create Mining Model-Anweisung  
 Um ein Mining Modell direkt zu erstellen und die zugrunde liegende Mining Struktur automatisch zu generieren, verwenden Sie die Anweisung [Create Mining Model &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx) . Der in der Anweisung enthaltene Code umfasst folgende Abschnitte:   
  
-   Benennen des Modells  
  
-   Definieren des Zeitstempels  
  
-   Definieren der optionalen Reihenschlüsselspalte  
  
-   Definieren der vorhersagbaren Attribute  
  
 Es folgt ein allgemeines Beispiel für die CREATE MINING MODEL-Anweisung:  
  
```  
CREATE MINING MODEL [<Mining Structure Name>]  
(  
   <key columns>,  
   <predictable attribute columns>  
)  
USING <algorithm name>([parameter list])  
WITH DRILLTHROUGH  
```  
  
 Die erste Codezeile definiert den Namen des Miningmodells:  
  
```  
CREATE MINING MODEL [Mining Model Name]  
```  
  
 Der Name für die zugrunde liegende Struktur wird von Analysis Services automatisch generiert, indem "_structure" an den Modellnamen angefügt wird. Dadurch ist sichergestellt, dass sich der Strukturname vom Modellnamen unterscheidet. Weitere Informationen zum Benennen eines Objekts in DMX finden Sie unter Bezeichner [&#40;DMX-&#41;](/sql/dmx/identifiers-dmx).  
  
 Die nächste Codezeile definiert die Schlüsselspalte für das Miningmodell, mit der bei einem Zeitreihenmodell ein Zeitschritt in den Quelldaten eindeutig identifiziert wird. Der Zeit Schritt wird durch die `KEY TIME` Schlüsselwörter nach dem Spaltennamen und den Datentypen identifiziert. Wenn ein Zeitreihenmodell über einen separaten Reihenschlüssel verfügt, wird es anhand des `KEY`-Schlüsselworts identifiziert.  
  
```  
<key columns>  
```  
  
 Die nächste Codezeile definiert die Spalten im Modell, die vorhergesagt werden. Sie können mehrere vorhersagbare Attribute in einem Miningmodell verwenden. Bei mehreren vorhersagbaren Attributen wird vom Microsoft Time Series-Algorithmus eine separate Analyse für jede Reihe generiert:  
  
```  
<predictable attribute columns>  
```  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Erstellen einer neuen leeren Abfrage  
  
-   Ändern der Abfrage zum Erstellen des Miningmodells  
  
-   Ausführen der Abfrage  
  
## <a name="creating-the-query"></a>Erstellen einer Abfrage  
 Im ersten Schritt stellen Sie eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] her und erstellen eine neue DMX-Abfrage in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>So erstellen Sie eine neue DMX-Abfrage in SQL Server Management Studio  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Wählen Sie im Dialogfeld **Verbindung mit Server herstellen** unter **Servertyp**die Option **Analysis Services**aus. Geben Sie unter **Server Name**den Namen ein, oder geben `LocalHost`Sie den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Namen der Instanz von ein, mit der Sie für diese Lektion eine Verbindung herstellen möchten. Klicken Sie auf **Verbinden**.  
  
3.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
## <a name="altering-the-query"></a>Ändern der Abfrage  
 Im nächsten Schritt ändern Sie die CREATE MINING MODEL-Anweisung und erstellen das Miningmodell für Vorhersagen mit der zugrunde liegenden Struktur.  
  
#### <a name="to-customize-the-create-mining-model-statement"></a>So passen Sie die CREATE MINING MODEL-Anweisung an  
  
1.  Kopieren Sie im Abfrage-Editor das allgemeine Beispiel der CREATE MINING MODEL-Anweisung in die leere Abfrage.  
  
2.  Ersetzen Sie Folgendes:  
  
    ```  
    [mining model name]   
    ```  
  
     Durch:  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <key columns>  
    ```  
  
     Durch:  
  
    ```  
    [Reporting Date] DATE KEY TIME,  
    [Model Region] TEXT KEY  
    ```  
  
     Das `TIME KEY`-Schlüsselwort gibt an, dass die ReportingDate-Spalte die Zeitschrittwerte enthält, die zur Sortierung der Werte verwendet werden. Zeitschritte können Daten und Uhrzeiten, ganze Zahlen oder jeder beliebige geordnete Datentyp sein; die Werte müssen lediglich eindeutig und sortiert sein.  
  
     Das `TEXT`-Schlüsselwort und `KEY`-Schlüsselwort geben an, dass die ModelRegion-Spalte einen weiteren Reihenschlüssel enthält. Sie können nur einen Reihenschlüssel verwenden, und die Werte in der Spalte müssen unterschiedlich sein.  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    < predictable attribute columns> )  
    ```  
  
     Durch:  
  
    ```  
    [Quantity] LONG CONTINUOUS PREDICT,  
    [Amount] DOUBLE CONTINUOUS PREDICT  
    )  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    USING <algorithm name>([parameter list])  
    WITH DRILLTHROUGH  
    ```  
  
     Durch:  
  
    ```  
    USING Microsoft_Time_Series(AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
    ```  
  
     Der Algorithmusparameter `AUTO_DETECT_PERIODICITY` = 0,8 gibt an, dass Zyklen in den Daten vom Algorithmus erkannt werden sollen. Das Festlegen dieses Werts näher bei 1 begünstigt die Ermittlung vieler Muster, verlangsamt jedoch die Verarbeitung.  
  
     Der Algorithumsparameter `FORECAST_METHOD` gibt an, dass die Daten mit ARTXP, ARIMA oder einer Kombination aus beiden analysiert werden sollen.  
  
     Das Schlüsselwort `WITH DRILLTHROUGH` gibt an, dass detaillierte Statistiken in den Quelldaten verfügbar sein sollen, sobald das Modell vollständig ist. Diese Klausel muss hinzugefügt werden, wenn Sie das Modell mit dem Microsoft Time Series-Viewer durchsuchen möchten. Für Vorhersagen ist die Klausel nicht erforderlich.  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    CREATE MINING MODEL [Forecasting_MIXED]  
         (  
        [Reporting Date] DATE KEY TIME,  
        [Model Region] TEXT KEY,  
        [Quantity] LONG CONTINUOUS PREDICT,  
        [Amount] DOUBLE CONTINUOUS PREDICT  
        )  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
  
    ```  
  
6.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
7.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `Forecasting_MIXED.dmx`.  
  
## <a name="executing-the-query"></a>Ausführen der Abfrage  
 Im letzten Schritt führen Sie die Abfrage aus. Nachdem Sie eine Abfrage erstellt und gespeichert haben, muss diese ausgeführt werden, damit das Miningmodell und die Miningstruktur auf dem Server erstellt werden. Weitere Informationen zum Ausführen von Abfragen im Abfrage-Editor finden Sie unter [Datenbank-Engine-Abfrage-Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>So führen Sie die Abfrage aus  
  
-   Klicken Sie im Abfrage-Editor auf der Symbolleiste auf **Ausführen**.  
  
     Der Status der Abfrage wird auf der Registerkarte **Nachrichten** unten im Abfrage-Editor angezeigt, nachdem die Ausführung der Anweisung abgeschlossen wurde. Die Meldung sollte Folgendes anzeigen:  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     Auf dem Server ist nun eine neue Struktur mit dem Namen **Forecasting_MIXED_Structure** vorhanden, zusammen mit dem zugehörigen Mining Modell **Forecasting_MIXED**.  
  
 In der nächsten Lektion fügen Sie der **Forecasting_MIXED** Mining Struktur, die Sie soeben erstellt haben, ein Mining Modell hinzu.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Hinzufügen von Miningmodellen zur Miningstruktur für Zeitreihen](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Modell Inhalt von Zeitreihen Modellen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)   
 [Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
