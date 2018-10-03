---
title: 'Lektion 1: Erstellen der Market Basket-Miningstruktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: a817c8d1-aff4-42b4-b194-ad9cc1c60f35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: be8768c5d638904240cc1499a594b0d2c8a97aa7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128880"
---
# <a name="lesson-1-creating-the-market-basket-mining-structure"></a>Lektion 1: Erstellen der Market Basket-Miningstruktur
  In dieser Lektion erstellen Sie eine Miningstruktur, mit der sich vorhersagen lässt, welche [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]-Produkte ein Kunde tendenziell als Kombinationskauf erwirbt. Wenn Sie nicht mit Miningstrukturen und ihre Rolle beim Datamining vertraut sind, finden Sie unter [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
 Die Association-Miningstruktur, die Sie in dieser Lektion erstellen unterstützt das Hinzufügen von Miningmodellen, die basierend auf den [Microsoft Association-Algorithmus](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md). In späteren Lektionen verwenden Sie die Miningmodelle, um vorherzusagen, welche Produkttypen ein Kunde tendenziell als Kombinationskauf erwirbt. Dieses Verfahren wird als Warenkorbanalyse bezeichnet. So könnten Sie beispielsweise zu dem Ergebnis kommen, dass Kunden tendenziell gleichzeitig Mountainbikes, Fahrradreifen und Helme kaufen.  
  
 In dieser Lektion wird die Miningstruktur mithilfe von geschachtelten Tabellen definiert. Geschachtelte Tabellen werden deshalb verwendet, weil die Datendomäne, die durch die Struktur definiert wird, in zwei verschiedenen Quelltabellen enthalten ist. Weitere Informationen zu geschachtelten Tabellen finden Sie unter [geschachtelte Tabellen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).  
  
## <a name="create-mining-structure-statement"></a>CREATE MINING STRUCTURE-Anweisung  
 Verwenden Sie zum Erstellen einer Miningstruktur eine geschachtelte Tabelle enthält die [CREATE MINING STRUCTURE &#40;DMX&#41; ](/sql/dmx/create-mining-structure-dmx) Anweisung. Der in der Anweisung enthaltene Code umfasst folgende Abschnitte:   
  
-   Benennen der Struktur  
  
-   Definieren der Schlüsselspalte  
  
-   Definieren der miningspalten  
  
-   Definieren der Spalten der geschachtelten Tabellen  
  
 Es folgt ein allgemeines Beispiel für die CREATE MINING STRUCTURE-Anweisung:  
  
```  
CREATE MINING STRUCTURE [<Mining Structure Name>]  
(  
   <key column>,  
   <mining structure columns>,  
   <table columns>  
   (  <nested key column>,  
      <nested mining structure columns> )  
)  
  
```  
  
 Die erste Codezeile definiert den Namen der Struktur:  
  
```  
CREATE MINING STRUCTURE [Mining Structure Name]  
```  
  
 Informationen zum Benennen eines Objekts in DMX finden Sie unter [Bezeichner &#40;DMX&#41;](/sql/dmx/identifiers-dmx).  
  
 Die nächste Codezeile definiert die Schlüsselspalte für die Miningstruktur, die eine Entität in den Quelldaten eindeutig identifiziert:  
  
```  
<key column>  
```  
  
 Mit der nächsten Codezeile werden die Miningspalten definiert, die von den Miningmodellen verwendet werden, die der Miningstruktur zugeordnet sind:  
  
```  
<mining structure columns>  
```  
  
 Die nächsten Codezeilen definieren die Spalten der geschachtelten Tabellen:  
  
```  
<table columns>  
(  <nested key column>,  
   <nested mining structure columns> )  
```  
  
 Informationen zu den Arten von Miningstrukturspalten, die Sie definieren können, finden Sie unter [Miningstrukturspalten](../../2014/analysis-services/data-mining/mining-structure-columns.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] erstellt standardmäßig ein zu 30 % zurückgehaltenes Dataset für jede Miningstruktur. Wenn Sie jedoch DMX zum Erstellen einer Miningstruktur verwenden, müssen Sie das zurückgehaltene Dataset (falls gewünscht) manuell hinzufügen.  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Erstellen einer neuen leeren Abfrage  
  
-   Ändern der Abfrage, um die Miningstruktur zu erstellen  
  
-   Führen Sie die Abfrage  
  
## <a name="creating-the-query"></a>Erstellen einer Abfrage  
 Im ersten Schritt stellen Sie eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] her und erstellen eine neue DMX-Abfrage in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>So erstellen Sie eine neue DMX-Abfrage in SQL Server Management Studio  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  In der **Herstellen einer Verbindung mit Server** im Dialogfeld für **Servertyp**Option **Analysis Services**. In **Servernamen**, Typ `LocalHost`, oder den Namen der Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , die Sie für diese Lektion herstellen möchten. Klicken Sie auf **Verbinden**.  
  
3.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
## <a name="altering-the-query"></a>Ändern der Abfrage  
 Im nächsten Schritt ändern Sie die oben beschriebene CREATE MINING STRUCTURE-Anweisung und erstellen die Market Basket-Miningstruktur.  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>So passen Sie die CREATE MINING STRUCTURE-Anweisung an  
  
1.  Kopieren Sie im Abfrage-Editor, das allgemeine Beispiel der CREATE MINING STRUCTURE-Anweisung in die leere Abfrage.  
  
2.  Ersetzen Sie Folgendes:  
  
    ```  
    [mining structure name]   
    ```  
  
     durch:  
  
    ```  
    [Market Basket]  
    ```  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <key column>  
    ```  
  
     durch:  
  
    ```  
    OrderNumber TEXT KEY  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <table columns>  
    (  <nested key column>,  
       <nested mining structure columns> )  
    ```  
  
     durch:  
  
    ```  
    [Products] TABLE (  
        [Model] TEXT KEY  
    )  
    ```  
  
     Die TEXT KEY-Sprache gibt an, dass die Model-Spalte die Schlüsselspalte für die geschachtelte Tabelle ist.  
  
     Die gesamte Miningstrukturanweisung sollte jetzt wie folgt aussehen:  
  
    ```  
    CREATE MINING STRUCTURE [Market Basket] (  
        OrderNumber TEXT KEY,  
        [Products] TABLE (  
            [Model] TEXT KEY  
        )  
    )  
    ```  
  
5.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
6.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `Market Basket Structure.dmx`.  
  
## <a name="executing-the-query"></a>Ausführen der Abfrage  
 Im letzten Schritt führen Sie die Abfrage aus. Nachdem Sie eine Abfrage erstellt und gespeichert haben, muss sie (d. h. die Anweisung) ausgeführt werden, damit die Miningstruktur auf dem Server erstellt wird. Weitere Informationen zum Ausführen von Abfragen im Abfrage-Editor finden Sie unter [Datenbank-Engine-Abfrage-Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>So führen Sie die Abfrage aus  
  
-   Klicken Sie im Abfrage-Editor auf der Symbolleiste **Execute**.  
  
     Der Status der Abfrage wird angezeigt, der **Nachrichten** Registerkarte am unteren Rand des Abfrage-Editors nach Abschluss der Ausführung die Anweisung. Die Meldung sollte Folgendes anzeigen:  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     Eine neue Struktur mit dem Namen **Warenkorbanalyse** jetzt auf dem Server vorhanden ist.  
  
 In der nächsten Lektion fügen Sie der soeben erstellten Market Basket-Miningstruktur Miningmodelle hinzu.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Hinzufügen von Miningmodellen zur Market Basket-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
  
  
