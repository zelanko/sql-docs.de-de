---
title: 'Lektion 1: Erstellen einer Zeitreihe Miningmodell und Miningstruktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: b201f2b8-9ab5-425b-9ff3-fe321a60a7b7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5ea66ce1ef677e150a93fbd873c8b97f939e19e1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174020"
---
# <a name="lesson-1-creating-a-time-series-mining-model-and-mining-structure"></a>Lektion 1: Erstellen eines Miningmodells und einer Miningstruktur für eine Zeitreihe
  In dieser Lektion erstellen Sie ein Miningmodell, mit dem Sie auf Basis von Vergangenheitsdaten Werte für einen Zeitraum vorhersagen können. Beim Erstellen des Modells wird die zugrunde liegende Struktur automatisch generiert und kann als Basis für weitere Miningmodelle verwendet werden.  
  
 In dieser Lektion wird davon ausgegangen, dass Sie mit Forecasting-Modellen sowie mit den Anforderungen des Microsoft Time Series-Algorithmus vertraut sind. Weitere Informationen finden Sie unter [Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md).  
  
## <a name="create-mining-model-statement"></a>Erstellen von MINING MODEL-Anweisung  
 Um ein Miningmodell direkt erstellen, und die zugrunde liegende Miningstruktur automatisch generieren, verwenden Sie die [CREATE MINING MODEL &#40;DMX&#41; ](/sql/dmx/create-mining-model-dmx) Anweisung. Der in der Anweisung enthaltene Code umfasst folgende Abschnitte:   
  
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
  
 Der Name für die zugrunde liegende Struktur wird von Analysis Services automatisch generiert, indem "_structure" an den Modellnamen angefügt wird. Dadurch ist sichergestellt, dass sich der Strukturname vom Modellnamen unterscheidet. Informationen zum Benennen eines Objekts in DMX finden Sie unter [Bezeichner &#40;DMX&#41;](/sql/dmx/identifiers-dmx).  
  
 Die nächste Codezeile definiert die Schlüsselspalte für das Miningmodell, mit der bei einem Zeitreihenmodell ein Zeitschritt in den Quelldaten eindeutig identifiziert wird. Der Zeitschritt wird identifiziert, mit der `KEY TIME` -Schlüsselwörtern im Anschluss an die Spalte und die Datentypen. Wenn ein Zeitreihenmodell über einen separaten Reihenschlüssel verfügt, wird es anhand des `KEY`-Schlüsselworts identifiziert.  
  
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
  
-   Führen Sie die Abfrage  
  
## <a name="creating-the-query"></a>Erstellen einer Abfrage  
 Im ersten Schritt stellen Sie eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] her und erstellen eine neue DMX-Abfrage in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>So erstellen Sie eine neue DMX-Abfrage in SQL Server Management Studio  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  In der **Herstellen einer Verbindung mit Server** im Dialogfeld für **Servertyp**Option **Analysis Services**. In **Servernamen**, Typ `LocalHost`, oder den Namen der Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , die Sie für diese Lektion herstellen möchten. Klicken Sie auf **Verbinden**.  
  
3.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
## <a name="altering-the-query"></a>Ändern der Abfrage  
 Im nächsten Schritt ändern Sie die CREATE MINING MODEL-Anweisung und erstellen das Miningmodell für Vorhersagen mit der zugrunde liegenden Struktur.  
  
#### <a name="to-customize-the-create-mining-model-statement"></a>So passen Sie die CREATE MINING MODEL-Anweisung an  
  
1.  Kopieren Sie im Abfrage-Editor das allgemeine Beispiel der CREATE MINING MODEL-Anweisung in die leere Abfrage.  
  
2.  Ersetzen Sie Folgendes:  
  
    ```  
    [mining model name]   
    ```  
  
     durch:  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <key columns>  
    ```  
  
     durch:  
  
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
  
     durch:  
  
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
  
     durch:  
  
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
  
6.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
7.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `Forecasting_MIXED.dmx`.  
  
## <a name="executing-the-query"></a>Ausführen der Abfrage  
 Im letzten Schritt führen Sie die Abfrage aus. Nachdem Sie eine Abfrage erstellt und gespeichert haben, muss diese ausgeführt werden, damit das Miningmodell und die Miningstruktur auf dem Server erstellt werden. Weitere Informationen zum Ausführen von Abfragen im Abfrage-Editor finden Sie unter [Datenbank-Engine-Abfrage-Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>So führen Sie die Abfrage aus  
  
-   Klicken Sie im Abfrage-Editor auf der Symbolleiste **Execute**.  
  
     Der Status der Abfrage wird angezeigt, der **Nachrichten** Registerkarte am unteren Rand des Abfrage-Editors nach Abschluss der Ausführung die Anweisung. Die Meldung sollte Folgendes anzeigen:  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     Eine neue Struktur mit dem Namen **Forecasting_MIXED_Structure** jetzt vorhanden ist, auf dem Server, zusammen mit dem verwandten Miningmodell **Forecasting_MIXED**.  
  
 In der nächsten Lektion fügen Sie ein anzuzeigendes Miningmodell die **Forecasting_MIXED** Miningstruktur, die Sie gerade erstellt haben.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Hinzufügen von Miningmodellen zur Zeitreihen-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Mingingmodellinhalt von Zeitreihenmodellen &#40;Analysis Services – Datamining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)   
 [Technische Referenz für den Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
