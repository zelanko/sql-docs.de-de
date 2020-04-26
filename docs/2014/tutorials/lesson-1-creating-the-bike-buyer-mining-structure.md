---
title: 'Lektion 1: Erstellen der Bike Buyer-Mining Struktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a73ac60b-660f-458a-bd2f-993fbeba7226
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6384910858d87a80aa3c8f897bc88e45f4504fb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62678503"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a>Lektion 1: Erstellen der Bike Buyer-Miningstruktur
  In dieser Lektion erstellen Sie eine Miningstruktur, mit der sich vorhersagen lässt, ob ein potenzieller Kunde von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] ein Fahrrad kaufen wird. Wenn Sie mit Mining Strukturen und deren Rolle in Data Mining nicht vertraut sind, finden Sie weitere Informationen unter [Mining Strukturen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
 Die Bike Buyer-Mining Struktur, die Sie in dieser Lektion erstellen, unterstützt das Hinzufügen von Mining Modellen, die [auf dem Microsoft](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Decision Trees](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)-Algorithmus basieren. In späteren Lektionen untersuchen Sie mithilfe der Clustering-Miningmodelle verschiedene Möglichkeiten zum Gruppieren von Kunden und verwenden Entscheidungsstruktur-Miningmodelle, um vorherzusagen, ob ein potenzieller Kunde ein Fahrrad kaufen wird oder nicht.  
  
## <a name="create-mining-structure-statement"></a>CREATE MINING STRUCTURE-Anweisung  
 Zum Erstellen einer Mining Struktur verwenden Sie die Anweisung [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) . Der in der Anweisung enthaltene Code umfasst folgende Abschnitte:   
  
-   Benennen der-Struktur.  
  
-   Definieren der Schlüssel Spalte.  
  
-   Definieren der Miningspalten  
  
-   Definieren eines optionalen Test-Datasets  
  
 Es folgt ein allgemeines Beispiel für die CREATE MINING STRUCTURE-Anweisung:  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
(  
    <key column>,  
    <mining structure columns>  
)   
WITH HOLDOUT (<holdout specifier>)  
```  
  
 Die erste Codezeile definiert den Namen der Struktur:  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
```  
  
 Weitere Informationen zum Benennen eines Objekts in Data Mining-Erweiterungen (DMX) finden Sie unter Bezeichner [&#40;DMX-&#41;](/sql/dmx/identifiers-dmx).  
  
 Die nächste Codezeile definiert die Schlüsselspalte für die Miningstruktur, die eine Entität in den Quelldaten eindeutig identifiziert:  
  
```  
<key column>,  
```  
  
 In der Miningstruktur, die Sie erstellen, definiert der Kundenbezeichner `CustomerKey` eine Entität in den Quelldaten.  
  
 Mit der nächsten Codezeile werden die Miningspalten definiert, die von den Miningmodellen verwendet werden, die der Miningstruktur zugeordnet sind:  
  
```  
<mining structure columns>  
```  
  
 Mithilfe der diskretisieren-Funktion können Sie \<in Mining Struktur Spalten> kontinuierliche Spalten mithilfe der folgenden Syntax diskretisieren:  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 Weitere Informationen zum Diskretisieren von Spalten finden Sie unter [Diskretisierungsmethoden &#40;Data Mining-&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md). Weitere Informationen zu den Typen von Mining Struktur Spalten, die Sie definieren können, finden Sie unter [Mining Struktur Spalten](../../2014/analysis-services/data-mining/mining-structure-columns.md).  
  
 In der letzten Codezeile wird eine optionale Partition in der Miningstruktur definiert:  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 Sie geben einen Teil der Daten an, die zum Testen von Miningmodellen verwendet werden sollen, die mit der Struktur verknüpft sind. Die übrigen Daten werden zum Trainieren der Modelle verwendet. Standardmäßig erstellt [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ein Test-Dataset, das 30 % aller Falldaten enthält. Sie fügen die Spezifikation hinzu, dass das Test-Dataset 30 % der Fälle bis zu einem Maximum von 1000 Fällen enthalten soll. Wenn 30 % der Fälle weniger sind als 1000, enthält das Test-Dataset den kleineren Wert.  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Erstellen Sie eine neue leere Abfrage.  
  
-   Ändern Sie die Abfrage, um die Mining Struktur zu erstellen.  
  
-   Ausführen der Abfrage  
  
## <a name="creating-the-query"></a>Erstellen einer Abfrage  
 Im ersten Schritt stellen Sie eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] her und erstellen eine neue DMX-Abfrage in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>So erstellen Sie eine neue DMX-Abfrage in SQL Server Management Studio  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Wählen Sie im Dialogfeld **Verbindung mit Server herstellen** unter **Servertyp**die Option **Analysis Services**aus. Geben `LocalHost`Sie unter **Server Name**den Namen ein, oder geben Sie den Namen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] der Instanz von ein, mit der Sie für diese Lektion eine Verbindung herstellen möchten. Klicken Sie auf **Verbinden**.  
  
3.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX** , um den **Abfrage-Editor** und eine neue, leere Abfrage zu öffnen.  
  
## <a name="altering-the-query"></a>Ändern der Abfrage  
 Im nächsten Schritt ändern Sie die oben beschriebene CREATE MINING STRUCTURE-Anweisung und erstellen die Bike Buyer-Miningstruktur.  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>So passen Sie die CREATE MINING STRUCTURE-Anweisung an  
  
1.  Kopieren Sie im Abfrage-Editor das allgemeine Beispiel der CREATE MINING STRUCTURE-Anweisung in die leere Abfrage.  
  
2.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining structure>]   
    ```  
  
     Durch:  
  
    ```  
    [Bike Buyer]  
    ```  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <key column>   
    ```  
  
     Durch:  
  
    ```  
    CustomerKey LONG KEY  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure columns>   
    ```  
  
     Durch:  
  
    ```  
    [Age] LONG DISCRETIZED(Automatic,10),  
    [Bike Buyer] LONG DISCRETE,  
    [Commute Distance] TEXT DISCRETE,  
    [Education] TEXT DISCRETE,  
    [Gender] TEXT DISCRETE,  
    [House Owner Flag] TEXT DISCRETE,  
    [Marital Status] TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Number Children At Home] LONG DISCRETE,  
    [Occupation] TEXT DISCRETE,  
    [Region] TEXT DISCRETE,  
    [Total Children]LONG DISCRETE,  
    [Yearly Income] DOUBLE CONTINUOUS  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    WITH HOLDOUT (holdout specifier>)  
    ```  
  
     Durch:  
  
    ```  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
    ```  
  
     Die gesamte Miningstrukturanweisung sollte jetzt wie folgt aussehen:  
  
    ```  
    CREATE MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key] LONG KEY,  
       [Age]LONG DISCRETIZED(Automatic,10),  
       [Bike Buyer] LONG DISCRETE,  
       [Commute Distance] TEXT DISCRETE,  
       [Education] TEXT DISCRETE,  
       [Gender] TEXT DISCRETE,  
       [House Owner Flag] TEXT DISCRETE,  
       [Marital Status] TEXT DISCRETE,  
       [Number Cars Owned]LONG DISCRETE,  
       [Number Children At Home]LONG DISCRETE,  
       [Occupation] TEXT DISCRETE,  
       [Region] TEXT DISCRETE,  
       [Total Children]LONG DISCRETE,  
       [Yearly Income] DOUBLE CONTINUOUS  
    )  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
  
    ```  
  
6.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
7.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `Bike Buyer Structure.dmx`.  
  
## <a name="executing-the-query"></a>Ausführen der Abfrage  
 Im letzten Schritt führen Sie die Abfrage aus. Nachdem eine Abfrage erstellt und gespeichert wurde, muss sie ausgeführt werden. Das bedeutet, die Anweisung muss ausgeführt werden, um auf dem Server eine Miningstruktur zu erstellen. Weitere Informationen zum Ausführen von Abfragen im Abfrage-Editor finden Sie unter [Datenbank-Engine-Abfrage-Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>So führen Sie die Abfrage aus  
  
1.  Klicken Sie im Abfrage-Editor auf der Symbolleiste auf **Ausführen**.  
  
     Der Status der Abfrage wird auf der Registerkarte **Nachrichten** unten im Abfrage-Editor angezeigt, nachdem die Ausführung der Anweisung abgeschlossen wurde. Die Meldung sollte Folgendes anzeigen:  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     Eine neue Struktur mit dem Namen **Bike Buyer** ist jetzt auf dem Server vorhanden.  
  
 In der nächsten Lektion fügen Sie der soeben erstellten Struktur Miningmodelle hinzu.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Hinzufügen von Miningmodellen zur Bike Buyer-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  
