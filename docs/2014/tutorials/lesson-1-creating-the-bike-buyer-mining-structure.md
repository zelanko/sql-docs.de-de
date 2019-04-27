---
title: 'Lektion 1: Erstellen der Bike Buyer-Miningstruktur | Microsoft-Dokumentation'
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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62678503"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a>Lektion 1: Erstellen der Bike Buyer-Miningstruktur
  In dieser Lektion erstellen Sie eine Miningstruktur, mit der sich vorhersagen lässt, ob ein potenzieller Kunde von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] ein Fahrrad kaufen wird. Wenn Sie nicht mit Miningstrukturen und ihre Rolle beim Datamining vertraut sind, finden Sie unter [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
 Die Bike Buyer-Miningstruktur, die Sie in dieser Lektion erstellen unterstützt das Hinzufügen von Miningmodellen, die basierend auf den [Microsoft Clustering-Algorithmus](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft Decision Trees-Algorithmus](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md). In späteren Lektionen untersuchen Sie mithilfe der Clustering-Miningmodelle verschiedene Möglichkeiten zum Gruppieren von Kunden und verwenden Entscheidungsstruktur-Miningmodelle, um vorherzusagen, ob ein potenzieller Kunde ein Fahrrad kaufen wird oder nicht.  
  
## <a name="create-mining-structure-statement"></a>CREATE MINING STRUCTURE-Anweisung  
 Um eine Miningstruktur zu erstellen, verwenden Sie die [CREATE MINING STRUCTURE &#40;DMX&#41; ](/sql/dmx/create-mining-structure-dmx) Anweisung. Der in der Anweisung enthaltene Code umfasst folgende Abschnitte:   
  
-   Benennen die Struktur.  
  
-   Definieren der Schlüsselspalte.  
  
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
  
 Informationen zum Benennen eines Objekts in Data Mining Extensions (DMX) finden Sie unter [Bezeichner &#40;DMX&#41;](/sql/dmx/identifiers-dmx).  
  
 Die nächste Codezeile definiert die Schlüsselspalte für die Miningstruktur, die eine Entität in den Quelldaten eindeutig identifiziert:  
  
```  
<key column>,  
```  
  
 In der Miningstruktur, die Sie erstellen, definiert der Kundenbezeichner `CustomerKey` eine Entität in den Quelldaten.  
  
 Mit der nächsten Codezeile werden die Miningspalten definiert, die von den Miningmodellen verwendet werden, die der Miningstruktur zugeordnet sind:  
  
```  
<mining structure columns>  
```  
  
 Können Sie die DISCRETIZE-Funktion in \<Miningstrukturspalten > kontinuierliche Spalten Diskretisieren, mithilfe der folgenden Syntax:  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 Weitere Informationen zur Diskretisierung von Spalten finden Sie unter [Diskretisierungsmethoden &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md). Weitere Informationen zu den Arten von Miningstrukturspalten, die Sie definieren können, finden Sie unter [Miningstrukturspalten](../../2014/analysis-services/data-mining/mining-structure-columns.md).  
  
 In der letzten Codezeile wird eine optionale Partition in der Miningstruktur definiert:  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 Sie geben einen Teil der Daten an, die zum Testen von Miningmodellen verwendet werden sollen, die mit der Struktur verknüpft sind. Die übrigen Daten werden zum Trainieren der Modelle verwendet. Standardmäßig erstellt [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ein Test-Dataset, das 30 % aller Falldaten enthält. Sie fügen die Spezifikation hinzu, dass das Test-Dataset 30 % der Fälle bis zu einem Maximum von 1000 Fällen enthalten soll. Wenn 30 % der Fälle weniger sind als 1000, enthält das Test-Dataset den kleineren Wert.  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Erstellen einer neuen leeren Abfrage.  
  
-   Ändern Sie die Abfrage zum Erstellen der Miningstruktur an.  
  
-   Führen Sie die Abfrage an.  
  
## <a name="creating-the-query"></a>Erstellen einer Abfrage  
 Im ersten Schritt stellen Sie eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] her und erstellen eine neue DMX-Abfrage in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>So erstellen Sie eine neue DMX-Abfrage in SQL Server Management Studio  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  In der **Herstellen einer Verbindung mit Server** im Dialogfeld für **Servertyp**Option **Analysis Services**. In **Servernamen**, Typ `LocalHost`, oder geben Sie den Namen der Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , die Sie für diese Lektion herstellen möchten. Klicken Sie auf **Verbinden**.  
  
3.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX** zum Öffnen der **Abfrage-Editor**und eine neue, leere Abfrage.  
  
## <a name="altering-the-query"></a>Ändern der Abfrage  
 Im nächsten Schritt ändern Sie die oben beschriebene CREATE MINING STRUCTURE-Anweisung und erstellen die Bike Buyer-Miningstruktur.  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>So passen Sie die CREATE MINING STRUCTURE-Anweisung an  
  
1.  Kopieren Sie im Abfrage-Editor das allgemeine Beispiel der CREATE MINING STRUCTURE-Anweisung in die leere Abfrage.  
  
2.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining structure>]   
    ```  
  
     durch:  
  
    ```  
    [Bike Buyer]  
    ```  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <key column>   
    ```  
  
     durch:  
  
    ```  
    CustomerKey LONG KEY  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <mining structure columns>   
    ```  
  
     durch:  
  
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
  
     durch:  
  
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
  
6.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
7.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `Bike Buyer Structure.dmx`.  
  
## <a name="executing-the-query"></a>Ausführen der Abfrage  
 Im letzten Schritt führen Sie die Abfrage aus. Nachdem eine Abfrage erstellt und gespeichert wurde, muss sie ausgeführt werden. Das bedeutet, die Anweisung muss ausgeführt werden, um auf dem Server eine Miningstruktur zu erstellen. Weitere Informationen zum Ausführen von Abfragen im Abfrage-Editor finden Sie unter [Datenbank-Engine-Abfrage-Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>So führen Sie die Abfrage aus  
  
1.  Klicken Sie im Abfrage-Editor auf der Symbolleiste **Execute**.  
  
     Der Status der Abfrage wird angezeigt, der **Nachrichten** Registerkarte am unteren Rand des Abfrage-Editors nach Abschluss der Ausführung die Anweisung. Die Meldung sollte Folgendes anzeigen:  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     Eine neue Struktur mit dem Namen **Bike Buyer** jetzt auf dem Server vorhanden ist.  
  
 In der nächsten Lektion fügen Sie der soeben erstellten Struktur Miningmodelle hinzu.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Hinzufügen von Miningmodellen zur Bike Buyer-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  
