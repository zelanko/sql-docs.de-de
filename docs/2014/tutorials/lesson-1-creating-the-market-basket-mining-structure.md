---
title: 'Lektion 1: Erstellen der Market Basket-Mining Struktur | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a817c8d1-aff4-42b4-b194-ad9cc1c60f35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6a6e123e525512a72d70bcc8ca2eba549d1347e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62676279"
---
# <a name="lesson-1-creating-the-market-basket-mining-structure"></a>Lektion 1: Erstellen der Market Basket-Miningstruktur
  In dieser Lektion erstellen Sie eine Miningstruktur, mit der sich vorhersagen lässt, welche [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]-Produkte ein Kunde tendenziell als Kombinationskauf erwirbt. Wenn Sie mit Mining Strukturen und deren Rolle in Data Mining nicht vertraut sind, finden Sie weitere Informationen unter [Mining Strukturen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
 Die Association-Mining Struktur, die Sie in dieser Lektion erstellen, unterstützt das Hinzufügen von Mining Modellen auf der Grundlage des [Microsoft Association-Algorithmus](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md). In späteren Lektionen verwenden Sie die Miningmodelle, um vorherzusagen, welche Produkttypen ein Kunde tendenziell als Kombinationskauf erwirbt. Dieses Verfahren wird als Warenkorbanalyse bezeichnet. So könnten Sie beispielsweise zu dem Ergebnis kommen, dass Kunden tendenziell gleichzeitig Mountainbikes, Fahrradreifen und Helme kaufen.  
  
 In dieser Lektion wird die Miningstruktur mithilfe von geschachtelten Tabellen definiert. Geschachtelte Tabellen werden deshalb verwendet, weil die Datendomäne, die durch die Struktur definiert wird, in zwei verschiedenen Quelltabellen enthalten ist. Weitere Informationen zu den Tabellen finden Sie unter [Tabellen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).  
  
## <a name="create-mining-structure-statement"></a>CREATE MINING STRUCTURE-Anweisung  
 Um eine Mining Struktur zu erstellen, die eine Tabellen Tabelle enthält, verwenden Sie die Anweisung [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) . Der in der Anweisung enthaltene Code umfasst folgende Abschnitte:   
  
-   Benennen der Struktur  
  
-   Definieren der Schlüsselspalte  
  
-   Definieren der Mining Spalten  
  
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
  
 Weitere Informationen zum Benennen eines Objekts in DMX finden Sie unter Bezeichner [&#40;DMX-&#41;](/sql/dmx/identifiers-dmx).  
  
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
  
 Informationen zu den Typen von Mining Struktur Spalten, die Sie definieren können, finden Sie unter [Mining Struktur Spalten](../../2014/analysis-services/data-mining/mining-structure-columns.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] erstellt standardmäßig ein zu 30 % zurückgehaltenes Dataset für jede Miningstruktur. Wenn Sie jedoch DMX zum Erstellen einer Miningstruktur verwenden, müssen Sie das zurückgehaltene Dataset (falls gewünscht) manuell hinzufügen.  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Erstellen einer neuen leeren Abfrage  
  
-   Ändern der Abfrage, um die Miningstruktur zu erstellen  
  
-   Ausführen der Abfrage  
  
## <a name="creating-the-query"></a>Erstellen einer Abfrage  
 Im ersten Schritt stellen Sie eine Verbindung zu einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] her und erstellen eine neue DMX-Abfrage in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>So erstellen Sie eine neue DMX-Abfrage in SQL Server Management Studio  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Wählen Sie im Dialogfeld **Verbindung mit Server herstellen** unter **Servertyp**die Option **Analysis Services**aus. Geben Sie unter **Server Name**den Namen ein, oder geben `LocalHost`Sie den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Namen der Instanz von ein, mit der Sie für diese Lektion eine Verbindung herstellen möchten. Klicken Sie auf **Verbinden**.  
  
3.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
## <a name="altering-the-query"></a>Ändern der Abfrage  
 Im nächsten Schritt ändern Sie die oben beschriebene CREATE MINING STRUCTURE-Anweisung und erstellen die Market Basket-Miningstruktur.  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>So passen Sie die CREATE MINING STRUCTURE-Anweisung an  
  
1.  Kopieren Sie im Abfrage-Editor das allgemeine Beispiel der CREATE MINING STRUCTURE-Anweisung in die leere Abfrage.  
  
2.  Ersetzen Sie Folgendes:  
  
    ```  
    [mining structure name]   
    ```  
  
     Durch:  
  
    ```  
    [Market Basket]  
    ```  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <key column>  
    ```  
  
     Durch:  
  
    ```  
    OrderNumber TEXT KEY  
    ```  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    <table columns>  
    (  <nested key column>,  
       <nested mining structure columns> )  
    ```  
  
     Durch:  
  
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
  
5.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
6.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `Market Basket Structure.dmx`.  
  
## <a name="executing-the-query"></a>Ausführen der Abfrage  
 Im letzten Schritt führen Sie die Abfrage aus. Nachdem Sie eine Abfrage erstellt und gespeichert haben, muss sie (d. h. die Anweisung) ausgeführt werden, damit die Miningstruktur auf dem Server erstellt wird. Weitere Informationen zum Ausführen von Abfragen im Abfrage-Editor finden Sie unter [Datenbank-Engine-Abfrage-Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>So führen Sie die Abfrage aus  
  
-   Klicken Sie im Abfrage-Editor auf der Symbolleiste auf **Ausführen**.  
  
     Der Status der Abfrage wird auf der Registerkarte **Nachrichten** unten im Abfrage-Editor angezeigt, nachdem die Ausführung der Anweisung abgeschlossen wurde. Die Meldung sollte Folgendes anzeigen:  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     Eine neue Struktur mit dem Namen **Market Basket** ist jetzt auf dem Server vorhanden.  
  
 In der nächsten Lektion fügen Sie der soeben erstellten Market Basket-Miningstruktur Miningmodelle hinzu.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Hinzufügen von Miningmodellen zur Market Basket-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
  
  
